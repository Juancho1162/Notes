#ai #aprendizaje_automático_II #ai/ml 

##### **Objectives**
- Understand non-linear separability.
- Understand the fundamentals of kernel trick from a computational point of view.
- Know the math behind the kernel trick.
- Learn how to define the kernels in order to be able to transform datasets with non-linear separability.

#### Linear Separability
Let $X_0$ and $X_1$ be two sets of points in an n-dimensional Euclidean space. Then $X_0$ and $X_1$ are linearly separable if there exist ($n+1$) real numbers ($w_1, w_2, ..., w_n, k$) such that:
$$
\begin{gather}
\text{Every point, } x \in X_0 \text{ satisfies }
\sum _{i=1}^{n} w_i x_i > k \\

\text{and every point } x \in X_1 \text{ satisfies  } \sum_{i=1}^{n}w_i x_i <k, \text{ where } x_i \text{ is the $i$-th component of x.} \hspace{3em}(1)\\ 
\end{gather}

$$

##### **Example**
Let's say we are working with vectors (to represent the points), in 2-dim Space. We have two sets of vectors (or points), $P_1$ and $P_2$.
$$
\begin{gather}
P_1=\{ v_1, v_2, ...,v_m \}\\
P_2=\{ \hat{v_1}, \hat{v_2}, ...,\hat{v_b}\}
\end{gather}
$$
We are working in an 2-Dim Euclidean space, our basis would be:
$$
B={e_1,e_2}
$$
Let's clarify the notation:
$$
\begin{gather}
p^{i}_{j,k} \text{ ,($i$) represents the set, ($j$) the index of the point,}\\
\text{($k$) the index of the weight corresponding to each vector of the basis}
\end{gather}
$$

So in terms of the basis:
$$
\begin{gather}
v_1 = p^{1}_{1,1}e_1 + p^{1}_{1,2}e_2\\
\hat{v_1} = p^{2}_{1,1}e_1 + p^{2}_{1,2}e_1 
\end{gather}
$$
If we assume the canonical orthonormal basis ($e_1 = (1,0); e_2 = (0,1)$ we can simplify so
we would need to satisfy:
$$
\begin{gather}
\forall v_j \in P_1 \exists k\in \mathbb{R} / \sum_{i=1}^{2}w_ip^{1}_{j,i} > k \text{ and }\\
\forall \hat{v_j} \in P_2; \sum_{i=1}^{2}w_ip^{2}_{j,i} < k
\end{gather}
$$
This system of equations will have $m+b$ inequalities (the total number of points). We could solve them and find if that k exists.

 With the help of GPT4 I created this code to brute force a simple case.
 
```python
def brute_force_separability(group1, group2):
    # Define the range for the weights and k
    weight_range = np.arange(-1, 1.1, 0.1)
    k_range = np.arange(-10, 10.1, 0.1)
    
    for w1 in weight_range: # BAD INDENTATION BECAUSE OF VISUALIZATION!
	  for w2 in weight_range:
	    for k in k_range:
            # Check the conditions for all points in group1 and group2
            condition1 = all(np.dot([w1, w2], point) > k for point in group1)
            condition2 = all(np.dot([w1, w2], point) < k for point in group2)
            # If both conditions are satisfied, we've found a separating line
            if condition1 and condition2:
                return True, w1, w2, k
            else:
                condition3 = all(np.dot([w1, w2], point) < k for point in group1)
                condition4 = all(np.dot([w1, w2], point) > k for point in group2)
                if condition3 and condition4:
	                return True, w1, w2, k
                    
                    
    # If we finish the loop without returning, no separating line was found
	return False, None, None, None

# Example groups of points
group1 = np.array([[1, 2], [2, 3], [3, 4]])
group2 = np.array([[5, 6], [6, 7], [7, 8]])

# Perform the brute force search
separable, w1, w2, k = brute_force_separability(group1, group2)

if separable:
    print(f"Groups are linearly separable with w1={w1}, w2={w2}, and k={k}.")
    plot_hyperplane(group1, group2, w1, w2, k)
else:
    print("No hyperplane found, thus no corrected plot.")```

Also this function to plot it:
```python
def plot_hyperplane(group1, group2, w1, w2, k):
    """
    Plot the groups and the separating hyperplane based on the provided weights and k.
    """
    # Check if w2 is not 0 to avoid division by zero
    if w2 == 0:
        print("w2 cannot be 0 for this plotting method.")
        return

    # Generate x values based on the range of all points
    x_values = np.linspace(min(np.min(group1[:,0]), np.min(group2[:,0])), 
                           max(np.max(group1[:,0]), np.max(group2[:,0])), 100)
    # Calculate y values for the hyperplane: y = (-w1/w2)x - (k/w2)
    y_values = (-w1 / w2) * x_values + (k / w2)
    
    # Plot the points
    plt.figure(figsize=(8, 6))
    plt.scatter(group1[:, 0], group1[:, 1], color='blue', label='Group 1')
    plt.scatter(group2[:, 0], group2[:, 1], color='red', label='Group 2')
    
    # Plot the hyperplane
    plt.plot(x_values, y_values, label='Separating Hyperplane', color='green')
    
    # Label the plot
    plt.xlabel('x1')
    plt.ylabel('x2')
    plt.legend()
    plt.grid(True)
    plt.title('Generalized Linear Separability')
    plt.show()
```

![[l_separability.png]]

##### **Easier example**
In order to gain more intuition of the mathematical operations, let's consider 2 vectors in 2D:
$$
\begin{gather}
\vec{v_1} = 1e_1+2e_2\\
\vec{v_2}= 5e_1+4e_2
\end{gather}
$$
If we want to check if that 2 points or vectors are linearly separable, we have to find ($\vec{w}, k$) or such that:
$$
\begin{gather}
\vec{w} = w_1e_1+w_2e_2\\
\vec{w}\cdot \vec{v_1}= 1w_1+2w_2 < k\\
\vec{w}\cdot \vec{v_2}= 5w_1+4w_2 > k
\end{gather}
$$
It is trivial that ($w_1 = 1, w_2 = 1, k =5$) works. That conforms an hyperplane:
$$
\begin{gather}
e_1+e_2=5\\
\text{Using "normal" notation, }x+y = 5\\
y = 5-x
\end{gather}
$$
And we can see that these 2 points are linearly separable:
![[l_separability_2.png]]
When we don't have this linear separability we can choose 2 options:
- Use/create a model that is able to separate non-linear data. This is the example of neural networks.
- Transform the data in order to make it linearly separable. In this approach we can use **the kernel trick**.
#### The kernel trick





#### References
- Author1, Author2, Author3. **Python Machine Learning**. 
- Wikipedia contributors. (2024). **Linear separability**. Retrieved from https://en.wikipedia.org/wiki/Linear_separability
-  Wikipedia contributors. (2024). **Kernel method**. Retrieved from https://en.wikipedia.org/wiki/Kernel_method.
- Private notes corresponding to my university subject called "Aprendizaje Automático II".


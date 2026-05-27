projection is basically splitting vector \(u\) into two components:

a component from vector \(u\) which is parallel to vector \(v\)

and

a component from vector \(u\) which is

$$
90^\circ
$$

(perpendicular) to vector \(v\)

so we get two components of \(u\):

- first one is parallel to projected vector
- another one is perpendicular

$$
(90^\circ)
$$

to vector \(v\)

how to find them?

first component is formula

$$
\left( \frac{u \cdot v}{\|v\|^2} \right) v
$$

\(u \cdot v\) is dot product

$$
u_1v_1 + u_2v_2
$$

\(\|v\|^2\) is length of vector under square root, squared so

$$
\left( \sqrt{v_1^2 + v_2^2} \right)^2
$$

put into the formula

$$
\left( \frac{u \cdot v}{\|v\|^2} \right)
$$

and multiply by vector \(v\) so you multiply the vectors elements with the number you got and that is component \(w_1\)

\(w_2\) is \(u - w_1\) so vector \(u\) minus component \(w_1\), so subtract to get vector

$$
(u_1 - w_{1,1},\ u_2 - w_{1,2})
$$

this component is \(90^\circ\) (perpendicular) to vector \(v\)

we need only these \(90^\circ\) components since we are making orthogonal basis, we need these vectors

gram schmidt is just doing this same projection thing multiple times

start with vectors \(v_1, v_2, v_3\) (input, not orthogonal, just linearly independent)

goal:
\(u_1, u_2, u_3\) all perpendicular to each other (orthogonal basis)

step 1:

$$
u_1 = v_1
$$

nothing to do, first input becomes first orthogonal vector

step 2: plug into your projection formula with

$$
u = v_2,\quad v = u_1
$$

$$
w_1 =
\left(
\frac{v_2 \cdot u_1}{\|u_1\|^2}
\right)
u_1
$$

parallel to \(u_1\), throw away

$$
w_2 = v_2 - w_1
$$

perpendicular to \(u_1\), keep

$$
u_2 = w_2
$$

now \(u_2\) is perpendicular to \(u_1\), exactly what we wanted

step 3:

\(v_3\) has to be made perpendicular to BOTH \(u_1\) and \(u_2\) so subtract TWO projections, not one

$$
\text{proj\_on\_}u_1 =
\left(
\frac{v_3 \cdot u_1}{\|u_1\|^2}
\right)
u_1
$$

$$
\text{proj\_on\_}u_2 =
\left(
\frac{v_3 \cdot u_2}{\|u_2\|^2}
\right)
u_2
$$

$$
u_3 = v_3 - \text{proj\_on\_}u_1 - \text{proj\_on\_}u_2
$$

what remains after cutting both shadows is perpendicular to both \(u_1\) and \(u_2\)

general formula for step \(k\):

$$
u_k =
v_k
-
\left(
\frac{v_k \cdot u_1}{\|u_1\|^2}
\right)
u_1
-
\left(
\frac{v_k \cdot u_2}{\|u_2\|^2}
\right)
u_2
-
\cdots
-
\left(
\frac{v_k \cdot u_{k-1}}{\|u_{k-1}\|^2}
\right)
u_{k-1}
$$

in words:

take new input vector, subtract its projection onto every previous orthogonal vector, what's left is the new orthogonal vector

important catch:

project onto \(u_i\) (already orthogonalized), NOT onto \(v_i\) (originals)

this is the most common mistake

by step 3 you do NOT touch \(v_1\) or \(v_2\) anymore, only \(u_1\) and \(u_2\)

check at the end:

$$
u_1 \cdot u_2 = 0
$$

$$
u_1 \cdot u_3 = 0
$$

$$
u_2 \cdot u_3 = 0
$$

if all dot products are zero, gram schmidt worked

orthoNORMAL basis (length 1):

$$
e_k = \frac{u_k}{\|u_k\|}
$$

divide each orthogonal vector by its own length, done

now \(e_1, e_2, e_3\) are all perpendicular AND length \(1\)

summary:

gram schmidt = repeated projection

keep only the perpendicular parts (the \(w_2\) from your notes)

each new orthogonal vector = original input minus shadows on everything you already built

that's the whole algorithm

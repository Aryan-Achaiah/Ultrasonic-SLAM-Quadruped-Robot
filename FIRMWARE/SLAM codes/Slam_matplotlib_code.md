\#You can paste this in online matplotlib compilier and run it for the 2d-mapped output



**Matplotlib**







import matplotlib.pyplot as plt



distance = \[

25.33,

23.86,

21.06,

19.43,

22.96,

19.76,

19.76,

22.96,

22.96,

4.56,

5.78,

25.67,

6.12,

8.34,

5.63

]



x = \[0] \* len(distance)

y = distance



plt.figure(figsize=(5,8))

plt.scatter(x, y, s=80)



plt.xlabel("Robot Center")

plt.ylabel("Distance (cm)")

plt.title("Detected Obstacle")



plt.grid(True)

plt.axis("equal")



plt.show()


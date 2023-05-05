# Codigos
Codigos Python
# Bibliotecas necessárias
import numpy as np # biblioteca para trabalhar com arrays
import matplotlib.pyplot as plt # biblioteca para desenhar gráficos
Nx = 10 # número de pontos na direção x
Ny = 20 # número de pontos na direção y

# limites inferior e superior e x e y
xmin, xmax = (0, 1) 
ymin, ymax = (-1, 1)

# criando os pontos x e y
x = np.linspace(xmin, xmax, Nx)
y = np.linspace(ymin, ymax, Ny)

# x e y são vetores lineares. Precisamos combiná-los em uma malha de pontos
X,Y = np.meshgrid(x,y) # função meshgrid cria a malha
plt.plot(X,Y,'b.') # 'b.' faz plotar pontinhos azuis (b de blue)
print()
def func(X,Y):
    return X*Y**2

Z = func(X,Y)

ax = plt.axes(projection = '3d') # criamos um objeto ax (eixo) indicando que a projeção é em 3d
ax.plot_surface(X,Y,Z, cmap="plasma") # plot_surface cria o gráfico. cmap é o mapa de cores. Tente cmap="jet"
ax.set_xlabel("x")
ax.set_ylabel("y")
ax.set_zlabel(r"$z = f(x,y)$")

%matplotlib notebook 
# Este comando torna o gráfico interativo, mas somente no jupyter-notebook.
# Não deve ser usado no editor (Spyder, Pycharm, etc.)
x = np.linspace(-1,1.5,101)
y = np.linspace(-1,1.5,101)
X,Y = np.meshgrid(x,y)

Z = X**2 + Y**2 # não é obrigatório definir uma função, você pode calcular Z diretamente.
W = 0.5*(X + Y) + 1

ax = plt.axes(projection = '3d') 
ax.plot_surface(X,Y, np.where( Z < W, Z, None) ) # onde Z for menor que W, retorna Z. Onde não for, retorna nada.
ax.plot_surface(X,Y, np.where( W > Z, W, None) ) # onde W for maior que Z, retorna W. Onde não for, retorna nada.
ax.set_xlabel("x")
ax.set_ylabel("y")
# Outros exemplos de uso da função np.where:
n = np.array( range(10) )
print(n)
print( np.where( n % 2 == 0, "par", "ímpar" ) )
print( np.where( n < 5, n**2, -n ) )

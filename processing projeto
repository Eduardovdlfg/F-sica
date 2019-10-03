"""
Grupo: Eduardo Vianna, Marina Vaz e Matheus Edson
"""
# (unidades 1 s de simulação = 10^7 s na vida real)
# (1 pixel = 10^9 m)
# (1 unidade de massa = 10^22 kg)
#Tamanhos dos astros fora de escala para preservar a facilidade da visualização da animação.
t0     = millis()/1000.0 #marcação inicial do tempo
Sol    = PVector(500,500) #posição inicial do Sol
Marte  = PVector(500+230,500) #posição inicial de marte
v      = PVector(0,-240) #Velocidade inicial de Marte, considerando a trajetória semelhante a uma circunferência pela excentricidade ser 0.093
r      = PVector(Marte.x-Sol.x,Marte.y-Sol.y) #vetor que liga Marte ao Sol
MSol   = 2*(10**8) #massa do Sol
MMarte = 62 #massa de Marte
G      = 0.067 #constante da gravitação universal
photo = loadImage("https://i1.wp.com/myphuket-holiday.com/wp-content/uploads/2014/12/sun.png?ssl=1.png")


def longe():
    textSize(20)
    global t0,Sol,Marte,v,r,MSol,MMarte,G
    r      = Sol-Marte
    d      = r.mag()
    F      = r*(MSol*MMarte*G/(d**3)) #A partir da Lei de Gravitação Universal de Newton
    t      = millis()/1000.0
    dt     = t-t0 #a variação de tempo usada no método de Euler
    t0     = t
    Marte  = Marte +v*dt #Marte se movimenta
    a      = F/MMarte #acel. de Marte
    v      = v + a*dt  #velocidade de marte se altera
    #Plotando as imagens onde os astros devem estar:
    background(0)
    fill(255,100,10)
    image(photo, Sol.x-163, Sol.y-140)
    fill(255)
    text("Sol",500,410)
    fill(255,100,50)
    ellipse(Marte.x,Marte.y,10,10)
    fill(255)
    text("Marte",Marte.x,Marte.y - 50)
    
# (unidades 1 s de simulação = 10^4 s na vida real)
# (1 pixel = 10^5 m)
# (1 unidade de massa = 10^15 kg)
#Tamanhos dos astros fora de escala para preservar a facilidade da visualização da animação.
t0     = millis()/1000.0 #marcação inicial de tempo
Martep = PVector(500,500) #posição fixa de Marte
MMartep= 6.4*(10**8) #Massa de Marte
Fobos  = PVector(500-94,500) #posição de Fobos
Deimos = PVector(500,500-235) #posição de Deimos
vfobos = PVector(0,197) #vel. inicial de Fobos
vdeimos= PVector(134,0) #vel. inicial de Deimos
rfobos = Marte - Fobos #vetor que liga Fobos a Marte
rdeimos= Marte - Deimos #vetor que lida Deimos à Marte
Mfobos = 10.8 #massa de Fobos
Mdeimos= 1.4 #massa de Deimos
Gperto=0.0067 #constande da Gravitação Universal de Newton 
def perto():
    textSize(20)
    global t0,Fobos,Deimos,vfobos,vdeimos,rfobos,rdeimos,MMarte,Mfobos,Mdeimos,Gperto,Martep,MMartep
    rfobos  = Martep-Fobos    
    dfobos  = rfobos.mag()
    Ffobos  = rfobos*(Mfobos*MMartep*Gperto/(dfobos**3)) #Força que Marte atrai Fobos
    rdeimos = Martep-Deimos
    ddeimos = rdeimos.mag()
    Fdeimos = rdeimos*(Mdeimos*MMartep*Gperto/(ddeimos**3)) #Força que Marte atrai Deimos
    t       = millis()/1000.0
    dt      = t-t0 #variação de tempo usada no método de Euler nesta função
    t0      = t
    adeimos = Fdeimos/Mdeimos #acel. de Deimos
    vdeimos = vdeimos + adeimos*dt #vel. de deimos se altera
    Deimos  = Deimos + vdeimos*dt #posição de Deimos se altera
    afobos  = Ffobos/Mfobos #acel de Fobos
    vfobos  = vfobos + afobos*dt #vel. de Fobos se altera
    Fobos   = Fobos +vfobos*dt #posição de Fobos se altera
    #Os desenhos dos astros propriamente:
    background(0)
    fill(200)
    ellipse(Fobos.x,Fobos.y,20,20)
    fill(255)
    text("Fobos",Fobos.x,Fobos.y-50)

    fill(255,200,200)
    ellipse(Deimos.x,Deimos.y,10,10)
    fill(255)
    text("Deimos",Deimos.x,Deimos.y-30)

    fill(255,200,100)
    ellipse(Martep.x,Martep.y,80,80)
    fill(255)
    text("Marte",Martep.x,Martep.y-100)

def setup():
    size(1000,1000)
    background(0)
visao=longe #no início observamos o Sol e Marte
def keyPressed():
    #desta forma alteramos nossa perspectiva
    global perto,visao,longe
    if visao==longe:
        visao=perto
    else:
        visao=longe
    
def draw():
    global visao,longe,perto
    visao()

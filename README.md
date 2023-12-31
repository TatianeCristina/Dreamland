# Dreamland
Viva a maior experiência de suas vidas
import pygame
import random

# Inicialização do Pygame
pygame.init()

# Definição das cores
PRETO = (0, 0, 0)
BRANCO = (255, 255, 255)
VERMELHO = (255, 0, 0)
VERDE = (0, 255, 0)
AZUL = (0, 0, 255)

# Definição das dimensões da tela
largura_tela = 800
altura_tela = 600

# Criação da tela
tela = pygame.display.set_mode((largura_tela, altura_tela))
pygame.display.set_caption("Dreamland - O Jogo")

# Variáveis do jogo
clock = pygame.time.Clock()
pontos = 0

# Classe do jogador
class Jogador(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        self.image = pygame.Surface([50, 50])
        self.image.fill(VERMELHO)
        self.rect = self.image.get_rect()
        self.rect.x = largura_tela // 2
        self.rect.y = altura_tela // 2

    def update(self):
        # Movimento do jogador com as teclas de seta
        keys = pygame.key.get_pressed()
        if keys[pygame.K_UP]:
            self.rect.y -= 5
        if keys[pygame.K_DOWN]:
            self.rect.y += 5
        if keys[pygame.K_LEFT]:
            self.rect.x -= 5
        if keys[pygame.K_RIGHT]:
            self.rect.x += 5

# Classe dos inimigos
class Inimigo(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        self.image = pygame.Surface([30, 30])
        self.image.fill(AZUL)
        self.rect = self.image.get_rect()
        self.rect.x = random.randrange(largura_tela - self.rect.width)
        self.rect.y = random.randrange(altura_tela - self.rect.height)

    def update(self):
        # Movimento aleatório dos inimigos
        self.rect.x += random.randint(-3, 3)
        self.rect.y += random.randint(-3, 3)

# Classe dos itens
class Item(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        self.image = pygame.Surface([20, 20])
        self.image.fill(VERDE)
        self.rect = self.image.get_rect()
        self.rect.x = random.randrange(largura_tela - self.rect.width)
        self.rect.y = random.randrange(altura_tela - self.rect.height)

# Criação dos grupos de sprites
todos_sprites = pygame.sprite.Group()
inimigos = pygame.sprite.Group()
itens = pygame.sprite.Group()

# Criação do jogador
jogador = Jogador()
todos_sprites.add(jogador)

# Criação dos inimigos
for _ in range(10):
    inimigo = Inimigo()
    todos_sprites.add(inimigo)
    inimigos.add(inimigo)

# Criação dos itens
for _ in range(5):
    item = Item()
    todos_sprites.add(item)
    itens.add(item)

# Loop principal do jogo
rodando = True
while rodando:
    for evento in pygame.event.get():
import pygame
import random

# Inicialização do Pygame
pygame.init()

# Configurações da janela do jogo
largura_tela = 800
altura_tela = 600
tela = pygame.display.set_mode((largura_tela, altura_tela))
pygame.display.set_caption("Dreamland - Explorando o Mundo")

# Cores
branco = (255, 255, 255)
preto = (0, 0, 0)

# Classe para representar o jogador
class Jogador(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        self.image = pygame.Surface((50, 50))
        self.image.fill(branco)
        self.rect = self.image.get_rect()
        self.rect.center = (largura_tela // 2, altura_tela // 2)

    def update(self):
        # Movimento do jogador com as teclas de seta
        keys = pygame.key.get_pressed()
        if keys[pygame.K_LEFT]:
            self.rect.x -= 5
        if keys[pygame.K_RIGHT]:
            self.rect.x += 5
        if keys[pygame.K_UP]:
            self.rect.y -= 5
        if keys[pygame.K_DOWN]:
            self.rect.y += 5

# Classe para representar outros jogadores no mesmo local
class OutroJogador(pygame.sprite.Sprite):
    def __init__(self):
        super().__init__()
        self.image = pygame.Surface((50, 50))
        self.image.fill(preto)
        self.rect = self.image.get_rect()
        self.rect.center = (random.randint(0, largura_tela), random.randint(0, altura_tela))

    def update(self):
        # Movimento aleatório dos outros jogadores
        self.rect.x += random.randint(-5, 5)
        self.rect.y += random.randint(-5, 5)

# Grupo de sprites para os jogadores
todos_sprites = pygame.sprite.Group()
jogador = Jogador()
todos_sprites.add(jogador)

# Adicionar outros jogadores ao grupo de sprites
for _ in range(10):
    outro_jogador = OutroJogador()
    todos_sprites.add(outro_jogador)

# Loop principal do jogo
rodando = True
while rodando:
    # Eventos do Pygame
    for evento in pygame.event.get():
        if evento.type == pygame.QUIT:
            rodando = False

    # Atualizar todos os sprites
    todos_sprites.update()

    # Renderizar a tela
    tela.fill(preto)
    todos_sprites.draw(tela)
    pygame.display.flip()

# Encerramento do Pygame
pygame.quit()

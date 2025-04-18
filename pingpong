#pip install pygame
import pygame
import sys

# Aloitus
pygame.init()
width, height = 640, 480
screen = pygame.display.set_mode((width, height))
pygame.display.set_caption("Pong")

# Värit
white = (255, 255, 255)
black = (0, 0, 0)

# Pallo
ball = pygame.Rect(width // 2, height // 2, 20, 20)
ball_speed = [4, 4]

# Mailat
player = pygame.Rect(width - 20, height // 2 - 40, 10, 80)
opponent = pygame.Rect(10, height // 2 - 40, 10, 80)
player_speed = 0

clock = pygame.time.Clock()

# Päälooppi
while True:
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            pygame.quit()
            sys.exit()

        # Ohjaus
        if event.type == pygame.KEYDOWN:
            if event.key == pygame.K_UP:
                player_speed = -6
            if event.key == pygame.K_DOWN:
                player_speed = 6
        if event.type == pygame.KEYUP:
            if event.key in (pygame.K_UP, pygame.K_DOWN):
                player_speed = 0

    # Liikuta mailaa
    player.y += player_speed
    if player.top < 0: player.top = 0
    if player.bottom > height: player.bottom = height

    # Liikuta palloa
    ball.x += ball_speed[0]
    ball.y += ball_speed[1]

    if ball.top <= 0 or ball.bottom >= height:
        ball_speed[1] *= -1
    if ball.colliderect(player) or ball.colliderect(opponent):
        ball_speed[0] *= -1

    # Yksinkertainen vastus
    if opponent.centery < ball.centery:
        opponent.y += 4
    else:
        opponent.y -= 4

    # Päivitä näyttö
    screen.fill(black)
    pygame.draw.rect(screen, white, player)
    pygame.draw.rect(screen, white, opponent)
    pygame.draw.ellipse(screen, white, ball)
    pygame.draw.aaline(screen, white, (width // 2, 0), (width // 2, height))
    pygame.display.flip()
    clock.tick(60)

import pygame
import sys

# Pygame-ni ishga tushiramiz
pygame.init()

# Ekran o'lchamini belgilaymiz
WIDTH, HEIGHT = 800, 500
screen = pygame.display.set_mode((WIDTH, HEIGHT))
pygame.display.set_caption("Git Animatsiyasi")

# Ranglar
WHITE = (255, 255, 255)
BLACK = (0, 0, 0)
BLUE = (50, 100, 255)

# Shrift sozlamalari
font = pygame.font.Font(None, 36)

# Git jarayonlari ro‘yxati
steps = [
    "git init - Repository yaratildi!",
    "git add . - Fayllar stage'ga qo‘shildi!",
    "git commit -m 'Birinchi commit' - O‘zgarishlar saqlandi!",
    "git push - GitHub'ga yuklandi!"
]

step_index = 0  # Hozirgi bosqich
running = True  # O'yin sikli

while running:
    screen.fill(WHITE)  # Ekranni tozalaymiz
    
    # Matn chiqarish
    text = font.render(steps[step_index], True, BLACK)
    screen.blit(text, (50, HEIGHT // 2))
    
    # Harakat qilish uchun tugmalarni tekshiramiz
    for event in pygame.event.get():
        if event.type == pygame.QUIT:
            running = False
        elif event.type == pygame.KEYDOWN:
            if event.key == pygame.K_RIGHT:  # O'ngga bosilsa, keyingi bosqich
                step_index = min(step_index + 1, len(steps) - 1)
            elif event.key == pygame.K_LEFT:  # Chapga bosilsa, oldingi bosqich
                step_index = max(step_index - 1, 0)

    pygame.display.flip()  # Oynani yangilaymiz

pygame.quit()
sys.exit()

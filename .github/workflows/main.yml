import pygame
import random

pygame.init()
pygame.display.set_caption("SNAKE GAME")
icon=pygame.image.load(r"C:\Users\bertug\PycharmProjects\Snake_Game\Images\logo.png")
pygame.display.set_icon(icon)
ekran_en=800
ekran_boy=600

skorDosyasi=open(r"C:\Users\bertug\PycharmProjects\Snake_Game\skorlar.txt","a+")

pencere=pygame.display.set_mode((ekran_en,ekran_boy))

zaman=pygame.time.Clock()
block_size=10
FPS=15

black=(0,0,0)
chocalate=(210,105,30)
white=(255,255,255)
green=(0,128,0)
red=(255,0,0)
blue=(0,0,255)
aqua=(0,255,255)
yellow=(255,255,0)
purple=(255,0,255)
orange=(255,165,0)
lime=(0,255,0)
gold=(255,215,0)
salmon=(250,128,114)
deepPink=(255,0,127)
brown=(204,102,0)

class otherGameSettings():
    def logo(self):
        logo=pygame.image.load(r"C:\Users\bertug\PycharmProjects\Snake_Game\Images\snake2.jpg")
        rect=logo.get_rect()
        rect.x,rect.y=(0,-20)
        pencere.blit(logo,rect)

    def pause(self):
        paused = True
        while paused:
            for event in pygame.event.get():
                if event.type == pygame.QUIT:
                    pygame.quit()
                    quit()
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_SPACE:
                        paused = False
                    elif event.key == pygame.K_q:
                        pygame.quit()
                        quit()
            pencere.fill((0, 0, 0))
            txt = texts()
            txt.write("PAUSE", deepPink, 300, 100, 80)
            txt.write("SPACE TO CONTINUE OR Q TO EXIT", red, 100, 350, 50)
            pygame.display.update()
            zaman.tick(5)

class texts():
    def write(self,message,color,x,y,size):
        self.message=message
        self.color=color
        self.x=x
        self.y=y
        self.size=size
        font=pygame.font.SysFont(None,size)
        text=font.render(message,True,color)
        pencere.blit(text,[x,y])

class snake():
    def snake(self,block_size,snakelist,snakeColor):
        self.snakeColor=snakeColor
        for XnY in snakelist:
            pygame.draw.rect(pencere,snakeColor,[XnY[0], XnY[1], block_size, block_size])

class Game_Intro():
    ogs=otherGameSettings()
    ogs.logo()
    def Intro(self):
        intro = True
        while intro:
            for event in pygame.event.get():
                if event.type == pygame.QUIT:
                    pygame.quit()
                    quit()
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_SPACE:
                        intro = False
                    elif event.key == pygame.K_q:
                        pygame.quit()
                        quit()
            txt=texts()
            txt.write("Yılan yön tuşları kullanılarak hareket ettirilir.",orange,80,450,40)
            txt.write("HER SEVİYE ARTIŞIN DA YILANIN HIZI DA ARTAR",aqua,50,500,40)
            txt.write("Oyuna başlamak için 'Space' tuşuna;Çıkış yapmak için 'Q' tuşuna basın.",purple,50,550,30)
            pygame.display.update()
            zaman.tick(5)

class gameLoop():
    def game(self):
        pygame.mixer_music.load(r"C:\Users\bertug\PycharmProjects\Snake_Game\Music\snakeSound.mp3")
        pygame.mixer_music.play(0)
        level = 1
        gameExit = False
        gameOver = False
        skor = 0
        yilanX = ekran_en / 2
        yilanY = ekran_boy / 2
        FPS = 10
        snakelist = []
        snake_length = 1

        bg=pygame.image.load(r"C:\Users\bertug\PycharmProjects\Snake_Game\Images\bg.jpg")

        randyemX = round(random.randrange(0, ekran_en - block_size) / 10.0) * 10.0
        randyemY = round(random.randrange(0, ekran_boy - block_size) / 10.0) * 10.0
        yilanX_Yon = 0
        yilanY_Yon = 0
        txt = texts()
        ogs=otherGameSettings()

        while not gameExit:
            while gameOver == True:
                pencere.fill((0, 0, 0))
                snakeLogo=pygame.image.load(r"C:\Users\bertug\PycharmProjects\Snake_Game\Images\snake.jpg")
                txt.write("GAME OVER",red,200,50,100)
                pencere.blit(snakeLogo,(300,150))
                txt.write("PRESS SPACE TO PLAY AGAIN OR Q TO QUIT",white,60,450,45)
                pygame.display.update()
                for event in pygame.event.get():
                    if event.type == pygame.QUIT:
                        gameExit = True
                        gameOver = False
                    if event.type == pygame.KEYDOWN:
                        if event.key == pygame.K_q:
                            gameExit = True
                            gameOver = False
                        elif event.key == pygame.K_SPACE:
                            game=gameLoop()
                            game.game()
            for event in pygame.event.get():
                if event.type == pygame.QUIT:
                    gameExit = True
                if event.type == pygame.KEYDOWN:
                    if event.key == pygame.K_LEFT:
                        yilanX_Yon = -block_size
                        yilanY_Yon = 0
                    elif event.key == pygame.K_RIGHT:
                        yilanX_Yon = block_size
                        yilanY_Yon = 0
                    elif event.key == pygame.K_UP:
                        yilanY_Yon = -block_size
                        yilanX_Yon = 0
                    elif event.key == pygame.K_DOWN:
                        yilanY_Yon = block_size
                        yilanX_Yon = 0
                    elif event.key == pygame.K_p:
                        ogs.pause()
            if yilanX >= ekran_en or yilanX <= 0 or yilanY >= ekran_boy or yilanY < 0:
                gameOver = True

            yilanX += yilanX_Yon
            yilanY += yilanY_Yon

            pencere.fill((0, 0, 0))
            pencere.blit(bg, (0, 0))
            pygame.draw.rect(pencere, (255, 0, 0), [randyemX, randyemY, block_size, block_size])

            snakehead = []
            snakehead.append(yilanX)
            snakehead.append(yilanY)
            snakelist.append(snakehead)

            if len(snakelist) > snake_length:
                del snakelist[0]

            for eachSegment in snakelist[:-1]:
                if eachSegment == snakehead:
                    gameOver = True

            pygame.display.update()
            if yilanX == randyemX and yilanY == randyemY:
                skor = skor + 10
                snake_length += 4
                if skor % 50 == 0:
                    level += 1
                if skor >= 50:
                    FPS = 20
                if skor >= 100:
                    FPS = 25
                if skor >= 150:
                    FPS = 30
                if skor >= 200:
                    FPS = 35
                if skor >= 250:
                    FPS = 40
                if skor>=300:
                    FPS=50
                    pygame.display.update()
                randyemX = round(random.randrange(0, ekran_en - block_size) / 10.0) * 10.0
                randyemY = round(random.randrange(0, ekran_boy - block_size) / 10.0) * 10.0

            snk = snake()
            snakeColor=blue
            if level==2:
               snakeColor=purple
            if level==3:
                snakeColor=deepPink
            if level == 4:
                snakeColor = gold
            if level>4:
                snakeColor=white

            snk.snake(block_size, snakelist, snakeColor)

            pygame.draw.rect(pencere, black, (yilanX, yilanY, 3, 3))
            pygame.draw.rect(pencere,black,(yilanX+5,yilanY,3,3))
            txt.write("SKOR: ",black,0,0,40)
            txt.write(str(skor),black,100,0,40)
            txt.write("LEVEL: ",black,680,0,40)
            txt.write(str(level),black,780,0,40)
            pygame.display.update()
            zaman.tick(FPS)

            if gameOver==True:
                pygame.mixer_music.pause()

        skorDosyasi.write("Skor: " + str(skor) + "\n")
        skorDosyasi.close()
        pygame.quit()
        quit()

intro=Game_Intro()
intro.Intro()
game=gameLoop()
game.game()

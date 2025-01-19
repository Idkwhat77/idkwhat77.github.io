---
layout: post
title: "Fu Xuan's quest For Milkshake"
date: 2024-11-24
categories: [project, python]
tags: [hsr]
image:
 path: /assets/img/fuxuan.png
---
## Welcome to my first major project for one of my classes in University!
This isn't an end semester project, but still an important one. I basically have to code a game in Python using whatever resources I have, so I made this.

![gane](/assets/img/game1.PNG)
*Main Menu*
Alright, let's get on with it.

## What's the game about?
My project revolves around the plot where the main character, [Fu Xuan](https://honkai-star-rail.fandom.com/wiki/Fu_Xuan) from [Honkai: Star Rail](https://hsr.hoyoverse.com/), embarks on an epic quest to obtain a vanilla milkshake. Along the way, players encounter various challenges, including turn-based battles, a cooking minigame, and more accompanied by visual novel style dialogue. 

## Character Introductions

1. **Fu Xuan**
    ![fu_xuan](/assets/img/Character_Fu_Xuan_Splash_Art.webp)
    *Fu Xuan's ingame splash art*

    The confident yet blunt Master Diviner of the Xianzhou Luofu's Divination Commission and one of the Six Charioteers. She calculates the Xianzhou Luofu's route and foretells the outcome of future events, as she feels that what she does is the wisest course of action[^1]. Behind her serious expression, she hides an undying love for sugary drinks, which inspired this whole entire game to be made.
    
    Fu Xuan is the main character of this game and appears on every single route and ending.

    [^1]: "Fu Xuan - Honkai Star Rail Wiki," Fandom, https://honkai-star-rail.fandom.com/wiki/Fu_Xuan. Accessed 2024-11-24.

2. **Qingque**
    ![qingque](/assets/img/Character_Qingque_Splash_Art.webp)
    *Qingque's ingame splash art*

    An average Diviner of the Divination Commission on the Xianzhou Luofu, and a librarian. She never slacks off when it comes to slacking off and is about to be demoted to a "door guardian."[^2]

    Qingque is a side character that only appears during the battle route and its respective endings.
    
    [^2]: "Qingque - Honkai Star Rail Wiki," Fandom, https://honkai-star-rail.fandom.com/wiki/Qingque. Accessed 2024-11-24.

## Features

1. **Storytelling and "Humor"**
    - The game features playful dialogue and situations, such as Fu Xuan’s unusual request and many others. There are also multiple endings which are all doable while some may require some effort to get (such as letting Fu Xuan die in the Turn Based RPG minigame), which adds replayability and fun. It's coded by printing each character in a string every 3 miliseconds.
    ![GIF_VN](/assets/gif/vn_fu_xuan.gif)
    *Intro + Water ending*

2. **Turn Based minigame**
    - Players control two characters, Fu Xuan and [Qingque](https://honkai-star-rail.fandom.com/wiki/Qingque), each with abilities directly from the game and stats from my own personal account. Fu Xuan excels in defensive and keeping the party alive while turning most damage into her, while Qingque offers powerful but RNG attack mechanics. The combat system uses a queue to manage turn order, alternating between characters and the enemy.
    ![GIF_FIGHT](/assets/gif/fight_fu_xuan.gif)
    *Fu Xuan and Qingque using their skill and basic attack.*

3. **Cooking Minigame**
    - A lighthearted path other than combat where players gather ingredients and attempt to create the perfect milkshake (or something else). Depending on the ingredients used, players can unlock multiple endings.
    ![GIF_COOK](/assets/gif/cooking_fu_xuan.gif)
    *Making a Vanilla Milkshake*

## Coding Concepts Used

1. **Classes**
    - Each character in the turn based RPG uses classes to define their stats, basic attack, skill, and ultimate, while the enemy only has a single basic attack. Here's a snippet of Fu Xuan's class.
    ```python
        class Fu_Xuan:
        def __init__(self): # Define Fu Xuan's stats from the beginning
            self.energy = 0
            self.ORIGINAL_HP = 10000
            self.HP = 10000          
            self.Max_HP = 10000     
            self.ATK = 1400          
            self.CRIT_RATE = 20.0  
            self.CRIT_DMG = 0.6     
            self.matrix = False      
            self.skill_counter = 0
            self.talent_counter = 1    
            self.alive = True 
        
        def stats(self): # Print Fu Xuan's stats
            print(f"""
            Fu Xuan:
            HP = {self.HP:,}/{self.Max_HP:,}
            ATK = {self.ATK}
            Crit Rate = {self.CRIT_RATE}%
            Crit Damage = {self.CRIT_DMG * 100}%
            """)
            time.sleep(1)
            
        def energize(self, amount): # So her energy cannot go above 135
            self.energy += amount
            if self.energy > 135:
                self.energy = 135

        def basic_atk(self): # Basic atk with crit effects + voiceline
            global skill_point
            damage = self.HP * 0.5  
            crit = random.randint(0, 100)
            is_critical = crit < self.CRIT_RATE
            fuxuan_basicatk = random.choice(fu_xuan_basicatk)
            if fuxuan_basicatk == fu_xuan_basicatk1:
                fu_xuan_basicatk1.play()
                lmao("\"With all my power.. Scry the future!\"", color = "magenta")
            elif fuxuan_basicatk == fu_xuan_basicatk2:
                fu_xuan_basicatk2.play()
                lmao("\"In formation, in accordance!\"", color = "magenta")
            sound_effectfxb.play()
            sound_effectfxb2.play()
            if is_critical:
                damage += damage * self.CRIT_DMG
                n("CRIT!", color = "yellow")

            self.energize(20)
            if skill_point < 5:
                skill_point += 1

            print(f"Fu Xuan dealt {damage:.2f} damage.")
            enemy.HP -= damage
            time.sleep(0.5)

        def skill(self): # Fu Xuan's skill to increase HP and Crit Rate of teammates
            global skill_point
            if skill_point == 0:
                print("Not enough SP!")
                pass
            else:    
                fuxuan_skill = random.choice(fu_xuan_skill)
                if fuxuan_skill == fu_xuan_skill1:
                    fu_xuan_skill1.play()
                    lmao("\"Converge... and awaken!\"", color = "magenta")
                elif fuxuan_skill == fu_xuan_skill2:
                    fu_xuan_skill2.play()
                    lmao("\"Together... as one!\"", color = "magenta")
                sound_effectfxs.play()
                
                if self.matrix == True:
                    self.energize(50)
                else:
                    self.energize(30)
                    
                if not self.matrix:
                    self.matrix = True
                    self.skill_counter = 3
                    self.Max_HP += self.ORIGINAL_HP * 0.06
                    self.HP += self.ORIGINAL_HP * 0.06
                    self.CRIT_RATE += 12
                    print(f"Fu Xuan's Max HP increased to {self.Max_HP:,} and Crit Rate increased to {self.CRIT_RATE}%")
                    if qingque.alive == True:
                        qingque.Max_HP += self.ORIGINAL_HP * 0.06
                        qingque.HP += self.ORIGINAL_HP * 0.06
                        qingque.CRIT_RATE += 12
                        print(f"Qingque's Max HP increased to {qingque.Max_HP:,} and Crit Rate increased to {qingque.CRIT_RATE}%")
                    skill_point -= 1
                else:
                    if self.skill_counter < 3:
                        self.skill_counter = 3
                    if self.matrix == True:
                        self.energize(50)
                    else:
                        self.energize(30)
                    skill_point -= 1
                    print("Matrix of Prescience turn refreshed.")
                time.sleep(0.5)

        def ultimate(self): # Ultimate to heal teammates
            
            if self.energy == 135:
                fu_xuan_ultimate1.play()
                lmao("\"All things in this world have their laws.\"", color = "magenta")
                damage = self.HP
                crit = random.randint(0, 100)
                is_critical = crit < self.CRIT_RATE
                fu_xuan_ultimate2.play()
                lmao("\"Yet stratagems... constellations.. are human.. creations! Hmph!\"", color = "magenta")
                sound_effectfxu.play()
                sound_effectfxu2.play()
                if is_critical:
                    damage += damage * self.CRIT_DMG
                    n("CRIT!", color = "yellow")
                    
                print(f"Fu Xuan dealt {damage:.2f} damage with her ultimate!")
                enemy.HP -= damage
                time.sleep(1)
                if qingque.HP > 0:
                    recover = fu_xuan.Max_HP * 0.05 + 133
                    qingque.HP += recover
                    if qingque.HP > qingque.Max_HP:
                        qingque.HP = qingque.Max_HP
                        print(f"Qingque restored {qingque.Max_HP - qingque.HP} HP!")
                    else:
                        print(f"Qingque restored {recover} HP!")
                    
                if self.talent_counter < 2:
                    self.talent_counter += 1
                self.energy = 0
                self.energize(5)
            else:
                print("Not enough energy...")

            time.sleep(0.5)

        def talent(self): # Restore HP when below 50% HP
            if self.HP < self.Max_HP * 0.5 and self.talent_counter > 0: 
                missing_hp = self.Max_HP - self.HP
                restore_amount = missing_hp * 0.9 
                self.HP += restore_amount
                self.HP = min(self.HP, self.Max_HP)
                self.talent_counter -= 1
                print(f"Fu Xuan restored {restore_amount:.2f} HP. Current HP: {self.HP:.2f}")
            time.sleep(0.5)

        def matrix_of_prescience(self): # For reducing the number of turns her skill has
            if self.skill_counter > 0:
                self.skill_counter -= 1
                if self.skill_counter == 0:
                    self.matrix = False
                    self.Max_HP = self.ORIGINAL_HP
                    if self.HP > self.Max_HP:
                        self.HP = self.Max_HP
                    self.CRIT_RATE -= 12
                    
                    qingque.Max_HP = qingque.ORIGINAL_HP
                    if qingque.HP > qingque.Max_HP:
                        qingque.HP = qingque.Max_HP
                    qingque.CRIT_RATE -= 12
                    print("Matrix Of Prescience turn has run off.")
                    time.sleep(1)
    ```
2. **Pygame Music and Sound Effects**
    - All music and sound effects played in my project were implemented using [Pygame](https://www.pygame.org). Doing this was kind of a chore with the sound effects due to how many variables I have to load plus using the OS import to read the file in the same directory. 
    ![sfx](/assets/img/sfx.PNG)
    *Small snippet of sound effect loads*

3. **Randomization**
    - Qingque's skill shuffles randomly between 3 cards with the number 1 - 3 three times and places the card in her deck. If all numbers are the same (let's say [3,3,3]), then her enhanced basic attack will activate and her skill will be temporarily disabled until Qingque uses her enhanced basic attack. Here's the code snippet below :
    ![qs](/assets/img/qingque_skill.PNG)
    *Qingque's skill function on her class*

## Where to download?
You can download the zip file of the entire project [here](https://drive.google.com/file/d/1WrD4h7bwPcNL9g-jWWiU05fan--avIKo).

## What's next?
After this, I'm planning to develop the battle system further independently of the project, which will include all of Star Rail's characters and mechanics. It'll take a while, but I assure you that I ***am*** commited to making this a reality, no matter what it takes!

## Conclusion
This project has been a fantastic way to apply the concepts I’ve learned in my algorithm programming class. It’s been both a technical and creative journey, and I’m proud of what I’ve accomplished so far. Fu Xuan’s quest for a milkshake is a testament to how programming can bring even the wildest and randomness (does that word even exist?[sic]) to life. I hope to inspire others to take on similar projects and explore the exciting world of game development.
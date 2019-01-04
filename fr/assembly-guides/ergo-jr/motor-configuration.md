# Configuration des moteurs

L'Ergo Jr est composé de 6 moteurs XL-320 fabriqués par [Robotis](http://support.robotis.com/en/product/dynamixel/xl-series/xl-320.htm). Chacun de ces servomoteurs possèdent une carte électronique lui permettant de recevoir différents types de commandes (sur sa position, sa vitesse, son couple...) et de communiquer avec d’autres servos. Vous pouvez chainer ces servomoteurs entre eux et tous les commander depuis un bout de la chaîne.

<img src="img/assembly/xl_320.jpg" alt="XL320" height="150" />

Cependant, afin d’être connecté et identifié sur le même bus (de donnée), ils doivent avoir un identifiant unique. Out of the factory they all set to the same ID (1). Dans cette section, nous vous donnerons plus de détails sur comment vous pouvez définir un nouvel identifiant unique à chacun de vos moteurs.

Nous vous recommandons de configurer des moteurs en parallèle de l’assemblage des pièces du robot. Ce qui signifie qu’avant d’assembler un moteur neuf, vous commencez par le configurer puis le monter sur le reste du robot. Pendant la procédure d'assemblage, nous indiquerons chaque fois qu'il faut configurer un nouveau moteur.

## Allumer le robot

Si vous utilisez Windows ou Linux (inutile pour Mac OSX) vous devez d'abord **installer Bonjour/Zeroconf ([lien pour Windows](https://support.apple.com/kb/DL999))** pour pouvoir vous connecter au robot. Pour plus de détail, rendez-vous à la page dédiée : [Bonjour/Zeroconf protocol](../../installation/install-zeroconf.md).

Avant de configure les moteurs, **débrancher le robot du secteur**

* Connecter le câble Ethernet entre le robot et votre ordinateur (ou routeur/box si vous voulez utiliser un réseau existant)
* Brancher la prise jack (alimentation électrique) sur la carte pixl

Rendez-vous maintenant sur la page web de votre robot <http://poppy.local>.

Si Bonjour n'est pas présent, vous aurez un message d'erreur comme celui-ci. ![Page doesn't exist](img/IHM/webpage_not_available.jpg). Si Bonjour est installé est que le message d'erreur apparaît, veuillez réinstaller Bonjour. 

## Configuring motors one at a time

As explained above, all motors have the same ID by default. **Only one motor at a time should be connected to the data bus when you configure them.** Otherwise, it will not work as all motors connected will think that the order sent on the line is intended for them, they will all try to answer resulting in a big mess.

Your electronic setup when configuring a motor should look like this:

* a Raspberry Pi
* a Pixl shield on top and the AC plugged
* a wire from the shield to the motor you want to configure
* an Ethernet cable going from the Raspberry Pi to your computer or your router

![XL-320 configuration ; one motor at a time](img/motor_one_by_one.jpg).

### Utilitaire en ligne de commande

Robots come with a command line utility `poppy-configure` ; to use it you'll need to open a terminal on your Raspberry Pi.

To do so, first, **open the page http://poppy.local in a web browser**.

If everything goes well, you should see the Poppy home page:

![Poppy home page](img/IHM/home_page_jupyter.png)

Click on the **"Jupyter — Python"** link and after, select on the right "New" and "Terminal". <img src="img/IHM/jupyter_new_terminal.png" alt="Terminal Jupyter" height="300" />

You have now access to the Terminal:

![terminal for configuration](img/IHM/terminal_for_configuration.PNG)

Once the terminal is open, re-copy the command below and press enter to execute it.

```bash
poppy-configure ergo-jr m1
```

After a few seconds you will see the following message: ![terminal for configuration 2](img/IHM/poppy-configure-terminal-output.png)

You have now configured the motor m1 of your robot, congratulation !

Once configured and that you see the message indicating that everything went well, you can unplug the motor (the Raspberry Pi can stay powered). The configuration is stored in the motor internal memory (eprom).

> **Info** Poppy Ergo Jr motors are named m1, m2, m3, m4, m5, m6. To configure the others motors, you have to change m1 by the name of the motor you want to configure in the command above.

<img src="img/assembly/motors.png" alt="Motors list" height="300" />

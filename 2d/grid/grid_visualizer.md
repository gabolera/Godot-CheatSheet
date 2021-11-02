# Godot 2D Grid Visualizer


<p align="center">

![GodotImage](../../imagens/godot_icon.png)

</p>



### Início

Necessário ter uma câmera 2D instanciada na cena que será usada!

Criar um Node2D e adicionar o script abaixo para gerar a grade



Variáveis acessíveis

| Variável | Tipo | Descrição                                   |
| -------- | ---- | ------------------------------------------- |
| on       | Bool | Ativa ou desativa o visualizador            |
| tileSize | Int  | Tamanho do grid que será desenhado ex 64x64 |



```gscript
extends Node2D

export var on = true
export var tileSize = 64

func _draw():
	if on: 
		var size = get_viewport_rect().size  * get_parent().get_node("Camera2D").zoom
		var cam = get_parent().get_node("Camera2D").position
		for i in range(int((cam.x - size.x) / tileSize) - 1, int((size.x + cam.x) / tileSize) + 1):
			draw_line(Vector2(i * tileSize, cam.y + size.y + 100), Vector2(i * tileSize, cam.y - size.y - 100), "000000")
		for i in range(int((cam.y - size.y) / tileSize) - 1, int((size.y + cam.y) / tileSize) + 1):
			draw_line(Vector2(cam.x + size.x + 100, i * tileSize), Vector2(cam.x - size.x - 100, i * tileSize), "000000")

func _process(delta):
	update()

```


 
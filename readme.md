# Pac-Man com Aprendizagem por Reforço

Um Pac-Man aprende sozinho, por tentativa e erro (**Q-learning**), a atravessar um labirinto 16x16 até a cereja, desviando dos fantasmas e comendo bolinhas pelo caminho. Tudo está no notebook `notebook/labirinto_rl_video.ipynb`.

## Como funciona

- **Estado:** a posição `(linha, coluna)` do Pac-Man.
- **Ações:** cima, baixo, esquerda, direita.
- **Recompensas:**

| Situação | Recompensa |
|---|---|
| Passo normal | -1 |
| Parede ou borda | -5 |
| Bolinha (só na 1ª vez no episódio) | +2 |
| Fantasma | -100 (fim) |
| Cereja | +100 (fim) |

- **Tabela Q:** uma nota para cada ação em cada célula. No fim, ele segue a ação de maior nota.
- **Exploração:** começa agindo quase aleatório (`epsilon = 1.0`) e passa a usar o que aprendeu conforme `epsilon` diminui.

## como rodar

```bash
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```


## Parâmetros principais

| Parâmetro | Valor | Significado |
|---|---|---|
| `alpha` | 0.2 | taxa de aprendizado |
| `gamma` | 0.5 | peso do futuro |
| `epsilon` / `epsilon_min` | 1.0 / 0.001 | exploração inicial / mínima |
| `decay` | 0.998 | quanto o epsilon diminui por episódio |
| `N_EPISODES` | 3000 | tentativas de treino |
| `MAX_STEPS` | 400 | limite de passos por tentativa |
| `PELLET_BONUS` | 3 | bônus ao comer bolinha |


# automatos-assistencia-tecnica

**Projeto desenvolvido por:**

Felipe Ferreira - 2993620

Nicole Vieira - 2438577

Sthefany Alves - 2457820

Vitória Santos - 2392314

Igor Xavier - 2352643

**Curso:** Ciência da Computação, 8° Semestre, noturno.

Projeto acadêmico de Ciência da Computação que demonstra três aplicações de autômatos em um domínio real: validadores com expressões regulares, máquina de estados de negócio e mini-scanner para uma linguagem de comandos.

## Requisitos cobertos
- **R3:** testes automatizados de RegEx com exemplos aceitos e rejeitados, incluindo string vazia.
- **R4:** máquina de estados com pelo menos cinco estados e seis transições, eventos permitidos após recusa e dois fluxos válidos e dois inválidos.
- **R5:** mini-scanner com mais de oito tipos de token, três palavras reservadas, maximal munch, números inteiros e reais, comentários/espaços ignorados, erros com linha, coluna e dicas específicas, continuando a análise após erros.
- **R6:** interface com ipywidgets.

## Desenhos AFD
### AFD 1 — Validador de número de chamado

**Linguagem reconhecida:** `CH[0-9]{4}`

**Exemplo aceito:** `CH1234`

```text
                         C        H       [0-9]    [0-9]    [0-9]    [0-9]
                      ┌─────┐  ┌─────┐  ┌─────┐  ┌─────┐  ┌─────┐  ┌─────┐
--> (q0) ────────────> (q1) ──> (q2) ──> (q3) ──> (q4) ──> (q5) ──> ((q6))
                                                                         Final

Estados:
- q0: estado inicial.
- q1: recebeu a letra C.
- q2: recebeu o prefixo CH.
- q3: recebeu o primeiro dígito.
- q4: recebeu o segundo dígito.
- q5: recebeu o terceiro dígito.
- q6: recebeu os quatro dígitos; estado final.
- q⊥: estado morto, para entradas inválidas.

Transições:
- q0 --C--> q1
- q1 --H--> q2
- q2 --dígito--> q3
- q3 --dígito--> q4
- q4 --dígito--> q5
- q5 --dígito--> q6
- Qualquer símbolo inesperado leva ao estado morto q⊥.
- q6 recebe qualquer símbolo adicional e vai para q⊥.
- q⊥ permanece em q⊥ para qualquer símbolo.

Onde dígito representa um caractere entre 0 e 9.
```

### AFD 2 — Validador de código de impressora

**Linguagem reconhecida:** `IMP-[0-9]{3}`

**Exemplo aceito:** `IMP-001`

```text
          I       M       P       -       [0-9]   [0-9]   [0-9]
       ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐ ┌─────┐
--> (q0) ───> (q1) ─> (q2) ─> (q3) ─> (q4) ─> (q5) ─> (q6) ─> ((q7))
                                                                      Final

Estados:
- q0: estado inicial.
- q1: recebeu a letra I.
- q2: recebeu o prefixo IM.
- q3: recebeu o prefixo IMP.
- q4: recebeu o prefixo IMP-.
- q5: recebeu o primeiro dígito.
- q6: recebeu o segundo dígito.
- q7: recebeu os três dígitos; estado final.
- q⊥: estado morto, para entradas inválidas.

Transições:
- q0 --I--> q1
- q1 --M--> q2
- q2 --P--> q3
- q3 -----> q4
- q4 --dígito--> q5
- q5 --dígito--> q6
- q6 --dígito--> q7
- Qualquer símbolo inesperado leva ao estado morto q⊥.
- q7 recebe qualquer símbolo adicional e vai para q⊥.
- q⊥ permanece em q⊥ para qualquer símbolo.

Onde dígito representa um caractere entre 0 e 9.





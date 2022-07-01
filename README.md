# Oscar!

### Hoje vamos trabalhar com o Oscar.
A ideia de premiar ou ser premiado é para reconhecer:
- Reconhecer uma qualidade
- Reconhecer um atributo
- Reconhecer o esforço... 

Reconhecer sempre.

Nem todos os prêmios são merecidos e nem todos que merecem ganham. 
Então vale mesmo a pena, premiar? ###

## 1. Quantas vezes Natalie Portman foi indicada ao Oscar?

#### Ela foi indicada 3 Vezes.
<code> SELECT COUNT(*) FROM oscar WHERE name = 'Natalie Portman' </code>

## 2. Quantos Oscars Natalie Portman ganhou?

#### Ela ganhou 1 Oscar.
<code> SELECT COUNT(*) FROM oscar WHERE name LIKE 'Natalie Portman' AND winner LIKE 'True' </code>

## 3. Amy Adams já ganhou algum Oscar?

#### Não.
<code> SELECT COUNT(*) FROM oscar WHERE name LIKE 'Amy Adams' AND winner LIKE 'True' </code>

## 4. Alguém já ganhou um Oscar e tem o seu primeiro nome?

#### Não.
<code> SELECT COUNT(*) FROM oscar WHERE name LIKE 'Ellen' AND winner LIKE 'True' </code>

## 5. Toy Story 3 ganhou um Oscar em quais anos?

#### No ano de 2010.
<code> SELECT name, year_film FROM oscar WHERE film LIKE 'Toy Story 3' AND winner LIKE 'True' </code>

## 6. Quem tem mais Oscars: a categoria "Melhor Ator" ou "Melhor Filme"?

#### A categoria melhor ator.
<code> SELECT category, COUNT(category) FROM oscar WHERE category LIKE 'Actor' OR category LIKE 'Cinematography' AND winner LIKE 'True' GROUP BY category </code>

## 7. O primeiro Oscar para melhor Atriz foi para quem? Em que ano?

#### Foi para Janet Gaynor, em 1928.
<code> SELECT name, MIN(year_ceremony) FROM oscar WHERE category LIKE 'Actress' AND winner LIKE 'True' </code>

## 8. Na categoria Winner, altere todos os valores com "True" para 1 e todos os valores "False" para 0.

<code> UPDATE oscar SET winner = '1' WHERE winner LIKE 'True' </code>
<code> UPDATE oscar SET winner = '0' WHERE winner LIKE 'False' </code>

## 9. Em qual edição do Oscar "Crash" ganhou o prêmio?

#### 2006.
<code> SELECT year_ceremony FROM oscar WHERE film LIKE 'Crash' AND winner LIKE '1' </code>

## 10. Que filme merecia ganhar um Oscar e não ganhou?

#### Django Livre.

## 11. Bom... dê um Oscar para esse filme, então.

<code> UPDATE oscar SET winner = '1' WHERE id = 9415 </code>

## 12. O filme Central do Brasil aparece no Oscar?

#### Sim, mas com o nome em inglês.
<code> SELECT * FROM oscar WHERE film LIKE 'Central Station' </code>

## 13. Aliás... Qual sua opinião sobre central do Brasil

#### Esse filme é maravilhoso. É emocionante, triste e bonito. Eu não queria que a Dora tivesse ido embora daquele jeito, mas o fim do filme é de partir o coração. A música do filme é muito boa, a fotografia, tudo. É lindo, uma obra de arte. (O cinema brasileiro é uma obra de arte)

## 14. Inclua no banco 7 filmes que nunca nem foram nomeados ao Oscar, mas que na sua opinião, merecem.

<code> INSERT INTO oscar (year_film, category, name, film, winner) VALUES ('2007', 'CINEMATOGRAPHY', 'Marcos Jorge', 'Estômago', '0'), ('2021', 'CINEMATOGRAPHY', 'Sam Levinson', 'Malcolm & Marie', '0'), ('2009', 'CINEMATOGRAPHY', 'Mark Webb', '500 Dias com Ela', '0'), ('2000', 'CINEMATOGRAPHY', 'Mary Harron', 'Psicopata Americano', '0'), ('2015', 'CINEMATOGRAPHY', 'Anna Muylaert', 'Que Horas Ela Volta?', '0'), ('2019', 'CINEMATOGRAPHY', 'Kleber Mendonça Filho', 'Bacurau', '0'), ('2005', 'CINEMATOGRAPHY', 'Lukas Moodysson', 'Para Sempre Lilya', '0'); </code>

## 15. Crie uma nova categoria de premiação. Qualquer prêmio que você queira dar. Agora vamos dar esses prêmios aos filmes que você cadastrou na questão acima.

<code> ALTER TABLE oscar ADD grandes_filmes BINARY </code>

<code> UPDATE oscar SET curto = 1 WHERE id BETWEEN 10396 AND 10402 </code>

## 16. Qual foi o primeiro ano a ter um prêmio do Oscar?

#### Foi 1928.
<code> SELECT MIN(year_ceremony) FROM oscar </code>

## 17. Pensando no ano em que você nasceu: Qual foi o Oscar de melhor filme, Melhor Atriz e Melhor Diretor?

#### Melhor filme: The Devil Dancer
Melhor atriz: Louise Dresser
Melhor diretor: Roman Polanski ###
<code> SELECT name, film, category FROM oscar WHERE category LIKE 'Cinematography' OR category LIKE 'Actress' OR category LIKE 'Directing' AND winner LIKE '1' AND year_ceremony = '2003' GROUP BY category </code>

## 18. Agora procure 7 atrizes que não sejam americanas, europeias ou brasileiras.  Vamos cadastrá-los no nosso banco, mas eles ainda não ganharam o Oscar. Só foram nomeados.

<code> INSERT INTO oscar (name) VALUES ('Margot Robbie'), ('So-dam Park'), ('Yael Stone'), ('Dascha Polanco'), ('Amybeth McNulty'), ('Charlotte Gainsbourg'), ('Ruby Rose'); </code>

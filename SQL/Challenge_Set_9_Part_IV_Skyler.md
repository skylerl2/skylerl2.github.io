# 1:

with men_players as (with 
us_men_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, count(player1) as count1 from us_men_2013 group by player order by player),
us_men_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, count(player2) as count2 from us_men_2013 group by player order by player),
aus_men_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, count(player1) as count1 from aus_men_2013 group by player order by player),
aus_men_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, count(player2) as count2 from aus_men_2013 group by player order by player),
french_men_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, count(player1) as count1 from french_men_2013 group by player order by player),
french_men_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, count(player2) as count2 from french_men_2013 group by player order by player),
wimbledon_men_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), '.')-1)) as player, count(player1) as count1 from wimbledon_men_2013 group by player order by player),
wimbledon_men_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), '.')-1)) as player, count(player2) as count2 from wimbledon_men_2013 group by player order by player)
select coalesce(us_men_p1.player, us_men_p2.player, aus_men_p1.player, aus_men_p2.player, 
french_men_p1.player, french_men_p2.player, wimbledon_men_p1.player, wimbledon_men_p2.player) as player,
coalesce(us_men_p1.count1+us_men_p2.count2, us_men_p1.count1, us_men_p2.count2) as us_count,
coalesce(aus_men_p1.count1+aus_men_p2.count2, aus_men_p1.count1, aus_men_p2.count2) as aus_count,
coalesce(french_men_p1.count1+french_men_p2.count2, french_men_p1.count1, french_men_p2.count2) as french_count,
coalesce(wimbledon_men_p1.count1+wimbledon_men_p2.count2, wimbledon_men_p1.count1, wimbledon_men_p2.count2) as wimbledon_count
from us_men_p1
full outer join us_men_p2 on us_men_p1.player=us_men_p2.player
full outer join aus_men_p1 on us_men_p1.player=aus_men_p1.player
full outer join aus_men_p2 on us_men_p1.player=aus_men_p2.player
full outer join french_men_p1 on us_men_p1.player=french_men_p1.player
full outer join french_men_p2 on us_men_p1.player=french_men_p2.player
full outer join wimbledon_men_p1 on us_men_p1.player=wimbledon_men_p1.player
full outer join wimbledon_men_p2 on us_men_p1.player=wimbledon_men_p2.player)
select player, us_count, aus_count, french_count, wimbledon_count from men_players;

with ladies_players as (with 
us_ladies_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, count(player1) as count1 from us_ladies_2013 group by player order by player),
us_ladies_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, count(player2) as count2 from us_ladies_2013 group by player order by player),
aus_ladies_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, count(player1) as count1 from aus_ladies_2013 group by player order by player),
aus_ladies_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, count(player2) as count2 from aus_ladies_2013 group by player order by player),
french_ladies_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, count(player1) as count1 from french_ladies_2013 group by player order by player),
french_ladies_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, count(player2) as count2 from french_ladies_2013 group by player order by player),
wimbledon_ladies_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), '.')-1)) as player, count(player1) as count1 from wimbledon_ladies_2013 group by player order by player),
wimbledon_ladies_p2 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), '.')-1)) as player, count(player2) as count2 from wimbledon_ladies_2013 group by player order by player)
select coalesce(us_ladies_p1.player, us_ladies_p2.player, aus_ladies_p1.player, aus_ladies_p2.player, 
french_ladies_p1.player, french_ladies_p2.player, wimbledon_ladies_p1.player, wimbledon_ladies_p2.player) as player,
coalesce(us_ladies_p1.count1+us_ladies_p2.count2, us_ladies_p1.count1, us_ladies_p2.count2) as us_count,
coalesce(aus_ladies_p1.count1+aus_ladies_p2.count2, aus_ladies_p1.count1, aus_ladies_p2.count2) as aus_count,
coalesce(french_ladies_p1.count1+french_ladies_p2.count2, french_ladies_p1.count1, french_ladies_p2.count2) as french_count,
coalesce(wimbledon_ladies_p1.count1+wimbledon_ladies_p2.count2, wimbledon_ladies_p1.count1, wimbledon_ladies_p2.count2) as wimbledon_count
from us_ladies_p1
full outer join us_ladies_p2 on us_ladies_p1.player=us_ladies_p2.player
full outer join aus_ladies_p1 on us_ladies_p1.player=aus_ladies_p1.player
full outer join aus_ladies_p2 on us_ladies_p1.player=aus_ladies_p2.player
full outer join french_ladies_p1 on us_ladies_p1.player=french_ladies_p1.player
full outer join french_ladies_p2 on us_ladies_p1.player=french_ladies_p2.player
full outer join wimbledon_ladies_p1 on us_ladies_p1.player=wimbledon_ladies_p1.player
full outer join wimbledon_ladies_p2 on us_ladies_p1.player=wimbledon_ladies_p2.player)
select player, us_count, aus_count, french_count, wimbledon_count from ladies_players;


# 2:

with men_players as (with 
us_men_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, count(player1) as count1 from us_men_2013 group by player order by player),
us_men_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, count(player2) as count2 from us_men_2013 group by player order by player),
aus_men_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, count(player1) as count1 from aus_men_2013 group by player order by player),
aus_men_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, count(player2) as count2 from aus_men_2013 group by player order by player),
french_men_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, count(player1) as count1 from french_men_2013 group by player order by player),
french_men_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, count(player2) as count2 from french_men_2013 group by player order by player)
select coalesce(us_men_p1.player, us_men_p2.player, aus_men_p1.player, aus_men_p2.player, 
french_men_p1.player, french_men_p2.player) as player,
coalesce(us_men_p1.count1+us_men_p2.count2, us_men_p1.count1, us_men_p2.count2) as us_count,
coalesce(aus_men_p1.count1+aus_men_p2.count2, aus_men_p1.count1, aus_men_p2.count2) as aus_count,
coalesce(french_men_p1.count1+french_men_p2.count2, french_men_p1.count1, french_men_p2.count2) as french_count
from us_men_p1
full outer join us_men_p2 on us_men_p1.player=us_men_p2.player
full outer join aus_men_p1 on us_men_p1.player=aus_men_p1.player
full outer join aus_men_p2 on us_men_p1.player=aus_men_p2.player
full outer join french_men_p1 on us_men_p1.player=french_men_p1.player
full outer join french_men_p2 on us_men_p1.player=french_men_p2.player)
select player, coalesce((coalesce(us_count+aus_count, us_count, aus_count)+french_count), coalesce(us_count+aus_count, us_count, aus_count), french_count) as total_count from men_players order by total_count desc limit 1;

**N Djokovic**


with ladies_players as (with 
us_ladies_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, count(player1) as count1 from us_ladies_2013 group by player order by player),
us_ladies_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, count(player2) as count2 from us_ladies_2013 group by player order by player),
aus_ladies_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, count(player1) as count1 from aus_ladies_2013 group by player order by player),
aus_ladies_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, count(player2) as count2 from aus_ladies_2013 group by player order by player),
french_ladies_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, count(player1) as count1 from french_ladies_2013 group by player order by player),
french_ladies_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, count(player2) as count2 from french_ladies_2013 group by player order by player)
select coalesce(us_ladies_p1.player, us_ladies_p2.player, aus_ladies_p1.player, aus_ladies_p2.player, 
french_ladies_p1.player, french_ladies_p2.player) as player,
coalesce(us_ladies_p1.count1+us_ladies_p2.count2, us_ladies_p1.count1, us_ladies_p2.count2) as us_count,
coalesce(aus_ladies_p1.count1+aus_ladies_p2.count2, aus_ladies_p1.count1, aus_ladies_p2.count2) as aus_count,
coalesce(french_ladies_p1.count1+french_ladies_p2.count2, french_ladies_p1.count1, french_ladies_p2.count2) as french_count
from us_ladies_p1
full outer join us_ladies_p2 on us_ladies_p1.player=us_ladies_p2.player
full outer join aus_ladies_p1 on us_ladies_p1.player=aus_ladies_p1.player
full outer join aus_ladies_p2 on us_ladies_p1.player=aus_ladies_p2.player
full outer join french_ladies_p1 on us_ladies_p1.player=french_ladies_p1.player
full outer join french_ladies_p2 on us_ladies_p1.player=french_ladies_p2.player)
select player, coalesce((coalesce(us_count+aus_count, us_count, aus_count)+french_count), coalesce(us_count+aus_count, us_count, aus_count), french_count) as total_count from ladies_players order by total_count desc limit 1;

**S Williams**


# 3

with men_players as (with 
us_men_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, fsp_1 as us_fsp_1 from us_men_2013 order by player),
us_men_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, fsp_2 as us_fsp_2 from us_men_2013 order by player),
aus_men_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, fsp_1 as aus_fsp_1 from aus_men_2013 order by player),
aus_men_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, fsp_2 as aus_fsp_2 from aus_men_2013 order by player),
french_men_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, fsp_1 as french_fsp_1 from french_men_2013 order by player),
french_men_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, fsp_2 as french_fsp_2 from french_men_2013 order by player),
wimbledon_men_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), '.')-1)) as player, fsp_1 as wimbledon_fsp_1 from wimbledon_men_2013 order by player),
wimbledon_men_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), '.')-1)) as player, fsp_2 as wimbledon_fsp_2 from wimbledon_men_2013 order by player)
select coalesce(us_men_p1.player, us_men_p2.player, aus_men_p1.player, aus_men_p2.player, 
french_men_p1.player, french_men_p2.player, wimbledon_men_p1.player, wimbledon_men_p2.player) as player, 
us_fsp_1, us_fsp_2, aus_fsp_1, aus_fsp_2, french_fsp_1, french_fsp_2, wimbledon_fsp_1, wimbledon_fsp_2
from us_men_p1
full outer join us_men_p2 on us_men_p1.player=us_men_p2.player
full outer join aus_men_p1 on us_men_p1.player=aus_men_p1.player
full outer join aus_men_p2 on us_men_p1.player=aus_men_p2.player
full outer join french_men_p1 on us_men_p1.player=french_men_p1.player
full outer join french_men_p2 on us_men_p1.player=french_men_p2.player
full outer join wimbledon_men_p1 on us_men_p1.player=wimbledon_men_p1.player
full outer join wimbledon_men_p2 on us_men_p1.player=wimbledon_men_p2.player)
select player, (SELECT MAX(fsp)
      FROM (VALUES 
      (us_fsp_1),
      (us_fsp_2),
      (aus_fsp_1),
      (aus_fsp_2),
      (french_fsp_1),
      (french_fsp_2),
      (wimbledon_fsp_1),
      (wimbledon_fsp_2)) 
      AS fsp(fsp)) from men_players
      order by max desc limit 1;
      
**V Hanescu**
      
      
with ladies_players as (with 
us_ladies_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, fsp_1 as us_fsp_1 from us_ladies_2013 order by player),
us_ladies_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, fsp_2 as us_fsp_2 from us_ladies_2013 order by player),
aus_ladies_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, fsp_1 as aus_fsp_1 from aus_ladies_2013 order by player),
aus_ladies_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, fsp_2 as aus_fsp_2 from aus_ladies_2013 order by player),
french_ladies_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, fsp_1 as french_fsp_1 from french_ladies_2013 order by player),
french_ladies_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, fsp_2 as french_fsp_2 from french_ladies_2013 order by player),
wimbledon_ladies_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), '.')-1)) as player, fsp_1 as wimbledon_fsp_1 from wimbledon_ladies_2013 order by player),
wimbledon_ladies_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), '.')-1)) as player, fsp_2 as wimbledon_fsp_2 from wimbledon_ladies_2013 order by player)
select coalesce(us_ladies_p1.player, us_ladies_p2.player, aus_ladies_p1.player, aus_ladies_p2.player, 
french_ladies_p1.player, french_ladies_p2.player, wimbledon_ladies_p1.player, wimbledon_ladies_p2.player) as player, 
us_fsp_1, us_fsp_2, aus_fsp_1, aus_fsp_2, french_fsp_1, french_fsp_2, wimbledon_fsp_1, wimbledon_fsp_2
from us_ladies_p1
full outer join us_ladies_p2 on us_ladies_p1.player=us_ladies_p2.player
full outer join aus_ladies_p1 on us_ladies_p1.player=aus_ladies_p1.player
full outer join aus_ladies_p2 on us_ladies_p1.player=aus_ladies_p2.player
full outer join french_ladies_p1 on us_ladies_p1.player=french_ladies_p1.player
full outer join french_ladies_p2 on us_ladies_p1.player=french_ladies_p2.player
full outer join wimbledon_ladies_p1 on us_ladies_p1.player=wimbledon_ladies_p1.player
full outer join wimbledon_ladies_p2 on us_ladies_p1.player=wimbledon_ladies_p2.player)
select player, (SELECT MAX(fsp)
      FROM (VALUES 
      (us_fsp_1),
      (us_fsp_2),
      (aus_fsp_1),
      (aus_fsp_2),
      (french_fsp_1),
      (french_fsp_2),
      (wimbledon_fsp_1),
      (wimbledon_fsp_2)) 
      AS fsp(fsp)) from ladies_players
      order by max desc limit 1; 
      
**S Errani**


# 4

with men_players as (with 
us_men_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, sum(result) as us_result_1, sum(coalesce(ufe_1,0)) as us_ufe_1, sum(coalesce(tpw_1,0)) as us_tpw_1 from us_men_2013 group by player order by player),
us_men_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, sum(1-result) as us_result_2, sum(coalesce(ufe_2,0)) as us_ufe_2, sum(coalesce(tpw_2,0)) as us_tpw_2 from us_men_2013 group by player order by player),
aus_men_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, sum(result) as aus_result_1, sum(coalesce(ufe_1,0)) as aus_ufe_1, sum(coalesce(tpw_1,0)) as aus_tpw_1 from aus_men_2013 group by player order by player),
aus_men_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, sum(1-result) as aus_result_2, sum(coalesce(ufe_2,0)) as aus_ufe_2, sum(coalesce(tpw_2,0)) as aus_tpw_2 from aus_men_2013 group by player order by player),
french_men_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, sum(result) as french_result_1, sum(coalesce(ufe_1,0)) as french_ufe_1, sum(coalesce(tpw_1,0)) as french_tpw_1 from french_men_2013 group by player order by player),
french_men_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, sum(1-result) as french_result_2, sum(coalesce(ufe_2,0)) as french_ufe_2, sum(coalesce(tpw_2,0)) as french_tpw_2 from french_men_2013 group by player order by player),
wimbledon_men_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), '.')-1)) as player, sum(result) as wimbledon_result_1, sum(coalesce(ufe_1,0)) as wimbledon_ufe_1, sum(coalesce(tpw_1,0)) as wimbledon_tpw_1 from wimbledon_men_2013 group by player order by player),
wimbledon_men_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), '.')-1)) as player, sum(1-result) as wimbledon_result_2, sum(coalesce(ufe_2,0)) as wimbledon_ufe_2, sum(coalesce(tpw_2,0)) as wimbledon_tpw_2 from wimbledon_men_2013 group by player order by player)
select coalesce(us_men_p1.player, us_men_p2.player, aus_men_p1.player, aus_men_p2.player, 
french_men_p1.player, french_men_p2.player, wimbledon_men_p1.player, wimbledon_men_p2.player) as player,
us_result_1, us_result_2, aus_result_1, aus_result_2, french_result_1, french_result_2, wimbledon_result_1, wimbledon_result_2,
us_ufe_1, us_ufe_2, aus_ufe_1, aus_ufe_2, french_ufe_1, french_ufe_2, wimbledon_ufe_1, wimbledon_ufe_2, 
us_tpw_1, us_tpw_2, aus_tpw_1, aus_tpw_2, french_tpw_1, french_tpw_2, wimbledon_tpw_1, wimbledon_tpw_2
from us_men_p1
full outer join us_men_p2 on us_men_p1.player=us_men_p2.player
full outer join aus_men_p1 on us_men_p1.player=aus_men_p1.player
full outer join aus_men_p2 on us_men_p1.player=aus_men_p2.player
full outer join french_men_p1 on us_men_p1.player=french_men_p1.player
full outer join french_men_p2 on us_men_p1.player=french_men_p2.player
full outer join wimbledon_men_p1 on us_men_p1.player=wimbledon_men_p1.player
full outer join wimbledon_men_p2 on us_men_p1.player=wimbledon_men_p2.player)
select player,
sum(coalesce(us_result_1,0))+sum(coalesce(us_result_2,0))+sum(coalesce(aus_result_1,0))+sum(coalesce(aus_result_2,0))+sum(coalesce(french_result_1,0))+sum(coalesce(french_result_2,0))+sum(coalesce(wimbledon_result_1,0))+sum(coalesce(wimbledon_result_2,0)) as total_games_won,
(100*(sum(coalesce(us_ufe_1,0.000001))+sum(coalesce(us_ufe_2,0.000001))+sum(coalesce(aus_ufe_1,0.000001))+sum(coalesce(aus_ufe_2,0.000001))+sum(coalesce(french_ufe_1,0.000001))+sum(coalesce(french_ufe_2,0.000001))+sum(coalesce(wimbledon_ufe_1,0.000001))+sum(coalesce(wimbledon_ufe_2,0.000001)))/
(sum(coalesce(us_tpw_1,0.001))+sum(coalesce(us_tpw_2,0.001))+sum(coalesce(aus_tpw_1,0.001))+sum(coalesce(aus_tpw_2,0.001))+sum(coalesce(french_tpw_1,0.001))+sum(coalesce(french_tpw_2,0.001))+sum(coalesce(wimbledon_tpw_1,0.001))+sum(coalesce(wimbledon_tpw_2,0.001)))) as ufe_pct
from men_players group by player order by total_games_won
desc limit 3;

**N Djokovic, 27%; R Nadal, 18%; D Ferrer, 23%**


with ladies_players as (with 
us_ladies_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, sum(result) as us_result_1, sum(coalesce(ufe_1,0)) as us_ufe_1, sum(coalesce(tpw_1,0)) as us_tpw_1 from us_ladies_2013 group by player order by player),
us_ladies_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, sum(1-result) as us_result_2, sum(coalesce(ufe_2,0)) as us_ufe_2, sum(coalesce(tpw_2,0)) as us_tpw_2 from us_ladies_2013 group by player order by player),
aus_ladies_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, sum(result) as aus_result_1, sum(coalesce(ufe_1,0)) as aus_ufe_1, sum(coalesce(tpw_1,0)) as aus_tpw_1 from aus_ladies_2013 group by player order by player),
aus_ladies_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, sum(1-result) as aus_result_2, sum(coalesce(ufe_2,0)) as aus_ufe_2, sum(coalesce(tpw_2,0)) as aus_tpw_2 from aus_ladies_2013 group by player order by player),
french_ladies_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), ' ')-1)) as player, sum(result) as french_result_1, sum(coalesce(ufe_1,0)) as french_ufe_1, sum(coalesce(tpw_1,0)) as french_tpw_1 from french_ladies_2013 group by player order by player),
french_ladies_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), ' ')-1)) as player, sum(1-result) as french_result_2, sum(coalesce(ufe_2,0)) as french_ufe_2, sum(coalesce(tpw_2,0)) as french_tpw_2 from french_ladies_2013 group by player order by player),
wimbledon_ladies_p1 as (select concat_ws(' ', left(player1, 1), right(player1, strpos(reverse(player1), '.')-1)) as player, sum(result) as wimbledon_result_1, sum(coalesce(ufe_1,0)) as wimbledon_ufe_1, sum(coalesce(tpw_1,0)) as wimbledon_tpw_1 from wimbledon_ladies_2013 group by player order by player),
wimbledon_ladies_p2 as (select concat_ws(' ', left(player2, 1), right(player2, strpos(reverse(player2), '.')-1)) as player, sum(1-result) as wimbledon_result_2, sum(coalesce(ufe_2,0)) as wimbledon_ufe_2, sum(coalesce(tpw_2,0)) as wimbledon_tpw_2 from wimbledon_ladies_2013 group by player order by player)
select coalesce(us_ladies_p1.player, us_ladies_p2.player, aus_ladies_p1.player, aus_ladies_p2.player, 
french_ladies_p1.player, french_ladies_p2.player, wimbledon_ladies_p1.player, wimbledon_ladies_p2.player) as player,
us_result_1, us_result_2, aus_result_1, aus_result_2, french_result_1, french_result_2, wimbledon_result_1, wimbledon_result_2,
us_ufe_1, us_ufe_2, aus_ufe_1, aus_ufe_2, french_ufe_1, french_ufe_2, wimbledon_ufe_1, wimbledon_ufe_2, 
us_tpw_1, us_tpw_2, aus_tpw_1, aus_tpw_2, french_tpw_1, french_tpw_2, wimbledon_tpw_1, wimbledon_tpw_2
from us_ladies_p1
full outer join us_ladies_p2 on us_ladies_p1.player=us_ladies_p2.player
full outer join aus_ladies_p1 on us_ladies_p1.player=aus_ladies_p1.player
full outer join aus_ladies_p2 on us_ladies_p1.player=aus_ladies_p2.player
full outer join french_ladies_p1 on us_ladies_p1.player=french_ladies_p1.player
full outer join french_ladies_p2 on us_ladies_p1.player=french_ladies_p2.player
full outer join wimbledon_ladies_p1 on us_ladies_p1.player=wimbledon_ladies_p1.player
full outer join wimbledon_ladies_p2 on us_ladies_p1.player=wimbledon_ladies_p2.player)
select player,
sum(coalesce(us_result_1,0))+sum(coalesce(us_result_2,0))+sum(coalesce(aus_result_1,0))+sum(coalesce(aus_result_2,0))+sum(coalesce(french_result_1,0))+sum(coalesce(french_result_2,0))+sum(coalesce(wimbledon_result_1,0))+sum(coalesce(wimbledon_result_2,0)) as total_games_won,
(100*(sum(coalesce(us_ufe_1,0.000001))+sum(coalesce(us_ufe_2,0.000001))+sum(coalesce(aus_ufe_1,0.000001))+sum(coalesce(aus_ufe_2,0.000001))+sum(coalesce(french_ufe_1,0.000001))+sum(coalesce(french_ufe_2,0.000001))+sum(coalesce(wimbledon_ufe_1,0.000001))+sum(coalesce(wimbledon_ufe_2,0.000001)))/
(sum(coalesce(us_tpw_1,0.001))+sum(coalesce(us_tpw_2,0.001))+sum(coalesce(aus_tpw_1,0.001))+sum(coalesce(aus_tpw_2,0.001))+sum(coalesce(french_tpw_1,0.001))+sum(coalesce(french_tpw_2,0.001))+sum(coalesce(wimbledon_tpw_1,0.001))+sum(coalesce(wimbledon_tpw_2,0.001)))) as ufe_pct
from ladies_players group by player order by total_games_won
desc limit 3;

**S Williams, 52%; N Li, 75%; V Azarenka, 55%**
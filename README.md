# Checkers-MinMax-AI
 
## Approach to Raichu
<h2>Abstraction:</h2><br><br>
<b>Set of Valid States: </b>
<p>All legal moves made by the player's pichu(w/b) , pikachu(W,B) and raichu(@,$).</p><br><br>
<b>Successor Function:</b>
<p>This function takes board as a parameter and return the list of legal possible moves of the player pieces by validating all scenarios.</p><br><br>
<b>Cost Function:</b>
<p>Cost of generating legal move for the pieces available is uniform.</p><br><br>
<b>Goal State:</b>
<p>The goal state, according to the problem statement, is the best possible legal move for the board that maximizes the likelihood of a player winning within a defined timeframe.</p><br><br>
<b>Initial State:</b>
<p>Board consiting of pieces of two players to determine possible next move.</p><br><br>

<b>Description of Successor Function:</b><br>
<p>It takes board as a parameter.</p><br>
<b>Valid Pichu moves:</b>
<ol>
<li>Pichu can travel diagonally forward, i.e. left and right for one step which should be empty.</li>
<li>Furthermore, pichu can jump over other player single pichu, eliminating them from the board, and placing our pichu on the second step, which should be empty.</li>
</ol><br>
<b>Valid Pikachu moves:</b>
<ol>
<li>Pikachu can travel forward, left and right for one and two steps which should be empty.</li>
<li>Furthermore, Pikachu can jump over other player's single Pichu or Pikachu, eliminating them from the board, and placing our pikachu on second and third step, which should be empty.</li>
</ol><br>
<b>Valid Raichu Moves:</b>
<ol>
<li>Raichu is generated in the board whenever pichu or pikachu reaches the oppsoite end of the board.</li>
<li>Raichu can travel forward,left,right and diagonally as long as empty squares.</li>
<li>Furthermore, raichu can jump over other player's single Pichu,Pikachu and raichu as well, eliminating them from the board, and placing our raichu on any sqaure as long as empty sqaures in between.</li>
</ol>
<br>
<p>Based on the above rules, player generates all the legal moves and add them into the list which will be used to generate best possible move using min max algorithm.</p><br><br> 


<b>Description of Algorithm:</b><br>
<p>Implemented the <b>MIN-MAX</b> Algorithm along with <i>alpha-beta pruning</i> to disregard some states in order to determine the best next move for the given board.</p><br>
<ol>
<li>This algorithm takes (board,depth,maxplayer as boolean value,alpha,beta) values and returns the max move after exploring specified depth.</li>
<li>Algorithm creates a recursive tree starting with max moves and min moves recursively for specified depth and when it reaches the leaf node, evaluation function is invoked to calculate the score of the leaf board.</li>
<li>Using this algorithm, determines the optimal move among all the possible moves which increases the chance of winning by exploring the opponent's move by the move we make in recursive manner by minimizing their chance of winning and after certain depth evaluates the score of the leaf board and by bottom up approach takes the min score and gives to their parent board and max score of those will be given to their parent.when this reaches to the root move, we get the max move out of all the possible moves which can be safe and increase our chance of winning game.</li>
<li>We use alpha beta pruning, for ignoring some of the states which may not lead to the solution by expanding those moves.So we check alpha and beta everytime we expand, such that when beta value is less than the max value of min boards explored we ignore expanding those moves in same level.
Similarly when the alpha value is greater than the min value of max boards explored we ignore expanding that moves in same level.</li>
</ol>

<bR><br>

<b>Evaluation Function:</b>
<br>
<ol>
<li>Calculating the difference between left over pieces on board of each player.</li>
<li>Along with the above one, assigned some weights for pieces such that some pieces get more preference when they are present on board.
Calculating the weighted difference between left over pieces on board of each player.</li>
<li>Weights Assigned are:
<ul>
<li><b>Pichu:</b>1</li>
<li><b>Pikachu:</b> 10</li>
<li><b>Raichu:</b> 50 </li>
</ul></li></ol><br><br>

<p>Increasing depth everytime for minmax algorithm starting from 1, since there is a time limit by which the program gets killed.Thought of having atleast one move before exceeding the timelimit. So used this approach iteratively.</p><br>
<p>It was nice experience playing with AI on tank server ended in couple of draws and win.</p>

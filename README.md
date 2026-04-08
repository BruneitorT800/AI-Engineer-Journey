# AI-Engineer-Journey
Curso de Bruno

Introduction - DONE 31/03/26

 Lunes
   SEARCH EDX audit

 Lecture 0 - Pendant 06/04
 Notes
 Slides
 Source Code

 Martes
 Repasar y practicar con QUIZ 0 - Pendant 07/04

 Miercoles
 Project 0 - Pendant 08/04

 Jueves
 Lecture 1 - Pendant 09/04
 Notes
 Slides
 Source Code

 Viernes
  Repasar y practicar con QUIZ 1 - Pendant 10/04

 Sabado
Project 1 - Pendant 11/04


  # Introduction

Search - Its when we have a Problem and want de AI to find a solution.

Knowledge - We want de AI to know information and use it to resolve problems

Uncertainty -  What happens if a computer isnt sure about a fact, but has some probability about something. How does it deal with uncertain events.

Optimization - Problems in where the computer is looking for the best way to solve a problem

Learning - When we have acces to data our Computer can became smarter learning for past experiences and past data.

Neural Networks - How computers are able to draw inspiration in human inteligence, looking at the construction of the human brain

Language - Human languagues, challenges that come with computers understanding human.

 # Lecture 0 SEARCH

A puzzle can be a search problem, or trying to find the way in a maze. What goes in to find a solution?

 AGENT - entity that perceives its environment and acts upon that environment

 STATE - a configuration of the agent and its environment

 INITIAL STATE - State in which the Agent begins

 ACTIONS - choices that can be made in a state
 Can be written as a function

 ACTIONS(S) returns the set of actions that can be executed in state s

 TRANSITION MODEL - a description of what state results from performing any applicable action in any state. Also can be defined as a function:

  RESULT(s,a) returns the state resulting from performing action a in state s. Then the output is a new state

 STATE SPACE - the set of all states reachable from the initial state by any sequence of actions

 GOAL TEST - way to determine whether a given state is a goal state. Some problems may have multiple ways to solve a problem.

 PATH COST - numerical cost associated with a given path. How expensive is the option.

 SOLUTION - a sequence of actions that leads from the initial state to a goal state

 OPTIMAL SOLUTION - a solution that has the lowest pasth cost among the other solutions

 NODE - a data structure that keeps track of

  - a state
  - a parent (node that generated this node)
  - an action (action applied to parent to get node)
  - a path cost (from initial state to node)


        APPROACH

    - Start with a frontier that contains the initial state.
    - Repeat:
      - if the frontier is empty, then no solution
      - Remove a node from the frontier
      - If a node contains goal state. return solution
      - Expand node, add resulting nodes to the frontier

       REVISED APPROACH

    - Start with a frontier that contains the initial state.
    - Start with an empty explored set.
    - Repeat:
      - if the frontier is empty, then no solution
      - Remove a node from the frontier
      - If a node contains goal state. return solution
      - add the node to the explored set
      - Expand node, add resulting nodes to the frontier if they aren't already in the frontier or the explored set

  STACK - last-in first-out data type that allow the...

  DEPTH-FIRST SEARCH - search algorithm that always expands the deepest node in the frontier / or

  BREADTH-FIRST SEARCH - search algorithm that always expands the shallowest node in the frontier. This uses queue instead of stack

  QUEUE - first-in first-out data type

 # PRACTICE IN MAZE.py

 UNINFORMED SEARCH - search strategy that uses no problem-specific knowledge

 INFORMED SEARCH - search strategy that uses problem-specific knowledge to find solutions more efficiently

  - GREEDY BEST_FIRST SEARCH: search agorithm that expands the node that is closet to the goal, as estimated by a heuristic function h(n)
  - A* SEARCH: search algorithm that expands node with lowest value of g(n) + h(n)

   g(n) = cost to reach node
   h(n) = estimated cost to goal

    Optimal if:
    - h(n) is admissible (never overestimates the true cost), and
    - h(n) is consistent (for every node n and successor n' with step cost c, h(n) ≤ h(n') + c)

 - ADVERSARIAL SEARCH: When someone wants me to fail, like in tic tac toe.

  We need to translate it in terms that the computer can undestand, something numerical (bigger o smaller)

  - MINIMAX: 3 possibles outcomes, player one wins (-1) nobody wins (0) player two wins (1).

   MAX(X) is triyng to maximize the escore
   MIN(O) aims to minimize score


# ECODING TIC TAC TOE IN AI:

 - GAME

  - So: Initial state
  - Player(s): returns which player to move in state "s"
  - Actions(s): returns legal moves in state "s"
  - Result(s,a): returns state after action "a" taken in state "s"
  - Terminal(s): checks if state "s" is a terminal state
  - Utility(s): Final numerical value for terminal state "s"

# MINIMAX

- Given a state "s":
  - MAX picks action "a" in ACTIONS(s) that produces highest value of MIN-VALUE(RESULT(s,a))
  - MIN picks action "a" in ACTIONS(s) that produces smallest value of MAX-VALUE(RESULT(s,a))

- function MAX-VALUE(state)
  - if TERMINAL(state):
    return UTILITY(state)
  v= -infinity
  for action in ACTIONS(state):
    v= MAX(v,MIN-VALUE(RESULT(state,action)))
  return v

- function MIN-VALUE(state)
  - if TERMINAL(state):
    return UTILITY(state)
  v= infinity
  for action in ACTIONS(state):
    v= MIN(v,MAX-VALUE(RESULT(state,action)))
  return v


- ALPHA-BETHA PRUNING: Optimal way to search, save us time making it more efficient.

- DEPTH-LIMITED MINIMAX: Limits the amount of moves that it will consider
  - EVALUATION FUNCTION: function that estimates the expected utility of the game from a given state
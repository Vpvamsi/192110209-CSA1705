from collections import deque
def is_valid_state(state):
    missionaries_left, cannibals_left, boat = state
    missionaries_right = 3 - missionaries_left
    cannibals_right = 3 - cannibals_left
    if missionaries_left > 0 and missionaries_left < cannibals_left:
        return False
    if missionaries_right > 0 and missionaries_right < cannibals_right:
        return False

    return True
def get_successor_states(state):
    states = []
    missionaries_left, cannibals_left, boat = state

    if boat == 1:
        for m in range(3 + 1):
            for c in range(3 + 1):
                if 1 <= m + c <= 2:
                    new_state = (missionaries_left - m, cannibals_left - c, 0)
                    if is_valid_state(new_state):
                        states.append(new_state)
    else:
        for m in range(3 + 1):
            for c in range(3 + 1):
                if 1 <= m + c <= 2:  # At most two people in the boat
                    new_state = (missionaries_left + m, cannibals_left + c, 1)
                    if is_valid_state(new_state):
                        states.append(new_state)
    return states
def solve_missionaries_cannibals():
    start_state = (3, 3, 1)  # Initial state: 3 missionaries, 3 cannibals, boat on the left
    goal_state = (0, 0, 0)    # Goal state: 0 missionaries, 0 cannibals, boat on the right
    visited = set()
    queue = deque([(start_state, [])])
    while queue:
        current_state, path = queue.popleft()
        if current_state == goal_state:
            return path + [goal_state]
        visited.add(current_state)
        for successor_state in get_successor_states(current_state):
            if successor_state not in visited:
                queue.append((successor_state, path + [current_state]))
    return None
def main():
    solution = solve_missionaries_cannibals()
    if solution:
        print("Solution found:")
        for step, state in enumerate(solution):
            print(f"Step {step + 1}: {state}")
    else:
        print("No solution found for the given problem.")
if __name__ == "__main__":
    main()

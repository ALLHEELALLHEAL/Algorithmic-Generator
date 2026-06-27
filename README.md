# Algorithmic-Generator
birth to create

import random

class GenerativeBirthEngine:
    """
    A constraint-based generative engine.
    Rules:
    1. Image = Birth
    2. Birth enforces (!=0, !=1) constraint
    3. Origin = (random0 - (0, 1))
    """
    
    def __init__(self, retry_limit=100):
        self.retry_limit = retry_limit

    def _get_origin(self, random_val):
        # The dynamic differential operator
        return [0, 1, random_val - 0, random_val - 1]

    def birth(self):
        # The resolution mechanism with safety constraint
        for _ in range(self.retry_limit):
            r = random.random()
            origin_set = self._get_origin(r)
            candidate = random.choice(origin_set)
            
            # The Human Fingerprint: Exclusion constraint
            if candidate != 0 and candidate != 1:
                return candidate
        
        return "ERROR: Constraint not satisfied"

    def generate_image(self, length=20):
        # The formatting loop
        sequence = [f"{self.birth():.3f}-" for _ in range(length)]
        return "".join(sequence)

# --- Execution ---
if __name__ == "__main__":
    engine = GenerativeBirthEngine()
    print("--- Generative Pattern Output ---")
    print(engine.generate_image(15))


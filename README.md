- 👋 Hi, I’m @Lalithakoyinana
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
Lalithakoyinana/Lalithakoyinana is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
import java.util.Random;

class Player {
    int health;
    int strength;
    int attack;

    public Player(int health, int strength, int attack) {
        this.health = health;
        this.strength = strength;
        this.attack = attack;
    }
}

public class MagicalArena {
    static Random random = new Random();

    public static int rollDie() {
        return random.nextInt(6) + 1; // 1 to 6 sided die
    }

    public static void fight(Player attacker, Player defender) {
        int attackRoll = rollDie();
        int defenseRoll = rollDie();

        int attackDamage = attacker.attack * attackRoll;
        int defenseStrength = defender.strength * defenseRoll;

        int damageTaken = Math.max(0, attackDamage - defenseStrength);
        defender.health -= damageTaken;

        System.out.println("Attacker rolls " + attackRoll + ", Defender rolls " + defenseRoll);
        System.out.println("Attack damage: " + attackDamage + ", Defense strength: " + defenseStrength);
        System.out.println("Defender health reduced by " + damageTaken + " to " + defender.health + "\n");
    }

    public static void main(String[] args) {
        Player playerA = new Player(50, 5, 10);
        Player playerB = new Player(100, 10, 5);

        while (playerA.health > 0 && playerB.health > 0) {
            if (playerA.health < playerB.health) {
                fight(playerA, playerB);
                if (playerB.health <= 0) {
                    System.out.println("Player A wins!");
                    break;
                }
                fight(playerB, playerA);
                if (playerA.health <= 0) {
                    System.out.println("Player B wins!");
                    break;
                }
            } else {
                fight(playerB, playerA);
                if (playerA.health <= 0) {
                    System.out.println("Player B wins!");
                    break;
                }
                fight(playerA, playerB);
                if (playerB.health <= 0) {
                    System.out.println("Player A wins!");
                    break;
                }
            }
        }
    }
}

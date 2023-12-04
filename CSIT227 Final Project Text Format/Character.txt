/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */

/**
 *
 * @author Nathan
 */
class Character implements Damageable {
    String name;
    int health;
    int attackPower;

    public Character(String name, int health, int attackPower) {
        this.name = name;
        this.health = health;
        this.attackPower = attackPower;
    }

     public void attack(Enemy enemy, String attackType) {
        int damage = 0;

        switch (attackType.toLowerCase()) {
            case "normal":
                damage = calculateDamage(1.0);
                break;
            case "skill":
                damage = calculateDamage(1.5);
                break;
            case "special":
                damage = calculateDamage(2.0);
                break;
            default:
                System.out.println("Invalid attack type. Using normal attack.");
                damage = calculateDamage(1.0);
        }

        enemy.takeDamage(damage);
        System.out.println(name + " uses " + attackType + " attack on " + enemy.name + " for " + damage + " damage!");
     }
     
     @Override
    public void takeDamage(int damage) {
        health -= damage;
        if (health <= 0) {
            System.out.println(name + " has been defeated!");
        }
    }
     
      private int calculateDamage(double multiplier) {
        // Implement damage calculation logic here
        // You can modify this based on your game's requirements
        return (int) (attackPower * multiplier);
    }
}

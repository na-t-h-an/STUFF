/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */

/**
 *
 * @author Nathan
 */
import java.util.Random;
class Enemy implements Damageable {
    String name;
    int health;
    int attackPower;
    int minDamage;
    int maxDamage;

    private Random random = new Random();

    public Enemy(String name, int health, int attackPower, int minDamage, int maxDamage) {
        this.name = name;
        this.health = health;
        this.attackPower = attackPower;
        this.minDamage = minDamage;
        this.maxDamage = maxDamage;
    }
    
    @Override
    public void takeDamage(int damage) {
        health -= damage;
        if (health <= 0) {
            System.out.println(name + " has been defeated!");
        }
    }
    
    public void attack(Character character) {
        int damage = random.nextInt(maxDamage - minDamage + 1) + minDamage;
        character.health -= damage;

        System.out.println(name + " attacks " + character.name + " for " + damage + " damage!");

        if (character.health <= 0) {
            System.out.println(character.name + " has been defeated!");
        }
    }
}

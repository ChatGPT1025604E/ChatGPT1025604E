- 👋 Hi, I’m @ChatGPT1025604E
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
ChatGPT1025604E/ChatGPT1025604E is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
jogo de mundo ab// Movimento básico da personagem
float speed = 5.0f;
void Update() {
    float moveHorizontal = Input.GetAxis("Horizontal");
    float moveVertical = Input.GetAxis("Vertical");
    Vector3 movement = new Vector3(moveHorizontal, 0.0f, moveVertical);
    transform.Translate(movement * speed * Time.deltaTime);
}// Sistema de combate básico
public float attackDamage = 10.0f;
void OnTriggerEnter(Collider other) {
    if (other.gameObject.CompareTag("Enemy")) {
        other.gameObject.GetComponent<EnemyHealth>().TakeDamage(attackDamage);
    }
}// Gerenciamento de missões básico
public List<Mission> missions = new List<Mission>();
void CheckMissionCompletion() {
    foreach (Mission mission in missions) {
        if (mission.IsComplete()) {
            CompleteMission(mission);
        }
    }
}// Sistema de inventário básico
public class Inventory : MonoBehaviour {
    public List<Item> items = new List<Item>();

    public void AddItem(Item item) {
        items.Add(item);
    }

    public void RemoveItem(Item item) {
        items.Remove(item);
    }
}

public class Item : MonoBehaviour {
    public string itemName;
    public int itemID;
}// Sistema de diálogo básico
public class DialogueTrigger : MonoBehaviour {
    public Dialogue dialogue;

    public void TriggerDialogue() {
        FindObjectOfType<DialogueManager>().StartDialogue(dialogue);
    }
}

[System.Serializable]
public class Dialogue {
    public string name;
    [TextArea(3, 10)]
    public string[] sentences;
}// Sistema de pontuação básico
public class ScoreManager : MonoBehaviour {
    public int score = 0;
// Sistema de pontuação básico
public class ScoreManager : MonoBehaviour {
    public int score = 0;

    public void IncreaseScore(int amount) {
        score += amount;
    }

    public void ResetScore() {
        score = 0;
    }
}using UnityEngine;

public class Gatona : MonoBehaviour
{
    public float speed = 5.0f;
    public int health = 100;
    public int attackDamage = 10;

    private Rigidbody rb;

    void Start()
    {
        rb = GetComponent<Rigidbody>();
    }

    void Update()
    {
        float moveHorizontal = Input.GetAxis("Horizontal");
        float moveVertical = Input.GetAxis("Vertical");
        Vector3 movement = new Vector3(moveHorizontal, 0.0f, moveVertical);
        rb.AddForce(movement * speed);
    }

    void OnTriggerEnter(Collider other)
    {
        if (other.gameObject.CompareTag("Enemy"))
        {
            other.gameObject.GetComponent<Enemy>().TakeDamage(attackDamage);
        }
    }

    public void TakeDamage(int damage)
    {
        health -= damage;
        if (health <= 0)
        {
            Die();
        }
    }

    void Die()
    {
        // Implementação da morte da Gatona
    }
}
    // Movimentação de câmera suave
public class CameraController : MonoBehaviour {
    public Transform target;
    public float smoothSpeed = 0.125f;
    public Vector3 offset;

    void LateUpdate() {
        Vector3 desiredPosition = target.position + offset;
        Vector3 smoothedPosition = Vector3.Lerp(transform.position, desiredPosition, smoothSpeed);
        transform.position = smoothedPosition;
        transform.LookAt(target);
    }
}// Controle de jogo básico
public class GameController : MonoBehaviour {
    public void PauseGame() {
        Time.timeScale = 0;
    }

    public void ResumeGame() {
        Time.timeScale = 1;
    }

    public void QuitGame() {
        Application.Quit();
    }
}// Sistema de animação básico
public class AnimatorController : MonoBehaviour {
    private Animator anim;

    void Start() {
        anim = GetComponent<Animator>();
    }

    public void PlayAnimation(string animationName) {
        anim.Play(animationName);
    }
}// Sistema de animação básico
public class AnimatorController : MonoBehaviour {
    private Animator anim;

    void Start() {
        anim = GetComponent<Animator>();
    }

    public void PlayAnimation(string animationName) {
        anim.Play(animationName);
    }// Sistema de HUD básico
public class HUDController : MonoBehaviour {
    public Text healthText;
    public Text scoreText;

    public void UpdateHealth(int health) {
        healthText.text = "Health: " + health.ToString();
    }

    public void UpdateScore(int score) {
        scoreText.text = "Score: " + score.ToString();
    }
}
}// Sistema de áudio básico
public class AudioManager : MonoBehaviour {
    public AudioSource soundEffect;

    public void PlaySoundEffect() {
        soundEffect.Play();
    }
}public class FinalBattle : MonoBehaviour
{
    public Gatona gatona;
    public Vilao vilao;

    void Start()
    {
        // Iniciar a luta final
        StartFinalBattle();
    }

    void StartFinalBattle()
    {
        // Mover a Gatona e o vilão para a arena de batalha
        gatona.transform.position = new Vector3(-5, 0, 0);
        vilao.transform.position = new Vector3(5, 0, 0);

        // Iniciar a animação de introdução da luta

        // Iniciar a batalha
        StartCoroutine(BattleRoutine());
    }

    IEnumerator BattleRoutine()
    {
        while (gatona.health > 0 && vilao.health > 0)
        {
            // Gatona ataca o vilão
            vilao.TakeDamage(gatona.attackDamage);

            // Vilão ataca a Gatona
            gatona.TakeDamage(vilao.attackDamage);

            yield return new WaitForSeconds(1.0f);
        }

        if (gatona.health <= 0)
        {
            // Vilão venceu
            EndBattle(false);
        }
        else
        {
            // Gatona venceu
            EndBattle(true);
        }
    }

    void EndBattle(bool gatonaVenceu)
    {
        if (gatonaVenceu)
        {
            // Gatona venceu, mostrar animação de vitória da Gatona
        }
        else
        {
            // Vilão venceu, mostrar animação de derrota da Gatona
        }

        // Exibir tela de fim de jogo ou retornar ao menu principal
    }
}

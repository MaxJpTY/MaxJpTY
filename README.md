using UnityEngine;
using UnityEngine.UI;

public class LoadingScreen : MonoBehaviour
{
    public Slider progressBar;
    public Text loadingText;

    private float loadingProgress = 0f;

    void Start()
    {
        // Simulate loading process (replace with actual loading logic)
        StartCoroutine(LoadGame());
    }

    System.Collections.IEnumerator LoadGame()
    {
        while (loadingProgress < 1f)
        {
            loadingProgress += Time.deltaTime; // Increment progress over time
            progressBar.value = loadingProgress;
            loadingText.text = "Loading... " + (int)(loadingProgress * 100) + "%";
            yield return null;
        }
        // Load complete, transition to game scene
        UnityEngine.SceneManagement.SceneManager.LoadScene("GameScene");
    }
}

# WordStatsAnalyzer









        import java.util.*; // کتابخانه‌های موردنیاز برای کار با مجموعه‌ها و نقشه‌ها

public class TextAnalyzer {
    public static void main(String[] args) {
        String text = "This is a sample text. This text is used for testing word and letter frequency.";
        text = text.toLowerCase(); 

        
        String[] words = text.replaceAll("[^a-zA-Z ]", "").split("\\s+");
        Map<String, Integer> wordCount = new HashMap<>(); 

        for (String word : words) {
            wordCount.put(word, wordCount.getOrDefault(word, 0) + 1); 
        }

        
        Map<Character, Integer> letterCount = new HashMap<>();
        for (char ch : text.replaceAll("[^a-zA-Z]", "").toCharArray()) {
            letterCount.put(ch, letterCount.getOrDefault(ch, 0) + 1); 
        }

        String mostFrequentWord = "";
        int maxFrequency = 0;
        for (Map.Entry<String, Integer> entry : wordCount.entrySet()) {
            if (entry.getValue() > maxFrequency) {
                mostFrequentWord = entry.getKey();
                maxFrequency = entry.getValue();
            }
        }

        List<Map.Entry<String, Integer>> sortedWords = new ArrayList<>(wordCount.entrySet());
        sortedWords.sort((a, b) -> Integer.compare(b.getValue(), a.getValue())); 

        System.out.println("Number of repetitions of each word:");
        for (Map.Entry<String, Integer> entry : sortedWords) {
            System.out.println(entry.getKey() + " <- " + entry.getValue());
        }

        System.out.println("\nNumber of repetitions of each letter:");
        for (Map.Entry<Character, Integer> entry : letterCount.entrySet()) {
            System.out.println(entry.getKey() + " <- " + entry.getValue());
        }

        System.out.println("\nMost frequent word: " + mostFrequentWord + " <- " + maxFrequency);
    }
}

import SwiftUI

struct ContentView: View {
    @State private var playerChoice = ""
    @State private var computerChoice = ""
    @State private var result = ""
    
    let choices = ["剪刀", "石頭", "布"]
    
    var body: some View {
        VStack {
            Text("好玩遊戲剪刀石頭布")
                .font(.largeTitle)
                .padding()
            
            Text("你的選擇: \(playerChoice)")
            Text("電腦的選擇: \(computerChoice)")
            
            HStack {
                ForEach(choices, id: \.self) { choice in
                    Button(action: {
                        playerChoice = choice
                        playGame()
                    }) {
                        Text(choice)
                            .padding()
                            .background(Color.blue)
                            .foregroundColor(.white)
                            .cornerRadius(10)
                    }
                }
            }
            
            Text("結果: \(result)")
                .font(.title)
                .padding()
        }
    }
    
    func playGame() {
        let randomIndex = Int.random(in: 0..<choices.count)
        computerChoice = choices[randomIndex]
        
        if playerChoice == computerChoice {
            result = "平手"
        } else if (playerChoice == "剪刀" && computerChoice == "布") || (playerChoice == "石頭" && computerChoice == "剪刀") || (playerChoice == "布" && computerChoice == "石頭") {
            result = "你贏了！"
        } else {
            result = "電腦贏了！"
        }
    }
}



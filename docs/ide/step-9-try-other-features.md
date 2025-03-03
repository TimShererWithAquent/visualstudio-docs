---
title: "Step 9: Try other features"
ms.date: 11/04/2016
ms.topic: tutorial
ms.prod: visual-studio-windows
ms.technology: vs-ide-general
ms.assetid: 1b0c5c80-e5a6-4f69-a4a4-0e89a82d4de0
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
  - "multiple"
---
# Step 9: Try other features
To learn more, try changing icons and colors, adding a game timer, and adding sounds. To make the game more challenging, try making the board bigger and adjusting the timer.

To download a completed version of the sample, see [Complete matching game tutorial sample](https://code.msdn.microsoft.com/Complete-Matching-Game-4cffddba).

## To try other features

- Replace the icons and colors with ones you choose.

    > [!TIP]
    > Try looking at the label's [Forecolor](<xref:System.Windows.Forms.Control.ForeColor%2A>) property.

- Add a game timer that tracks how long it takes for the player to win.

    > [!TIP]
    > To do this, you can add a label to display the elapsed time on the form above the <xref:System.Windows.Forms.TableLayoutPanel>, and add another timer to the form to track the time. Use code to start the timer when the player starts the game, and stop the timer after they match the last two icons.

- Add a sound when the player finds a match, another sound when the player uncovers two icons that don't match, and a third sound when the program hides the icons again.

    > [!TIP]
    > To play sounds, you can use the <xref:System.Media> namespace. See [Play sounds in Windows Forms app (C#)](http://youtu.be/qOh4ooHg1UU) or [How to play audio in Visual Basic](http://youtu.be/-4oPDeQrtMs) for more information.

- Make the game more difficult by making the board bigger.

    > [!TIP]
    > You'll need to do more than just add rows and columns to the TableLayoutPanel - you'll also need to consider the number of icons you create.

- Make the game more challenging by hiding the first icon if the player is too slow to respond and doesn't choose the second icon before a certain amount of time.

## To continue or review

- If you get stuck or have programming questions, try posting your question on one of the MSDN forums. See [Visual Basic forum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=vbgeneral) and [Visual C# forum](https://social.msdn.microsoft.com/Forums/vstudio/home?forum=csharpgeneral).

- There are great, free video learning resources available to you. To learn more about programming in Visual Basic, see [Visual Basic fundamentals: Development for absolute beginners](https://channel9.msdn.com/Series/Visual-Basic-Development-for-Absolute-Beginners). To learn more about programming in Visual C#, see [C# fundamentals: Development for absolute beginners](https://channel9.msdn.com/Series/C-Sharp-Fundamentals-Development-for-Absolute-Beginners).

- To return to the previous tutorial step, see [Step 8: Add a method to verify whether the player won](../ide/step-8-add-a-method-to-verify-whether-the-player-won.md).

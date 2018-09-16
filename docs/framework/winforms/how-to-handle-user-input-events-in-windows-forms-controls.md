---
title: 'Postupy: Obsluha událostí uživatelského vstupu v ovládacích prvcích Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: 3b15edfec25282d5a0b79ef48cabd2a27c694055
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/16/2018
ms.locfileid: "45677172"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="95c2e-102">Postupy: Obsluha událostí uživatelského vstupu v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95c2e-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="95c2e-103">Tento příklad ukazuje, jak zpracovat většinu klávesnice, myši, fokus a ověřovací události, které mohou nastat v ovládacím prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="95c2e-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="95c2e-104">Textové pole s názvem `TextBoxInput` přijímá události, když má fokus, a informace o každé události je zapsaný do textového pole s názvem `TextBoxOutput` v pořadí, ve kterém jsou vyvolány události.</span><span class="sxs-lookup"><span data-stu-id="95c2e-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="95c2e-105">Aplikace také obsahuje sadu políčka, která umožňuje filtrovat události do sestavy.</span><span class="sxs-lookup"><span data-stu-id="95c2e-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="95c2e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="95c2e-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="95c2e-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="95c2e-107">Compiling the Code</span></span>  
 <span data-ttu-id="95c2e-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="95c2e-108">This example requires:</span></span>  
  
-   <span data-ttu-id="95c2e-109">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="95c2e-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="95c2e-110">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="95c2e-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="95c2e-111">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="95c2e-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="95c2e-112">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="95c2e-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95c2e-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="95c2e-113">See Also</span></span>  
 [<span data-ttu-id="95c2e-114">Uživatelský vstup ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="95c2e-114">User Input in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-in-windows-forms.md)

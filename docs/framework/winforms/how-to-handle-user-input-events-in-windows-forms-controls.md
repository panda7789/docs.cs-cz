---
title: "Postupy: Obsluha událostí uživatelského vstupu v ovládacích prvcích Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b8255d279f6a5e33df696673bae749f62b8ecf2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="40e53-102">Postupy: Obsluha událostí uživatelského vstupu v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40e53-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="40e53-103">Tento příklad ukazuje, jak zpracovat většinu klávesnice, myš, fokus a události ověřování, které se můžou vyskytnout v ovládacím prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="40e53-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="40e53-104">Textové pole s názvem `TextBoxInput` přijímá události, když je zaměřen a informace o každé události jsou zapsány do textového pole s názvem `TextBoxOutput` v pořadí, ve kterém jsou vyvolány události.</span><span class="sxs-lookup"><span data-stu-id="40e53-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="40e53-105">Aplikace také obsahuje sadu políček, která mohou být použity k filtrování události, které do sestavy.</span><span class="sxs-lookup"><span data-stu-id="40e53-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="40e53-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="40e53-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="40e53-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="40e53-107">Compiling the Code</span></span>  
 <span data-ttu-id="40e53-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="40e53-108">This example requires:</span></span>  
  
-   <span data-ttu-id="40e53-109">Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="40e53-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="40e53-110">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="40e53-110">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="40e53-111">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="40e53-111">You can also build this example in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="40e53-112">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="40e53-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40e53-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="40e53-113">See Also</span></span>  
 [<span data-ttu-id="40e53-114">Uživatelský vstup ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="40e53-114">User Input in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-in-windows-forms.md)

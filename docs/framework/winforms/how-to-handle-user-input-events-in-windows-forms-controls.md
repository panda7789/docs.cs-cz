---
title: Zpracování událostí vstupu uživatele v ovládacích prvcích
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, user input
- user input [Windows Forms], Windows Forms controls
ms.assetid: 3de74dcf-fae3-42d0-92b5-bc04a61a6888
ms.openlocfilehash: 19adeb6c803c76cba4139841f58087487d523a50
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739419"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="bc114-102">Postupy: Obsluha událostí uživatelského vstupu v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bc114-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="bc114-103">Tento příklad ukazuje, jak zpracovat většinu událostí klávesnice, myši, fokusu a ověřování, které mohou nastat v ovládacím prvku model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="bc114-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="bc114-104">Textové pole s názvem `TextBoxInput` přijímá události, když má fokus, a informace o každé události jsou zapsány do textového pole s názvem `TextBoxOutput` v pořadí, ve kterém jsou události vyvolány.</span><span class="sxs-lookup"><span data-stu-id="bc114-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="bc114-105">Aplikace taky obsahuje sadu zaškrtávacích políček, která se dají použít k filtrování událostí, které se mají ohlásit.</span><span class="sxs-lookup"><span data-stu-id="bc114-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc114-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc114-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="bc114-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="bc114-107">Compiling the Code</span></span>  
 <span data-ttu-id="bc114-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="bc114-108">This example requires:</span></span>  
  
- <span data-ttu-id="bc114-109">Odkazy na sestavení System, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="bc114-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc114-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc114-110">See also</span></span>

- [<span data-ttu-id="bc114-111">Uživatelský vstup ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="bc114-111">User Input in Windows Forms</span></span>](user-input-in-windows-forms.md)

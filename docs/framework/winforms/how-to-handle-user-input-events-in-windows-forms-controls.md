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
ms.openlocfilehash: ae230f22c929be39ea00eafe378c6910c4a9d35f
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592069"
---
# <a name="how-to-handle-user-input-events-in-windows-forms-controls"></a><span data-ttu-id="cd15f-102">Postupy: Obsluha událostí uživatelského vstupu v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd15f-102">How to: Handle User Input Events in Windows Forms Controls</span></span>
<span data-ttu-id="cd15f-103">Tento příklad ukazuje, jak zpracovat většinu klávesnice, myši, fokus a ověřovací události, které mohou nastat v ovládacím prvku Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="cd15f-103">This example demonstrates how to handle most keyboard, mouse, focus, and validation events that can occur in a Windows Forms control.</span></span> <span data-ttu-id="cd15f-104">Textové pole s názvem `TextBoxInput` přijímá události, když má fokus, a informace o každé události je zapsaný do textového pole s názvem `TextBoxOutput` v pořadí, ve kterém jsou vyvolány události.</span><span class="sxs-lookup"><span data-stu-id="cd15f-104">The text box named `TextBoxInput` receives the events when it has focus, and information about each event is written in the text box named `TextBoxOutput` in the order in which the events are raised.</span></span> <span data-ttu-id="cd15f-105">Aplikace také obsahuje sadu políčka, která umožňuje filtrovat události do sestavy.</span><span class="sxs-lookup"><span data-stu-id="cd15f-105">The application also includes a set of check boxes that can be used to filter which events to report.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd15f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd15f-106">Example</span></span>  
 [!code-cpp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/cpp/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.UserInputWalkthrough#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.UserInputWalkthrough/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cd15f-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="cd15f-107">Compiling the Code</span></span>  
 <span data-ttu-id="cd15f-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="cd15f-108">This example requires:</span></span>  
  
- <span data-ttu-id="cd15f-109">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="cd15f-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd15f-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cd15f-110">See also</span></span>

- [<span data-ttu-id="cd15f-111">Uživatelský vstup ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cd15f-111">User Input in Windows Forms</span></span>](user-input-in-windows-forms.md)

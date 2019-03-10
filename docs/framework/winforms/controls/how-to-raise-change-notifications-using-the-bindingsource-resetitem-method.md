---
title: 'Postupy: Vytváření oznámení o změnách pomocí metody BindingSource Resetitem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- change notifications [Windows Forms], raising
- data binding [Windows Forms], change notifications
- BindingSource component [Windows Forms], raising change notifications with
- data sources [Windows Forms], detecting changes
- change notifications
ms.assetid: ab8b4096-37ff-4e30-aabc-de79a2f2e972
ms.openlocfilehash: a24adf06999784476cd40b91ed53c068b94819e0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721889"
---
# <a name="how-to-raise-change-notifications-using-the-bindingsource-resetitem-method"></a><span data-ttu-id="5cf4b-102">Postupy: Vytváření oznámení o změnách pomocí metody BindingSource Resetitem</span><span class="sxs-lookup"><span data-stu-id="5cf4b-102">How to: Raise Change Notifications Using the BindingSource ResetItem Method</span></span>
<span data-ttu-id="5cf4b-103">Některé zdroje dat pro ovládací prvky nevyvolávejte oznámení o změnách při změně, přidání nebo odstranění položek.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-103">Some data sources for your controls do not raise change notifications when items are changed, added, or deleted.</span></span> <span data-ttu-id="5cf4b-104">S <xref:System.Windows.Forms.BindingSource> součásti, můžete vytvořit vazbu k takovým zdrojům dat a vyvolání oznámení o změně v kódu.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-104">With the <xref:System.Windows.Forms.BindingSource> component, you can bind to such data sources and raise a change notification from your code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5cf4b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="5cf4b-105">Example</span></span>  
 <span data-ttu-id="5cf4b-106">Tento formulář ukazuje použití <xref:System.Windows.Forms.BindingSource> součásti pro vytvoření vazby seznam <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-106">This form demonstrates using a <xref:System.Windows.Forms.BindingSource> component to bind a list to a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5cf4b-107">V seznamu nevyvolává oznámení o změnách, proto <xref:System.Windows.Forms.BindingSource.ResetItem%2A> metodu na <xref:System.Windows.Forms.BindingSource> se volá při změně položky v seznamu.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-107">The list does not raise change notifications, so the <xref:System.Windows.Forms.BindingSource.ResetItem%2A> method on the <xref:System.Windows.Forms.BindingSource> is called when an item in the list is changed.</span></span> <span data-ttu-id="5cf4b-108">.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-108">.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetItem#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetItem/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5cf4b-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5cf4b-109">Compiling the Code</span></span>  
 <span data-ttu-id="5cf4b-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="5cf4b-110">This example requires:</span></span>  
  
-   <span data-ttu-id="5cf4b-111">Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-111">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="5cf4b-112">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="5cf4b-112">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="5cf4b-113">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="5cf4b-113">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5cf4b-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5cf4b-114">See also</span></span>
- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="5cf4b-115">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="5cf4b-115">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="5cf4b-116">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="5cf4b-116">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)

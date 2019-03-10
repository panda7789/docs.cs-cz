---
title: 'Postupy: Uplatňování aktualizací zdroje dat v ovládacím prvku Windows Forms pomocí BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- data binding [Windows Forms], updating
- BindingSource component [Windows Forms], updating data binding
- examples [Windows Forms], BindingSource component
- data sources [Windows Forms], updating
- BindingSource component [Windows Forms], examples
ms.assetid: bd8bd9b2-af8a-4f11-a3d5-54eecbe2400b
ms.openlocfilehash: 06204c909987041ac6bf4e64e6f72a850910ca67
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710105"
---
# <a name="how-to-reflect-data-source-updates-in-a-windows-forms-control-with-the-bindingsource"></a><span data-ttu-id="2e9f0-102">Postupy: Uplatňování aktualizací zdroje dat v ovládacím prvku Windows Forms pomocí BindingSource</span><span class="sxs-lookup"><span data-stu-id="2e9f0-102">How to: Reflect Data Source Updates in a Windows Forms Control with the BindingSource</span></span>
<span data-ttu-id="2e9f0-103">Pokud používáte ovládací prvky vázané na data, máte někdy reakce na změny ve zdroji dat, pokud zdroj dat události změny seznamu nevyvolá.</span><span class="sxs-lookup"><span data-stu-id="2e9f0-103">When you use data-bound controls, you sometimes have to respond to changes in the data source when the data source does not raise list-changed events.</span></span> <span data-ttu-id="2e9f0-104">Při použití <xref:System.Windows.Forms.BindingSource> součásti pro vytvoření vazby zdroje dat do ovládacího prvku Windows Forms, ovládací prvek, který se změnil zdroj dat voláním může upozornit <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> – metoda.</span><span class="sxs-lookup"><span data-stu-id="2e9f0-104">When you use the <xref:System.Windows.Forms.BindingSource> component to bind your data source to a Windows Forms control, you can notify the control that your data source has changed by calling the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e9f0-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="2e9f0-105">Example</span></span>  
 <span data-ttu-id="2e9f0-106">Následující příklad kódu ukazuje použití <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> metoda oznámení o aktualizaci ve zdroji dat vázaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2e9f0-106">The following code example demonstrates using the <xref:System.Windows.Forms.BindingSource.ResetBindings%2A> method to notify a bound control about an update in the data source.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.ResetBindings#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.ResetBindings/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="2e9f0-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="2e9f0-107">Compiling the Code</span></span>  
 <span data-ttu-id="2e9f0-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="2e9f0-108">This example requires:</span></span>  
  
-   <span data-ttu-id="2e9f0-109">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="2e9f0-109">References to the System, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="2e9f0-110">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="2e9f0-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="2e9f0-111">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="2e9f0-111">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e9f0-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e9f0-112">See also</span></span>
- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="2e9f0-113">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="2e9f0-113">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="2e9f0-114">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="2e9f0-114">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)

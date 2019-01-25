---
title: 'Postupy: Vytvoření vazby ovládacího prvku Windows Forms k objektu Factory'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], binding
- factory objects [Windows Forms], binding to
- BindingSource component [Windows Forms], binding to a factory object
- BindingSource component [Windows Forms], examples
ms.assetid: 7d59af89-ff82-41d8-a48a-f1fbae788b0d
ms.openlocfilehash: 0173a4ef19765a74df819640f134e782b89395a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730006"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-factory-object"></a><span data-ttu-id="446a7-102">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k objektu Factory</span><span class="sxs-lookup"><span data-stu-id="446a7-102">How to: Bind a Windows Forms Control to a Factory Object</span></span>
<span data-ttu-id="446a7-103">Při vytváření ovládacích prvků, které pracují s daty, někdy najdete je nezbytné pro vytvoření vazby ovládacího prvku na objekt nebo metoda, která generuje jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="446a7-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to an object or method that generates other objects.</span></span> <span data-ttu-id="446a7-104">Takový objekt nebo metoda je volána objekt pro vytváření.</span><span class="sxs-lookup"><span data-stu-id="446a7-104">Such an object or method is called a factory.</span></span> <span data-ttu-id="446a7-105">Zdroj dat může být například návratová hodnota z volání metody, namísto objektu v paměti nebo typu.</span><span class="sxs-lookup"><span data-stu-id="446a7-105">Your data source might be, for example, the return value from a method call, instead of an object in memory or a type.</span></span> <span data-ttu-id="446a7-106">K tomuto typu zdroje dat lze svázat ovládací prvek jako zdroj vrátí kolekci.</span><span class="sxs-lookup"><span data-stu-id="446a7-106">You can bind a control to this kind of data source as long as the source returns a collection.</span></span>  
  
 <span data-ttu-id="446a7-107">Můžete snadno vázání ovládacího prvku k objektu factory pomocí <xref:System.Windows.Forms.BindingSource> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="446a7-107">You can easily bind a control to a factory object by using the <xref:System.Windows.Forms.BindingSource> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="446a7-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="446a7-108">Example</span></span>  
 <span data-ttu-id="446a7-109">Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Forms.DataGridView> ovládacího prvku metodě objekt pro vytváření s použitím <xref:System.Windows.Forms.BindingSource> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="446a7-109">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a factory method by using a <xref:System.Windows.Forms.BindingSource> control.</span></span> <span data-ttu-id="446a7-110">Metoda factory jmenuje `GetOrdersByCustomerId`, a vrátí všechny objednávky daného zákazníka v databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="446a7-110">The factory method is named `GetOrdersByCustomerId`, and it returns all the orders for a given customer in the Northwind database.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindToFactory#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindToFactory/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="446a7-111">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="446a7-111">Compiling the Code</span></span>  
 <span data-ttu-id="446a7-112">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="446a7-112">This example requires:</span></span>  
  
-   <span data-ttu-id="446a7-113">Odkazy na sestavení systému, System.Data, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="446a7-113">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="446a7-114">Informace o vytváření tento příklad z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="446a7-114">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="446a7-115">Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="446a7-115">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="446a7-116">Viz také [jak: Kompilace a spuštění příkladu kódu dokončení Windows Forms pomocí sady Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="446a7-116">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="446a7-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="446a7-117">See also</span></span>
- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="446a7-118">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="446a7-118">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)
- [<span data-ttu-id="446a7-119">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="446a7-119">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)

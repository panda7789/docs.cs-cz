---
title: 'Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 39ee45e7bfc0d9ca7fbdadb44514feb67b767dce
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="b3b5d-102">Postupy: Přizpůsobení přidávání položek pomocí Windows Forms BindingSource</span><span class="sxs-lookup"><span data-stu-id="b3b5d-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="b3b5d-103">Při použití <xref:System.Windows.Forms.BindingSource> součásti pro vazbu ovládacího prvku Windows Forms ke zdroji dat může být nutné přizpůsobit vytvoření nové položky.</span><span class="sxs-lookup"><span data-stu-id="b3b5d-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="b3b5d-104"><xref:System.Windows.Forms.BindingSource> Součást je tato možnost přehledné tím, že poskytuje <xref:System.Windows.Forms.BindingSource.AddingNew> událost, která se obvykle vyvolá, když je potřeba vytvořit novou položku připojeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b3b5d-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="b3b5d-105">Vaší obslužné rutiny událostí můžete zadat jakoukoli vlastní chování se vyžaduje (například volání metody na webové službě nebo získávání nový objekt ze třídy vytváření).</span><span class="sxs-lookup"><span data-stu-id="b3b5d-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b3b5d-106">Když je položka přidána ve zpracování <xref:System.Windows.Forms.BindingSource.AddingNew> událostí, přidání nelze zrušit.</span><span class="sxs-lookup"><span data-stu-id="b3b5d-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b3b5d-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="b3b5d-107">Example</span></span>  
 <span data-ttu-id="b3b5d-108">Následující příklad ukazuje, jak vytvořit vazbu <xref:System.Windows.Forms.DataGridView> řízení pro vytváření třídy pomocí <xref:System.Windows.Forms.BindingSource> součásti.</span><span class="sxs-lookup"><span data-stu-id="b3b5d-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="b3b5d-109">Když uživatel klikne <xref:System.Windows.Forms.DataGridView> ovládacího prvku nový řádek, <xref:System.Windows.Forms.BindingSource.AddingNew> událost se vyvolá.</span><span class="sxs-lookup"><span data-stu-id="b3b5d-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="b3b5d-110">Vytvoří novou obslužnou rutinu události `DemoCustomer` objektu, která je přiřazená <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b3b5d-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="b3b5d-111">To způsobí, že nové `DemoCustomer` objekt, který chcete přidat do <xref:System.Windows.Forms.BindingSource> seznamu součásti a který se má zobrazit na novém řádku z <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="b3b5d-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="b3b5d-112">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="b3b5d-112">Compiling the Code</span></span>  
 <span data-ttu-id="b3b5d-113">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="b3b5d-113">This example requires:</span></span>  
  
-   <span data-ttu-id="b3b5d-114">Odkazy na systém, System.Data, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="b3b5d-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="b3b5d-115">Informace o vytváření tento příklad z příkazového řádku pro visual Basic a Visual C# najdete v tématu [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="b3b5d-115">For information about building this example from the command line for visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="b3b5d-116">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="b3b5d-116">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="b3b5d-117">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="b3b5d-117">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3b5d-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3b5d-118">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.BindingSource>  
 [<span data-ttu-id="b3b5d-119">Komponenta BindingSource</span><span class="sxs-lookup"><span data-stu-id="b3b5d-119">BindingSource Component</span></span>](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="b3b5d-120">Postupy: Vytvoření vazby ovládacího prvku Windows Forms k typu</span><span class="sxs-lookup"><span data-stu-id="b3b5d-120">How to: Bind a Windows Forms Control to a Type</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)

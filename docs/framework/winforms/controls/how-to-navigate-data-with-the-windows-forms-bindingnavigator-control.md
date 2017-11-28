---
title: "Postupy: Navigace daty pomocí ovládacího prvku Windows Forms BindingNavigator"
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
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 08b9fb555966cf8459646a12da69c6db3361f0b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="15764-102">Postupy: Navigace daty pomocí ovládacího prvku Windows Forms BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="15764-102">How to: Navigate Data with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="15764-103">Nástupem <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku Windows Forms umožňuje vývojářům poskytnout koncovým uživatelům s jednoduché datové navigaci a manipulace s uživatelským rozhraním ve formulářích jejich vytvoření.</span><span class="sxs-lookup"><span data-stu-id="15764-103">The advent of the <xref:System.Windows.Forms.BindingNavigator> control in Windows Forms enables developers to provide end users with a simple data navigation and manipulation user interface on the forms they create.</span></span>  
  
 <span data-ttu-id="15764-104"><xref:System.Windows.Forms.BindingNavigator> Ovládacího prvku <xref:System.Windows.Forms.ToolStrip> předkonfigurované ovládacího prvku pomocí tlačítka pro navigaci na první, poslední, další a předchozí záznam v datových sad, jakož i tlačítka pro přidání a odstranění záznamů.</span><span class="sxs-lookup"><span data-stu-id="15764-104">The <xref:System.Windows.Forms.BindingNavigator> control is a <xref:System.Windows.Forms.ToolStrip> control with buttons preconfigured for navigation to the first, last, next, and previous record in a data set, as well as buttons to add and delete records.</span></span> <span data-ttu-id="15764-105">Přidání tlačítek do <xref:System.Windows.Forms.BindingNavigator> ovládací prvek je snadné, protože je <xref:System.Windows.Forms.ToolStrip> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="15764-105">Adding buttons to the <xref:System.Windows.Forms.BindingNavigator> control is easy, because it is a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  <span data-ttu-id="15764-106">Viz také [postupy: Přidání načíst, uložit, a tlačítka Storno do ovládacího prvku Windows Forms BindingNavigator](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="15764-106">Also see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](http://msdn.microsoft.com/library/safa4957\(v=vs.110\)).</span></span>  
  
 <span data-ttu-id="15764-107">Pro každé tlačítko na <xref:System.Windows.Forms.BindingNavigator> řídit, není členem příslušné skupiny <xref:System.Windows.Forms.BindingSource> komponenty, která umožňuje prostřednictvím kódu programu stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="15764-107">For each button on the <xref:System.Windows.Forms.BindingNavigator> control, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically allows the same functionality.</span></span> <span data-ttu-id="15764-108">Například <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> tlačítko odpovídá <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> metodu <xref:System.Windows.Forms.BindingSource> součásti, <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> tlačítko odpovídá <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> metoda a tak dále.</span><span class="sxs-lookup"><span data-stu-id="15764-108">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span> <span data-ttu-id="15764-109">V důsledku toho povolení <xref:System.Windows.Forms.BindingNavigator> řízení přejděte záznamů dat je jednoduchý jako nastavení jeho <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> vlastnost na příslušné <xref:System.Windows.Forms.BindingSource> součásti na formuláři.</span><span class="sxs-lookup"><span data-stu-id="15764-109">As a result, enabling the <xref:System.Windows.Forms.BindingNavigator> control to navigate data records is a simple as setting its <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the appropriate <xref:System.Windows.Forms.BindingSource> component on the form.</span></span>  
  
### <a name="to-set-up-the-bindingnavigator-control"></a><span data-ttu-id="15764-110">Nastavit BindingNavigator – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="15764-110">To set up the BindingNavigator control</span></span>  
  
1.  <span data-ttu-id="15764-111">Přidat <xref:System.Windows.Forms.BindingSource> součást s názvem `bindingSource1` a dvě <xref:System.Windows.Forms.TextBox> ovládací prvky s názvem `textBox1` a `textBox2`.</span><span class="sxs-lookup"><span data-stu-id="15764-111">Add a <xref:System.Windows.Forms.BindingSource> component named `bindingSource1` and two <xref:System.Windows.Forms.TextBox> controls named `textBox1` and `textBox2`.</span></span>  
  
2.  <span data-ttu-id="15764-112">Vytvoření vazby `bindingSource1` k datům a ovládací prvky textbox `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="15764-112">Bind `bindingSource1` to data, and the textbox controls to `bindingSource1`.</span></span> <span data-ttu-id="15764-113">Chcete-li to provést, vložte následující kód do formuláře a volání `LoadData` z konstruktoru formuláře nebo <xref:System.Windows.Forms.Form.Load> metoda zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="15764-113">To do this, paste the following code into your form and call `LoadData` from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3.  <span data-ttu-id="15764-114">Přidat <xref:System.Windows.Forms.BindingNavigator> ovládací prvek s názvem `bindingNavigator1` do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="15764-114">Add a <xref:System.Windows.Forms.BindingNavigator> control named `bindingNavigator1` to your form.</span></span>  
  
4.  <span data-ttu-id="15764-115">Nastavte <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> vlastnost pro `bindingNavigator1` k `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="15764-115">Set the <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property for `bindingNavigator1` to `bindingSource1`.</span></span> <span data-ttu-id="15764-116">Můžete to provést pomocí návrháře nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="15764-116">You can do this with the designer or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="15764-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="15764-117">Example</span></span>  
 <span data-ttu-id="15764-118">Následující příklad kódu je na kompletní příklad dříve uvedených kroků.</span><span class="sxs-lookup"><span data-stu-id="15764-118">The following code example is the complete example for the steps listed previously.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="15764-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="15764-119">Compiling the Code</span></span>  
 <span data-ttu-id="15764-120">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="15764-120">This example requires:</span></span>  
  
-   <span data-ttu-id="15764-121">Odkazy na systém, System.Data, System.Drawing, System.Windows.Forms a System.Xml sestavení.</span><span class="sxs-lookup"><span data-stu-id="15764-121">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
 <span data-ttu-id="15764-122">Informace o sestavení z příkazového řádku pro tento příklad [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] nebo [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], najdete v části [sestavení z příkazového řádku](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [vytváření pomocí příkazového řádku csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="15764-122">For information about building this example from the command line for [!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)] or [!INCLUDE[csprcs](../../../../includes/csprcs-md.md)], see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="15764-123">V tomto příkladu můžete také vytvořit [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] zadáním nebo vložením kódu do nového projektu.</span><span class="sxs-lookup"><span data-stu-id="15764-123">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="15764-124">Viz také [postupy: zkompilování a spuštění dokončení Windows Forms kód příklad pomocí sady Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="15764-124">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="15764-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="15764-125">See Also</span></span>  
 <xref:System.Windows.Forms.BindingNavigator>  
 [<span data-ttu-id="15764-126">BindingNavigator – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="15764-126">BindingNavigator Control</span></span>](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)  
 [<span data-ttu-id="15764-127">ToolStrip – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="15764-127">ToolStrip Control</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)

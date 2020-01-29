---
title: Navigace v datech pomocí ovládacího prvku BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- BindingNavigator control [Windows Forms], navigating data
- data [Windows Forms], navigating
- data navigation
- examples [Windows Forms], BindingNavigator control
ms.assetid: 0e5d4f34-bc9b-47cf-9b8d-93acbb1f1dbb
ms.openlocfilehash: 10508cb447e70cc387f9d98effa3bc4b5ccbbaa9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736010"
---
# <a name="how-to-navigate-data-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="9ebe3-102">Postupy: Navigace daty pomocí ovládacího prvku Windows Forms BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="9ebe3-102">How to: Navigate Data with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="9ebe3-103">Nástupem ovládacího prvku <xref:System.Windows.Forms.BindingNavigator> v model Windows Forms umožňuje vývojářům poskytnout koncovým uživatelům jednoduchou navigaci v datech a manipulaci s uživatelským rozhraním formulářů, které vytvoří.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-103">The advent of the <xref:System.Windows.Forms.BindingNavigator> control in Windows Forms enables developers to provide end users with a simple data navigation and manipulation user interface on the forms they create.</span></span>  
  
 <span data-ttu-id="9ebe3-104"><xref:System.Windows.Forms.BindingNavigator> ovládací prvek je <xref:System.Windows.Forms.ToolStrip> ovládací prvek s tlačítky předem nakonfigurovanými pro navigaci na první, poslední, další a předchozí záznam v sadě dat a také na tlačítka pro přidávání a odstraňování záznamů.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-104">The <xref:System.Windows.Forms.BindingNavigator> control is a <xref:System.Windows.Forms.ToolStrip> control with buttons preconfigured for navigation to the first, last, next, and previous record in a data set, as well as buttons to add and delete records.</span></span> <span data-ttu-id="9ebe3-105">Přidávání tlačítek do ovládacího prvku <xref:System.Windows.Forms.BindingNavigator> je snadné, protože se jedná o ovládací prvek <xref:System.Windows.Forms.ToolStrip>.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-105">Adding buttons to the <xref:System.Windows.Forms.BindingNavigator> control is easy, because it is a <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="9ebe3-106">Příklady naleznete v tématu [Postupy: Přidání tlačítek Load, Save a Cancel do ovládacího prvku BindingNavigator model Windows Forms](load-save-and-cancel-bindingnavigator.md).</span><span class="sxs-lookup"><span data-stu-id="9ebe3-106">For examples, see [How to: Add Load, Save, and Cancel Buttons to the Windows Forms BindingNavigator Control](load-save-and-cancel-bindingnavigator.md).</span></span>  
  
 <span data-ttu-id="9ebe3-107">Pro každé tlačítko ovládacího prvku <xref:System.Windows.Forms.BindingNavigator> existuje odpovídající člen <xref:System.Windows.Forms.BindingSource> komponenty, který programově umožňuje stejné funkce.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-107">For each button on the <xref:System.Windows.Forms.BindingNavigator> control, there is a corresponding member of the <xref:System.Windows.Forms.BindingSource> component that programmatically allows the same functionality.</span></span> <span data-ttu-id="9ebe3-108">Například tlačítko <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> odpovídá metodě <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> <xref:System.Windows.Forms.BindingSource> komponenty, <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> tlačítko, které odpovídá metodě <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A>, a tak dále.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-108">For example, the <xref:System.Windows.Forms.BindingNavigator.MoveFirstItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.MoveFirst%2A> method of the <xref:System.Windows.Forms.BindingSource> component, the <xref:System.Windows.Forms.BindingNavigator.DeleteItem%2A> button corresponds to the <xref:System.Windows.Forms.BindingSource.RemoveCurrent%2A> method, and so on.</span></span> <span data-ttu-id="9ebe3-109">Výsledkem je, že povolení ovládacího prvku <xref:System.Windows.Forms.BindingNavigator> pro navigaci datových záznamů je jednoduché jako nastavení vlastnosti <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> na příslušnou <xref:System.Windows.Forms.BindingSource> komponentu na formuláři.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-109">As a result, enabling the <xref:System.Windows.Forms.BindingNavigator> control to navigate data records is a simple as setting its <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property to the appropriate <xref:System.Windows.Forms.BindingSource> component on the form.</span></span>  
  
### <a name="to-set-up-the-bindingnavigator-control"></a><span data-ttu-id="9ebe3-110">Nastavení ovládacího prvku BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="9ebe3-110">To set up the BindingNavigator control</span></span>  
  
1. <span data-ttu-id="9ebe3-111">Přidejte komponentu <xref:System.Windows.Forms.BindingSource> s názvem `bindingSource1` a dva <xref:System.Windows.Forms.TextBox> ovládací prvky s názvem `textBox1` a `textBox2`.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-111">Add a <xref:System.Windows.Forms.BindingSource> component named `bindingSource1` and two <xref:System.Windows.Forms.TextBox> controls named `textBox1` and `textBox2`.</span></span>  
  
2. <span data-ttu-id="9ebe3-112">Navažte `bindingSource1` na data a ovládací prvky TextBox `bindingSource1`.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-112">Bind `bindingSource1` to data, and the textbox controls to `bindingSource1`.</span></span> <span data-ttu-id="9ebe3-113">Chcete-li to provést, vložte do formuláře následující kód a zavolejte `LoadData` z konstruktoru formuláře nebo metody zpracování událostí <xref:System.Windows.Forms.Form.Load>.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-113">To do this, paste the following code into your form and call `LoadData` from the form's constructor or <xref:System.Windows.Forms.Form.Load> event-handling method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#2)]  
  
3. <span data-ttu-id="9ebe3-114">Do formuláře přidejte ovládací prvek <xref:System.Windows.Forms.BindingNavigator> s názvem `bindingNavigator1`.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-114">Add a <xref:System.Windows.Forms.BindingNavigator> control named `bindingNavigator1` to your form.</span></span>  
  
4. <span data-ttu-id="9ebe3-115">Pro `bindingNavigator1` `bindingSource1`nastavte vlastnost <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A>.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-115">Set the <xref:System.Windows.Forms.BindingNavigator.BindingSource%2A> property for `bindingNavigator1` to `bindingSource1`.</span></span> <span data-ttu-id="9ebe3-116">Můžete to provést pomocí návrháře nebo v kódu.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-116">You can do this with the designer or in code.</span></span>  
  
     [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="9ebe3-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="9ebe3-117">Example</span></span>  
 <span data-ttu-id="9ebe3-118">Následující příklad kódu je kompletní příklad pro výše uvedené kroky.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-118">The following code example is the complete example for the steps listed previously.</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingNavigatorNavigate#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingNavigatorNavigate/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9ebe3-119">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9ebe3-119">Compiling the Code</span></span>  
 <span data-ttu-id="9ebe3-120">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="9ebe3-120">This example requires:</span></span>  
  
- <span data-ttu-id="9ebe3-121">Odkazy na sestavení System, System. data, System. Drawing, System. Windows. Forms a System. XML.</span><span class="sxs-lookup"><span data-stu-id="9ebe3-121">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ebe3-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9ebe3-122">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- [<span data-ttu-id="9ebe3-123">Ovládací prvek BindingNavigator</span><span class="sxs-lookup"><span data-stu-id="9ebe3-123">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="9ebe3-124">Ovládací prvek ToolStrip</span><span class="sxs-lookup"><span data-stu-id="9ebe3-124">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)

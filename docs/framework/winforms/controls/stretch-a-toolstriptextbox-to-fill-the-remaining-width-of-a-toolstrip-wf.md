---
title: 'Postupy: Roztažení prvku ToolStripTextBox k vyplnění zbývající šířky prvku ToolStrip (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: bd58cbd109b8e3dd04c6a284dc6926e95830fb61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537717"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a><span data-ttu-id="24e2b-102">Postupy: Roztažení prvku ToolStripTextBox k vyplnění zbývající šířky prvku ToolStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="24e2b-102">How to: Stretch a ToolStripTextBox to Fill the Remaining Width of a ToolStrip (Windows Forms)</span></span>
<span data-ttu-id="24e2b-103">Když nastavíte <xref:System.Windows.Forms.ToolStrip.Stretch%2A> vlastnost <xref:System.Windows.Forms.ToolStrip> řídit k `true`, ovládacího prvku vyplní celé jeho kontejneru a provést tak kompletní a změní, když se změní jeho kontejneru.</span><span class="sxs-lookup"><span data-stu-id="24e2b-103">When you set the <xref:System.Windows.Forms.ToolStrip.Stretch%2A> property of a <xref:System.Windows.Forms.ToolStrip> control to `true`, the control fills its container from end to end, and resizes when its container resizes.</span></span> <span data-ttu-id="24e2b-104">V této konfiguraci může být užitečné k roztahování položky v ovládacím prvku, například <xref:System.Windows.Forms.ToolStripTextBox>, vyplňování dostupného místa a velikost, pokud se změní velikost ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="24e2b-104">In this configuration, you may find it useful to stretch an item in the control, such as a <xref:System.Windows.Forms.ToolStripTextBox>, to fill the available space and to resize when the control resizes.</span></span> <span data-ttu-id="24e2b-105">Tato roztažení je užitečné, například, pokud chcete dosáhnout vzhled a chování podobná panelu Adresa v aplikaci Microsoft® Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="24e2b-105">This stretching is useful, for example, if you want to achieve appearance and behavior similar to the address bar in Microsoft® Internet Explorer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="24e2b-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="24e2b-106">Example</span></span>  
 <span data-ttu-id="24e2b-107">Následující příklad kódu poskytuje třídy odvozené od <xref:System.Windows.Forms.ToolStripTextBox> názvem `ToolStripSpringTextBox`.</span><span class="sxs-lookup"><span data-stu-id="24e2b-107">The following code example provides a class derived from <xref:System.Windows.Forms.ToolStripTextBox> called `ToolStripSpringTextBox`.</span></span> <span data-ttu-id="24e2b-108">Tato třída přepsání <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> metodu pro výpočet dostupná šířka nadřazené <xref:System.Windows.Forms.ToolStrip> řízení po odečtení kombinované šířku všechny ostatní položky.</span><span class="sxs-lookup"><span data-stu-id="24e2b-108">This class overrides the <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> method to calculate the available width of the parent <xref:System.Windows.Forms.ToolStrip> control after the combined width of all other items has been subtracted.</span></span> <span data-ttu-id="24e2b-109">Také poskytuje tento příklad kódu <xref:System.Windows.Forms.Form> třídy a `Program` třída k předvedení nové chování.</span><span class="sxs-lookup"><span data-stu-id="24e2b-109">This code example also provides a <xref:System.Windows.Forms.Form> class and a `Program` class to demonstrate the new behavior.</span></span>  
  
 [!code-csharp[ToolStripSpringTextBox#00](../../../../samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="24e2b-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="24e2b-110">Compiling the Code</span></span>  
 <span data-ttu-id="24e2b-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="24e2b-111">This example requires:</span></span>  
  
-   <span data-ttu-id="24e2b-112">Odkazy na systém, System.Drawing a System.Windows.Forms sestavení.</span><span class="sxs-lookup"><span data-stu-id="24e2b-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="24e2b-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="24e2b-113">See Also</span></span>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.ToolStripTextBox>  
 <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="24e2b-114">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="24e2b-114">ToolStrip Control Architecture</span></span>](../../../../docs/framework/winforms/controls/toolstrip-control-architecture.md)  
 [<span data-ttu-id="24e2b-115">Postupy: Interaktivní používání vlastnosti Spring v prvku StatusStrip</span><span class="sxs-lookup"><span data-stu-id="24e2b-115">How to: Use the Spring Property Interactively in a StatusStrip</span></span>](../../../../docs/framework/winforms/controls/how-to-use-the-spring-property-interactively-in-a-statusstrip.md)

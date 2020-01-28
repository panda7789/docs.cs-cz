---
title: 'Postupy: Roztažení prvku ToolStripTextBox k zaplnění zbývající šířky prvku ToolStrip'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: c60cc2a377f08a73159f25b2ab5f2812d41f0c10
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742839"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a><span data-ttu-id="0d288-102">Postupy: Roztažení prvku ToolStripTextBox k vyplnění zbývající šířky prvku ToolStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="0d288-102">How to: Stretch a ToolStripTextBox to Fill the Remaining Width of a ToolStrip (Windows Forms)</span></span>
<span data-ttu-id="0d288-103">Když nastavíte vlastnost <xref:System.Windows.Forms.ToolStrip.Stretch%2A> ovládacího prvku <xref:System.Windows.Forms.ToolStrip> na `true`, ovládací prvek vyplní svůj kontejner od konce až do konce a změní velikost kontejneru při změně velikosti kontejneru.</span><span class="sxs-lookup"><span data-stu-id="0d288-103">When you set the <xref:System.Windows.Forms.ToolStrip.Stretch%2A> property of a <xref:System.Windows.Forms.ToolStrip> control to `true`, the control fills its container from end to end, and resizes when its container resizes.</span></span> <span data-ttu-id="0d288-104">V této konfiguraci může být užitečné roztáhnout položku v ovládacím prvku, jako je například <xref:System.Windows.Forms.ToolStripTextBox>, vyplnit dostupný prostor a změnit velikost ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="0d288-104">In this configuration, you may find it useful to stretch an item in the control, such as a <xref:System.Windows.Forms.ToolStripTextBox>, to fill the available space and to resize when the control resizes.</span></span> <span data-ttu-id="0d288-105">Toto roztažení je užitečné, například pokud chcete dosáhnout vzhledu a chování podobného adresnímu řádku v aplikaci Microsoft® Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="0d288-105">This stretching is useful, for example, if you want to achieve appearance and behavior similar to the address bar in Microsoft® Internet Explorer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d288-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d288-106">Example</span></span>  
 <span data-ttu-id="0d288-107">Následující příklad kódu poskytuje třídu odvozenou z <xref:System.Windows.Forms.ToolStripTextBox> s názvem `ToolStripSpringTextBox`.</span><span class="sxs-lookup"><span data-stu-id="0d288-107">The following code example provides a class derived from <xref:System.Windows.Forms.ToolStripTextBox> called `ToolStripSpringTextBox`.</span></span> <span data-ttu-id="0d288-108">Tato třída přepisuje metodu <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> pro výpočet dostupné šířky nadřazeného ovládacího prvku <xref:System.Windows.Forms.ToolStrip> poté, co byla odečtena kombinovaná šířka všech ostatních položek.</span><span class="sxs-lookup"><span data-stu-id="0d288-108">This class overrides the <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> method to calculate the available width of the parent <xref:System.Windows.Forms.ToolStrip> control after the combined width of all other items has been subtracted.</span></span> <span data-ttu-id="0d288-109">Tento příklad kódu poskytuje také třídu <xref:System.Windows.Forms.Form> a třídu `Program`, která demonstruje nové chování.</span><span class="sxs-lookup"><span data-stu-id="0d288-109">This code example also provides a <xref:System.Windows.Forms.Form> class and a `Program` class to demonstrate the new behavior.</span></span>  
  
 [!code-csharp[ToolStripSpringTextBox#00](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0d288-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="0d288-110">Compiling the Code</span></span>  
 <span data-ttu-id="0d288-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="0d288-111">This example requires:</span></span>  
  
- <span data-ttu-id="0d288-112">Odkazy na sestavení System, System. Drawing a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="0d288-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d288-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0d288-113">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0d288-114">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="0d288-114">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="0d288-115">Postupy: Interaktivní používání vlastnosti Spring v prvku StatusStrip</span><span class="sxs-lookup"><span data-stu-id="0d288-115">How to: Use the Spring Property Interactively in a StatusStrip</span></span>](how-to-use-the-spring-property-interactively-in-a-statusstrip.md)

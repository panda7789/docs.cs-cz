---
title: 'Postupy: Roztažení prvku ToolStripTextBox k zaplnění zbývající šířky prvku ToolStrip (Windows Forms)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text boxes [Windows Forms], stretching in ToolStrip control [Windows Forms]
- ToolStrip control [Windows Forms], stretching a text box
ms.assetid: 0e610fbf-85fe-414c-900c-9704a5dd5cc6
ms.openlocfilehash: 707fd2e470a9be1d61d2878eeff845b3cad270db
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59223573"
---
# <a name="how-to-stretch-a-toolstriptextbox-to-fill-the-remaining-width-of-a-toolstrip-windows-forms"></a><span data-ttu-id="7e07e-102">Postupy: Roztažení prvku ToolStripTextBox k zaplnění zbývající šířky prvku ToolStrip (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="7e07e-102">How to: Stretch a ToolStripTextBox to Fill the Remaining Width of a ToolStrip (Windows Forms)</span></span>
<span data-ttu-id="7e07e-103">Při nastavení <xref:System.Windows.Forms.ToolStrip.Stretch%2A> vlastnost <xref:System.Windows.Forms.ToolStrip> mít pod kontrolou `true`, ovládací prvek vyplní svého kontejneru od začátku do konce a velikost přizpůsobí svou velikost svého kontejneru.</span><span class="sxs-lookup"><span data-stu-id="7e07e-103">When you set the <xref:System.Windows.Forms.ToolStrip.Stretch%2A> property of a <xref:System.Windows.Forms.ToolStrip> control to `true`, the control fills its container from end to end, and resizes when its container resizes.</span></span> <span data-ttu-id="7e07e-104">V této konfiguraci, možná bude užitečné k roztahování položku v ovládacím prvku, například <xref:System.Windows.Forms.ToolStripTextBox>, aby vyplnil dostupné místo a pro změnu velikosti při změní velikost ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="7e07e-104">In this configuration, you may find it useful to stretch an item in the control, such as a <xref:System.Windows.Forms.ToolStripTextBox>, to fill the available space and to resize when the control resizes.</span></span> <span data-ttu-id="7e07e-105">Tato roztažení je užitečné, například, pokud chcete dosáhnout vzhled a chování podobný panelu Adresa v aplikaci Microsoft® Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="7e07e-105">This stretching is useful, for example, if you want to achieve appearance and behavior similar to the address bar in Microsoft® Internet Explorer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e07e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e07e-106">Example</span></span>  
 <span data-ttu-id="7e07e-107">Následující příklad kódu obsahuje třídu odvozenou z <xref:System.Windows.Forms.ToolStripTextBox> volá `ToolStripSpringTextBox`.</span><span class="sxs-lookup"><span data-stu-id="7e07e-107">The following code example provides a class derived from <xref:System.Windows.Forms.ToolStripTextBox> called `ToolStripSpringTextBox`.</span></span> <span data-ttu-id="7e07e-108">Tato třída přepíše <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> metodu pro výpočet dostupná šířka nadřazené <xref:System.Windows.Forms.ToolStrip> řídit po odečtení kombinované šířku všechny ostatní položky.</span><span class="sxs-lookup"><span data-stu-id="7e07e-108">This class overrides the <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A> method to calculate the available width of the parent <xref:System.Windows.Forms.ToolStrip> control after the combined width of all other items has been subtracted.</span></span> <span data-ttu-id="7e07e-109">Tento příklad kódu také poskytuje <xref:System.Windows.Forms.Form> třídy a `Program` třídy, na které si předvedeme nové chování.</span><span class="sxs-lookup"><span data-stu-id="7e07e-109">This code example also provides a <xref:System.Windows.Forms.Form> class and a `Program` class to demonstrate the new behavior.</span></span>  
  
 [!code-csharp[ToolStripSpringTextBox#00](~/samples/snippets/csharp/VS_Snippets_Winforms/ToolStripSpringTextBox/cs/ToolStripSpringTextBox.cs#00)]
 [!code-vb[ToolStripSpringTextBox#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/ToolStripSpringTextBox/vb/ToolStripSpringTextBox.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7e07e-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="7e07e-110">Compiling the Code</span></span>  
 <span data-ttu-id="7e07e-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="7e07e-111">This example requires:</span></span>  
  
-   <span data-ttu-id="7e07e-112">Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="7e07e-112">References to the System, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e07e-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e07e-113">See also</span></span>

- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStrip.Stretch%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.ToolStripTextBox>
- <xref:System.Windows.Forms.ToolStripTextBox.GetPreferredSize%2A?displayProperty=nameWithType>
- [<span data-ttu-id="7e07e-114">Architektura ovládacího prvku ToolStrip</span><span class="sxs-lookup"><span data-stu-id="7e07e-114">ToolStrip Control Architecture</span></span>](toolstrip-control-architecture.md)
- [<span data-ttu-id="7e07e-115">Postupy: Interaktivní používání vlastnosti Spring v prvku StatusStrip</span><span class="sxs-lookup"><span data-stu-id="7e07e-115">How to: Use the Spring Property Interactively in a StatusStrip</span></span>](how-to-use-the-spring-property-interactively-in-a-statusstrip.md)

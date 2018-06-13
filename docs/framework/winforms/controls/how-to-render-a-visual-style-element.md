---
title: 'Postupy: Vykreslení elementu vizuálního stylu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- visual themes [Windows Forms], applying to elements of Windows Forms applications
- professional appearance [Windows Forms], applying to elements of Windows Forms applications
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a207781b-1baa-4ce9-b788-1e951bd4b5df
ms.openlocfilehash: 284fca2d3f2b8f47b60e4d9c639df4a6bd43c701
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33537615"
---
# <a name="how-to-render-a-visual-style-element"></a><span data-ttu-id="73f40-102">Postupy: Vykreslení elementu vizuálního stylu</span><span class="sxs-lookup"><span data-stu-id="73f40-102">How to: Render a Visual Style Element</span></span>
<span data-ttu-id="73f40-103"><xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Zpřístupní obor názvů <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> objekty, které představují uživatelem systému Windows rozhraní (UI) elementy nepodporuje vizuální styly.</span><span class="sxs-lookup"><span data-stu-id="73f40-103">The <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespace exposes <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> objects that represent the Windows user interface (UI) elements supported by visual styles.</span></span> <span data-ttu-id="73f40-104">Toto téma ukazuje, jak používat <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> třída k vykreslení <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> představující **Odhlásit** a **vypnout** tlačítka nabídky Start.</span><span class="sxs-lookup"><span data-stu-id="73f40-104">This topic demonstrates how to use the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> class to render the <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> that represents the **Log Off** and **Shut Down** buttons of the Start menu.</span></span>  
  
### <a name="to-render-a-visual-style-element"></a><span data-ttu-id="73f40-105">K vykreslení elementu vizuálního stylu</span><span class="sxs-lookup"><span data-stu-id="73f40-105">To render a visual style element</span></span>  
  
1.  <span data-ttu-id="73f40-106">Vytvoření <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> a nastavte ji na element, který má k vykreslení.</span><span class="sxs-lookup"><span data-stu-id="73f40-106">Create a <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> and set it to the element you want to draw.</span></span> <span data-ttu-id="73f40-107">Všimněte si použití <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> vlastnost a <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> metoda; <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> konstruktor vyvolá výjimku, pokud vizuální styly jsou zakázané nebo element není definován.</span><span class="sxs-lookup"><span data-stu-id="73f40-107">Note the use of the <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> property and the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> method; the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> constructor will throw an exception if visual styles are disabled or an element is undefined.</span></span>  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2.  <span data-ttu-id="73f40-108">Volání <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> metodu pro vykreslení elementu, který <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> aktuálně představuje.</span><span class="sxs-lookup"><span data-stu-id="73f40-108">Call the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> method to render the element that the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> currently represents.</span></span>  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="73f40-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="73f40-109">Compiling the Code</span></span>  
 <span data-ttu-id="73f40-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="73f40-110">This example requires:</span></span>  
  
-   <span data-ttu-id="73f40-111">Vlastní ovládací prvek odvozen od <xref:System.Windows.Forms.Control> třídy.</span><span class="sxs-lookup"><span data-stu-id="73f40-111">A custom control derived from the <xref:System.Windows.Forms.Control> class.</span></span>  
  
-   <span data-ttu-id="73f40-112">A <xref:System.Windows.Forms.Form> který je hostitelem vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="73f40-112">A <xref:System.Windows.Forms.Form> that hosts the custom control.</span></span>  
  
-   <span data-ttu-id="73f40-113">Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, a <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="73f40-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73f40-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="73f40-114">See Also</span></span>  
 [<span data-ttu-id="73f40-115">Vykreslování ovládacích prvků s vizuálními styly</span><span class="sxs-lookup"><span data-stu-id="73f40-115">Rendering Controls with Visual Styles</span></span>](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)

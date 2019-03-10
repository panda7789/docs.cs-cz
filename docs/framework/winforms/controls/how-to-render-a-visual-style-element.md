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
ms.openlocfilehash: 33c73bf8faa9dfafe5f4889875887dc3aef5985c
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57714109"
---
# <a name="how-to-render-a-visual-style-element"></a><span data-ttu-id="e28ce-102">Postupy: Vykreslení elementu vizuálního stylu</span><span class="sxs-lookup"><span data-stu-id="e28ce-102">How to: Render a Visual Style Element</span></span>
<span data-ttu-id="e28ce-103"><xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Obor názvů poskytuje <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> prvky (UI) podporuje vizuální styly rozhraní objektů, které představují uživatele Windows.</span><span class="sxs-lookup"><span data-stu-id="e28ce-103">The <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespace exposes <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> objects that represent the Windows user interface (UI) elements supported by visual styles.</span></span> <span data-ttu-id="e28ce-104">Toto téma popisuje způsob použití <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> třídy k vykreslení <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> , která představuje **Odhlásit** a **vypnout** tlačítka v nabídce Start.</span><span class="sxs-lookup"><span data-stu-id="e28ce-104">This topic demonstrates how to use the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> class to render the <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> that represents the **Log Off** and **Shut Down** buttons of the Start menu.</span></span>  
  
### <a name="to-render-a-visual-style-element"></a><span data-ttu-id="e28ce-105">K vykreslení elementu vizuálního stylu</span><span class="sxs-lookup"><span data-stu-id="e28ce-105">To render a visual style element</span></span>  
  
1.  <span data-ttu-id="e28ce-106">Vytvoření <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> a nastavte ho na element, který chcete kreslit.</span><span class="sxs-lookup"><span data-stu-id="e28ce-106">Create a <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> and set it to the element you want to draw.</span></span> <span data-ttu-id="e28ce-107">Všimněte si použití <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> vlastnost a <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> metoda; <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> konstruktor vyvolá výjimku, pokud vizuální styly jsou zakázané nebo element není definován.</span><span class="sxs-lookup"><span data-stu-id="e28ce-107">Note the use of the <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> property and the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> method; the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> constructor will throw an exception if visual styles are disabled or an element is undefined.</span></span>  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2.  <span data-ttu-id="e28ce-108">Volání <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> metody vykreslení elementu, který <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> aktuálně představuje.</span><span class="sxs-lookup"><span data-stu-id="e28ce-108">Call the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> method to render the element that the <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> currently represents.</span></span>  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e28ce-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e28ce-109">Compiling the Code</span></span>  
 <span data-ttu-id="e28ce-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e28ce-110">This example requires:</span></span>  
  
-   <span data-ttu-id="e28ce-111">Vlastní ovládací prvek odvozený z <xref:System.Windows.Forms.Control> třídy.</span><span class="sxs-lookup"><span data-stu-id="e28ce-111">A custom control derived from the <xref:System.Windows.Forms.Control> class.</span></span>  
  
-   <span data-ttu-id="e28ce-112">A <xref:System.Windows.Forms.Form> , který je hostitelem vlastního ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e28ce-112">A <xref:System.Windows.Forms.Form> that hosts the custom control.</span></span>  
  
-   <span data-ttu-id="e28ce-113">Odkazy <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, a <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="e28ce-113">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, and <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> namespaces.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e28ce-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e28ce-114">See also</span></span>
- [<span data-ttu-id="e28ce-115">Vykreslování ovládacích prvků s vizuálními styly</span><span class="sxs-lookup"><span data-stu-id="e28ce-115">Rendering Controls with Visual Styles</span></span>](rendering-controls-with-visual-styles.md)

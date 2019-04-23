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
ms.openlocfilehash: 57c2bc5722f77338225d70b514345344211656dc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312394"
---
# <a name="how-to-render-a-visual-style-element"></a>Postupy: Vykreslení elementu vizuálního stylu
<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Obor názvů poskytuje <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> prvky (UI) podporuje vizuální styly rozhraní objektů, které představují uživatele Windows. Toto téma popisuje způsob použití <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> třídy k vykreslení <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> , která představuje **Odhlásit** a **vypnout** tlačítka v nabídce Start.  
  
### <a name="to-render-a-visual-style-element"></a>K vykreslení elementu vizuálního stylu  
  
1. Vytvoření <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> a nastavte ho na element, který chcete kreslit. Všimněte si použití <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> vlastnost a <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> metoda; <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> konstruktor vyvolá výjimku, pokud vizuální styly jsou zakázané nebo element není definován.  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2. Volání <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> metody vykreslení elementu, který <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> aktuálně představuje.  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Vlastní ovládací prvek odvozený z <xref:System.Windows.Forms.Control> třídy.  
  
-   A <xref:System.Windows.Forms.Form> , který je hostitelem vlastního ovládacího prvku.  
  
-   Odkazy <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, a <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> obory názvů.  
  
## <a name="see-also"></a>Viz také:

- [Vykreslování ovládacích prvků s vizuálními styly](rendering-controls-with-visual-styles.md)

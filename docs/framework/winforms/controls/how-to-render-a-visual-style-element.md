---
title: "Postupy: Vykreslení elementu vizuálního stylu"
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
- cpp
helpviewer_keywords:
- visual themes [Windows Forms], applying to elements of Windows Forms applications
- professional appearance [Windows Forms], applying to elements of Windows Forms applications
- visual styles [Windows Forms], rendering Windows Forms controls
ms.assetid: a207781b-1baa-4ce9-b788-1e951bd4b5df
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 350b6969cfa4ae1b378c574acee73d87ff1dffca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-render-a-visual-style-element"></a>Postupy: Vykreslení elementu vizuálního stylu
<xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> Zpřístupní obor názvů <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> objekty, které představují uživatelem systému Windows rozhraní (UI) elementy nepodporuje vizuální styly. Toto téma ukazuje, jak používat <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> třída k vykreslení <xref:System.Windows.Forms.VisualStyles.VisualStyleElement> představující **Odhlásit** a **vypnout** tlačítka nabídky Start.  
  
### <a name="to-render-a-visual-style-element"></a>K vykreslení elementu vizuálního stylu  
  
1.  Vytvoření <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> a nastavte ji na element, který má k vykreslení. Všimněte si použití <xref:System.Windows.Forms.Application.RenderWithVisualStyles%2A?displayProperty=nameWithType> vlastnost a <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.IsElementDefined%2A?displayProperty=nameWithType> metoda; <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.%23ctor%2A> konstruktor vyvolá výjimku, pokud vizuální styly jsou zakázané nebo element není definován.  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#4)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#4)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#4)]  
  
2.  Volání <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer.DrawBackground%2A> metodu pro vykreslení elementu, který <xref:System.Windows.Forms.VisualStyles.VisualStyleRenderer> aktuálně představuje.  
  
     [!code-cpp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/cpp/form1.cpp#6)]
     [!code-csharp[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/CS/form1.cs#6)]
     [!code-vb[System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.VisualStyles.VisualStyleRenderer_Simple/VB/form1.vb#6)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   Vlastní ovládací prvek odvozen od <xref:System.Windows.Forms.Control> třídy.  
  
-   A <xref:System.Windows.Forms.Form> který je hostitelem vlastního ovládacího prvku.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, a <xref:System.Windows.Forms.VisualStyles?displayProperty=nameWithType> obory názvů.  
  
## <a name="see-also"></a>Viz také  
 [Vykreslování ovládacích prvků s vizuálními styly](../../../../docs/framework/winforms/controls/rendering-controls-with-visual-styles.md)

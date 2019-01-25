---
title: 'Postupy: Kreslení vlastní přerušované čáry'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- lines [Windows Forms], custom
- lines [Windows Forms], drawing
- lines [Windows Forms], dashed
ms.assetid: cd0ed96a-cce4-47b9-b58a-3bae2e3d1bee
ms.openlocfilehash: 77b4b959523c6d35dece2d759eeb71be04b53d93
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54538619"
---
# <a name="how-to-draw-a-custom-dashed-line"></a>Postupy: Kreslení vlastní přerušované čáry
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje několik styly čar, které jsou uvedeny v <xref:System.Drawing.Drawing2D.DashStyle> výčtu. Pokud tyto styly standardní dash nevyhovují vašim potřebám, můžete vytvořit vlastní dash vzor.  
  
## <a name="example"></a>Příklad  
 Kreslení vlastní přerušované čáry, umístěte délek pomlčky a mezery v poli a přiřaďte pole jako hodnotu <xref:System.Drawing.Pen.DashPattern%2A> vlastnost <xref:System.Drawing.Pen> objektu. Následující příklad kreslení vlastní přerušované čáry podle pole `{5, 2, 15, 4}`. Pokud je šířka pera 5 vynásobit prvky pole, můžete získat `{25, 10, 75, 20}`. Alternativní zobrazené pomlčky v délce 25 a 75 a mezery alternativní délku 10 až 20.  
  
 Následující obrázek znázorňuje výsledný přerušované čáry. Všimněte si, že poslední dash musí být kratší než 25 jednotky tak, aby můžete konec řádku (405, 5).  
  
 ![Pera](../../../../docs/framework/winforms/advanced/media/pens6.gif "pens6")  
  
 [!code-csharp[System.Drawing.UsingAPen#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvoření formuláře Windows a zpracování formuláře <xref:System.Windows.Forms.Control.Paint> událostí. Předchozí kód vložte do <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:
- [Kreslení čar a obrazců pomocí pera](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)

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
ms.openlocfilehash: d2184a8d7d7f24b8f631818608ab4bcdb89857c7
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67506032"
---
# <a name="how-to-draw-a-custom-dashed-line"></a>Postupy: Kreslení vlastní přerušované čáry
Rozhraní GDI + poskytuje několik styly čar, které jsou uvedeny v <xref:System.Drawing.Drawing2D.DashStyle> výčtu. Pokud tyto styly standardní dash nevyhovují vašim potřebám, můžete vytvořit vlastní dash vzor.  
  
## <a name="example"></a>Příklad  
 Kreslení vlastní přerušované čáry, umístěte délek pomlčky a mezery v poli a přiřaďte pole jako hodnotu <xref:System.Drawing.Pen.DashPattern%2A> vlastnost <xref:System.Drawing.Pen> objektu. Následující příklad kreslení vlastní přerušované čáry podle pole `{5, 2, 15, 4}`. Pokud je šířka pera 5 vynásobit prvky pole, můžete získat `{25, 10, 75, 20}`. Alternativní zobrazené pomlčky v délce 25 a 75 a mezery alternativní délku 10 až 20.  
  
 Následující obrázek znázorňuje výsledný přerušované čáry. Všimněte si, že poslední dash musí být kratší než 25 jednotky tak, aby můžete konec řádku (405, 5).  
  
 ![Obrázek, který ukazuje na přerušovanou čáru. ](./media/how-to-draw-a-custom-dashed-line/dashed-line-illustration.gif "pens6")  
  
 [!code-csharp[System.Drawing.UsingAPen#51](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvoření formuláře Windows a zpracování formuláře <xref:System.Windows.Forms.Control.Paint> událostí. Předchozí kód vložte do <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také:

- [Kreslení čar a obrazců pomocí pera](using-a-pen-to-draw-lines-and-shapes.md)

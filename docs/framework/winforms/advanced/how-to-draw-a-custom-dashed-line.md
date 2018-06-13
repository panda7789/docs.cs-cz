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
ms.openlocfilehash: 39dde3bb45165783171326b79e98744807350952
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33521612"
---
# <a name="how-to-draw-a-custom-dashed-line"></a>Postupy: Kreslení vlastní přerušované čáry
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] poskytuje několik dash stylů, které jsou uvedeny v <xref:System.Drawing.Drawing2D.DashStyle> výčtu. Pokud tyto styly standardní dash nevyhovují vašim potřebám, můžete vytvořit vlastní čárkovém vzoru.  
  
## <a name="example"></a>Příklad  
 Kreslení vlastní přerušované čáry, do pole umístit délky čárek a mezer a přiřaďte pole jako hodnotu <xref:System.Drawing.Pen.DashPattern%2A> vlastnost <xref:System.Drawing.Pen> objektu. Následující příklad nevykresluje vlastní přerušované čáry podle pole `{5, 2, 15, 4}`. Jestliže jste elementy pole vynásobit šířku pera 5, můžete získat `{25, 10, 75, 20}`. Zobrazené pomlčky alternativní v délce 25 a 75 a prostory alternativní délku mezi 10 a 20.  
  
 Následující obrázek znázorňuje výsledné přerušovanou čáru. Všimněte si, že poslední čárka musí být kratší než 25 jednotek, aby řádek můžete ukončit na (405, 5).  
  
 ![Pera](../../../../docs/framework/winforms/advanced/media/pens6.gif "pens6")  
  
 [!code-csharp[System.Drawing.UsingAPen#51](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.UsingAPen/CS/Class1.cs#51)]
 [!code-vb[System.Drawing.UsingAPen#51](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.UsingAPen/VB/Class1.vb#51)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Vytvoření formuláře Windows a zpracování formuláře <xref:System.Windows.Forms.Control.Paint> událostí. Předchozí kód vložte do <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.  
  
## <a name="see-also"></a>Viz také  
 [Kreslení čar a obrazců pomocí pera](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)

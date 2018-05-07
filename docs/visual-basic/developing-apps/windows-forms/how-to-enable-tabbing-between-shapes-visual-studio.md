---
title: 'Postupy: Povolení přecházení mezi tvary pomocí tabulátoru (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Line control [Visual Basic], implementing tabbing
- Shape control [Visual Basic], implementing tabbing
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
ms.openlocfilehash: 437027e53cb651dd5fabe40b9d8952250f108dad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a>Postupy: Povolení přecházení mezi tvary pomocí tabulátoru (Visual Studio)
Ovládací prvky Line a shape nemají `TabStop` nebo `TabIndex` vlastností, ale můžete pořád povolení přecházení mezi nimi pomocí tabulátoru. V následujícím příkladu se klávesy CTRL a klíče karta kartě mezi tvary; Stisknutím klávesy TAB bude kartě mezi tlačítka.  
  
> [!NOTE]
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení prostředí Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="to-enable-tabbing-among-shapes"></a>K povolení přecházení mezi tvary pomocí tabulátoru  
  
1.  Přetáhněte tři <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> ovládací prvky a dvě <xref:System.Windows.Forms.Button> z ovládací prvky **sada nástrojů** do formuláře.  
  
2.  V **Editor kódu**, přidejte `Imports` nebo `using` příkaz v horní části modulu:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  Přidejte následující kód v proceduře události:  
  
[!code-csharp[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  Přidejte následující kód v `Button1_PreviewKeyDown` procedury události:  
  
[!code-csharp[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Postupy: Kreslení obrazců pomocí ovládacích prvků OvalShape a RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [Postupy: Kreslení čar pomocí ovládacího prvku LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [Úvod k ovládacím prvkům Čára a Tvar](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)

---
title: "Postupy: Povolení přecházení mezi tvary pomocí tabulátoru (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Line control [Visual Basic], implementing tabbing
- Shape control [Visual Basic], implementing tabbing
ms.assetid: 09731b34-3900-4fcb-a9df-ce5280328433
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: a39957ffaa67d6abeb6d394ae9826d42ad2230de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a>Postupy: Povolení přecházení mezi tvary pomocí tabulátoru (Visual Studio)
Ovládací prvky Line a shape nemají `TabStop` nebo `TabIndex` vlastností, ale můžete pořád povolení přecházení mezi nimi pomocí tabulátoru. V následujícím příkladu se klávesy CTRL a klíče karta kartě mezi tvary; Stisknutím klávesy TAB bude kartě mezi tlačítka.  
  
> [!NOTE]
>  Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
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
 [Postupy: kreslení obrazců pomocí OvalShape a RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [Postupy: kreslení čar pomocí ovládacího prvku LineShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [Úvod k čára a tvar – ovládací prvky](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)

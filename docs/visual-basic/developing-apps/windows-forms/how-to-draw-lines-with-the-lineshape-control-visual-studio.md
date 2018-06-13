---
title: 'Postupy: Kreslení čar pomocí ovládacího prvku LineShape (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
ms.openlocfilehash: 5e1a837578aab4b4609a58ffee46406b022b8f97
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33587342"
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a>Postupy: Kreslení čar pomocí ovládacího prvku LineShape (Visual Studio)
Můžete použít <xref:Microsoft.VisualBasic.PowerPacks.LineShape> řízení k vykreslení diagonálních, svislé nebo vodorovné čáry na formulář nebo kontejneru, v době návrhu i v době běhu.  
  
 **Poznámka:** váš počítač může zobrazovat odlišné názvy nebo umístění pro některé uživatele, Visual Studio prvky rozhraní v následujících pokynech. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení prostředí Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-draw-a-line-at-design-time"></a>Kreslení čáry v době návrhu  
  
1.  Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.LineShape> řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** přetáhněte do ovládacího prvku formuláře nebo kontejneru.  
  
2.  Přetáhněte velikost a přesuňte velikost a umístění řádku.  
  
     Můžete také upravit velikost a umístění řádku změnou `X1`, `X2`, `Y1`, a `Y2` vlastnosti v **vlastnosti** okno.  
  
3.  V **vlastnosti** okně můžete nastavit další vlastnosti, jako `BorderStyle` nebo `BorderColor` změnit vzhled čáry.  
  
### <a name="to-draw-a-line-at-run-time"></a>Kreslení čáry v době běhu  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz na**.  
  
2.  V **přidat odkaz na** dialogové okno, vyberte **Microsoft.VisualBasic.PowerPacks.VS**a potom klikněte na **OK**.  
  
3.  V **Editor kódu**, přidejte `Imports` nebo `using` příkaz v horní části modulu:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  Přidejte následující kód v `Event` postup:  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
 [Úvod k ovládacím prvkům Čára a Tvar](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [Postupy: Kreslení obrazců pomocí ovládacích prvků OvalShape a RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)

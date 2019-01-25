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
ms.openlocfilehash: 46360c01dfaf2c6fe199725a9ecfba2248c72d6d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596225"
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a>Postupy: Kreslení čar pomocí ovládacího prvku LineShape (Visual Studio)
Můžete použít <xref:Microsoft.VisualBasic.PowerPacks.LineShape> ovládací prvek kreslení čar vodorovné, svislé nebo úhlopříčné ve formuláři nebo kontejneru, v době návrhu i době běhu.  
  
 **Poznámka:** váš počítač může zobrazit jiné názvy nebo umístění pro některé uživatele sady Visual Studio prvky rozhraní v následujících pokynech. Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením. Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-draw-a-line-at-design-time"></a>Nakreslení čáry v době návrhu  
  
1.  Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.LineShape> ovládacího prvku **sady Visual Basic PowerPack** kartu **nástrojů** přetáhněte do ovládacího prvku formulář nebo kontejneru.  
  
2.  Přetažením úchytů a přesunout obslužné rutiny pro velikost a umístění řádku.  
  
     Můžete také změnit velikost a umístění řádku změnou `X1`, `X2`, `Y1`, a `Y2` vlastnosti **vlastnosti** okno.  
  
3.  V **vlastnosti** okno, jako například volitelně nastavit další vlastnosti `BorderStyle` nebo `BorderColor` změnit vzhled čáry.  
  
### <a name="to-draw-a-line-at-run-time"></a>Nakreslení čáry v době běhu  
  
1.  Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz**.  
  
2.  V **přidat odkaz** dialogu **Microsoft.VisualBasic.PowerPacks.VS**a potom klikněte na tlačítko **OK**.  
  
3.  V **Editor kódu**, přidejte `Imports` nebo `using` příkazu v horní části modulu:  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  Přidejte následující kód `Event` postup:  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- <xref:Microsoft.VisualBasic.PowerPacks.LineShape>
- [Úvod k ovládacím prvkům Čára a Tvar](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
- [Postupy: Kreslení obrazců pomocí ovládacích prvků OvalShape a RectangleShape](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)

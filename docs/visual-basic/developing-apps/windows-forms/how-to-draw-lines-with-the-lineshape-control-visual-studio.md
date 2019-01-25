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
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a><span data-ttu-id="f6432-102">Postupy: Kreslení čar pomocí ovládacího prvku LineShape (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="f6432-102">How to: Draw Lines with the LineShape Control (Visual Studio)</span></span>
<span data-ttu-id="f6432-103">Můžete použít <xref:Microsoft.VisualBasic.PowerPacks.LineShape> ovládací prvek kreslení čar vodorovné, svislé nebo úhlopříčné ve formuláři nebo kontejneru, v době návrhu i době běhu.</span><span class="sxs-lookup"><span data-stu-id="f6432-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control to draw horizontal, vertical, or diagonal lines on a form or container, both at design time and at run time.</span></span>  
  
 <span data-ttu-id="f6432-104">**Poznámka:** váš počítač může zobrazit jiné názvy nebo umístění pro některé uživatele sady Visual Studio prvky rozhraní v následujících pokynech.</span><span class="sxs-lookup"><span data-stu-id="f6432-104">**Note** Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="f6432-105">Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením.</span><span class="sxs-lookup"><span data-stu-id="f6432-105">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="f6432-106">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="f6432-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-draw-a-line-at-design-time"></a><span data-ttu-id="f6432-107">Nakreslení čáry v době návrhu</span><span class="sxs-lookup"><span data-stu-id="f6432-107">To draw a line at design time</span></span>  
  
1.  <span data-ttu-id="f6432-108">Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.LineShape> ovládacího prvku **sady Visual Basic PowerPack** kartu **nástrojů** přetáhněte do ovládacího prvku formulář nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="f6432-108">Drag the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control from the **Visual Basic PowerPacks** tab in the **Toolbox** drag to a form or container control.</span></span>  
  
2.  <span data-ttu-id="f6432-109">Přetažením úchytů a přesunout obslužné rutiny pro velikost a umístění řádku.</span><span class="sxs-lookup"><span data-stu-id="f6432-109">Drag the sizing and move handles to size and position the line.</span></span>  
  
     <span data-ttu-id="f6432-110">Můžete také změnit velikost a umístění řádku změnou `X1`, `X2`, `Y1`, a `Y2` vlastnosti **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="f6432-110">You can also size and position the line by changing the `X1`, `X2`, `Y1`, and `Y2` properties in the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="f6432-111">V **vlastnosti** okno, jako například volitelně nastavit další vlastnosti `BorderStyle` nebo `BorderColor` změnit vzhled čáry.</span><span class="sxs-lookup"><span data-stu-id="f6432-111">In the **Properties** window, optionally set additional properties such as `BorderStyle` or `BorderColor` to change the appearance of the line.</span></span>  
  
### <a name="to-draw-a-line-at-run-time"></a><span data-ttu-id="f6432-112">Nakreslení čáry v době běhu</span><span class="sxs-lookup"><span data-stu-id="f6432-112">To draw a line at run time</span></span>  
  
1.  <span data-ttu-id="f6432-113">Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz**.</span><span class="sxs-lookup"><span data-stu-id="f6432-113">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="f6432-114">V **přidat odkaz** dialogu **Microsoft.VisualBasic.PowerPacks.VS**a potom klikněte na tlačítko **OK**.</span><span class="sxs-lookup"><span data-stu-id="f6432-114">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="f6432-115">V **Editor kódu**, přidejte `Imports` nebo `using` příkazu v horní části modulu:</span><span class="sxs-lookup"><span data-stu-id="f6432-115">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="f6432-116">Přidejte následující kód `Event` postup:</span><span class="sxs-lookup"><span data-stu-id="f6432-116">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f6432-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f6432-117">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.LineShape>
- [<span data-ttu-id="f6432-118">Úvod k ovládacím prvkům Čára a Tvar</span><span class="sxs-lookup"><span data-stu-id="f6432-118">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)
- [<span data-ttu-id="f6432-119">Postupy: Kreslení obrazců pomocí ovládacích prvků OvalShape a RectangleShape</span><span class="sxs-lookup"><span data-stu-id="f6432-119">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)

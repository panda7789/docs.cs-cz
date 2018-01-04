---
title: "Postupy: Kreslení čar pomocí ovládacího prvku LineShape (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- LineShape control [Visual Basic]
- lines, drawing
ms.assetid: 83e71b4e-aa76-4f9b-b547-8704309fd1e5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 42e7f01a57a514ad1dc64e3d4451ce38ea199f93
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-draw-lines-with-the-lineshape-control-visual-studio"></a><span data-ttu-id="d0bdb-102">Postupy: Kreslení čar pomocí ovládacího prvku LineShape (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="d0bdb-102">How to: Draw Lines with the LineShape Control (Visual Studio)</span></span>
<span data-ttu-id="d0bdb-103">Můžete použít <xref:Microsoft.VisualBasic.PowerPacks.LineShape> řízení k vykreslení diagonálních, svislé nebo vodorovné čáry na formulář nebo kontejneru, v době návrhu i v době běhu.</span><span class="sxs-lookup"><span data-stu-id="d0bdb-103">You can use the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control to draw horizontal, vertical, or diagonal lines on a form or container, both at design time and at run time.</span></span>  
  
 <span data-ttu-id="d0bdb-104">**Poznámka:** váš počítač může zobrazovat odlišné názvy nebo umístění pro některé uživatele, Visual Studio prvky rozhraní v následujících pokynech.</span><span class="sxs-lookup"><span data-stu-id="d0bdb-104">**Note** Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="d0bdb-105">Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením.</span><span class="sxs-lookup"><span data-stu-id="d0bdb-105">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="d0bdb-106">Další informace najdete v tématu [přizpůsobení prostředí Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="d0bdb-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-draw-a-line-at-design-time"></a><span data-ttu-id="d0bdb-107">Kreslení čáry v době návrhu</span><span class="sxs-lookup"><span data-stu-id="d0bdb-107">To draw a line at design time</span></span>  
  
1.  <span data-ttu-id="d0bdb-108">Přetáhněte <xref:Microsoft.VisualBasic.PowerPacks.LineShape> řídit z **PowerPacks jazyka Visual Basic** ve **sada nástrojů** přetáhněte do ovládacího prvku formuláře nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="d0bdb-108">Drag the <xref:Microsoft.VisualBasic.PowerPacks.LineShape> control from the **Visual Basic PowerPacks** tab in the **Toolbox** drag to a form or container control.</span></span>  
  
2.  <span data-ttu-id="d0bdb-109">Přetáhněte velikost a přesuňte velikost a umístění řádku.</span><span class="sxs-lookup"><span data-stu-id="d0bdb-109">Drag the sizing and move handles to size and position the line.</span></span>  
  
     <span data-ttu-id="d0bdb-110">Můžete také upravit velikost a umístění řádku změnou `X1`, `X2`, `Y1`, a `Y2` vlastnosti v **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="d0bdb-110">You can also size and position the line by changing the `X1`, `X2`, `Y1`, and `Y2` properties in the **Properties** window.</span></span>  
  
3.  <span data-ttu-id="d0bdb-111">V **vlastnosti** okně můžete nastavit další vlastnosti, jako `BorderStyle` nebo `BorderColor` změnit vzhled čáry.</span><span class="sxs-lookup"><span data-stu-id="d0bdb-111">In the **Properties** window, optionally set additional properties such as `BorderStyle` or `BorderColor` to change the appearance of the line.</span></span>  
  
### <a name="to-draw-a-line-at-run-time"></a><span data-ttu-id="d0bdb-112">Kreslení čáry v době běhu</span><span class="sxs-lookup"><span data-stu-id="d0bdb-112">To draw a line at run time</span></span>  
  
1.  <span data-ttu-id="d0bdb-113">Na **projektu** nabídky, klikněte na tlačítko **přidat odkaz na**.</span><span class="sxs-lookup"><span data-stu-id="d0bdb-113">On the **Project** menu, click **Add Reference**.</span></span>  
  
2.  <span data-ttu-id="d0bdb-114">V **přidat odkaz na** dialogové okno, vyberte **Microsoft.VisualBasic.PowerPacks.VS**a potom klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="d0bdb-114">In the **Add Reference** dialog box, select **Microsoft.VisualBasic.PowerPacks.VS**, and then click **OK**.</span></span>  
  
3.  <span data-ttu-id="d0bdb-115">V **Editor kódu**, přidejte `Imports` nebo `using` příkaz v horní části modulu:</span><span class="sxs-lookup"><span data-stu-id="d0bdb-115">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  
  
4.  <span data-ttu-id="d0bdb-116">Přidejte následující kód v `Event` postup:</span><span class="sxs-lookup"><span data-stu-id="d0bdb-116">Add the following code in an `Event` procedure:</span></span>  
  
     [!code-csharp[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksLine#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-draw-lines-with-the-lineshape-control-visual-studio_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d0bdb-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0bdb-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.LineShape>  
 [<span data-ttu-id="d0bdb-118">Úvod k ovládacím prvkům Čára a Tvar</span><span class="sxs-lookup"><span data-stu-id="d0bdb-118">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)  
 [<span data-ttu-id="d0bdb-119">Postupy: Kreslení obrazců pomocí ovládacích prvků OvalShape a RectangleShape</span><span class="sxs-lookup"><span data-stu-id="d0bdb-119">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)

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
ms.locfileid: "33589544"
---
# <a name="how-to-enable-tabbing-between-shapes-visual-studio"></a><span data-ttu-id="537d0-102">Postupy: Povolení přecházení mezi tvary pomocí tabulátoru (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="537d0-102">How to: Enable Tabbing Between Shapes (Visual Studio)</span></span>
<span data-ttu-id="537d0-103">Ovládací prvky Line a shape nemají `TabStop` nebo `TabIndex` vlastností, ale můžete pořád povolení přecházení mezi nimi pomocí tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="537d0-103">Line and shape controls do not have `TabStop` or `TabIndex` properties, but you can still enable tabbing among them.</span></span> <span data-ttu-id="537d0-104">V následujícím příkladu se klávesy CTRL a klíče karta kartě mezi tvary; Stisknutím klávesy TAB bude kartě mezi tlačítka.</span><span class="sxs-lookup"><span data-stu-id="537d0-104">In the following example, pressing both the CTRL and the TAB keys will tab between shapes; pressing only the TAB key will tab between the buttons.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="537d0-105">Váš počítač může v následujících pokynech zobrazovat odlišné názvy nebo umístění některých prvků uživatelského rozhraní sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="537d0-105">Your computer might show different names or locations for some of the Visual Studio user interface elements in the following instructions.</span></span> <span data-ttu-id="537d0-106">Tyto prvky jsou určeny edicí sady Visual Studio a použitým nastavením.</span><span class="sxs-lookup"><span data-stu-id="537d0-106">The Visual Studio edition that you have and the settings that you use determine these elements.</span></span> <span data-ttu-id="537d0-107">Další informace najdete v tématu [přizpůsobení prostředí Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="537d0-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="to-enable-tabbing-among-shapes"></a><span data-ttu-id="537d0-108">K povolení přecházení mezi tvary pomocí tabulátoru</span><span class="sxs-lookup"><span data-stu-id="537d0-108">To enable tabbing among shapes</span></span>  
  
1.  <span data-ttu-id="537d0-109">Přetáhněte tři <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> ovládací prvky a dvě <xref:System.Windows.Forms.Button> z ovládací prvky **sada nástrojů** do formuláře.</span><span class="sxs-lookup"><span data-stu-id="537d0-109">Drag three <xref:Microsoft.VisualBasic.PowerPacks.RectangleShape> controls and two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to a form.</span></span>  
  
2.  <span data-ttu-id="537d0-110">V **Editor kódu**, přidejte `Imports` nebo `using` příkaz v horní části modulu:</span><span class="sxs-lookup"><span data-stu-id="537d0-110">In the **Code Editor**, add an `Imports` or `using` statement at the top of the module:</span></span>  
  
```vb  
Imports Microsoft.VisualBasic.PowerPacks  
```  
  
```csharp  
using Microsoft.VisualBasic.PowerPacks;  
```  

3.  <span data-ttu-id="537d0-111">Přidejte následující kód v proceduře události:</span><span class="sxs-lookup"><span data-stu-id="537d0-111">Add the following code in an event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_1.cs)]
[!code-vb[VbPowerPacksTabbing#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_1.vb)]  
  
4.  <span data-ttu-id="537d0-112">Přidejte následující kód v `Button1_PreviewKeyDown` procedury události:</span><span class="sxs-lookup"><span data-stu-id="537d0-112">Add the following code in the `Button1_PreviewKeyDown` event procedure:</span></span>  
  
[!code-csharp[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-enable-tabbing-between-shapes-visual-studio_2.cs)]
[!code-vb[VbPowerPacksTabbing#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-enable-tabbing-between-shapes-visual-studio_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="537d0-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="537d0-113">See Also</span></span>  
 [<span data-ttu-id="537d0-114">Postupy: Kreslení obrazců pomocí ovládacích prvků OvalShape a RectangleShape</span><span class="sxs-lookup"><span data-stu-id="537d0-114">How to: Draw Shapes with the OvalShape and RectangleShape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-shapes-with-the-ovalshape-and-rectangleshape-controls.md)  
 [<span data-ttu-id="537d0-115">Postupy: Kreslení čar pomocí ovládacího prvku LineShape</span><span class="sxs-lookup"><span data-stu-id="537d0-115">How to: Draw Lines with the LineShape Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-draw-lines-with-the-lineshape-control-visual-studio.md)  
 [<span data-ttu-id="537d0-116">Úvod k ovládacím prvkům Čára a Tvar</span><span class="sxs-lookup"><span data-stu-id="537d0-116">Introduction to the Line and Shape Controls</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-line-and-shape-controls-visual-studio.md)

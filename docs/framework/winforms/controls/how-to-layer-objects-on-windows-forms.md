---
title: Uspořádání objektů ve vrstvách
description: Naučte se, jak vrstvy objektů na model Windows Forms ovládací prvky a podřízené formuláře pro vytváření složitějších uživatelských rozhraní.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6269b09c56963fefd500b9e1e6c9d7f51f9619cf
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174507"
---
# <a name="how-to-layer-objects-on-windows-forms"></a><span data-ttu-id="3d27e-103">Postupy: vrstvení objektů na model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d27e-103">How to: Layer objects on Windows Forms</span></span>

<span data-ttu-id="3d27e-104">Když vytváříte složité uživatelské rozhraní nebo pracujete s formulářem MDI (Multiple Document Interface), často budete chtít navrstvit ovládací prvky i podřízené formuláře pro vytváření složitějších uživatelských rozhraní (UI).</span><span class="sxs-lookup"><span data-stu-id="3d27e-104">When you create a complex user interface, or work with a multiple document interface (MDI) form, you will often want to layer both controls and child forms to create more complex user interfaces (UI).</span></span> <span data-ttu-id="3d27e-105">Chcete-li přesunout a sledovat ovládací prvky a okna v kontextu skupiny, budete pracovat s jejich *pořadím z*.</span><span class="sxs-lookup"><span data-stu-id="3d27e-105">To move and keep track of controls and windows within the context of a group, you manipulate their *z-order*.</span></span> <span data-ttu-id="3d27e-106">Pořadí vykreslování je vizuální vrstvení ovládacích prvků na formuláři podél osy z (hloubka) formuláře.</span><span class="sxs-lookup"><span data-stu-id="3d27e-106">Z-order is the visual layering of controls on a form along the form's z-axis (depth).</span></span> <span data-ttu-id="3d27e-107">Okno v horní části pořadí vykreslování překrývá všechna ostatní okna.</span><span class="sxs-lookup"><span data-stu-id="3d27e-107">The window at the top of the z-order overlaps all other windows.</span></span> <span data-ttu-id="3d27e-108">Všechna ostatní okna překrývají okno v dolní části pořadí vykreslování.</span><span class="sxs-lookup"><span data-stu-id="3d27e-108">All other windows overlap the window at the bottom of the z-order.</span></span>

## <a name="to-layer-controls-at-design-time"></a><span data-ttu-id="3d27e-109">Do vrstev ovládacích prvků v době návrhu</span><span class="sxs-lookup"><span data-stu-id="3d27e-109">To layer controls at design time</span></span>

1. <span data-ttu-id="3d27e-110">V aplikaci Visual Studio vyberte ovládací prvek, který chcete vytvořit do vrstvy.</span><span class="sxs-lookup"><span data-stu-id="3d27e-110">In Visual Studio, select a control that you want to layer.</span></span>

2. <span data-ttu-id="3d27e-111">V nabídce **Formát** vyberte možnost **pořadí**a potom vyberte možnost **přenést do popředí** nebo **přenést do pozadí**.</span><span class="sxs-lookup"><span data-stu-id="3d27e-111">On the **Format** menu, select **Order**, and then select **Bring To Front** or **Send To Back**.</span></span>

## <a name="to-layer-controls-programmatically"></a><span data-ttu-id="3d27e-112">Pro ovládací prvky vrstev programově</span><span class="sxs-lookup"><span data-stu-id="3d27e-112">To layer controls programmatically</span></span>

<span data-ttu-id="3d27e-113">Použijte <xref:System.Windows.Forms.Control.BringToFront%2A> metody a <xref:System.Windows.Forms.Control.SendToBack%2A> k manipulaci s pořadím z ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="3d27e-113">Use the <xref:System.Windows.Forms.Control.BringToFront%2A> and <xref:System.Windows.Forms.Control.SendToBack%2A> methods to manipulate the z-order of the controls.</span></span>

<span data-ttu-id="3d27e-114">Například pokud <xref:System.Windows.Forms.TextBox> ovládací prvek, `txtFirstName` , je pod jiným ovládacím prvkem a chcete jej použít nahoře, použijte následující kód:</span><span class="sxs-lookup"><span data-stu-id="3d27e-114">For example, if a <xref:System.Windows.Forms.TextBox> control, `txtFirstName`, is underneath another control and you want to have it on top, use the following code:</span></span>

```vb
txtFirstName.BringToFront()
```

```csharp
txtFirstName.BringToFront();
```

```cpp
txtFirstName->BringToFront();
```

> [!NOTE]
> <span data-ttu-id="3d27e-115">Model Windows Forms podporuje *omezení ovládacího prvku*.</span><span class="sxs-lookup"><span data-stu-id="3d27e-115">Windows Forms supports *control containment*.</span></span> <span data-ttu-id="3d27e-116">Zahrnutí ovládacího prvku zahrnuje vložení řady ovládacích prvků v rámci obsahujícího ovládacího prvku, jako je například počet <xref:System.Windows.Forms.RadioButton> ovládacích prvků v rámci <xref:System.Windows.Forms.GroupBox> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3d27e-116">Control containment involves placing a number of controls within a containing control, such as a number of <xref:System.Windows.Forms.RadioButton> controls within a <xref:System.Windows.Forms.GroupBox> control.</span></span> <span data-ttu-id="3d27e-117">Ovládací prvky lze následně rozvrstvit v rámci nadřazeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3d27e-117">You can then layer the controls within the containing control.</span></span> <span data-ttu-id="3d27e-118">Přesunutím skupinového pole se přesunou i ovládací prvky, protože jsou uvnitř ní obsažené.</span><span class="sxs-lookup"><span data-stu-id="3d27e-118">Moving the group box moves the controls as well, because they are contained inside it.</span></span>

## <a name="see-also"></a><span data-ttu-id="3d27e-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3d27e-119">See also</span></span>

- [<span data-ttu-id="3d27e-120">Ovládací prvky model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d27e-120">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="3d27e-121">Popisování jednotlivých ovládacích prvků Windows Forms a zajišťování zástupců pro tyto prvky</span><span class="sxs-lookup"><span data-stu-id="3d27e-121">Labeling Individual Windows Forms Controls and Providing Shortcuts to Them</span></span>](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [<span data-ttu-id="3d27e-122">Ovládací prvky používané ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3d27e-122">Controls to Use on Windows Forms</span></span>](controls-to-use-on-windows-forms.md)
- [<span data-ttu-id="3d27e-123">Ovládací prvky Windows Forms podle funkce</span><span class="sxs-lookup"><span data-stu-id="3d27e-123">Windows Forms Controls by Function</span></span>](windows-forms-controls-by-function.md)

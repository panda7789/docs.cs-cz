---
title: 'Postupy: Vystavení vlastností základních ovládacích prvků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- user controls [Windows Forms], exposing constituent controls
- controls [Windows Forms], constituent
- custom controls [Windows Forms], exposing properties
- constituent controls
ms.assetid: 5c1ec98b-aa48-4823-986e-4712551cfdf1
ms.openlocfilehash: f006e42771a5ecc71f6a508fd78d0e2dd8f2d2f2
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015881"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a><span data-ttu-id="b41af-102">Postupy: Vystavení vlastností základních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="b41af-102">How to: Expose Properties of Constituent Controls</span></span>
<span data-ttu-id="b41af-103">Ovládací prvky, které tvoří složený ovládací prvek, se nazývají *ovládací prvky prvků*.</span><span class="sxs-lookup"><span data-stu-id="b41af-103">The controls that make up a composite control are called *constituent controls*.</span></span> <span data-ttu-id="b41af-104">Tyto ovládací prvky jsou obvykle deklarovány jako soukromé, a proto nejsou k dispozici vývojáři.</span><span class="sxs-lookup"><span data-stu-id="b41af-104">These controls are normally declared private, and thus cannot be accessed by the developer.</span></span> <span data-ttu-id="b41af-105">Pokud chcete, aby byly vlastnosti těchto ovládacích prvků dostupné budoucím uživatelům, musíte je vystavit uživateli.</span><span class="sxs-lookup"><span data-stu-id="b41af-105">If you want to make properties of these controls available to future users, you must expose them to the user.</span></span> <span data-ttu-id="b41af-106">Vlastnost ovládacího prvku prvku je vystavena vytvořením vlastnosti v uživatelském ovládacím prvku a použitím `get` přístupových objektů a `set` dané vlastnosti pro změnu vlastnosti Private ovládacího prvku prvek.</span><span class="sxs-lookup"><span data-stu-id="b41af-106">A property of a constituent control is exposed by creating a property in the user control, and using the `get` and `set` accessors of that property to effect the change in the private property of the constituent control.</span></span>

 <span data-ttu-id="b41af-107">Zvažte hypotetický uživatelský ovládací prvek s tlačítkem na prvku `MyButton`s názvem.</span><span class="sxs-lookup"><span data-stu-id="b41af-107">Consider a hypothetical user control with a constituent button named `MyButton`.</span></span> <span data-ttu-id="b41af-108">V tomto příkladu, když uživatel požádá `ConstituentButtonBackColor` o vlastnost, hodnota uložená <xref:System.Windows.Forms.Control.BackColor%2A> ve vlastnosti `MyButton` je dodána.</span><span class="sxs-lookup"><span data-stu-id="b41af-108">In this example, when the user requests the `ConstituentButtonBackColor` property, the value stored in the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` is delivered.</span></span> <span data-ttu-id="b41af-109">Když uživatel přiřadí k této vlastnosti hodnotu, tato hodnota se <xref:System.Windows.Forms.Control.BackColor%2A> automaticky předává `MyButton` vlastnosti a `set` `MyButton`kód se spustí, změna barvy.</span><span class="sxs-lookup"><span data-stu-id="b41af-109">When the user assigns a value to this property, that value is automatically passed to the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` and the `set` code will execute, changing the color of `MyButton`.</span></span>

 <span data-ttu-id="b41af-110">Následující příklad ukazuje, jak vystavit <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost tlačítka prvku:</span><span class="sxs-lookup"><span data-stu-id="b41af-110">The following example shows how to expose the <xref:System.Windows.Forms.Control.BackColor%2A> property of the constituent button:</span></span>

```vb
Public Property ButtonColor() as System.Drawing.Color
   Get
      Return MyButton.BackColor
   End Get
   Set(Value as System.Drawing.Color)
      MyButton.BackColor = Value
   End Set
End Property
```

```csharp
public Color ButtonColor
{
   get
   {
      return(myButton.BackColor);
   }
   set
   {
      myButton.BackColor = value;
   }
}
```

### <a name="to-expose-a-property-of-a-constituent-control"></a><span data-ttu-id="b41af-111">Vystavení vlastnosti ovládacího prvku prvků</span><span class="sxs-lookup"><span data-stu-id="b41af-111">To expose a property of a constituent control</span></span>

1. <span data-ttu-id="b41af-112">Vytvořte veřejnou vlastnost pro uživatelský ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="b41af-112">Create a public property for your user control.</span></span>

2. <span data-ttu-id="b41af-113">`get` V části vlastnosti napište kód, který načte hodnotu vlastnosti, kterou chcete zveřejnit.</span><span class="sxs-lookup"><span data-stu-id="b41af-113">In the `get` section of the property, write code that retrieves the value of the property you want to expose.</span></span>

3. <span data-ttu-id="b41af-114">`set` V části vlastnosti napište kód, který předá hodnotu vlastnosti Vlastnosti vystavené vlastnosti ovládacího prvku prvek.</span><span class="sxs-lookup"><span data-stu-id="b41af-114">In the `set` section of the property, write code that passes the value of the property to the exposed property of the constituent control.</span></span>

## <a name="see-also"></a><span data-ttu-id="b41af-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b41af-115">See also</span></span>

- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="b41af-116">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b41af-116">Properties in Windows Forms Controls</span></span>](properties-in-windows-forms-controls.md)
- [<span data-ttu-id="b41af-117">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="b41af-117">Varieties of Custom Controls</span></span>](varieties-of-custom-controls.md)

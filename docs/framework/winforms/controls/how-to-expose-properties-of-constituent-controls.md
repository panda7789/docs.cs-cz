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
ms.openlocfilehash: f3ad37032ee2bb85f37a0eb754277cc9bc040a38
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54532159"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a><span data-ttu-id="dd1a3-102">Postupy: Vystavení vlastností základních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="dd1a3-102">How to: Expose Properties of Constituent Controls</span></span>
<span data-ttu-id="dd1a3-103">Ovládací prvky, které tvoří složeného ovládacího prvku se nazývají *základní ovládací prvky*.</span><span class="sxs-lookup"><span data-stu-id="dd1a3-103">The controls that make up a composite control are called *constituent controls*.</span></span> <span data-ttu-id="dd1a3-104">Tyto ovládací prvky jsou obvykle deklarována jako soukromá a proto není přístupná vývojářem.</span><span class="sxs-lookup"><span data-stu-id="dd1a3-104">These controls are normally declared private, and thus cannot be accessed by the developer.</span></span> <span data-ttu-id="dd1a3-105">Pokud chcete zpřístupnit vlastnosti těchto ovládacích prvků pro budoucí uživatele, musí zveřejnit uživatele.</span><span class="sxs-lookup"><span data-stu-id="dd1a3-105">If you want to make properties of these controls available to future users, you must expose them to the user.</span></span> <span data-ttu-id="dd1a3-106">Vlastnost základní ovládacího prvku je zveřejněný prostřednictvím vytváření vlastnost do uživatelského ovládacího prvku a používání `get` a `set` přistupující objekty vlastnosti provést změnu v hodnotě privátní vlastnost základní ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dd1a3-106">A property of a constituent control is exposed by creating a property in the user control, and using the `get` and `set` accessors of that property to effect the change in the private property of the constituent control.</span></span>  
  
 <span data-ttu-id="dd1a3-107">Vezměte v úvahu hypotetické uživatelský ovládací prvek s základní tlačítko s názvem `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="dd1a3-107">Consider a hypothetical user control with a constituent button named `MyButton`.</span></span> <span data-ttu-id="dd1a3-108">V tomto příkladu, když uživatel požádá `ConstituentButtonBackColor` vlastnost, hodnotou uloženou v části <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost `MyButton` doručuje.</span><span class="sxs-lookup"><span data-stu-id="dd1a3-108">In this example, when the user requests the `ConstituentButtonBackColor` property, the value stored in the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` is delivered.</span></span> <span data-ttu-id="dd1a3-109">Pokud uživatel přiřadí hodnotu této vlastnosti, je automaticky předat tuto hodnotu <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost `MyButton` a `set` bude kód spuštěn, změnou barvy `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="dd1a3-109">When the user assigns a value to this property, that value is automatically passed to the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` and the `set` code will execute, changing the color of `MyButton`.</span></span>  
  
 <span data-ttu-id="dd1a3-110">Následující příklad ukazuje, jak vystavit <xref:System.Windows.Forms.Control.BackColor%2A> základní vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="dd1a3-110">The following example shows how to expose the <xref:System.Windows.Forms.Control.BackColor%2A> property of the constituent button:</span></span>  
  
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
  
### <a name="to-expose-a-property-of-a-constituent-control"></a><span data-ttu-id="dd1a3-111">Vystavení vlastností základních ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="dd1a3-111">To expose a property of a constituent control</span></span>  
  
1.  <span data-ttu-id="dd1a3-112">Vytvoření veřejné vlastnosti uživatelského ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dd1a3-112">Create a public property for your user control.</span></span>  
  
2.  <span data-ttu-id="dd1a3-113">V `get` část vlastnosti, psaní kódu, který načte hodnotu vlastnosti, kterou chcete zveřejnit.</span><span class="sxs-lookup"><span data-stu-id="dd1a3-113">In the `get` section of the property, write code that retrieves the value of the property you want to expose.</span></span>  
  
3.  <span data-ttu-id="dd1a3-114">V `set` část vlastnosti, psaní kódu, který se předá hodnotu vlastnosti na vlastnost vystavené základní ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="dd1a3-114">In the `set` section of the property, write code that passes the value of the property to the exposed property of the constituent control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd1a3-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd1a3-115">See also</span></span>
- <xref:System.Windows.Forms.UserControl>
- [<span data-ttu-id="dd1a3-116">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="dd1a3-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)
- [<span data-ttu-id="dd1a3-117">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="dd1a3-117">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)

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
ms.openlocfilehash: 8f7b5c44a5cb20b5da10df5fd630b371cc959fa8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532630"
---
# <a name="how-to-expose-properties-of-constituent-controls"></a><span data-ttu-id="e6128-102">Postupy: Vystavení vlastností základních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="e6128-102">How to: Expose Properties of Constituent Controls</span></span>
<span data-ttu-id="e6128-103">Ovládací prvky, které tvoří složeného ovládacího prvku se nazývají *základních ovládacích prvků*.</span><span class="sxs-lookup"><span data-stu-id="e6128-103">The controls that make up a composite control are called *constituent controls*.</span></span> <span data-ttu-id="e6128-104">Tyto ovládací prvky jsou obvykle deklarovány privátní a proto nelze získat přístup, vývojáři.</span><span class="sxs-lookup"><span data-stu-id="e6128-104">These controls are normally declared private, and thus cannot be accessed by the developer.</span></span> <span data-ttu-id="e6128-105">Pokud chcete zpřístupnit vlastnosti těchto ovládacích prvků pro budoucí uživatele, umístěte je pro uživatele.</span><span class="sxs-lookup"><span data-stu-id="e6128-105">If you want to make properties of these controls available to future users, you must expose them to the user.</span></span> <span data-ttu-id="e6128-106">Vlastnost základní ovládacího prvku je vytvářena při vytvoření vlastnosti v uživatelského ovládacího prvku a pomocí `get` a `set` přístupové objekty této vlastnosti k ovlivnění změnu v hodnotě soukromá vlastnost základní ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e6128-106">A property of a constituent control is exposed by creating a property in the user control, and using the `get` and `set` accessors of that property to effect the change in the private property of the constituent control.</span></span>  
  
 <span data-ttu-id="e6128-107">Zvažte hypotetický uživatelského ovládacího prvku s základní tlačítko s názvem `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="e6128-107">Consider a hypothetical user control with a constituent button named `MyButton`.</span></span> <span data-ttu-id="e6128-108">V tomto příkladu, když uživatel požádá `ConstituentButtonBackColor` vlastnost, s hodnotou uloženou v <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost `MyButton` doručuje.</span><span class="sxs-lookup"><span data-stu-id="e6128-108">In this example, when the user requests the `ConstituentButtonBackColor` property, the value stored in the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` is delivered.</span></span> <span data-ttu-id="e6128-109">Když uživatel přiřazuje hodnotu této vlastnosti, je tato hodnota automaticky předaný <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost `MyButton` a `set` kód bude spuštěn, změnit barvu `MyButton`.</span><span class="sxs-lookup"><span data-stu-id="e6128-109">When the user assigns a value to this property, that value is automatically passed to the <xref:System.Windows.Forms.Control.BackColor%2A> property of `MyButton` and the `set` code will execute, changing the color of `MyButton`.</span></span>  
  
 <span data-ttu-id="e6128-110">Následující příklad ukazuje, jak vystavit <xref:System.Windows.Forms.Control.BackColor%2A> vlastnost základní tlačítka:</span><span class="sxs-lookup"><span data-stu-id="e6128-110">The following example shows how to expose the <xref:System.Windows.Forms.Control.BackColor%2A> property of the constituent button:</span></span>  
  
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
  
### <a name="to-expose-a-property-of-a-constituent-control"></a><span data-ttu-id="e6128-111">Aby se zveřejnily vlastnost základní ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="e6128-111">To expose a property of a constituent control</span></span>  
  
1.  <span data-ttu-id="e6128-112">Vytvoření veřejné vlastnosti pro váš uživatelský ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="e6128-112">Create a public property for your user control.</span></span>  
  
2.  <span data-ttu-id="e6128-113">V `get` části vlastnost napsat kód, který načte hodnotu vlastnosti, kterou chcete vystavit.</span><span class="sxs-lookup"><span data-stu-id="e6128-113">In the `get` section of the property, write code that retrieves the value of the property you want to expose.</span></span>  
  
3.  <span data-ttu-id="e6128-114">V `set` části vlastnost napsat kód, který předá hodnotu vlastnosti vlastnost zveřejněné základní ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="e6128-114">In the `set` section of the property, write code that passes the value of the property to the exposed property of the constituent control.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e6128-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6128-115">See Also</span></span>  
 <xref:System.Windows.Forms.UserControl>  
 [<span data-ttu-id="e6128-116">Vlastnosti v ovládacích prvcích Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e6128-116">Properties in Windows Forms Controls</span></span>](../../../../docs/framework/winforms/controls/properties-in-windows-forms-controls.md)  
 [<span data-ttu-id="e6128-117">Typy vlastních ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="e6128-117">Varieties of Custom Controls</span></span>](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md)

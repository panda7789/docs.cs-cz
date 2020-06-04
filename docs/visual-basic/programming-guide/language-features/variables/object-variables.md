---
title: Proměnné objektu
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: a5e61f9308d3484dc228a7d09cc2fd30a2f41b35
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410332"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="9d737-102">Proměnné objektu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9d737-102">Object Variables in Visual Basic</span></span>

<span data-ttu-id="9d737-103">Kromě přímého ukládání hodnot proměnná může odkazovat na objekt.</span><span class="sxs-lookup"><span data-stu-id="9d737-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="9d737-104">K proměnné přiřadíte objekt ze stejných důvodů, jako je přiřazení libovolné hodnoty k proměnné:</span><span class="sxs-lookup"><span data-stu-id="9d737-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>

- <span data-ttu-id="9d737-105">Název proměnné je často kratší a snazší si pamatovat než úplnou cestu metod a vlastností potřebných pro přístup k objektu samotnému.</span><span class="sxs-lookup"><span data-stu-id="9d737-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>

- <span data-ttu-id="9d737-106">Použití proměnné, která odkazuje na objekt, je efektivnější než opakované přístup k objektu prostřednictvím nezbytných metod nebo vlastností.</span><span class="sxs-lookup"><span data-stu-id="9d737-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>

- <span data-ttu-id="9d737-107">Můžete změnit proměnnou tak, aby odkazovala na jiné objekty v době, kdy váš kód běží.</span><span class="sxs-lookup"><span data-stu-id="9d737-107">You can change a variable to refer to other objects while your code is running.</span></span>

## <a name="making-code-shorter"></a><span data-ttu-id="9d737-108">Kratší vytváření kódu</span><span class="sxs-lookup"><span data-stu-id="9d737-108">Making Code Shorter</span></span>

<span data-ttu-id="9d737-109">Můžete použít proměnné objektu pro zkrácení kódu, který je třeba zadat.</span><span class="sxs-lookup"><span data-stu-id="9d737-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="9d737-110">Následující příklad používá úplnou cestu metod a vlastností pro přístup k <xref:System.Windows.Forms.Control> objektu.</span><span class="sxs-lookup"><span data-stu-id="9d737-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

<span data-ttu-id="9d737-111">Pokud použijete proměnnou objektu pro ovládací prvek, můžete tento kód zkrátit a zrychlit spouštění.</span><span class="sxs-lookup"><span data-stu-id="9d737-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="9d737-112">Měli byste deklarovat objektovou proměnnou se specifickou třídou, kterou máte v úmyslu přiřadit ( `Control` v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="9d737-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="9d737-113">Jakmile přiřadíte objekt proměnné, můžete s ní pracovat stejně, jako při zpracování objektu, na který odkazuje.</span><span class="sxs-lookup"><span data-stu-id="9d737-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="9d737-114">Můžete nastavit nebo načíst vlastnosti objektu nebo použít kteroukoli z jeho metod.</span><span class="sxs-lookup"><span data-stu-id="9d737-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="9d737-115">Následující příklad používá proměnnou objektu pro zjednodušení kódu v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9d737-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a><span data-ttu-id="9d737-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="9d737-116">See also</span></span>

- [<span data-ttu-id="9d737-117">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="9d737-117">Variable Declaration</span></span>](variable-declaration.md)
- [<span data-ttu-id="9d737-118">Postupy: Urychlení přístupu k objektu pomocí cesty s dlouhou kvalifikací</span><span class="sxs-lookup"><span data-stu-id="9d737-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [<span data-ttu-id="9d737-119">Deklarace proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="9d737-119">Object Variable Declaration</span></span>](object-variable-declaration.md)
- [<span data-ttu-id="9d737-120">Přiřazení proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="9d737-120">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="9d737-121">Hodnoty proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="9d737-121">Object Variable Values</span></span>](object-variable-values.md)

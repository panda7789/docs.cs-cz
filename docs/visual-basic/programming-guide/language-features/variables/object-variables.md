---
title: Proměnné objektu v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: cc5be13293a89e73d1790e94a99d7936f1711e12
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352968"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="71b96-102">Proměnné objektu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="71b96-102">Object Variables in Visual Basic</span></span>

<span data-ttu-id="71b96-103">Kromě ukládání hodnot přímo, mohou proměnné odkazovat na objekt.</span><span class="sxs-lookup"><span data-stu-id="71b96-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="71b96-104">Přiřazení objektu k proměnné ze stejného důvodu, kterou přiřadíte libovolnou hodnotu proměnné:</span><span class="sxs-lookup"><span data-stu-id="71b96-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>

- <span data-ttu-id="71b96-105">Název proměnné je často kratší a snadněji mějte na paměti než úplnou cestu k metodám a vlastnostem, které jsou potřebné pro přístup k objektu samotného.</span><span class="sxs-lookup"><span data-stu-id="71b96-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>

- <span data-ttu-id="71b96-106">Použití proměnné, která odkazuje na objekt je efektivnější než opakovaně přístup k objektu samotného prostřednictvím nezbytné metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="71b96-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>

- <span data-ttu-id="71b96-107">Můžete změnit proměnné k odkazování na jiné objekty, když váš kód běží.</span><span class="sxs-lookup"><span data-stu-id="71b96-107">You can change a variable to refer to other objects while your code is running.</span></span>

## <a name="making-code-shorter"></a><span data-ttu-id="71b96-108">Provádění kódu kratší</span><span class="sxs-lookup"><span data-stu-id="71b96-108">Making Code Shorter</span></span>

<span data-ttu-id="71b96-109">Objektové proměnné můžete použít ke zkrácení kód, který je nutné zadat.</span><span class="sxs-lookup"><span data-stu-id="71b96-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="71b96-110">Následující příklad používá pro přístup k úplnou cestu k metodám a vlastnostem <xref:System.Windows.Forms.Control> objektu.</span><span class="sxs-lookup"><span data-stu-id="71b96-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

<span data-ttu-id="71b96-111">Můžete zkrátit tento kód a rychlejší spuštění, pokud používáte proměnné objektu ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="71b96-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="71b96-112">By měla deklarovat proměnné objektu s konkrétní třídou, která máte v úmyslu přiřadit k ní (`Control` v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="71b96-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="71b96-113">Po přiřazení objektu k proměnné lze považovat ho stejně jako považovat objektu, na který odkazuje.</span><span class="sxs-lookup"><span data-stu-id="71b96-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="71b96-114">Můžete nastavit nebo načíst vlastnosti objektu nebo použít některou z jeho metod.</span><span class="sxs-lookup"><span data-stu-id="71b96-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="71b96-115">Následující příklad používá proměnné objektu pro zjednodušení kódu v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="71b96-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a><span data-ttu-id="71b96-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="71b96-116">See also</span></span>

- [<span data-ttu-id="71b96-117">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="71b96-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="71b96-118">Postupy: Urychlení přístupu k objektu pomocí cesty dlouhou kvalifikací</span><span class="sxs-lookup"><span data-stu-id="71b96-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [<span data-ttu-id="71b96-119">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="71b96-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="71b96-120">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="71b96-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="71b96-121">Hodnoty objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="71b96-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)

---
title: Proměnné objektu v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 8383261c1806732c4c8abea9834000f003a848a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649110"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="24d6b-102">Proměnné objektu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="24d6b-102">Object Variables in Visual Basic</span></span>
<span data-ttu-id="24d6b-103">Proměnné můžete kromě ukládání hodnot přímo, odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="24d6b-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="24d6b-104">Objekt můžete přiřadit proměnné ze stejného důvodu, který přiřadíte žádnou hodnotu proměnné:</span><span class="sxs-lookup"><span data-stu-id="24d6b-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>  
  
-   <span data-ttu-id="24d6b-105">Název proměnné je často kratší a snadněji mějte na paměti, než úplnou cestu metod a vlastností, které jsou potřebné pro přístup k objektu sám sebe.</span><span class="sxs-lookup"><span data-stu-id="24d6b-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>  
  
-   <span data-ttu-id="24d6b-106">Použití proměnné, která se vztahuje k objektu je efektivnější než opakovaně přístup k samotného objektu prostřednictvím nezbytné metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="24d6b-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>  
  
-   <span data-ttu-id="24d6b-107">Můžete změnit proměnnou, která bude odkazovat na další objekty, když běží váš kód.</span><span class="sxs-lookup"><span data-stu-id="24d6b-107">You can change a variable to refer to other objects while your code is running.</span></span>  
  
## <a name="making-code-shorter"></a><span data-ttu-id="24d6b-108">Kratší provádění kódu</span><span class="sxs-lookup"><span data-stu-id="24d6b-108">Making Code Shorter</span></span>  
 <span data-ttu-id="24d6b-109">Objektové proměnné můžete použít tak, aby zkrátil kód, který je třeba zadávat.</span><span class="sxs-lookup"><span data-stu-id="24d6b-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="24d6b-110">Následující příklad používá úplnou cestu metod a vlastností pro přístup <xref:System.Windows.Forms.Control> objektu.</span><span class="sxs-lookup"><span data-stu-id="24d6b-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 <span data-ttu-id="24d6b-111">Můžete zmenšit tento kód a urychlit spuštění, pokud používáte proměnné objektu pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="24d6b-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="24d6b-112">Objektová proměnná s určité třídy, které chcete přiřadit k němu by měly deklarovat (`Control` v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="24d6b-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="24d6b-113">Po přiřazení objektu k proměnné, lze považovat ho stejně jako považovat objektu, na který odkazuje.</span><span class="sxs-lookup"><span data-stu-id="24d6b-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="24d6b-114">Můžete nastavit nebo získat vlastnosti objektu nebo použít některou z jeho metod.</span><span class="sxs-lookup"><span data-stu-id="24d6b-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="24d6b-115">Následující příklad používá proměnné objektu můžete zjednodušit kód v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="24d6b-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a><span data-ttu-id="24d6b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="24d6b-116">See Also</span></span>  
 [<span data-ttu-id="24d6b-117">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="24d6b-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="24d6b-118">Postupy: Urychlení přístupu k objektu pomocí cesty s dlouhou kvalifikací</span><span class="sxs-lookup"><span data-stu-id="24d6b-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)  
 [<span data-ttu-id="24d6b-119">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="24d6b-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="24d6b-120">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="24d6b-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="24d6b-121">Hodnoty objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="24d6b-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)

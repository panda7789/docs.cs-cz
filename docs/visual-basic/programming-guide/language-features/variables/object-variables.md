---
title: "Proměnné objektu v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44689d649a381618e5d6c934deb2b7b9bea463ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="07a82-102">Proměnné objektu v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="07a82-102">Object Variables in Visual Basic</span></span>
<span data-ttu-id="07a82-103">Proměnné můžete kromě ukládání hodnot přímo, odkaz na objekt.</span><span class="sxs-lookup"><span data-stu-id="07a82-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="07a82-104">Objekt můžete přiřadit proměnné ze stejného důvodu, který přiřadíte žádnou hodnotu proměnné:</span><span class="sxs-lookup"><span data-stu-id="07a82-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>  
  
-   <span data-ttu-id="07a82-105">Název proměnné je často kratší a snadněji mějte na paměti, než úplnou cestu metod a vlastností, které jsou potřebné pro přístup k objektu sám sebe.</span><span class="sxs-lookup"><span data-stu-id="07a82-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>  
  
-   <span data-ttu-id="07a82-106">Použití proměnné, která se vztahuje k objektu je efektivnější než opakovaně přístup k samotného objektu prostřednictvím nezbytné metody nebo vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="07a82-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>  
  
-   <span data-ttu-id="07a82-107">Můžete změnit proměnnou, která bude odkazovat na další objekty, když běží váš kód.</span><span class="sxs-lookup"><span data-stu-id="07a82-107">You can change a variable to refer to other objects while your code is running.</span></span>  
  
## <a name="making-code-shorter"></a><span data-ttu-id="07a82-108">Kratší provádění kódu</span><span class="sxs-lookup"><span data-stu-id="07a82-108">Making Code Shorter</span></span>  
 <span data-ttu-id="07a82-109">Objektové proměnné můžete použít tak, aby zkrátil kód, který je třeba zadávat.</span><span class="sxs-lookup"><span data-stu-id="07a82-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="07a82-110">Následující příklad používá úplnou cestu metod a vlastností pro přístup <xref:System.Windows.Forms.Control> objektu.</span><span class="sxs-lookup"><span data-stu-id="07a82-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 <span data-ttu-id="07a82-111">Můžete zmenšit tento kód a urychlit spuštění, pokud používáte proměnné objektu pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="07a82-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="07a82-112">Objektová proměnná s určité třídy, které chcete přiřadit k němu by měly deklarovat (`Control` v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="07a82-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="07a82-113">Po přiřazení objektu k proměnné, lze považovat ho stejně jako považovat objektu, na který odkazuje.</span><span class="sxs-lookup"><span data-stu-id="07a82-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="07a82-114">Můžete nastavit nebo získat vlastnosti objektu nebo použít některou z jeho metod.</span><span class="sxs-lookup"><span data-stu-id="07a82-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="07a82-115">Následující příklad používá proměnné objektu můžete zjednodušit kód v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="07a82-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a><span data-ttu-id="07a82-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="07a82-116">See Also</span></span>  
 [<span data-ttu-id="07a82-117">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="07a82-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="07a82-118">Postupy: urychlení přístupu k objektu pomocí cesty dlouhou kvalifikací</span><span class="sxs-lookup"><span data-stu-id="07a82-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)  
 [<span data-ttu-id="07a82-119">Deklarace proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="07a82-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="07a82-120">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="07a82-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="07a82-121">Hodnoty proměnné objektu</span><span class="sxs-lookup"><span data-stu-id="07a82-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)

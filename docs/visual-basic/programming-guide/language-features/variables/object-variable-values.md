---
title: Hodnoty proměnné objektu (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 28307cc477f661c3046e125f297c1519485ad797
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="08326-102">Hodnoty proměnné objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08326-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="08326-103">Proměnná [Object – datový typ](../../../../visual-basic/language-reference/data-types/object-data-type.md) mohou odkazovat na data libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="08326-103">A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="08326-104">Hodnota uložená v `Object` proměnné je udržováno jinde v paměti, zatímco proměnnou obsahuje ukazatele na data.</span><span class="sxs-lookup"><span data-stu-id="08326-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="08326-105">Funkce třídění objektu</span><span class="sxs-lookup"><span data-stu-id="08326-105">Object Classifier Functions</span></span>  
 <span data-ttu-id="08326-106">Visual Basic poskytuje funkce, které vracejí informace o tom, co `Object` proměnná odkazuje na, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="08326-106">Visual Basic supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="08326-107">Funkce</span><span class="sxs-lookup"><span data-stu-id="08326-107">Function</span></span>|<span data-ttu-id="08326-108">Vrátí hodnotu True, pokud je proměnná objektu odkazuje</span><span class="sxs-lookup"><span data-stu-id="08326-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|<span data-ttu-id="08326-109">Pole hodnoty, než jednu hodnotu</span><span class="sxs-lookup"><span data-stu-id="08326-109">An array of values, rather than a single value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|<span data-ttu-id="08326-110">A [Date – datový typ](../../../../visual-basic/language-reference/data-types/date-data-type.md) hodnota nebo řetězec, který lze interpretovat jako hodnota data a času</span><span class="sxs-lookup"><span data-stu-id="08326-110">A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|<span data-ttu-id="08326-111">Objekt typu <xref:System.DBNull>, která představuje data chybí, nebo neexistuje</span><span class="sxs-lookup"><span data-stu-id="08326-111">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|<span data-ttu-id="08326-112">Objekt výjimky, která je odvozena z <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="08326-112">An exception object, which derives from <xref:System.Exception></span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|<span data-ttu-id="08326-113">[Nic](../../../../visual-basic/language-reference/nothing.md), tedy žádný objekt je aktuálně přiřazen k proměnné</span><span class="sxs-lookup"><span data-stu-id="08326-113">[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|<span data-ttu-id="08326-114">Číslo nebo řetězec, který lze interpretovat jako číslo</span><span class="sxs-lookup"><span data-stu-id="08326-114">A number, or a string that can be interpreted as a number</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|<span data-ttu-id="08326-115">Odkaz na typ (například řetězce, pole, delegát nebo typu třídy)</span><span class="sxs-lookup"><span data-stu-id="08326-115">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="08326-116">Aby se zabránilo odesílání neplatnou hodnotu pro operace nebo proceduru můžete použít tyto funkce.</span><span class="sxs-lookup"><span data-stu-id="08326-116">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="08326-117">TypeOf – operátor</span><span class="sxs-lookup"><span data-stu-id="08326-117">TypeOf Operator</span></span>  
 <span data-ttu-id="08326-118">Můžete také [typeof – operátor](../../../../visual-basic/language-reference/operators/typeof-operator.md) k určení, zda proměnná objektu aktuálně odkazuje na konkrétní typ.</span><span class="sxs-lookup"><span data-stu-id="08326-118">You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="08326-119">`TypeOf`... `Is` výraz vyhodnocen jako `True` Pokud běhového typu operandu je odvozený od nebo implementuje zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="08326-119">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="08326-120">Následující příklad používá `TypeOf` na objektové proměnné odkazující na typy hodnoty a odkazu.</span><span class="sxs-lookup"><span data-stu-id="08326-120">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
```  
' The following statement puts a value type (Integer) in an Object variable.  
Dim num As Object = 10  
' The following statement puts a reference type (Form) in an Object variable.  
Dim frm As Object = New Form()  
If TypeOf num Is Long Then Debug.WriteLine("num is Long")  
If TypeOf num Is Integer Then Debug.WriteLine("num is Integer")  
If TypeOf num Is Short Then Debug.WriteLine("num is Short")  
If TypeOf num Is Object Then Debug.WriteLine("num is Object")  
If TypeOf frm Is Form Then Debug.WriteLine("frm is Form")  
If TypeOf frm Is Label Then Debug.WriteLine("frm is Label")  
If TypeOf frm Is Object Then Debug.WriteLine("frm is Object")  
```  
  
 <span data-ttu-id="08326-121">V předchozím příkladu zapíše následující řádky, které se **ladění** okno:</span><span class="sxs-lookup"><span data-stu-id="08326-121">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="08326-122">Objektová proměnná `num` odkazuje na data typu `Integer`, a `frm` odkazuje na objekt třídy <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="08326-122">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="08326-123">Pole objektů</span><span class="sxs-lookup"><span data-stu-id="08326-123">Object Arrays</span></span>  
 <span data-ttu-id="08326-124">Můžete deklarování a použití pole `Object` proměnné.</span><span class="sxs-lookup"><span data-stu-id="08326-124">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="08326-125">To je užitečné, když potřebujete zpracovávat různé datové typy a tříd objektů.</span><span class="sxs-lookup"><span data-stu-id="08326-125">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="08326-126">Všechny elementy ve pole musí mít stejný deklarované datový typ.</span><span class="sxs-lookup"><span data-stu-id="08326-126">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="08326-127">Tento datový typ jako deklarace `Object` vám umožní ukládat objekty a třídy instance spolu s ostatními datovými typy v poli.</span><span class="sxs-lookup"><span data-stu-id="08326-127">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08326-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="08326-128">See Also</span></span>  
 [<span data-ttu-id="08326-129">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="08326-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="08326-130">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="08326-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="08326-131">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="08326-131">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="08326-132">Postupy: Odkazování na aktuální instanci objektu</span><span class="sxs-lookup"><span data-stu-id="08326-132">How to: Refer to the Current Instance of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)  
 [<span data-ttu-id="08326-133">Postupy: Určení, na jaký typ objektová proměnná odkazuje</span><span class="sxs-lookup"><span data-stu-id="08326-133">How to: Determine What Type an Object Variable Refers To</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)  
 [<span data-ttu-id="08326-134">Postupy: Určení, zda dva objekty spolu souvisí</span><span class="sxs-lookup"><span data-stu-id="08326-134">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [<span data-ttu-id="08326-135">Postupy: Určení, zda dva objekty jsou identické</span><span class="sxs-lookup"><span data-stu-id="08326-135">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)  
 [<span data-ttu-id="08326-136">Datové typy</span><span class="sxs-lookup"><span data-stu-id="08326-136">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)

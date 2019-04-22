---
title: Hodnoty proměnné objektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], values
- values [Visual Basic], of object variables
- data types [Visual Basic], object variable
- variables [Visual Basic], object
ms.assetid: 31555704-58a3-49f1-9a0a-6421f605664f
ms.openlocfilehash: c17c5f85952596f0a080ca473e8f792740e66b8f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58840390"
---
# <a name="object-variable-values-visual-basic"></a><span data-ttu-id="0c53f-102">Hodnoty proměnné objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0c53f-102">Object Variable Values (Visual Basic)</span></span>
<span data-ttu-id="0c53f-103">Proměnná [datový typ objektu](../../../../visual-basic/language-reference/data-types/object-data-type.md) mohou odkazovat na data libovolného typu.</span><span class="sxs-lookup"><span data-stu-id="0c53f-103">A variable of the [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md) can refer to data of any type.</span></span> <span data-ttu-id="0c53f-104">Hodnota ukládáte `Object` proměnná zůstane jinde v paměti, zatímco proměnné samotné drží ukazatel na data.</span><span class="sxs-lookup"><span data-stu-id="0c53f-104">The value you store in an `Object` variable is kept elsewhere in memory, while the variable itself holds a pointer to the data.</span></span>  
  
## <a name="object-classifier-functions"></a><span data-ttu-id="0c53f-105">Objekt funkce třídění</span><span class="sxs-lookup"><span data-stu-id="0c53f-105">Object Classifier Functions</span></span>  
 <span data-ttu-id="0c53f-106">Visual Basic poskytuje funkce, které vracejí informace o tom, co `Object` proměnná odkazuje na, jak je znázorněno v následující tabulce.</span><span class="sxs-lookup"><span data-stu-id="0c53f-106">Visual Basic supplies functions that return information about what an `Object` variable refers to, as shown in the following table.</span></span>  
  
|<span data-ttu-id="0c53f-107">Funkce</span><span class="sxs-lookup"><span data-stu-id="0c53f-107">Function</span></span>|<span data-ttu-id="0c53f-108">Vrátí True, pokud je proměnná objektu odkazuje</span><span class="sxs-lookup"><span data-stu-id="0c53f-108">Returns True if the Object variable refers to</span></span>|  
|--------------|---------------------------------------------------|  
|<xref:Microsoft.VisualBasic.Information.IsArray%2A>|<span data-ttu-id="0c53f-109">Pole hodnot, spíše než jednu hodnotu</span><span class="sxs-lookup"><span data-stu-id="0c53f-109">An array of values, rather than a single value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDate%2A>|<span data-ttu-id="0c53f-110">A [Date – datový typ](../../../../visual-basic/language-reference/data-types/date-data-type.md) hodnotu nebo řetězec, který lze interpretovat jako hodnotu data a času</span><span class="sxs-lookup"><span data-stu-id="0c53f-110">A [Date Data Type](../../../../visual-basic/language-reference/data-types/date-data-type.md) value, or a string that can be interpreted as a date and time value</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsDBNull%2A>|<span data-ttu-id="0c53f-111">Objekt typu <xref:System.DBNull>, která představuje data chybí nebo je nekonzistentní</span><span class="sxs-lookup"><span data-stu-id="0c53f-111">An object of type <xref:System.DBNull>, which represents missing or nonexistent data</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsError%2A>|<span data-ttu-id="0c53f-112">Objekt výjimky, která je odvozena z <xref:System.Exception></span><span class="sxs-lookup"><span data-stu-id="0c53f-112">An exception object, which derives from <xref:System.Exception></span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNothing%2A>|<span data-ttu-id="0c53f-113">[Nic](../../../../visual-basic/language-reference/nothing.md), to znamená žádný objekt je aktuálně přiřazená k proměnné</span><span class="sxs-lookup"><span data-stu-id="0c53f-113">[Nothing](../../../../visual-basic/language-reference/nothing.md), that is, no object is currently assigned to the variable</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsNumeric%2A>|<span data-ttu-id="0c53f-114">Číslo nebo řetězec, který může být interpretován jako číslo</span><span class="sxs-lookup"><span data-stu-id="0c53f-114">A number, or a string that can be interpreted as a number</span></span>|  
|<xref:Microsoft.VisualBasic.Information.IsReference%2A>|<span data-ttu-id="0c53f-115">Typ odkazu (například řetězce, pole, delegáta nebo typ třídy)</span><span class="sxs-lookup"><span data-stu-id="0c53f-115">A reference type (such as a string, array, delegate, or class type)</span></span>|  
  
 <span data-ttu-id="0c53f-116">Tyto funkce můžete vyhnout odesílání neplatná hodnota pro operaci nebo proceduru.</span><span class="sxs-lookup"><span data-stu-id="0c53f-116">You can use these functions to avoid submitting an invalid value to an operation or a procedure.</span></span>  
  
## <a name="typeof-operator"></a><span data-ttu-id="0c53f-117">TypeOf – operátor</span><span class="sxs-lookup"><span data-stu-id="0c53f-117">TypeOf Operator</span></span>  
 <span data-ttu-id="0c53f-118">Můžete také použít [TypeOf – operátor](../../../../visual-basic/language-reference/operators/typeof-operator.md) k určení, zda proměnné objektu aktuálně odkazuje na konkrétní data typu.</span><span class="sxs-lookup"><span data-stu-id="0c53f-118">You can also use the [TypeOf Operator](../../../../visual-basic/language-reference/operators/typeof-operator.md) to determine whether an object variable currently refers to a specific data type.</span></span> <span data-ttu-id="0c53f-119">`TypeOf`... `Is` výraz vyhodnocen jako `True` run-time typu operandu je odvozený od nebo implementuje zadaného typu.</span><span class="sxs-lookup"><span data-stu-id="0c53f-119">The `TypeOf`...`Is` expression evaluates to `True` if the run-time type of the operand is derived from or implements the specified type.</span></span>  
  
 <span data-ttu-id="0c53f-120">Následující příklad používá `TypeOf` v objektových proměnných odkazující na hodnotu a referenční typy.</span><span class="sxs-lookup"><span data-stu-id="0c53f-120">The following example uses `TypeOf` on object variables referring to value and reference types.</span></span>  
  
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
  
 <span data-ttu-id="0c53f-121">Předchozí příklad zapíše následující řádky do **ladění** okno:</span><span class="sxs-lookup"><span data-stu-id="0c53f-121">The preceding example writes the following lines to the **Debug** window:</span></span>  
  
 `num is Integer`  
  
 `num is Object`  
  
 `frm is Form`  
  
 `frm is Object`  
  
 <span data-ttu-id="0c53f-122">Objektová proměnná `num` odkazuje na datový typ `Integer`, a `frm` odkazuje na objekt třídy <xref:System.Windows.Forms.Form>.</span><span class="sxs-lookup"><span data-stu-id="0c53f-122">The object variable `num` refers to data of type `Integer`, and `frm` refers to an object of class <xref:System.Windows.Forms.Form>.</span></span>  
  
## <a name="object-arrays"></a><span data-ttu-id="0c53f-123">Pole objektů</span><span class="sxs-lookup"><span data-stu-id="0c53f-123">Object Arrays</span></span>  
 <span data-ttu-id="0c53f-124">Můžete deklarovat a používat celou řadu `Object` proměnné.</span><span class="sxs-lookup"><span data-stu-id="0c53f-124">You can declare and use an array of `Object` variables.</span></span> <span data-ttu-id="0c53f-125">To je užitečné, když potřebujete zpracovávat různé datové typy a třídy objektů.</span><span class="sxs-lookup"><span data-stu-id="0c53f-125">This is useful when you need to handle a variety of data types and object classes.</span></span> <span data-ttu-id="0c53f-126">Všechny prvky pole musí mít stejné deklarovanému datovému typu.</span><span class="sxs-lookup"><span data-stu-id="0c53f-126">All the elements in an array must have the same declared data type.</span></span> <span data-ttu-id="0c53f-127">Tento datový typ jako deklarace `Object` umožňuje ukládat objekty a třídy instance společně s ostatními datovými typy v poli.</span><span class="sxs-lookup"><span data-stu-id="0c53f-127">Declaring this data type as `Object` allows you to store objects and class instances alongside other data types in the array.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c53f-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0c53f-128">See also</span></span>

- [<span data-ttu-id="0c53f-129">Objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="0c53f-129">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="0c53f-130">Deklarace objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="0c53f-130">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="0c53f-131">Přiřazení objektové proměnné</span><span class="sxs-lookup"><span data-stu-id="0c53f-131">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="0c53f-132">Postupy: Odkazování na aktuální instanci objektu</span><span class="sxs-lookup"><span data-stu-id="0c53f-132">How to: Refer to the Current Instance of an Object</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-refer-to-the-current-instance-of-an-object.md)
- [<span data-ttu-id="0c53f-133">Postupy: Určit, jaký typ proměnná objektu odkazuje</span><span class="sxs-lookup"><span data-stu-id="0c53f-133">How to: Determine What Type an Object Variable Refers To</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-what-type-an-object-variable-refers-to.md)
- [<span data-ttu-id="0c53f-134">Postupy: Určení, zda dva objekty souvisejí</span><span class="sxs-lookup"><span data-stu-id="0c53f-134">How to: Determine Whether Two Objects Are Related</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [<span data-ttu-id="0c53f-135">Postupy: Určení, zda dva objekty jsou identické</span><span class="sxs-lookup"><span data-stu-id="0c53f-135">How to: Determine Whether Two Objects Are Identical</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-identical.md)
- [<span data-ttu-id="0c53f-136">Datové typy</span><span class="sxs-lookup"><span data-stu-id="0c53f-136">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)

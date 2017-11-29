---
title: "Určení typu objektu (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9a63b5cf5941deb4dcc7518880b4dc7d0545803c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="58ac1-102">Určení typu objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="58ac1-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="58ac1-103">Obecné objektové proměnné (to znamená, proměnné je deklarovat jako `Object`) může obsahovat objekty z libovolné třídy.</span><span class="sxs-lookup"><span data-stu-id="58ac1-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="58ac1-104">Při použití proměnné typu `Object`, budete muset provést různé akce na základě třídy objektu; například některé objekty nemusí podporovat konkrétní vlastnosti nebo metody.</span><span class="sxs-lookup"><span data-stu-id="58ac1-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]<span data-ttu-id="58ac1-105">poskytuje dvě prostředky pro určení toho, jaký typ objektu je uložené v proměnné objektu: `TypeName` funkce a `TypeOf...Is` operátor.</span><span class="sxs-lookup"><span data-stu-id="58ac1-105"> provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="58ac1-106">TypeName a TypeOf... Je</span><span class="sxs-lookup"><span data-stu-id="58ac1-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="58ac1-107">`TypeName` Funkce vrátí řetězec, je nejlepší volbou, když potřebujete uložit nebo zobrazit název třídy objektu, jak je znázorněno v následující fragment kódu:</span><span class="sxs-lookup"><span data-stu-id="58ac1-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_1.vb)]  
  
 <span data-ttu-id="58ac1-108">`TypeOf...Is` Operátor je nejlepší volbou pro testování typ objektu, protože je mnohem rychlejší než porovnání ekvivalentní řetězec pomocí `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="58ac1-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="58ac1-109">Následující fragment kódu používá `TypeOf...Is` v rámci `If...Then...Else` příkaz:</span><span class="sxs-lookup"><span data-stu-id="58ac1-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_2.vb)]  
  
 <span data-ttu-id="58ac1-110">Zde jsou kvůli slovo varování.</span><span class="sxs-lookup"><span data-stu-id="58ac1-110">A word of caution is due here.</span></span> <span data-ttu-id="58ac1-111">`TypeOf...Is` Vrátí operátor `True` Pokud objekt určitého typu nebo je odvozený z konkrétního typu.</span><span class="sxs-lookup"><span data-stu-id="58ac1-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="58ac1-112">Téměř všechno, co se děje s [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] zahrnuje objekty, které zahrnují některé prvky obvykle představit jako objekty, například řetězce a celá čísla.</span><span class="sxs-lookup"><span data-stu-id="58ac1-112">Almost everything you do with [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="58ac1-113">Tyto objekty jsou odvozeny od a dědí z metody <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="58ac1-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="58ac1-114">Když uplyne `Integer` a vyhodnotí s `Object`, `TypeOf...Is` vrátí operátor `True`.</span><span class="sxs-lookup"><span data-stu-id="58ac1-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="58ac1-115">Následující příklad uvádí, že parametr `InParam` se `Object` a `Integer`:</span><span class="sxs-lookup"><span data-stu-id="58ac1-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_3.vb)]  
  
 <span data-ttu-id="58ac1-116">Následující příklad používá obě `TypeOf...Is` a `TypeName` k určení typu objektu do ní předán v `Ctrl` argument.</span><span class="sxs-lookup"><span data-stu-id="58ac1-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="58ac1-117">`TestObject` Volání procedur `ShowType` s tři různé typy ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="58ac1-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="58ac1-118">Chcete-li spustit příklad</span><span class="sxs-lookup"><span data-stu-id="58ac1-118">To run the example</span></span>  
  
1.  <span data-ttu-id="58ac1-119">Vytvořte nový projekt aplikace Windows a přidejte <xref:System.Windows.Forms.Button> řízení, <xref:System.Windows.Forms.CheckBox> řízení a <xref:System.Windows.Forms.RadioButton> ovládacího prvku formuláře.</span><span class="sxs-lookup"><span data-stu-id="58ac1-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2.  <span data-ttu-id="58ac1-120">Z tlačítko ve formuláři, volání `TestObject` postupu.</span><span class="sxs-lookup"><span data-stu-id="58ac1-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3.  <span data-ttu-id="58ac1-121">Přidejte následující kód do svého formuláře:</span><span class="sxs-lookup"><span data-stu-id="58ac1-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](../../../../visual-basic/misc/codesnippet/VisualBasic/determining-object-type_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="58ac1-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="58ac1-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Information.TypeName%2A>  
 [<span data-ttu-id="58ac1-123">Volání vlastnosti nebo metody pomocí názvu řetězce</span><span class="sxs-lookup"><span data-stu-id="58ac1-123">Calling a Property or Method Using a String Name</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)  
 [<span data-ttu-id="58ac1-124">Object – datový typ</span><span class="sxs-lookup"><span data-stu-id="58ac1-124">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [<span data-ttu-id="58ac1-125">If... Potom... Else – příkaz</span><span class="sxs-lookup"><span data-stu-id="58ac1-125">If...Then...Else Statement</span></span>](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)  
 [<span data-ttu-id="58ac1-126">String – datový typ</span><span class="sxs-lookup"><span data-stu-id="58ac1-126">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)  
 [<span data-ttu-id="58ac1-127">Integer – datový typ</span><span class="sxs-lookup"><span data-stu-id="58ac1-127">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)

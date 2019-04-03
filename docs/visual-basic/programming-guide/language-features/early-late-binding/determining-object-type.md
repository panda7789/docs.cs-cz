---
title: Určení typu objektu (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: 625ddb8fc153708a80e8cf475f48d595efbe4df2
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58842626"
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="55f9c-102">Určení typu objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55f9c-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="55f9c-103">Generický objekt proměnné (tedy proměnné můžete deklarovat jako `Object`) může obsahovat objekty z jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="55f9c-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="55f9c-104">Při použití proměnné typu `Object`, možná budete muset provést různé akce na základě třídy objektu; například nemusí podporovat některé objekty určité vlastnosti nebo metody.</span><span class="sxs-lookup"><span data-stu-id="55f9c-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="55f9c-105">Visual Basic poskytuje dva prostředky určující, jaký typ objektu je uložen v proměnné objektu: `TypeName` funkce a `TypeOf...Is` operátor.</span><span class="sxs-lookup"><span data-stu-id="55f9c-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="55f9c-106">Vlastnosti TypeName a TypeOf... Je</span><span class="sxs-lookup"><span data-stu-id="55f9c-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="55f9c-107">`TypeName` Funkce vrátí řetězec a je nejlepší volbou, pokud potřebujete uložit nebo zobrazit název třídy objektu, jak je znázorněno v následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="55f9c-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 <span data-ttu-id="55f9c-108">`TypeOf...Is` Operátor je nejlepší volbou pro testování typ objektu, protože je mnohem rychlejší než porovnání odpovídající řetězec pomocí `TypeName`.</span><span class="sxs-lookup"><span data-stu-id="55f9c-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="55f9c-109">Následující fragment kódu používá `TypeOf...Is` v rámci `If...Then...Else` – příkaz:</span><span class="sxs-lookup"><span data-stu-id="55f9c-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 <span data-ttu-id="55f9c-110">Tady je termín slovo upozornění.</span><span class="sxs-lookup"><span data-stu-id="55f9c-110">A word of caution is due here.</span></span> <span data-ttu-id="55f9c-111">`TypeOf...Is` Operátor vrátí `True` Pokud objekt je určitého typu nebo je odvozen z určitého typu.</span><span class="sxs-lookup"><span data-stu-id="55f9c-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="55f9c-112">Téměř vše, co dělat s jazykem Visual Basic zahrnuje objekty, které obsahují některé prvky, které nejsou běžně považují za objekty, jako jsou řetězce a celá čísla.</span><span class="sxs-lookup"><span data-stu-id="55f9c-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="55f9c-113">Tyto objekty jsou odvozeny z a dědí z metody <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="55f9c-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="55f9c-114">Po uplynutí `Integer` a vyhodnocené s `Object`, `TypeOf...Is` operátor vrátí `True`.</span><span class="sxs-lookup"><span data-stu-id="55f9c-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="55f9c-115">Následující příklad uvádí, že parametr `InParam` je oba směry `Object` a `Integer`:</span><span class="sxs-lookup"><span data-stu-id="55f9c-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 <span data-ttu-id="55f9c-116">Následující příklad používá obě `TypeOf...Is` a `TypeName` k určení typu objektu do ní předán v `Ctrl` argument.</span><span class="sxs-lookup"><span data-stu-id="55f9c-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="55f9c-117">`TestObject` Volání procedur `ShowType` s tři různé typy ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="55f9c-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="55f9c-118">Chcete-li spustit příklad</span><span class="sxs-lookup"><span data-stu-id="55f9c-118">To run the example</span></span>  
  
1.  <span data-ttu-id="55f9c-119">Vytvořte nový projekt aplikace Windows a přidejte <xref:System.Windows.Forms.Button> ovládací prvek, <xref:System.Windows.Forms.CheckBox> ovládacího prvku a <xref:System.Windows.Forms.RadioButton> ovládacího prvku na formuláři.</span><span class="sxs-lookup"><span data-stu-id="55f9c-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2.  <span data-ttu-id="55f9c-120">Pomocí tlačítka na formuláři, zavolejte `TestObject` postup.</span><span class="sxs-lookup"><span data-stu-id="55f9c-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3.  <span data-ttu-id="55f9c-121">Přidejte následující kód do svého formuláře:</span><span class="sxs-lookup"><span data-stu-id="55f9c-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a><span data-ttu-id="55f9c-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="55f9c-122">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [<span data-ttu-id="55f9c-123">Volání vlastnosti nebo metody pomocí názvu řetězce</span><span class="sxs-lookup"><span data-stu-id="55f9c-123">Calling a Property or Method Using a String Name</span></span>](../../../../visual-basic/programming-guide/language-features/early-late-binding/calling-a-property-or-method-using-a-string-name.md)
- [<span data-ttu-id="55f9c-124">Datový typ Object</span><span class="sxs-lookup"><span data-stu-id="55f9c-124">Object Data Type</span></span>](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="55f9c-125">Příkaz If...Then...Else</span><span class="sxs-lookup"><span data-stu-id="55f9c-125">If...Then...Else Statement</span></span>](../../../../visual-basic/language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="55f9c-126">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="55f9c-126">String Data Type</span></span>](../../../../visual-basic/language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="55f9c-127">Datový typ Integer</span><span class="sxs-lookup"><span data-stu-id="55f9c-127">Integer Data Type</span></span>](../../../../visual-basic/language-reference/data-types/integer-data-type.md)

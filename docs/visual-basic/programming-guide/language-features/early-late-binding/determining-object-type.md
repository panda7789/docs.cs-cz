---
title: Určení typu objektu
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], discovering which an object belongs to
- types [Visual Basic], determining Visual Basic object types
- object variables [Visual Basic], testing values
- TypeOf...Is expression, object type at run time
- TypeName function
- objects [Visual Basic], type determining
ms.assetid: d95e7ad1-cd63-41d6-9a28-d7a1380d49c1
ms.openlocfilehash: 3b1c4ad0ab4fd8d2897aff6ad9097cdc81272455
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410641"
---
# <a name="determining-object-type-visual-basic"></a><span data-ttu-id="469b5-102">Určení typu objektu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="469b5-102">Determining Object Type (Visual Basic)</span></span>
<span data-ttu-id="469b5-103">Proměnné obecného objektu (to znamená, že proměnné, jako `Object` ), mohou uchovávat objekty z libovolné třídy.</span><span class="sxs-lookup"><span data-stu-id="469b5-103">Generic object variables (that is, variables you declare as `Object`) can hold objects from any class.</span></span> <span data-ttu-id="469b5-104">Při použití proměnných typu `Object` může být nutné provést různé akce na základě třídy objektu; například některé objekty nemusí podporovat určitou vlastnost nebo metodu.</span><span class="sxs-lookup"><span data-stu-id="469b5-104">When using variables of type `Object`, you may need to take different actions based on the class of the object; for example, some objects might not support a particular property or method.</span></span> <span data-ttu-id="469b5-105">Visual Basic poskytuje dva způsoby určení, který typ objektu je uložen v proměnné objektu: `TypeName` funkce a `TypeOf...Is` operátor.</span><span class="sxs-lookup"><span data-stu-id="469b5-105">Visual Basic provides two means of determining which type of object is stored in an object variable: the `TypeName` function and the `TypeOf...Is` operator.</span></span>  
  
## <a name="typename-and-typeofis"></a><span data-ttu-id="469b5-106">TypeName a TypeOf... Dojde</span><span class="sxs-lookup"><span data-stu-id="469b5-106">TypeName and TypeOf…Is</span></span>  
 <span data-ttu-id="469b5-107">`TypeName`Funkce vrátí řetězec a je nejvhodnější volbou, pokud potřebujete uložit nebo zobrazit název třídy objektu, jak je znázorněno v následujícím fragmentu kódu:</span><span class="sxs-lookup"><span data-stu-id="469b5-107">The `TypeName` function returns a string and is the best choice when you need to store or display the class name of an object, as shown in the following code fragment:</span></span>  
  
 [!code-vb[VbVbalrOOP#92](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#92)]  
  
 <span data-ttu-id="469b5-108">`TypeOf...Is`Operátor je nejlepší volbou pro testování typu objektu, protože je mnohem rychlejší než ekvivalentní porovnávání řetězců pomocí `TypeName` .</span><span class="sxs-lookup"><span data-stu-id="469b5-108">The `TypeOf...Is` operator is the best choice for testing an object's type, because it is much faster than an equivalent string comparison using `TypeName`.</span></span> <span data-ttu-id="469b5-109">Následující fragment kódu používá `TypeOf...Is` v rámci `If...Then...Else` příkazu:</span><span class="sxs-lookup"><span data-stu-id="469b5-109">The following code fragment uses `TypeOf...Is` within an `If...Then...Else` statement:</span></span>  
  
 [!code-vb[VbVbalrOOP#93](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#93)]  
  
 <span data-ttu-id="469b5-110">Zde je uvedeno slovo s upozorněním.</span><span class="sxs-lookup"><span data-stu-id="469b5-110">A word of caution is due here.</span></span> <span data-ttu-id="469b5-111">`TypeOf...Is`Operátor vrátí `True` , zda je objekt určitého typu nebo je odvozen z konkrétního typu.</span><span class="sxs-lookup"><span data-stu-id="469b5-111">The `TypeOf...Is` operator returns `True` if an object is of a specific type, or is derived from a specific type.</span></span> <span data-ttu-id="469b5-112">Téměř všechno, co děláte s Visual Basic zahrnuje objekty, které obsahují některé prvky, které nejsou obvykle považovány za objekty, jako jsou například řetězce a celá čísla.</span><span class="sxs-lookup"><span data-stu-id="469b5-112">Almost everything you do with Visual Basic involves objects, which include some elements not normally thought of as objects, such as strings and integers.</span></span> <span data-ttu-id="469b5-113">Tyto objekty jsou odvozeny z a dědí metody z <xref:System.Object> .</span><span class="sxs-lookup"><span data-stu-id="469b5-113">These objects are derived from and inherit methods from <xref:System.Object>.</span></span> <span data-ttu-id="469b5-114">Při předání `Integer` a vyhodnocení pomocí `Object` `TypeOf...Is` operátoru vrátí operátor `True` .</span><span class="sxs-lookup"><span data-stu-id="469b5-114">When passed an `Integer` and evaluated with `Object`, the `TypeOf...Is` operator returns `True`.</span></span> <span data-ttu-id="469b5-115">Následující příklad hlásí, že parametr `InParam` je `Object` a `Integer` :</span><span class="sxs-lookup"><span data-stu-id="469b5-115">The following example reports that the parameter `InParam` is both an `Object` and an `Integer`:</span></span>  
  
 [!code-vb[VbVbalrOOP#94](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#94)]  
  
 <span data-ttu-id="469b5-116">Následující příklad používá jak `TypeOf...Is` a `TypeName` k určení typu objektu předaného do něj v `Ctrl` argumentu.</span><span class="sxs-lookup"><span data-stu-id="469b5-116">The following example uses both `TypeOf...Is` and `TypeName` to determine the type of object passed to it in the `Ctrl` argument.</span></span> <span data-ttu-id="469b5-117">`TestObject`Procedura volá `ShowType` tři různé druhy ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="469b5-117">The `TestObject` procedure calls `ShowType` with three different kinds of controls.</span></span>  
  
#### <a name="to-run-the-example"></a><span data-ttu-id="469b5-118">Chcete-li spustit příklad</span><span class="sxs-lookup"><span data-stu-id="469b5-118">To run the example</span></span>  
  
1. <span data-ttu-id="469b5-119">Vytvořte nový projekt aplikace pro Windows a přidejte ovládací <xref:System.Windows.Forms.Button> prvek, <xref:System.Windows.Forms.CheckBox> ovládací prvek a ovládací prvek <xref:System.Windows.Forms.RadioButton> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="469b5-119">Create a new Windows Application project and add a <xref:System.Windows.Forms.Button> control, a <xref:System.Windows.Forms.CheckBox> control, and a <xref:System.Windows.Forms.RadioButton> control to the form.</span></span>  
  
2. <span data-ttu-id="469b5-120">Z tlačítka na formuláři zavolejte `TestObject` proceduru.</span><span class="sxs-lookup"><span data-stu-id="469b5-120">From the button on your form, call the `TestObject` procedure.</span></span>  
  
3. <span data-ttu-id="469b5-121">Do formuláře přidejte následující kód:</span><span class="sxs-lookup"><span data-stu-id="469b5-121">Add the following code to your form:</span></span>  
  
     [!code-vb[VbVbalrOOP#95](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#95)]  
  
## <a name="see-also"></a><span data-ttu-id="469b5-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="469b5-122">See also</span></span>

- <xref:Microsoft.VisualBasic.Information.TypeName%2A>
- [<span data-ttu-id="469b5-123">Volání vlastnosti nebo metody pomocí názvu řetězce</span><span class="sxs-lookup"><span data-stu-id="469b5-123">Calling a Property or Method Using a String Name</span></span>](calling-a-property-or-method-using-a-string-name.md)
- [<span data-ttu-id="469b5-124">Datový typ objektu</span><span class="sxs-lookup"><span data-stu-id="469b5-124">Object Data Type</span></span>](../../../language-reference/data-types/object-data-type.md)
- [<span data-ttu-id="469b5-125">If...Then...Else – příkaz</span><span class="sxs-lookup"><span data-stu-id="469b5-125">If...Then...Else Statement</span></span>](../../../language-reference/statements/if-then-else-statement.md)
- [<span data-ttu-id="469b5-126">Datový typ String</span><span class="sxs-lookup"><span data-stu-id="469b5-126">String Data Type</span></span>](../../../language-reference/data-types/string-data-type.md)
- [<span data-ttu-id="469b5-127">Integer – datový typ</span><span class="sxs-lookup"><span data-stu-id="469b5-127">Integer Data Type</span></span>](../../../language-reference/data-types/integer-data-type.md)

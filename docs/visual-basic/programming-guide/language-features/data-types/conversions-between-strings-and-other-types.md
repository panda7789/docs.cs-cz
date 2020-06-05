---
title: Převody mezi řetězci a ostatními typy
ms.date: 07/20/2015
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
ms.openlocfilehash: ae8f7c2159191536013fafd8bfd10fb9a93fb785
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84394218"
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="5828e-102">Převody mezi řetězci a ostatními typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5828e-102">Conversions Between Strings and Other Types (Visual Basic)</span></span>
<span data-ttu-id="5828e-103">Můžete převést číselnou `Boolean` hodnotu, nebo hodnotu data a času na `String` .</span><span class="sxs-lookup"><span data-stu-id="5828e-103">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="5828e-104">Můžete také převést v opačném směru – od řetězcové hodnoty na číslo, `Boolean` nebo `Date` – za předpokladu, že obsah řetězce může být interpretován jako platná hodnota cílového datového typu.</span><span class="sxs-lookup"><span data-stu-id="5828e-104">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="5828e-105">Pokud se nedaří, dojde k chybě za běhu.</span><span class="sxs-lookup"><span data-stu-id="5828e-105">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="5828e-106">Převody všech těchto přiřazení v obou směrech mají zúžené převody.</span><span class="sxs-lookup"><span data-stu-id="5828e-106">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="5828e-107">Měli byste použít klíčová slova konverze typu ( `CBool` , `CByte` , `CDate` , `CDbl` , `CDec` , `CInt` , `CLng` , `CSByte` , `CShort` , `CSng` , `CStr` , `CUInt` , `CULng` , `CUShort` , a `CType` ).</span><span class="sxs-lookup"><span data-stu-id="5828e-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="5828e-108"><xref:Microsoft.VisualBasic.Strings.Format%2A>Funkce a <xref:Microsoft.VisualBasic.Conversion.Val%2A> poskytují větší kontrolu nad převody mezi řetězci a čísly.</span><span class="sxs-lookup"><span data-stu-id="5828e-108">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="5828e-109">Pokud jste definovali třídu nebo strukturu, můžete definovat operátory převodu typů mezi `String` a typem vaší třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="5828e-109">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="5828e-110">Další informace naleznete v tématu [How to: define a Conversion operátor](../procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="5828e-110">For more information, see [How to: Define a Conversion Operator](../procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="5828e-111">Převod čísel na řetězce</span><span class="sxs-lookup"><span data-stu-id="5828e-111">Conversion of Numbers to Strings</span></span>  
 <span data-ttu-id="5828e-112">Funkci lze použít `Format` k převodu čísla na formátovaný řetězec, který může obsahovat nejen příslušné číslice, ale také formátování symbolů, jako je například symbol měny (například `$` ), oddělovače tisíců nebo *symboly seskupování číslic* (například `,` ), a oddělovač desetinných míst (například `.` ).</span><span class="sxs-lookup"><span data-stu-id="5828e-112">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="5828e-113">`Format`automaticky používá příslušné symboly podle nastavení **místní volby** , které jsou zadány v **Ovládacích panelech**systému Windows.</span><span class="sxs-lookup"><span data-stu-id="5828e-113">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="5828e-114">Všimněte si, že operátor zřetězení ( `&` ) může převést číslo na řetězec implicitně, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="5828e-114">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```vb  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="5828e-115">Konverze řetězců na čísla</span><span class="sxs-lookup"><span data-stu-id="5828e-115">Conversion of Strings to Numbers</span></span>  
 <span data-ttu-id="5828e-116">Funkci lze použít `Val` k explicitnímu převodu číslic v řetězci na číslo.</span><span class="sxs-lookup"><span data-stu-id="5828e-116">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="5828e-117">`Val`přečte řetězec, dokud nenalezne znak, který je jiný než číslice, mezera, karta, LF nebo tečka.</span><span class="sxs-lookup"><span data-stu-id="5828e-117">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="5828e-118">Sekvence "&O" a "&H" mění základ číselné soustavy a ukončí kontrolu.</span><span class="sxs-lookup"><span data-stu-id="5828e-118">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="5828e-119">Dokud přestane přečtení, `Val` převede všechny příslušné znaky na číselnou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="5828e-119">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="5828e-120">Například následující příkaz vrátí hodnotu `141.825` .</span><span class="sxs-lookup"><span data-stu-id="5828e-120">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="5828e-121">Když Visual Basic převede řetězec na číselnou hodnotu, použije nastavení **místní možnosti** zadané v **Ovládacích panelech** systému Windows k interpretaci oddělovače tisíců, oddělovače desetinných míst a symbolu měny.</span><span class="sxs-lookup"><span data-stu-id="5828e-121">When Visual Basic converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="5828e-122">To znamená, že převod může být úspěšný při jednom nastavení, ale ne na jiném.</span><span class="sxs-lookup"><span data-stu-id="5828e-122">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="5828e-123">Například `"$14.20"` je přijatelné v národním prostředí anglické verze (USA), ale ne v jakémkoli francouzském národním prostředí.</span><span class="sxs-lookup"><span data-stu-id="5828e-123">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5828e-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="5828e-124">See also</span></span>

- [<span data-ttu-id="5828e-125">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5828e-125">Type Conversions in Visual Basic</span></span>](type-conversions.md)
- [<span data-ttu-id="5828e-126">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="5828e-126">Widening and Narrowing Conversions</span></span>](widening-and-narrowing-conversions.md)
- [<span data-ttu-id="5828e-127">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="5828e-127">Implicit and Explicit Conversions</span></span>](implicit-and-explicit-conversions.md)
- [<span data-ttu-id="5828e-128">Postupy: Převedení objektu na jiný typ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5828e-128">How to: Convert an Object to Another Type in Visual Basic</span></span>](how-to-convert-an-object-to-another-type.md)
- [<span data-ttu-id="5828e-129">Převody polí</span><span class="sxs-lookup"><span data-stu-id="5828e-129">Array Conversions</span></span>](array-conversions.md)
- [<span data-ttu-id="5828e-130">Datové typy</span><span class="sxs-lookup"><span data-stu-id="5828e-130">Data Types</span></span>](../../../language-reference/data-types/index.md)
- [<span data-ttu-id="5828e-131">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="5828e-131">Type Conversion Functions</span></span>](../../../language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="5828e-132">Vývoj globálních a lokalizovaných aplikací</span><span class="sxs-lookup"><span data-stu-id="5828e-132">Develop globalized and localized apps</span></span>](/visualstudio/ide/globalizing-and-localizing-applications)

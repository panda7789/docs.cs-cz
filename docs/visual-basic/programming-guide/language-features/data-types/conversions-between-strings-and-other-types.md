---
title: "Převody mezi řetězci a ostatními typy (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data type conversion [Visual Basic], string
- conversions [Visual Basic], type
- string conversion [Visual Basic]
- conversions [Visual Basic], data type
- type conversion [Visual Basic], string
- regional options
ms.assetid: c3a99596-f09a-44a5-81dd-1b89a094f1df
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 71ece18d4ce33b7b637410110e825b389affcd67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="conversions-between-strings-and-other-types-visual-basic"></a><span data-ttu-id="00d1a-102">Převody mezi řetězci a ostatními typy (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="00d1a-102">Conversions Between Strings and Other Types (Visual Basic)</span></span>
<span data-ttu-id="00d1a-103">Můžete převést jednu číslici, `Boolean`, nebo hodnotu data a času `String`.</span><span class="sxs-lookup"><span data-stu-id="00d1a-103">You can convert a numeric, `Boolean`, or date/time value to a `String`.</span></span> <span data-ttu-id="00d1a-104">Můžete také převést v opačném směru – z řetězcové hodnoty číselné literály, `Boolean`, nebo `Date` – zadaný řetězec obsah lze interpretovat jako platná hodnota cílový datový typ.</span><span class="sxs-lookup"><span data-stu-id="00d1a-104">You can also convert in the reverse direction — from a string value to numeric, `Boolean`, or `Date` — provided the contents of the string can be interpreted as a valid value of the destination data type.</span></span> <span data-ttu-id="00d1a-105">Pokud to není možné, dojde k chybě spuštění.</span><span class="sxs-lookup"><span data-stu-id="00d1a-105">If they cannot, a run-time error occurs.</span></span>  
  
 <span data-ttu-id="00d1a-106">Převody pro všechny tyto úlohy, v obou směrech jsou zužující převody.</span><span class="sxs-lookup"><span data-stu-id="00d1a-106">The conversions for all these assignments, in either direction, are narrowing conversions.</span></span> <span data-ttu-id="00d1a-107">Měli byste použít klíčová slova převodu typu (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, a `CType`).</span><span class="sxs-lookup"><span data-stu-id="00d1a-107">You should use the type conversion keywords (`CBool`, `CByte`, `CDate`, `CDbl`, `CDec`, `CInt`, `CLng`, `CSByte`, `CShort`, `CSng`, `CStr`, `CUInt`, `CULng`, `CUShort`, and `CType`).</span></span> <span data-ttu-id="00d1a-108"><xref:Microsoft.VisualBasic.Strings.Format%2A> a <xref:Microsoft.VisualBasic.Conversion.Val%2A> funkce získáte další kontrolu nad převody mezi řetězci a čísla.</span><span class="sxs-lookup"><span data-stu-id="00d1a-108">The <xref:Microsoft.VisualBasic.Strings.Format%2A> and <xref:Microsoft.VisualBasic.Conversion.Val%2A> functions give you additional control over conversions between strings and numbers.</span></span>  
  
 <span data-ttu-id="00d1a-109">Pokud jste definovali třídu nebo strukturu, můžete definovat operátory převodu typu mezi `String` a typ třídu nebo strukturu.</span><span class="sxs-lookup"><span data-stu-id="00d1a-109">If you have defined a class or structure, you can define type conversion operators between `String` and the type of your class or structure.</span></span> <span data-ttu-id="00d1a-110">Další informace najdete v tématu [postupy: definice operátora převodu](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span><span class="sxs-lookup"><span data-stu-id="00d1a-110">For more information, see [How to: Define a Conversion Operator](../../../../visual-basic/programming-guide/language-features/procedures/how-to-define-a-conversion-operator.md).</span></span>  
  
## <a name="conversion-of-numbers-to-strings"></a><span data-ttu-id="00d1a-111">Převádění čísla na řetězce</span><span class="sxs-lookup"><span data-stu-id="00d1a-111">Conversion of Numbers to Strings</span></span>  
 <span data-ttu-id="00d1a-112">Můžete použít `Format` funkce převodu čísla na řetězec formátovaný, která může zahrnovat nejen příslušné číslic, ale také formátování symboly, jako je currency přihlašovací (například `$`), tisíc oddělovačů nebo *seskupování číslic symboly* (například `,`) a oddělovač desetinných míst (například `.`).</span><span class="sxs-lookup"><span data-stu-id="00d1a-112">You can use the `Format` function to convert a number to a formatted string, which can include not only the appropriate digits but also formatting symbols such as a currency sign (such as `$`), thousands separators or *digit grouping symbols* (such as `,`), and a decimal separator (such as `.`).</span></span> <span data-ttu-id="00d1a-113">`Format`automaticky použije příslušné symboly podle požadavků **místní nastavení** nastavení zadané v systému Windows **ovládací panely**.</span><span class="sxs-lookup"><span data-stu-id="00d1a-113">`Format` automatically uses the appropriate symbols according to the **Regional Options** settings specified in the Windows **Control Panel**.</span></span>  
  
 <span data-ttu-id="00d1a-114">Všimněte si, že zřetězení (`&`) operátor můžete čísla na řetězec implicitně převést, jak ukazuje následující příklad.</span><span class="sxs-lookup"><span data-stu-id="00d1a-114">Note that the concatenation (`&`) operator can convert a number to a string implicitly, as the following example shows.</span></span>  
  
```  
' The following statement converts count to a String value.  
Str = "The total count is " & count  
```  
  
## <a name="conversion-of-strings-to-numbers"></a><span data-ttu-id="00d1a-115">Převod řetězců na čísla</span><span class="sxs-lookup"><span data-stu-id="00d1a-115">Conversion of Strings to Numbers</span></span>  
 <span data-ttu-id="00d1a-116">Můžete použít `Val` funkce explicitně převést číslic v řetězec na číslo.</span><span class="sxs-lookup"><span data-stu-id="00d1a-116">You can use the `Val` function to explicitly convert the digits in a string to a number.</span></span> <span data-ttu-id="00d1a-117">`Val`načte řetězec, dokud zjistí znak než číslice, místo, karta, nového řádku nebo období.</span><span class="sxs-lookup"><span data-stu-id="00d1a-117">`Val` reads the string until it encounters a character other than a digit, space, tab, line feed, or period.</span></span> <span data-ttu-id="00d1a-118">Daná pořadí "& O" a "& H" alter základní číslo systému a ukončete kontrolu.</span><span class="sxs-lookup"><span data-stu-id="00d1a-118">The sequences "&O" and "&H" alter the base of the number system and terminate the scanning.</span></span> <span data-ttu-id="00d1a-119">Končí čtení, `Val` převede všechny znaky odpovídající číselná hodnota.</span><span class="sxs-lookup"><span data-stu-id="00d1a-119">Until it stops reading, `Val` converts all appropriate characters to a numeric value.</span></span> <span data-ttu-id="00d1a-120">Například následující příkaz vrátí hodnotu `141.825`.</span><span class="sxs-lookup"><span data-stu-id="00d1a-120">For example, the following statement returns the value `141.825`.</span></span>  
  
 `Val("   14   1.825 miles")`  
  
 <span data-ttu-id="00d1a-121">Když [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] převede řetězec na číselnou hodnotu, použije **místní nastavení** nastavení zadané v systému Windows **ovládací panely** interpretovat tisíců oddělovač, oddělovač desetinných míst a symbolu měny.</span><span class="sxs-lookup"><span data-stu-id="00d1a-121">When [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] converts a string to a numeric value, it uses the **Regional Options** settings specified in the Windows **Control Panel** to interpret the thousands separator, decimal separator, and currency symbol.</span></span> <span data-ttu-id="00d1a-122">To znamená, že převodu z může úspěšné pod jednou, ale není jiná nastavení.</span><span class="sxs-lookup"><span data-stu-id="00d1a-122">This means that a conversion might succeed under one setting but not another.</span></span> <span data-ttu-id="00d1a-123">Například `"$14.20"` je přijatelné v národním prostředí Czech (Czech Republic), ale není v kterémkoli národním prostředí francouzštině.</span><span class="sxs-lookup"><span data-stu-id="00d1a-123">For example, `"$14.20"` is acceptable in the English (United States) locale but not in any French locale.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="00d1a-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="00d1a-124">See Also</span></span>  
 [<span data-ttu-id="00d1a-125">Převody typů v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="00d1a-125">Type Conversions in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/type-conversions.md)  
 [<span data-ttu-id="00d1a-126">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="00d1a-126">Widening and Narrowing Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [<span data-ttu-id="00d1a-127">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="00d1a-127">Implicit and Explicit Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="00d1a-128">Postupy: převedení objektu na jiný typ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="00d1a-128">How to: Convert an Object to Another Type in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/how-to-convert-an-object-to-another-type.md)  
 [<span data-ttu-id="00d1a-129">Převody pole</span><span class="sxs-lookup"><span data-stu-id="00d1a-129">Array Conversions</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/array-conversions.md)  
 [<span data-ttu-id="00d1a-130">Datové typy</span><span class="sxs-lookup"><span data-stu-id="00d1a-130">Data Types</span></span>](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="00d1a-131">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="00d1a-131">Type Conversion Functions</span></span>](../../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="00d1a-132">Úvod do mezinárodních aplikací založených na rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="00d1a-132">Introduction to International Applications Based on the .NET Framework</span></span>](/visualstudio/ide/introduction-to-international-applications-based-on-the-dotnet-framework)

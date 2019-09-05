---
title: 'Postupy: Určení, zda řetězec představuje číselnou hodnotu – C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 8fc5051893882a6dbdbb4c9097949794d4430a93
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252956"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="d396e-102">Postupy: Určení, zda řetězec představuje číselnou hodnotu (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="d396e-102">How to: Determine Whether a String Represents a Numeric Value (C# Programming Guide)</span></span>
<span data-ttu-id="d396e-103">Chcete-li zjistit, zda je řetězec platnou reprezentací zadaného číselného typu, použijte statickou `TryParse` metodu, která je implementována všemi primitivními číselnými typy a také podle <xref:System.DateTime> typů <xref:System.Net.IPAddress>, jako jsou a.</span><span class="sxs-lookup"><span data-stu-id="d396e-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="d396e-104">Následující příklad ukazuje, jak určit, zda je "108" platný [int](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="d396e-104">The following example shows how to determine whether "108" is a valid [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
```csharp  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="d396e-105">Pokud řetězec obsahuje nenumerické znaky nebo číselná hodnota je pro konkrétní typ, který jste zadali, příliš velká nebo příliš malá, `TryParse` vrátí hodnotu false a nastaví výstupní parametr na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="d396e-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="d396e-106">V opačném případě vrátí hodnotu true a nastaví výstupní parametr na číselnou hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="d396e-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d396e-107">Řetězec může obsahovat pouze číselné znaky a stále není platný pro typ, jehož `TryParse` metodu používáte.</span><span class="sxs-lookup"><span data-stu-id="d396e-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="d396e-108">Například "256" není platná hodnota `byte` , ale je platná pro. `int`</span><span class="sxs-lookup"><span data-stu-id="d396e-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="d396e-109">"98,6" není platná hodnota `int` , ale je platná. `decimal`</span><span class="sxs-lookup"><span data-stu-id="d396e-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d396e-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="d396e-110">Example</span></span>  
 <span data-ttu-id="d396e-111">Následující `TryParse` příklady ukazují `long`, jak používat s řetězcovými reprezentacemi hodnot, `byte`a `decimal` .</span><span class="sxs-lookup"><span data-stu-id="d396e-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d396e-112">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="d396e-112">Robust Programming</span></span>  
 <span data-ttu-id="d396e-113">Primitivní číselné typy také implementují `Parse` statickou metodu, která vyvolá výjimku, pokud řetězec není platným číslem.</span><span class="sxs-lookup"><span data-stu-id="d396e-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="d396e-114">`TryParse`je všeobecně efektivnější, protože vrací hodnotu false pouze v případě, že je číslo neplatné.</span><span class="sxs-lookup"><span data-stu-id="d396e-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d396e-115">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d396e-115">.NET Framework Security</span></span>  
 <span data-ttu-id="d396e-116">Vždy použijte `TryParse` metody nebo `Parse` k ověření vstupu uživatele z ovládacích prvků, jako jsou textová pole a pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="d396e-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d396e-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d396e-117">See also</span></span>

- [<span data-ttu-id="d396e-118">Postupy: Převod bajtového pole na int</span><span class="sxs-lookup"><span data-stu-id="d396e-118">How to: Convert a byte Array to an int</span></span>](../types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="d396e-119">Postupy: Převést řetězec na číslo</span><span class="sxs-lookup"><span data-stu-id="d396e-119">How to: Convert a String to a Number</span></span>](../types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="d396e-120">Postupy: Převod mezi hexadecimálními řetězci a číselnými typy</span><span class="sxs-lookup"><span data-stu-id="d396e-120">How to: Convert Between Hexadecimal Strings and Numeric Types</span></span>](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="d396e-121">Analýza číselných řetězců</span><span class="sxs-lookup"><span data-stu-id="d396e-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="d396e-122">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="d396e-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)

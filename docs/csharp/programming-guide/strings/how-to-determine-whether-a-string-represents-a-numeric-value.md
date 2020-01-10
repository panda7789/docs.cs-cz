---
title: Jak zjistit, jestli řetězec představuje číselnou hodnotu – C# Průvodce programováním
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: bd89024a0a9bd62927d2d5e0eda248b57bb7d21d
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711919"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="c5bfe-102">Jak zjistit, zda řetězec představuje číselnou hodnotu (C# Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="c5bfe-102">How to determine whether a string represents a numeric value (C# Programming Guide)</span></span>
<span data-ttu-id="c5bfe-103">Chcete-li určit, zda je řetězec platnou reprezentací zadaného číselného typu, použijte metodu static `TryParse`, která je implementována všemi primitivními číselnými typy a také podle typů, jako je <xref:System.DateTime> a <xref:System.Net.IPAddress>.</span><span class="sxs-lookup"><span data-stu-id="c5bfe-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="c5bfe-104">Následující příklad ukazuje, jak určit, zda je "108" platný [int](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="c5bfe-104">The following example shows how to determine whether "108" is a valid [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
```csharp  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="c5bfe-105">Pokud řetězec obsahuje nenumerické znaky nebo číselná hodnota je příliš velká nebo příliš malá pro konkrétní typ, který jste zadali, `TryParse` vrátí hodnotu false a nastaví výstupní parametr na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="c5bfe-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="c5bfe-106">V opačném případě vrátí hodnotu true a nastaví výstupní parametr na číselnou hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="c5bfe-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5bfe-107">Řetězec může obsahovat pouze číselné znaky a stále není platný pro typ, jehož `TryParse` metoda, kterou používáte.</span><span class="sxs-lookup"><span data-stu-id="c5bfe-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="c5bfe-108">Například "256" není platná hodnota pro `byte`, ale je platná pro `int`.</span><span class="sxs-lookup"><span data-stu-id="c5bfe-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="c5bfe-109">"98,6" není platná hodnota pro `int`, ale jedná se o platný `decimal`.</span><span class="sxs-lookup"><span data-stu-id="c5bfe-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5bfe-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="c5bfe-110">Example</span></span>  
 <span data-ttu-id="c5bfe-111">Následující příklady ukazují, jak použít `TryParse` s řetězcovými reprezentacemi `long`, `byte`a `decimal` hodnot.</span><span class="sxs-lookup"><span data-stu-id="c5bfe-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c5bfe-112">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="c5bfe-112">Robust Programming</span></span>  
 <span data-ttu-id="c5bfe-113">Primitivní číselné typy také implementují metodu `Parse` static, která vyvolá výjimku, pokud řetězec není platným číslem.</span><span class="sxs-lookup"><span data-stu-id="c5bfe-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="c5bfe-114">`TryParse` je všeobecně efektivnější, protože vrací hodnotu false pouze v případě, že je číslo neplatné.</span><span class="sxs-lookup"><span data-stu-id="c5bfe-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c5bfe-115">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c5bfe-115">.NET Framework Security</span></span>  
 <span data-ttu-id="c5bfe-116">Pro ověření vstupu uživatele z ovládacích prvků, jako jsou textová pole a pole se seznamem, vždy použijte metody `TryParse` nebo `Parse`.</span><span class="sxs-lookup"><span data-stu-id="c5bfe-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5bfe-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5bfe-117">See also</span></span>

- [<span data-ttu-id="c5bfe-118">Postup převodu pole bajtů na typ int</span><span class="sxs-lookup"><span data-stu-id="c5bfe-118">How to convert a byte array to an int</span></span>](../types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="c5bfe-119">Jak převést řetězec na číslo</span><span class="sxs-lookup"><span data-stu-id="c5bfe-119">How to convert a string to a number</span></span>](../types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="c5bfe-120">Jak převádět mezi hexadecimálními řetězci a číselnými typy</span><span class="sxs-lookup"><span data-stu-id="c5bfe-120">How to convert between hexadecimal strings and numeric types</span></span>](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="c5bfe-121">Analýza číselných řetězců</span><span class="sxs-lookup"><span data-stu-id="c5bfe-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="c5bfe-122">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="c5bfe-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)

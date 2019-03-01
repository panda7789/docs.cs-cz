---
title: 'Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu - C# Průvodce programováním'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: dcba1651c736b58b2c95bac21f086c46417629df
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980747"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="d88cd-102">Postupy: Určení, zda řetězec reprezentuje číselnou hodnotu (C# Průvodce programováním v)</span><span class="sxs-lookup"><span data-stu-id="d88cd-102">How to: Determine Whether a String Represents a Numeric Value (C# Programming Guide)</span></span>
<span data-ttu-id="d88cd-103">Chcete-li zjistit, zda je řetězec reprezentaci platná zadané číselného typu, použijte statické `TryParse` metodu, která je implementována všechny primitivní číselné typy a také typy, jako <xref:System.DateTime> a <xref:System.Net.IPAddress>.</span><span class="sxs-lookup"><span data-stu-id="d88cd-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="d88cd-104">Následující příklad ukazuje, jak zjistit, jestli "108" je platný [int](../../../csharp/language-reference/keywords/int.md).</span><span class="sxs-lookup"><span data-stu-id="d88cd-104">The following example shows how to determine whether "108" is a valid [int](../../../csharp/language-reference/keywords/int.md).</span></span>  
  
```  
int i = 0;   
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="d88cd-105">Pokud řetězec obsahuje znaky číselného typu nebo číselná hodnota je příliš velký či příliš malý pro konkrétní typ, který jste zadali, `TryParse` vrátí hodnotu false a nastaví výstupní parametr na hodnotu nula.</span><span class="sxs-lookup"><span data-stu-id="d88cd-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="d88cd-106">V opačném případě vrátí hodnotu true a nastaví výstupní parametr na číselnou hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="d88cd-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d88cd-107">Řetězec může obsahovat pouze číselné znaky a stále není možné pro daný typ platná jehož `TryParse` metodu, která používáte.</span><span class="sxs-lookup"><span data-stu-id="d88cd-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="d88cd-108">Například "256" není platná hodnota pro `byte` , ale je platný pro `int`.</span><span class="sxs-lookup"><span data-stu-id="d88cd-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="d88cd-109">"98.6" není platná hodnota pro `int` je platný, ale `decimal`.</span><span class="sxs-lookup"><span data-stu-id="d88cd-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d88cd-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="d88cd-110">Example</span></span>  
 <span data-ttu-id="d88cd-111">Následující příklady ukazují, jak používat `TryParse` s řetězcové reprezentace `long`, `byte`, a `decimal` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="d88cd-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d88cd-112">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="d88cd-112">Robust Programming</span></span>  
 <span data-ttu-id="d88cd-113">Primitivní číselné typy i implementace `Parse` statická metoda, která vyvolá výjimku, pokud řetězec není platné číslo.</span><span class="sxs-lookup"><span data-stu-id="d88cd-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="d88cd-114">`TryParse` je obecně efektivnější, protože se právě vrací hodnotu false, pokud číslo není platné.</span><span class="sxs-lookup"><span data-stu-id="d88cd-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d88cd-115">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d88cd-115">.NET Framework Security</span></span>  
 <span data-ttu-id="d88cd-116">Vždy používat `TryParse` nebo `Parse` metody k ověření uživatelského vstupu z ovládacích prvků, jako je například textová pole a pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="d88cd-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d88cd-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d88cd-117">See also</span></span>

- [<span data-ttu-id="d88cd-118">Postupy: Převedení pole bajtů na typ int</span><span class="sxs-lookup"><span data-stu-id="d88cd-118">How to: Convert a byte Array to an int</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="d88cd-119">Postupy: Převod řetězce na číslo</span><span class="sxs-lookup"><span data-stu-id="d88cd-119">How to: Convert a String to a Number</span></span>](../../../csharp/programming-guide/types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="d88cd-120">Postupy: Převod mezi hexadecimálními řetězci a číselnými typy</span><span class="sxs-lookup"><span data-stu-id="d88cd-120">How to: Convert Between Hexadecimal Strings and Numeric Types</span></span>](../../../csharp/programming-guide/types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="d88cd-121">Analýza číselných řetězců</span><span class="sxs-lookup"><span data-stu-id="d88cd-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="d88cd-122">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="d88cd-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)

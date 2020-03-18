---
title: Jak zjistit, zda řetězec představuje číselnou hodnotu - C# Programovací průvodce
ms.date: 07/20/2015
helpviewer_keywords:
- numeric strings [C#]
- validating numeric input [C#]
- strings [C#], numeric
ms.assetid: a4e84e10-ea0a-489f-a868-503dded9d85f
ms.openlocfilehash: 15a21a6298f8f0a57e0189554246202b220dd259
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157062"
---
# <a name="how-to-determine-whether-a-string-represents-a-numeric-value-c-programming-guide"></a><span data-ttu-id="c1732-102">Jak zjistit, zda řetězec představuje číselnou hodnotu (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c1732-102">How to determine whether a string represents a numeric value (C# Programming Guide)</span></span>
<span data-ttu-id="c1732-103">Chcete-li zjistit, zda je řetězec platnou reprezentací zadaného číselného typu, použijte `TryParse` statickou <xref:System.DateTime> <xref:System.Net.IPAddress>metodu, která je implementována všemi primitivními číselnými typy a také typy, jako je například a .</span><span class="sxs-lookup"><span data-stu-id="c1732-103">To determine whether a string is a valid representation of a specified numeric type, use the static `TryParse` method that is implemented by all primitive numeric types and also by types such as <xref:System.DateTime> and <xref:System.Net.IPAddress>.</span></span> <span data-ttu-id="c1732-104">Následující příklad ukazuje, jak zjistit, zda "108" je platný [int](../../language-reference/builtin-types/integral-numeric-types.md).</span><span class="sxs-lookup"><span data-stu-id="c1732-104">The following example shows how to determine whether "108" is a valid [int](../../language-reference/builtin-types/integral-numeric-types.md).</span></span>  
  
```csharp  
int i = 0;
string s = "108";  
bool result = int.TryParse(s, out i); //i now = 108  
```  
  
 <span data-ttu-id="c1732-105">Pokud řetězec obsahuje nečíselné znaky nebo číselná hodnota je příliš velká `TryParse` nebo příliš malá pro konkrétní typ, který jste zadali, vrátí hodnotu false a nastaví parametr out na nulu.</span><span class="sxs-lookup"><span data-stu-id="c1732-105">If the string contains nonnumeric characters or the numeric value is too large or too small for the particular type you have specified, `TryParse` returns false and sets the out parameter to zero.</span></span> <span data-ttu-id="c1732-106">V opačném případě vrátí hodnotu true a nastaví parametr out na číselnou hodnotu řetězce.</span><span class="sxs-lookup"><span data-stu-id="c1732-106">Otherwise, it returns true and sets the out parameter to the numeric value of the string.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c1732-107">Řetězec může obsahovat pouze číselné znaky a `TryParse` stále není platný pro typ, jehož metodu používáte.</span><span class="sxs-lookup"><span data-stu-id="c1732-107">A string may contain only numeric characters and still not be valid for the type whose `TryParse` method that you use.</span></span> <span data-ttu-id="c1732-108">Například "256" není platná hodnota `byte` pro, ale `int`je platný pro .</span><span class="sxs-lookup"><span data-stu-id="c1732-108">For example, "256" is not a valid value for `byte` but it is valid for `int`.</span></span> <span data-ttu-id="c1732-109">"98.6" není platná hodnota, `int` ale je `decimal`platná .</span><span class="sxs-lookup"><span data-stu-id="c1732-109">"98.6" is not a valid value for `int` but it is a valid `decimal`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1732-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1732-110">Example</span></span>  
 <span data-ttu-id="c1732-111">Následující příklady ukazují, `TryParse` jak se používat `long` `byte`s `decimal` řetězcovými reprezentacemi , a hodnot.</span><span class="sxs-lookup"><span data-stu-id="c1732-111">The following examples show how to use `TryParse` with string representations of `long`, `byte`, and `decimal` values.</span></span>  
  
 [!code-csharp[csProgGuideStrings#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStrings/CS/Strings.cs#14)]  
  
## <a name="robust-programming"></a><span data-ttu-id="c1732-112">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="c1732-112">Robust Programming</span></span>  
 <span data-ttu-id="c1732-113">Primitivní číselné typy `Parse` také implementovat statickou metodu, která vyvolá výjimku, pokud řetězec není platné číslo.</span><span class="sxs-lookup"><span data-stu-id="c1732-113">Primitive numeric types also implement the `Parse` static method, which throws an exception if the string is not a valid number.</span></span> <span data-ttu-id="c1732-114">`TryParse`je obecně efektivnější, protože pouze vrátí false, pokud číslo není platné.</span><span class="sxs-lookup"><span data-stu-id="c1732-114">`TryParse` is generally more efficient because it just returns false if the number is not valid.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="c1732-115">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c1732-115">.NET Framework Security</span></span>  
 <span data-ttu-id="c1732-116">Vždy použijte `TryParse` `Parse` metody or k ověření vstupu uživatele z ovládacích prvků, jako jsou textová pole a pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="c1732-116">Always use the `TryParse` or `Parse` methods to validate user input from controls such as text boxes and combo boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1732-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="c1732-117">See also</span></span>

- [<span data-ttu-id="c1732-118">Jak převést pole bajtů na celé číslo</span><span class="sxs-lookup"><span data-stu-id="c1732-118">How to convert a byte array to an int</span></span>](../types/how-to-convert-a-byte-array-to-an-int.md)
- [<span data-ttu-id="c1732-119">Jak převést řetězec na číslo</span><span class="sxs-lookup"><span data-stu-id="c1732-119">How to convert a string to a number</span></span>](../types/how-to-convert-a-string-to-a-number.md)
- [<span data-ttu-id="c1732-120">Jak převádět mezi hexadecimálními řetězci a číselnými typy</span><span class="sxs-lookup"><span data-stu-id="c1732-120">How to convert between hexadecimal strings and numeric types</span></span>](../types/how-to-convert-between-hexadecimal-strings-and-numeric-types.md)
- [<span data-ttu-id="c1732-121">Analýza číselných řetězců</span><span class="sxs-lookup"><span data-stu-id="c1732-121">Parsing Numeric Strings</span></span>](../../../standard/base-types/parsing-numeric.md)
- [<span data-ttu-id="c1732-122">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="c1732-122">Formatting Types</span></span>](../../../standard/base-types/formatting-types.md)

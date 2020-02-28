---
title: Provádění změn velikosti písmen nezávisle na jazykové verzi
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- String.ToLower method
- culture, case sensitivity
- Char.ToLower method
- case, changing in culture-insensitive strings
- Char.ToUpper method
- culture-insensitive string operations, case changes
- String.ToUpper method
- culture parameter
ms.assetid: 822d551c-c69a-4191-82f4-183d82c9179c
ms.openlocfilehash: 7b2dee03619e24c5a2845699a06e88abab0c594b
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160128"
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="0d873-102">Provádění změn velikosti písmen nezávisle na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="0d873-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="0d873-103">Metody <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>a <xref:System.Char.ToLower%2A?displayProperty=nameWithType> poskytují přetížení, která nepřijímají žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="0d873-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="0d873-104">Ve výchozím nastavení tato přetížení bez parametrů mění velikost písmen v závislosti na hodnotě <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0d873-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="0d873-105">Výsledkem je, že se rozlišují malá a velká písmena, která se mohou lišit podle jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="0d873-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="0d873-106">Chcete-li zrušit zaškrtnutí bez ohledu na to, zda mají být změny velikosti písmen závislé na jazykové verzi nebo nezávislé na jazykové verzi, měli byste použít přetížení těchto metod, které vyžadují explicitní určení `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="0d873-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="0d873-107">Pro změny velikosti písmen závislé na jazykové verzi zadejte `CultureInfo.CurrentCulture` pro parametr `culture`.</span><span class="sxs-lookup"><span data-stu-id="0d873-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="0d873-108">U změn velikosti písmen nezávisle na jazykové verzi zadejte `CultureInfo.InvariantCulture` pro parametr `culture`.</span><span class="sxs-lookup"><span data-stu-id="0d873-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="0d873-109">Řetězce jsou často převedeny na standardní případ, aby bylo možné později povolit snadnější vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="0d873-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="0d873-110">Pokud jsou řetězce použity tímto způsobem, je vhodné zadat `CultureInfo.InvariantCulture` pro parametr `culture`, protože hodnota <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> může být možné měnit mezi časem změny případu a časem, kdy k vyhledávání dojde.</span><span class="sxs-lookup"><span data-stu-id="0d873-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="0d873-111">Je-li rozhodnutí o zabezpečení založeno na operaci změny velikosti písmen, operace by měla být nezávislá na jazykové verzi, aby se zajistilo, že výsledek není ovlivněn hodnotou `CultureInfo.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="0d873-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="0d873-112">V části "porovnání řetězců, které používají aktuální jazykovou verzi" v článku [osvědčené postupy pro použití řetězců](../../../docs/standard/base-types/best-practices-strings.md) najdete příklad, který ukazuje, jak mohou operace s řetězci závislé na jazykové verzi způsobit nekonzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="0d873-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="0d873-113">Použití metod String. ToUpper a String. ToLower</span><span class="sxs-lookup"><span data-stu-id="0d873-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="0d873-114">Pro přehlednost kódu doporučujeme vždy použít přetížení `String.ToUpper` a `String.ToLower` metody, které umožňují explicitně zadat `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="0d873-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="0d873-115">Například následující kód provádí vyhledávání identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="0d873-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="0d873-116">Ve výchozím nastavení je operace `key.ToLower` citlivá na jazykovou verzi, ale toto chování není jasné z čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="0d873-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="0d873-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d873-117">Example</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
   Return internalHashtable(key.ToLower())  
End Function  
```  
  
```csharp  
static object LookupKey(string key)
{  
    return internalHashtable[key.ToLower()];  
}  
```  
  
 <span data-ttu-id="0d873-118">Pokud chcete, aby operace `key.ToLower` byla nezávislá na jazykové verzi, změňte předchozí příklad takto, aby při změně velikosti písmen explicitně používal `CultureInfo.InvariantCulture`.</span><span class="sxs-lookup"><span data-stu-id="0d873-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
```vb  
Shared Function LookupKey(key As String) As Object  
    Return internalHashtable(key.ToLower(CultureInfo.InvariantCulture))  
End Function  
```  
  
```csharp  
static object LookupKey(string key)
{  
    return internalHashtable[key.ToLower(CultureInfo.InvariantCulture)];  
}  
```  
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="0d873-119">Použití metod Char. ToUpper a Char. ToLower</span><span class="sxs-lookup"><span data-stu-id="0d873-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="0d873-120">I když metody `Char.ToUpper` a `Char.ToLower` mají stejné vlastnosti jako `String.ToUpper` a `String.ToLower` metody, jsou tu ovlivněny pouze takové jazykové verze: Turečtina (Turecko) a Ázerbájdžánština (latinka, Ázerbájdžán).</span><span class="sxs-lookup"><span data-stu-id="0d873-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="0d873-121">Toto jsou jediné dvě kultury s rozdíly v malých a velkých znacích.</span><span class="sxs-lookup"><span data-stu-id="0d873-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="0d873-122">Další podrobnosti o tomto jedinečném mapování případu naleznete v části "velikost písmen" v tématu <xref:System.String> třídy.</span><span class="sxs-lookup"><span data-stu-id="0d873-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="0d873-123">Pro přehlednost kódu a zajištění konzistentních výsledků doporučujeme vždy použít přetížení těchto metod, které vám umožní explicitně zadat `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="0d873-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d873-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d873-124">See also</span></span>

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [<span data-ttu-id="0d873-125">Provádění řetězcových operací nezávislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="0d873-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)

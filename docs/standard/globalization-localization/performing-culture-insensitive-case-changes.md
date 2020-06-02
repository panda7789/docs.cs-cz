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
ms.openlocfilehash: 6baef7b0a5bbdacd33d84df01b1aa943897a9e3d
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276813"
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="5909d-102">Provádění změn velikosti písmen nezávisle na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="5909d-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="5909d-103"><xref:System.String.ToUpper%2A?displayProperty=nameWithType>Metody, <xref:System.String.ToLower%2A?displayProperty=nameWithType> , <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> a <xref:System.Char.ToLower%2A?displayProperty=nameWithType> poskytují přetížení, které nepřijímají žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="5909d-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="5909d-104">Ve výchozím nastavení tato přetížení bez parametrů provádějí změny velikosti písmen na základě hodnoty <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5909d-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5909d-105">Výsledkem je, že se rozlišují malá a velká písmena, která se mohou lišit podle jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="5909d-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="5909d-106">Chcete-li zrušit zaškrtnutí bez ohledu na to, zda mají být změny velikosti písmen závislé na jazykové verzi nebo nezávislé na jazykové verzi, měli byste použít přetížení těchto metod, které vyžadují explicitní zadání `culture` parametru.</span><span class="sxs-lookup"><span data-stu-id="5909d-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="5909d-107">Pro změny velikosti písmen závislé na jazykové verzi zadejte `CultureInfo.CurrentCulture` `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="5909d-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="5909d-108">Pro změny velikosti písmen nezávisle na jazykové verzi zadejte `CultureInfo.InvariantCulture` `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="5909d-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="5909d-109">Řetězce jsou často převedeny na standardní případ, aby bylo možné později povolit snadnější vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="5909d-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="5909d-110">Pokud jsou řetězce použity tímto způsobem, je vhodné zadat `CultureInfo.InvariantCulture` pro `culture` parametr, protože hodnota <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> může potenciálně změnit mezi časem změny případu a časem, kdy k vyhledávání dojde.</span><span class="sxs-lookup"><span data-stu-id="5909d-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="5909d-111">Je-li rozhodnutí o zabezpečení založeno na operaci změny velikosti písmen, operace by měla být nezávislá na jazykové verzi, aby se zajistilo, že výsledek není ovlivněn hodnotou `CultureInfo.CurrentCulture` .</span><span class="sxs-lookup"><span data-stu-id="5909d-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="5909d-112">V části "porovnání řetězců, které používají aktuální jazykovou verzi" v článku [osvědčené postupy pro použití řetězců](../base-types/best-practices-strings.md) najdete příklad, který ukazuje, jak mohou operace s řetězci závislé na jazykové verzi způsobit nekonzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="5909d-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="5909d-113">Použití metod String. ToUpper a String. ToLower</span><span class="sxs-lookup"><span data-stu-id="5909d-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="5909d-114">Pro přehlednost kódu doporučujeme vždy použít přetížení `String.ToUpper` `String.ToLower` metod a, které umožňují `culture` explicitně zadat parametr.</span><span class="sxs-lookup"><span data-stu-id="5909d-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="5909d-115">Například následující kód provádí vyhledávání identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="5909d-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="5909d-116">`key.ToLower`Ve výchozím nastavení je operace závislá na jazykové verzi, ale toto chování není jasné z čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="5909d-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="5909d-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="5909d-117">Example</span></span>  
  
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
  
 <span data-ttu-id="5909d-118">Pokud chcete, aby `key.ToLower` operace byla nezávislá na jazykové verzi, měli byste změnit předchozí příklad takto, aby explicitně používal `CultureInfo.InvariantCulture` při změně případu.</span><span class="sxs-lookup"><span data-stu-id="5909d-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
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
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="5909d-119">Použití metod Char. ToUpper a Char. ToLower</span><span class="sxs-lookup"><span data-stu-id="5909d-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="5909d-120">I když `Char.ToUpper` `Char.ToLower` metody a mají stejné vlastnosti jako `String.ToUpper` `String.ToLower` metody a, jsou to ovlivněny pouze v turečtině (Turecko) a Ázerbájdžánština (latinka, Ázerbájdžán).</span><span class="sxs-lookup"><span data-stu-id="5909d-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="5909d-121">Toto jsou jediné dvě kultury s rozdíly v malých a velkých znacích.</span><span class="sxs-lookup"><span data-stu-id="5909d-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="5909d-122">Další podrobnosti o tomto jedinečném mapování případu naleznete v části "velikost písmen" v <xref:System.String> tématu třídy.</span><span class="sxs-lookup"><span data-stu-id="5909d-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="5909d-123">Pro přehlednost kódu a zajištění konzistentních výsledků doporučujeme vždy použít přetížení těchto metod, které vám umožní explicitně zadat `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="5909d-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5909d-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="5909d-124">See also</span></span>

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5909d-125">Provádění řetězcových operací nezávislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="5909d-125">Performing Culture-Insensitive String Operations</span></span>](performing-culture-insensitive-string-operations.md)

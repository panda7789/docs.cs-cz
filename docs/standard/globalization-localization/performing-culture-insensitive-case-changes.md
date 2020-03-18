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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160128"
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="5bd9b-102">Provádění změn velikosti písmen nezávisle na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="5bd9b-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="5bd9b-103">Metody <xref:System.String.ToUpper%2A?displayProperty=nameWithType> <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>a <xref:System.Char.ToLower%2A?displayProperty=nameWithType> poskytují přetížení, která nepřijímají žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="5bd9b-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="5bd9b-104">Ve výchozím nastavení tato přetížení bez parametrů provádět změny <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>případu na základě hodnoty .</span><span class="sxs-lookup"><span data-stu-id="5bd9b-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5bd9b-105">To vytváří výsledky rozlišující malá a velká písmena, které se mohou lišit podle jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="5bd9b-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="5bd9b-106">Chcete-li jasně, zda chcete, aby změny případu byly citlivé na jazykovou verzi nebo necitlivé na `culture` jazykovou verzi, měli byste použít přetížení těchto metod, které vyžadují explicitně zadat parametr.</span><span class="sxs-lookup"><span data-stu-id="5bd9b-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="5bd9b-107">Pro změny malých a `CultureInfo.CurrentCulture` velkých `culture` písmen zjitřující jazykovou verzi zadejte pro parametr.</span><span class="sxs-lookup"><span data-stu-id="5bd9b-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="5bd9b-108">Pro změny malých a `CultureInfo.InvariantCulture` velkých `culture` písmen nerozlišující jazykovou verzi zadejte pro parametr.</span><span class="sxs-lookup"><span data-stu-id="5bd9b-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="5bd9b-109">Řetězce jsou často převedeny na standardní případ, aby bylo možné později snadněji vyhledat.</span><span class="sxs-lookup"><span data-stu-id="5bd9b-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="5bd9b-110">Při použití řetězců tímto způsobem byste `CultureInfo.InvariantCulture` měli `culture` zadat parametr, <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> protože hodnota může potenciálně změnit mezi čas, kdy je změněn případ a čas, kdy dojde k vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="5bd9b-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="5bd9b-111">Pokud je rozhodnutí o zabezpečení založeno na operaci změny případu, operace by měla být necitlivá `CultureInfo.CurrentCulture`na jazykovou verzi, aby bylo zajištěno, že výsledek není ovlivněn hodnotou .</span><span class="sxs-lookup"><span data-stu-id="5bd9b-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="5bd9b-112">Naleznete v části "Porovnání řetězců, které používají aktuální jazykovou verzi" v článku [Doporučené postupy pro použití řetězce](../../../docs/standard/base-types/best-practices-strings.md) pro příklad, který ukazuje, jak mohou operace řetězce citlivé na jazykovou verzi vytvářet nekonzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="5bd9b-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="5bd9b-113">Použití metod String.ToUpper a String.ToLower</span><span class="sxs-lookup"><span data-stu-id="5bd9b-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="5bd9b-114">Pro přehlednost kódu se doporučuje vždy používat `String.ToUpper` přetížení `String.ToLower` a metody, které `culture` umožňují explicitně zadat parametr.</span><span class="sxs-lookup"><span data-stu-id="5bd9b-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="5bd9b-115">Například následující kód provádí vyhledávání identifikátorů.</span><span class="sxs-lookup"><span data-stu-id="5bd9b-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="5bd9b-116">Operace `key.ToLower` je ve výchozím nastavení citlivá na jazykovou verzi, ale toto chování není jasné ze čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="5bd9b-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="5bd9b-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="5bd9b-117">Example</span></span>  
  
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
  
 <span data-ttu-id="5bd9b-118">Pokud `key.ToLower` chcete, aby operace byla necitlivá na jazykovou verzi, měli byste `CultureInfo.InvariantCulture` změnit předchozí příklad takto explicitně použít při změně případu.</span><span class="sxs-lookup"><span data-stu-id="5bd9b-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
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
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="5bd9b-119">Použití Char.ToUpper a Char.ToLower metody</span><span class="sxs-lookup"><span data-stu-id="5bd9b-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="5bd9b-120">Ačkoli `Char.ToUpper` metody `Char.ToLower` a mají stejné `String.ToUpper` vlastnosti jako metody a, `String.ToLower` jediné kultury, které jsou ovlivněny, jsou turečtina (Turecko) a ázerbájdžánština (latinka, Ázerbájdžán).</span><span class="sxs-lookup"><span data-stu-id="5bd9b-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="5bd9b-121">Jedná se o pouze dvě jazykové verze s rozdíly v tělese s jedním znakem.</span><span class="sxs-lookup"><span data-stu-id="5bd9b-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="5bd9b-122">Další podrobnosti o tomto jedinečném mapování případů naleznete <xref:System.String> v části "Velká písmena" v tématu třídy.</span><span class="sxs-lookup"><span data-stu-id="5bd9b-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="5bd9b-123">Pro srozumitelnost kódu a zajistit konzistentní výsledky, je doporučeno vždy používat přetížení těchto metod, které umožňují explicitně zadat `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="5bd9b-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bd9b-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="5bd9b-124">See also</span></span>

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5bd9b-125">Provádění řetězcových operací nezávislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="5bd9b-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)

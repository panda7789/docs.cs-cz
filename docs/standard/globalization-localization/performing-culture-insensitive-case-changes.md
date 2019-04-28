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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 04601ac0e6b1bc3289be36ce3e1a144ce57ccefb
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61683038"
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="d2428-102">Provádění změn velikosti písmen nezávisle na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="d2428-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="d2428-103"><xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, A <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metody poskytují přetížení, která nepřijímá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="d2428-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="d2428-104">Ve výchozím nastavení, tato přetížení bez parametrů, provést změny velikosti písmen podle hodnoty <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="d2428-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="d2428-105">To vytváří malá a velká písmena výsledky, které se můžou lišit podle jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="d2428-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="d2428-106">Aby bylo jasné, zda chcete, aby změny velikosti písmen zohledňující jazykovou verzi nebo nezávislých na jazykové verzi, by měla použít přetížení z těchto metod, které vyžadují, abyste s ohledem `culture` parametru.</span><span class="sxs-lookup"><span data-stu-id="d2428-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="d2428-107">Změny velikosti písmen zohledňující jazykovou verzi, zadejte `CultureInfo.CurrentCulture` pro `culture` parametru.</span><span class="sxs-lookup"><span data-stu-id="d2428-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="d2428-108">Změny velikosti písmen nezávislých na jazykové verzi, zadejte `CultureInfo.InvariantCulture` pro `culture` parametru.</span><span class="sxs-lookup"><span data-stu-id="d2428-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="d2428-109">Řetězce jsou často, převedeny na standardní případ umožňující snadnější vyhledávání později.</span><span class="sxs-lookup"><span data-stu-id="d2428-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="d2428-110">Použity tímto způsobem, je třeba zadat `CultureInfo.InvariantCulture` pro `culture` parametr, protože hodnota <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> by mohl změnit mezi časem, která se změnila tak a době vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="d2428-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="d2428-111">Pokud je rozhodnutí o zabezpečení je založená na operaci změny velikosti písmen, operace by měla být nezávislá na jazykové verzi k zajištění, že výsledek není ovlivněn hodnotou z `CultureInfo.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="d2428-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="d2428-112">Najdete v části "Řetězec porovnání, které používají aktuální jazykovou verzi" [osvědčené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md) najdete příklad, který ukazuje, jak operace s řetězci jazykovou verzi může způsobovat nekonzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="d2428-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="d2428-113">Pomocí String.ToUpper a String.ToLower – metody</span><span class="sxs-lookup"><span data-stu-id="d2428-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="d2428-114">Přehlednosti kódu doporučujeme použít vždy přetížení `String.ToUpper` a `String.ToLower` metody, které vám umožňují určit `culture` parametr explicitně.</span><span class="sxs-lookup"><span data-stu-id="d2428-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="d2428-115">Například následující kód provede vyhledání identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="d2428-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="d2428-116">`key.ToLower` Operace zohledňující jazykovou verzi ve výchozím nastavení, ale toto chování není jasné z čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="d2428-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="d2428-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2428-117">Example</span></span>  
  
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
  
 <span data-ttu-id="d2428-118">Pokud chcete, aby `key.ToLower` operace být nezávislá na jazykové verzi, měli byste změnit předchozí příklad následujícím způsobem, aby explicitně `CultureInfo.InvariantCulture` při změně velikosti písma.</span><span class="sxs-lookup"><span data-stu-id="d2428-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
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
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="d2428-119">Char.ToUpper – a Char.ToLower – metody</span><span class="sxs-lookup"><span data-stu-id="d2428-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="d2428-120">I když `Char.ToUpper` a `Char.ToLower` metody mají stejné vlastnosti jako `String.ToUpper` a `String.ToLower` turečtina (Turecko) a Ázerbájdžánština (latinka, Ázerbájdžán) jsou metody, pouze jazykové verze, které tím ovlivníte.</span><span class="sxs-lookup"><span data-stu-id="d2428-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="d2428-121">Jedná se o pouze dvě jazykových verzích s jedním znakem malých a velkých písmen rozdíly.</span><span class="sxs-lookup"><span data-stu-id="d2428-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="d2428-122">Další informace o tomto jedinečný mapování velikosti písmen, naleznete v části "Malá a velká písmena" v <xref:System.String> třídě.</span><span class="sxs-lookup"><span data-stu-id="d2428-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="d2428-123">Pro přehlednost kódu a dosahovat konzistentních výsledků, doporučujeme vždy použijte přetížení těchto metod, které umožňuje explicitně určit `culture` parametru.</span><span class="sxs-lookup"><span data-stu-id="d2428-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2428-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2428-124">See also</span></span>

- <xref:System.String.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.String.ToLower%2A?displayProperty=nameWithType>
- <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>
- <xref:System.Char.ToLower%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d2428-125">Provádění řetězcových operací nezávislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="d2428-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)

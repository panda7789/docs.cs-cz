---
title: "Provádění změn velikosti písmen nezávisle na jazykové verzi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "18"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e65eb85e1355d3aa98e04e7bd73f0194243dcdb1
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="performing-culture-insensitive-case-changes"></a><span data-ttu-id="32d61-102">Provádění změn velikosti písmen nezávisle na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="32d61-102">Performing Culture-Insensitive Case Changes</span></span>
<span data-ttu-id="32d61-103"><xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, A <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metody poskytují přetížení, které nepřijímá žádné parametry.</span><span class="sxs-lookup"><span data-stu-id="32d61-103">The <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods provide overloads that do not accept any parameters.</span></span> <span data-ttu-id="32d61-104">Ve výchozím nastavení, tato přetížení bez parametrů provádí změny velikosti písmen na základě hodnoty z <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="32d61-104">By default, these overloads without parameters perform case changes based on the value of the <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="32d61-105">To vytváří malá a velká písmena výsledky, které se mohou lišit podle jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="32d61-105">This produces case-sensitive results that can vary by culture.</span></span> <span data-ttu-id="32d61-106">Aby bylo jasné, zda chcete změny velikosti písmen zohledňující jazykovou verzi, nebo na jazykové verzi, by měl použít přetížení těchto metod, které vyžadují, abyste explicitně zadáte `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="32d61-106">To make it clear whether you want case changes to be culture-sensitive or culture-insensitive, you should use the overloads of these methods that require you to explicitly specify a `culture` parameter.</span></span> <span data-ttu-id="32d61-107">Změny velikosti písmen zohledňující jazykovou verzi, zadejte `CultureInfo.CurrentCulture` pro `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="32d61-107">For culture-sensitive case changes, specify `CultureInfo.CurrentCulture` for the `culture` parameter.</span></span> <span data-ttu-id="32d61-108">Nezávislé na jazykových změny velikosti písmen, zadejte `CultureInfo.InvariantCulture` pro `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="32d61-108">For culture-insensitive case changes, specify `CultureInfo.InvariantCulture` for the `culture` parameter.</span></span>  
  
 <span data-ttu-id="32d61-109">Často řetězce jsou převedeny na standardní případ povolit jednodušší vyhledávání později.</span><span class="sxs-lookup"><span data-stu-id="32d61-109">Often, strings are converted to a standard case to enable easier lookup later.</span></span> <span data-ttu-id="32d61-110">Pokud řetězce používají tímto způsobem, musíte zadat `CultureInfo.InvariantCulture` pro `culture` parametr, protože hodnota <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> by mohl změnit mezi časem, která tento případ se změnila a čas, který k vyhledávání.</span><span class="sxs-lookup"><span data-stu-id="32d61-110">When strings are used in this way, you should specify `CultureInfo.InvariantCulture` for the `culture` parameter, because the value of <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> can potentially change between the time that the case is changed and the time that the lookup occurs.</span></span>  
  
 <span data-ttu-id="32d61-111">Pokud rozhodnutí zabezpečení je založená na operaci případu změnit, operace by měla být nezávislé na jazykových zajistit, že výsledek není ovlivněn hodnotu `CultureInfo.CurrentCulture`.</span><span class="sxs-lookup"><span data-stu-id="32d61-111">If a security decision is based on a case change operation, the operation should be culture-insensitive to ensure that the result is not affected by the value of `CultureInfo.CurrentCulture`.</span></span> <span data-ttu-id="32d61-112">Najdete v části "Řetězec porovnání, použijte aktuální jazykovou verzi" [osvědčené postupy pro používání řetězců](../../../docs/standard/base-types/best-practices-strings.md) článek pro příklad, který ukazuje, jak operace s řetězci jazykovou verzi může způsobit nekonzistentní výsledky.</span><span class="sxs-lookup"><span data-stu-id="32d61-112">See the "String Comparisons that Use the Current Culture" section of the [Best Practices for Using Strings](../../../docs/standard/base-types/best-practices-strings.md) article for an example that demonstrates how culture-sensitive string operations can produce inconsistent results.</span></span>  
  
## <a name="using-the-stringtoupper-and-stringtolower-methods"></a><span data-ttu-id="32d61-113">Pomocí metod String.ToUpper and String.ToLower</span><span class="sxs-lookup"><span data-stu-id="32d61-113">Using the String.ToUpper and String.ToLower Methods</span></span>  
 <span data-ttu-id="32d61-114">Pro přehlednost kódu, se doporučuje použít vždy přetížení `String.ToUpper` a `String.ToLower` metody, které umožňují určit `culture` parametr explicitně.</span><span class="sxs-lookup"><span data-stu-id="32d61-114">For code clarity, it is recommended that you always use overloads of the `String.ToUpper` and `String.ToLower` methods that allow you to specify a `culture` parameter explicitly.</span></span> <span data-ttu-id="32d61-115">Například následující kód provede vyhledání identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="32d61-115">For example, the following code performs an identifier lookup.</span></span> <span data-ttu-id="32d61-116">`key.ToLower` Operace zohledňující jazykovou verzi ve výchozím nastavení, ale toto chování není jasné z čtení kódu.</span><span class="sxs-lookup"><span data-stu-id="32d61-116">The `key.ToLower` operation is culture-sensitive by default, but this behavior is not clear from reading the code.</span></span>  
  
### <a name="example"></a><span data-ttu-id="32d61-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="32d61-117">Example</span></span>  
  
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
  
 <span data-ttu-id="32d61-118">Pokud chcete `key.ToLower` operace, jazykové verzi, měli byste změnit v předchozím příkladu následujícím způsobem, aby explicitně použít `CultureInfo.InvariantCulture` při změně velikosti písma.</span><span class="sxs-lookup"><span data-stu-id="32d61-118">If you want the `key.ToLower` operation to be culture-insensitive, you should change the preceding example as follows to explicitly use the `CultureInfo.InvariantCulture` when changing the case.</span></span>  
  
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
  
## <a name="using-the-chartoupper-and-chartolower-methods"></a><span data-ttu-id="32d61-119">Pomocí Char.ToUpper a Char.ToLower – metody</span><span class="sxs-lookup"><span data-stu-id="32d61-119">Using the Char.ToUpper and Char.ToLower Methods</span></span>  
 <span data-ttu-id="32d61-120">I když `Char.ToUpper` a `Char.ToLower` metody mají stejné vlastnosti jako `String.ToUpper` a `String.ToLower` metody, pouze jazykové verze, které se vztahuje jsou Turečtina (Turecko) a Ázerbájdžánština (latinka, Ázerbájdžán).</span><span class="sxs-lookup"><span data-stu-id="32d61-120">Although the `Char.ToUpper` and `Char.ToLower` methods have the same characteristics as the `String.ToUpper` and `String.ToLower` methods, the only cultures that are affected are Turkish (Turkey) and Azerbaijani (Latin, Azerbaijan).</span></span> <span data-ttu-id="32d61-121">Toto jsou pouze dvě jazykové verze s rozdíly délce jednoho znaku velká a malá písmena.</span><span class="sxs-lookup"><span data-stu-id="32d61-121">These are the only two cultures with single-character casing differences.</span></span> <span data-ttu-id="32d61-122">Další podrobnosti o tomto jedinečný případu mapování, najdete v části "Malá a velká písmena" v <xref:System.String> třída tématu.</span><span class="sxs-lookup"><span data-stu-id="32d61-122">For more details about this unique case mapping, see the "Casing" section in the <xref:System.String> class topic.</span></span> <span data-ttu-id="32d61-123">Pro přehlednost kódu a dosahovat konzistentních výsledků, doporučujeme vždy použijte přetížení těchto metod, které vám umožní explicitně zadáte `culture` parametr.</span><span class="sxs-lookup"><span data-stu-id="32d61-123">For code clarity and to ensure consistent results, it is recommended that you always use the overloads of these methods that allow you to explicitly specify a `culture` parameter.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d61-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="32d61-124">See Also</span></span>  
 <xref:System.String.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.String.ToLower%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>  
 <xref:System.Char.ToLower%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="32d61-125">Provádění řetězcových operací nezávislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="32d61-125">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)

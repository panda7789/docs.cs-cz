---
title: "Manipulace s řetězci v .NET Frameworku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- strings [.NET Framework], manipulating
- manipulating strings
ms.assetid: d4568ff3-9f83-4549-acd8-47aec2194ac0
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: b1db77672928ebf4a03b69b4bef1af80f04124b5
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="manipulating-strings-in-net"></a><span data-ttu-id="bd92f-102">Manipulace s řetězci v .NET</span><span class="sxs-lookup"><span data-stu-id="bd92f-102">Manipulating Strings in .NET</span></span>
<span data-ttu-id="bd92f-103">Rozhraní .NET poskytuje rozsáhlou sadu rutin, které umožňují efektivně vytvářet, porovnat a upravovat řetězce a také rychle analyzovat velké objemy dat pro vyhledávání, odeberte a nahraďte textové vzory a text.</span><span class="sxs-lookup"><span data-stu-id="bd92f-103">.NET provides an extensive set of routines that enable you to efficiently create, compare, and modify strings as well as rapidly parse large amounts of text and data to search for, remove, and replace text patterns.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="bd92f-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="bd92f-104">In This Section</span></span>  
 [<span data-ttu-id="bd92f-105">Doporučené postupy pro používání řetězců</span><span class="sxs-lookup"><span data-stu-id="bd92f-105">Best Practices for Using Strings</span></span>](../../../docs/standard/base-types/best-practices-strings.md)  
 <span data-ttu-id="bd92f-106">Prozkoumá řazení řetězců, porovnání a metody velká a malá písmena v rozhraní .NET a poskytuje doporučení pro výběr metody zpracování řetězců.</span><span class="sxs-lookup"><span data-stu-id="bd92f-106">Examines string-sorting, comparison, and casing methods in .NET, and provides recommendations for selecting a string-handling method .</span></span>  
  
 [<span data-ttu-id="bd92f-107">Regulární výrazy rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="bd92f-107">.NET Regular Expressions</span></span>](../../../docs/standard/base-types/regular-expressions.md)  
 <span data-ttu-id="bd92f-108">Poskytuje podrobné informace o regulárních výrazech .NET, včetně jazykové elementy, chování regulárních výrazů a příkladů.</span><span class="sxs-lookup"><span data-stu-id="bd92f-108">Provides detailed information about .NET regular expressions, including language elements, regular expression behavior, and examples.</span></span>  
  
 [<span data-ttu-id="bd92f-109">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="bd92f-109">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)  
 <span data-ttu-id="bd92f-110">Popisuje operace s řetězci poskytované <xref:System.String?displayProperty=nameWithType> a <xref:System.Text.StringBuilder?displayProperty=nameWithType> třídy, včetně vytváření nových řetězců z pole bajtů, porovnání hodnot řetězců a úpravy existujících řetězců.</span><span class="sxs-lookup"><span data-stu-id="bd92f-110">Describes string operations provided by the <xref:System.String?displayProperty=nameWithType> and <xref:System.Text.StringBuilder?displayProperty=nameWithType> classes, including creating new strings from arrays of bytes, comparing string values, and modifying existing strings.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="bd92f-111">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="bd92f-111">Related Sections</span></span>  
 [<span data-ttu-id="bd92f-112">Převod typů v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="bd92f-112">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)  
 <span data-ttu-id="bd92f-113">Vysvětluje techniky a pravidla pro převod typů pomocí rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="bd92f-113">Explains the techniques and rules used to convert types using .NET.</span></span>  
  
 [<span data-ttu-id="bd92f-114">Typy formátování</span><span class="sxs-lookup"><span data-stu-id="bd92f-114">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)  
 <span data-ttu-id="bd92f-115">Poskytuje postupy pro použití knihovny základní třídu pro implementaci formátování, způsob formátování číselnými typy, způsob formátování řetězce typy a formátování pro konkrétní jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="bd92f-115">Provides how to use the base class library to implement formatting, how to format numeric types, how to format string types, and how to format for a specific culture.</span></span>  
  
 [<span data-ttu-id="bd92f-116">Analýza řetězců</span><span class="sxs-lookup"><span data-stu-id="bd92f-116">Parsing Strings</span></span>](../../../docs/standard/base-types/parsing-strings.md)  
 <span data-ttu-id="bd92f-117">Popisuje, jak inicializovat objekty s hodnotami popsanými řetězcové vyjádření těchto objektů.</span><span class="sxs-lookup"><span data-stu-id="bd92f-117">Describes how to initialize objects to the values described by string representations of those objects.</span></span> <span data-ttu-id="bd92f-118">Analýza je inverzní operace formátování.</span><span class="sxs-lookup"><span data-stu-id="bd92f-118">Parsing is the inverse operation of formatting.</span></span>

---
title: Vyplňování řetězců v .NET
description: Naučte se, jak odblokovat řetězce v .NET. Použijte metody String. PadLeft a String. PadRight pro přidání počátečních nebo koncových znaků k dosažení zadané celkové délky.
ms.date: 03/15/2018
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strings [.NET Framework], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
ms.openlocfilehash: 5bf7023a3429e932a44ad0a0bd3409012f77cbf9
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594527"
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="9e96e-104">Vyplňování řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="9e96e-104">Padding Strings in .NET</span></span>

<span data-ttu-id="9e96e-105">Použijte jednu z následujících <xref:System.String> metod pro vytvoření nového řetězce, který se skládá z původního řetězce, který je doplněn počátečními nebo koncovými znaky na určenou celkovou délku.</span><span class="sxs-lookup"><span data-stu-id="9e96e-105">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="9e96e-106">Znak odsazení může být mezerou nebo zadaným znakem.</span><span class="sxs-lookup"><span data-stu-id="9e96e-106">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="9e96e-107">Výsledný řetězec je pravděpodobně zarovnán vpravo nebo vlevo.</span><span class="sxs-lookup"><span data-stu-id="9e96e-107">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="9e96e-108">Pokud je délka původního řetězce již rovna nebo větší než požadovaná celková délka, metody odsazení vrátí původní řetězec beze změny; Další informace naleznete v oddílech **vrátí** v částech dvou přetížení <xref:System.String.PadLeft%2A?displayProperty=nameWithType> <xref:System.String.PadRight%2A?displayProperty=nameWithType> metod a.</span><span class="sxs-lookup"><span data-stu-id="9e96e-108">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="9e96e-109">Název metody</span><span class="sxs-lookup"><span data-stu-id="9e96e-109">Method name</span></span>|<span data-ttu-id="9e96e-110">Použití</span><span class="sxs-lookup"><span data-stu-id="9e96e-110">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="9e96e-111">Vyplní řetězec úvodními znaky o zadanou celkovou délku.</span><span class="sxs-lookup"><span data-stu-id="9e96e-111">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="9e96e-112">Vyplní řetězec koncovými znaky o zadanou celkovou délku.</span><span class="sxs-lookup"><span data-stu-id="9e96e-112">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="9e96e-113">PadLeft</span><span class="sxs-lookup"><span data-stu-id="9e96e-113">PadLeft</span></span>  
 <span data-ttu-id="9e96e-114"><xref:System.String.PadLeft%2A?displayProperty=nameWithType>Metoda vytvoří nový řetězec zřetězením dostatečného znaku přední plochy do původního řetězce, aby bylo možné dosáhnout zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="9e96e-114">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="9e96e-115"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType>Metoda používá prázdné znaky jako ohraničující znak a <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> Metoda umožňuje zadat vlastní ohraničující znak.</span><span class="sxs-lookup"><span data-stu-id="9e96e-115">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="9e96e-116">Následující příklad kódu používá <xref:System.String.PadLeft%2A> metodu k vytvoření nového řetězce, který je dvacet znaků dlouhé.</span><span class="sxs-lookup"><span data-stu-id="9e96e-116">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="9e96e-117">Příklad zobrazí " `--------Hello World!` " do konzoly.</span><span class="sxs-lookup"><span data-stu-id="9e96e-117">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="9e96e-118">PadRight</span><span class="sxs-lookup"><span data-stu-id="9e96e-118">PadRight</span></span>  
 <span data-ttu-id="9e96e-119"><xref:System.String.PadRight%2A?displayProperty=nameWithType>Metoda vytvoří nový řetězec zřetězením dostatek koncových znaků do původního řetězce pro dosažení zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="9e96e-119">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="9e96e-120"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType>Metoda používá prázdné znaky jako ohraničující znak a <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> Metoda umožňuje zadat vlastní ohraničující znak.</span><span class="sxs-lookup"><span data-stu-id="9e96e-120">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="9e96e-121">Následující příklad kódu používá <xref:System.String.PadRight%2A> metodu k vytvoření nového řetězce, který je dvacet znaků dlouhé.</span><span class="sxs-lookup"><span data-stu-id="9e96e-121">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="9e96e-122">Příklad zobrazí " `Hello World!--------` " do konzoly.</span><span class="sxs-lookup"><span data-stu-id="9e96e-122">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="9e96e-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="9e96e-123">See also</span></span>

- [<span data-ttu-id="9e96e-124">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="9e96e-124">Basic String Operations</span></span>](basic-string-operations.md)

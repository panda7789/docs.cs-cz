---
title: "Doplňování řetězců v .NET"
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
- cpp
helpviewer_keywords:
- strings [.NET Framework], padding
- white space
- PadRight method
- PadLeft method
- padding strings
ms.assetid: 84a9f142-3244-4c90-ba02-21af9bbaff71
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 29cd40645cf06ac9babb4738259938a3da04a155
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="97f11-102">Doplňování řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="97f11-102">Padding Strings in .NET</span></span>
<span data-ttu-id="97f11-103">Použijte jednu z následujících <xref:System.String> metody pro vytvoření nového řetězce, který se skládá z původního řetězce, který doplněno počáteční nebo koncové znaky zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="97f11-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="97f11-104">Znak odsazení může být mezery nebo je zadaný znak a proto se zobrazí se vpravo zarovnaný nebo zarovnaný doleva.</span><span class="sxs-lookup"><span data-stu-id="97f11-104">The padding character can be spaces or a specified character, and consequently appears to be either right-aligned or left-aligned.</span></span>  
  
|<span data-ttu-id="97f11-105">Název metody</span><span class="sxs-lookup"><span data-stu-id="97f11-105">Method name</span></span>|<span data-ttu-id="97f11-106">Použití</span><span class="sxs-lookup"><span data-stu-id="97f11-106">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="97f11-107">Ohraničí řetězec počátečními znaky na zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="97f11-107">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="97f11-108">Ohraničí řetězec koncové znaky k zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="97f11-108">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="97f11-109">padLeft</span><span class="sxs-lookup"><span data-stu-id="97f11-109">PadLeft</span></span>  
 <span data-ttu-id="97f11-110"><xref:System.String.PadLeft%2A?displayProperty=nameWithType> Metoda vytvoří nový řetězec zřetězením dostatek úvodní znaků na původní řetězec k dosažení zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="97f11-110">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="97f11-111"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> Metoda používá prázdné znaky jako znak odsazení a <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metoda umožňuje zadat vlastní znak odsazení.</span><span class="sxs-lookup"><span data-stu-id="97f11-111">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="97f11-112">Následující příklad kódu používá <xref:System.String.PadLeft%2A> metodu pro vytvoření nového řetězce, který je 20 znaků.</span><span class="sxs-lookup"><span data-stu-id="97f11-112">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="97f11-113">V příkladu se zobrazí "`--------Hello World!`" ke konzole.</span><span class="sxs-lookup"><span data-stu-id="97f11-113">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="97f11-114">PadRight –</span><span class="sxs-lookup"><span data-stu-id="97f11-114">PadRight</span></span>  
 <span data-ttu-id="97f11-115"><xref:System.String.PadRight%2A?displayProperty=nameWithType> Metoda vytvoří nový řetězec zřetězením dostatek koncových znaků pro původního řetězce pro dosažení zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="97f11-115">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="97f11-116"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> Metoda používá prázdné znaky jako znak odsazení a <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metoda umožňuje zadat vlastní znak odsazení.</span><span class="sxs-lookup"><span data-stu-id="97f11-116">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="97f11-117">Následující příklad kódu používá <xref:System.String.PadRight%2A> metodu pro vytvoření nového řetězce, který je 20 znaků.</span><span class="sxs-lookup"><span data-stu-id="97f11-117">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="97f11-118">V příkladu se zobrazí "`Hello World!--------`" ke konzole.</span><span class="sxs-lookup"><span data-stu-id="97f11-118">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="97f11-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="97f11-119">See Also</span></span>  
 [<span data-ttu-id="97f11-120">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="97f11-120">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)

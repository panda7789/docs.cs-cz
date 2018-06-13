---
title: Doplňování řetězců v .NET
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f8b71908d817625ca38f3b53a10fc20e9103ee15
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568079"
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="0d7a5-102">Doplňování řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="0d7a5-102">Padding Strings in .NET</span></span>

<span data-ttu-id="0d7a5-103">Použijte jednu z následujících <xref:System.String> metody pro vytvoření nového řetězce, který se skládá z původního řetězce, který doplněno počáteční nebo koncové znaky zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="0d7a5-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="0d7a5-104">Znak odsazení může být mezery nebo je zadaný znak.</span><span class="sxs-lookup"><span data-stu-id="0d7a5-104">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="0d7a5-105">Výsledný řetězec pravděpodobně zarovnaný doprava nebo zarovnaný doleva.</span><span class="sxs-lookup"><span data-stu-id="0d7a5-105">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="0d7a5-106">Pokud délka původního řetězce je již roven nebo větší než požadované celková délka, metody odsazení vrátí původní řetězec beze změny; Další informace najdete v tématu **vrátí** části dvě přetížení <xref:System.String.PadLeft%2A?displayProperty=nameWithType> a <xref:System.String.PadRight%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="0d7a5-106">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="0d7a5-107">Název metody</span><span class="sxs-lookup"><span data-stu-id="0d7a5-107">Method name</span></span>|<span data-ttu-id="0d7a5-108">Použití</span><span class="sxs-lookup"><span data-stu-id="0d7a5-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="0d7a5-109">Ohraničí řetězec počátečními znaky na zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="0d7a5-109">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="0d7a5-110">Ohraničí řetězec koncové znaky k zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="0d7a5-110">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="0d7a5-111">padLeft</span><span class="sxs-lookup"><span data-stu-id="0d7a5-111">PadLeft</span></span>  
 <span data-ttu-id="0d7a5-112"><xref:System.String.PadLeft%2A?displayProperty=nameWithType> Metoda vytvoří nový řetězec zřetězením dostatek úvodní znaků na původní řetězec k dosažení zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="0d7a5-112">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="0d7a5-113"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> Metoda používá prázdné znaky jako znak odsazení a <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metoda umožňuje zadat vlastní znak odsazení.</span><span class="sxs-lookup"><span data-stu-id="0d7a5-113">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="0d7a5-114">Následující příklad kódu používá <xref:System.String.PadLeft%2A> metodu pro vytvoření nového řetězce, který je 20 znaků.</span><span class="sxs-lookup"><span data-stu-id="0d7a5-114">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="0d7a5-115">V příkladu se zobrazí "`--------Hello World!`" ke konzole.</span><span class="sxs-lookup"><span data-stu-id="0d7a5-115">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="0d7a5-116">PadRight –</span><span class="sxs-lookup"><span data-stu-id="0d7a5-116">PadRight</span></span>  
 <span data-ttu-id="0d7a5-117"><xref:System.String.PadRight%2A?displayProperty=nameWithType> Metoda vytvoří nový řetězec zřetězením dostatek koncových znaků pro původního řetězce pro dosažení zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="0d7a5-117">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="0d7a5-118"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> Metoda používá prázdné znaky jako znak odsazení a <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metoda umožňuje zadat vlastní znak odsazení.</span><span class="sxs-lookup"><span data-stu-id="0d7a5-118">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="0d7a5-119">Následující příklad kódu používá <xref:System.String.PadRight%2A> metodu pro vytvoření nového řetězce, který je 20 znaků.</span><span class="sxs-lookup"><span data-stu-id="0d7a5-119">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="0d7a5-120">V příkladu se zobrazí "`Hello World!--------`" ke konzole.</span><span class="sxs-lookup"><span data-stu-id="0d7a5-120">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="0d7a5-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d7a5-121">See Also</span></span>  
 [<span data-ttu-id="0d7a5-122">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="0d7a5-122">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)

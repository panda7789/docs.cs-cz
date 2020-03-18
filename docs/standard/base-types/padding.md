---
title: Odsazení řetězců v rozhraní .NET
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
ms.openlocfilehash: 2cf114296005456f354d286aa2804fa8a95160dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73127629"
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="d5a58-102">Odsazení řetězců v rozhraní .NET</span><span class="sxs-lookup"><span data-stu-id="d5a58-102">Padding Strings in .NET</span></span>

<span data-ttu-id="d5a58-103">Pomocí jedné z <xref:System.String> následujících metod vytvořte nový řetězec, který se skládá z původního řetězce, který je doplněn úvodními nebo koncovými znaky na zadanou celkovou délku.</span><span class="sxs-lookup"><span data-stu-id="d5a58-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="d5a58-104">Znak odsazení může být mezera nebo zadaný znak.</span><span class="sxs-lookup"><span data-stu-id="d5a58-104">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="d5a58-105">Výsledný řetězec se zdá být buď zarovnaný doprava nebo doleva.</span><span class="sxs-lookup"><span data-stu-id="d5a58-105">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="d5a58-106">Pokud je délka původního řetězce již rovna nebo větší než požadovaná celková délka, metody odsazení vrátí původní řetězec beze změny; další informace naleznete v části **Vrátí** dvě přetížení <xref:System.String.PadLeft%2A?displayProperty=nameWithType> <xref:System.String.PadRight%2A?displayProperty=nameWithType> metody a.</span><span class="sxs-lookup"><span data-stu-id="d5a58-106">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="d5a58-107">Název metody</span><span class="sxs-lookup"><span data-stu-id="d5a58-107">Method name</span></span>|<span data-ttu-id="d5a58-108">Použití</span><span class="sxs-lookup"><span data-stu-id="d5a58-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="d5a58-109">Vykázne řetězec s úvodními znaky na zadanou celkovou délku.</span><span class="sxs-lookup"><span data-stu-id="d5a58-109">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="d5a58-110">Vykácí řetězec s koncovými znaky na zadanou celkovou délku.</span><span class="sxs-lookup"><span data-stu-id="d5a58-110">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="d5a58-111">PadLeft</span><span class="sxs-lookup"><span data-stu-id="d5a58-111">PadLeft</span></span>  
 <span data-ttu-id="d5a58-112">Metoda <xref:System.String.PadLeft%2A?displayProperty=nameWithType> vytvoří nový řetězec zřetězením dostatečného počtu znaků úvodní podložky do původního řetězce, aby bylo dosaženo zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="d5a58-112">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="d5a58-113">Metoda <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> používá prázdné místo jako znak <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> odsazení a metoda umožňuje zadat vlastní znak odsazení.</span><span class="sxs-lookup"><span data-stu-id="d5a58-113">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="d5a58-114">Následující příklad kódu <xref:System.String.PadLeft%2A> používá metodu k vytvoření nového řetězce, který je dlouhý dvacet znaků.</span><span class="sxs-lookup"><span data-stu-id="d5a58-114">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="d5a58-115">V příkladu`--------Hello World!`se zobrazí " " " do konzoly.</span><span class="sxs-lookup"><span data-stu-id="d5a58-115">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="d5a58-116">PadRight</span><span class="sxs-lookup"><span data-stu-id="d5a58-116">PadRight</span></span>  
 <span data-ttu-id="d5a58-117">Metoda <xref:System.String.PadRight%2A?displayProperty=nameWithType> vytvoří nový řetězec zřetězením dostatečného počtu znaků koncové podložky na původní řetězec, aby bylo dosaženo zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="d5a58-117">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="d5a58-118">Metoda <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> používá prázdné místo jako znak <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> odsazení a metoda umožňuje zadat vlastní znak odsazení.</span><span class="sxs-lookup"><span data-stu-id="d5a58-118">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="d5a58-119">Následující příklad kódu <xref:System.String.PadRight%2A> používá metodu k vytvoření nového řetězce, který je dlouhý dvacet znaků.</span><span class="sxs-lookup"><span data-stu-id="d5a58-119">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="d5a58-120">V příkladu`Hello World!--------`se zobrazí " " " do konzoly.</span><span class="sxs-lookup"><span data-stu-id="d5a58-120">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="d5a58-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5a58-121">See also</span></span>

- [<span data-ttu-id="d5a58-122">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="d5a58-122">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)

---
title: Vyplňování řetězců v .NET
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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127629"
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="b89a4-102">Vyplňování řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="b89a4-102">Padding Strings in .NET</span></span>

<span data-ttu-id="b89a4-103">Použijte jednu z následujících metod <xref:System.String> k vytvoření nového řetězce, který se skládá z původního řetězce, který je doplněn počátečními nebo koncovými znaky na určenou celkovou délku.</span><span class="sxs-lookup"><span data-stu-id="b89a4-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="b89a4-104">Znak odsazení může být mezerou nebo zadaným znakem.</span><span class="sxs-lookup"><span data-stu-id="b89a4-104">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="b89a4-105">Výsledný řetězec je pravděpodobně zarovnán vpravo nebo vlevo.</span><span class="sxs-lookup"><span data-stu-id="b89a4-105">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="b89a4-106">Pokud je délka původního řetězce již rovna nebo větší než požadovaná celková délka, metody odsazení vrátí původní řetězec beze změny; Další informace naleznete v oddílech **vrátí** v částech dvou přetížení <xref:System.String.PadLeft%2A?displayProperty=nameWithType> a <xref:System.String.PadRight%2A?displayProperty=nameWithType> metod.</span><span class="sxs-lookup"><span data-stu-id="b89a4-106">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="b89a4-107">Název metody</span><span class="sxs-lookup"><span data-stu-id="b89a4-107">Method name</span></span>|<span data-ttu-id="b89a4-108">Použití</span><span class="sxs-lookup"><span data-stu-id="b89a4-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="b89a4-109">Vyplní řetězec úvodními znaky o zadanou celkovou délku.</span><span class="sxs-lookup"><span data-stu-id="b89a4-109">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="b89a4-110">Vyplní řetězec koncovými znaky o zadanou celkovou délku.</span><span class="sxs-lookup"><span data-stu-id="b89a4-110">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="b89a4-111">PadLeft</span><span class="sxs-lookup"><span data-stu-id="b89a4-111">PadLeft</span></span>  
 <span data-ttu-id="b89a4-112">Metoda <xref:System.String.PadLeft%2A?displayProperty=nameWithType> vytvoří nový řetězec zřetězením dostatečného vodicího znaku k původnímu řetězci, abyste dosáhli zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="b89a4-112">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="b89a4-113">Metoda <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> používá prázdné znaky jako ohraničující znak a metoda <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> umožňuje zadat vlastní ohraničující znak.</span><span class="sxs-lookup"><span data-stu-id="b89a4-113">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="b89a4-114">Následující příklad kódu používá metodu <xref:System.String.PadLeft%2A> k vytvoření nového řetězce, který je dvacet znaků dlouhé.</span><span class="sxs-lookup"><span data-stu-id="b89a4-114">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="b89a4-115">V příkladu se zobrazí zpráva "`--------Hello World!`" do konzoly.</span><span class="sxs-lookup"><span data-stu-id="b89a4-115">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="b89a4-116">PadRight</span><span class="sxs-lookup"><span data-stu-id="b89a4-116">PadRight</span></span>  
 <span data-ttu-id="b89a4-117">Metoda <xref:System.String.PadRight%2A?displayProperty=nameWithType> vytvoří nový řetězec zřetězením dostatek koncových znaků do původního řetězce, aby bylo možné dosáhnout zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="b89a4-117">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="b89a4-118">Metoda <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> používá prázdné znaky jako ohraničující znak a metoda <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> umožňuje zadat vlastní ohraničující znak.</span><span class="sxs-lookup"><span data-stu-id="b89a4-118">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="b89a4-119">Následující příklad kódu používá metodu <xref:System.String.PadRight%2A> k vytvoření nového řetězce, který je dvacet znaků dlouhé.</span><span class="sxs-lookup"><span data-stu-id="b89a4-119">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="b89a4-120">V příkladu se zobrazí zpráva "`Hello World!--------`" do konzoly.</span><span class="sxs-lookup"><span data-stu-id="b89a4-120">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="b89a4-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b89a4-121">See also</span></span>

- [<span data-ttu-id="b89a4-122">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="b89a4-122">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)

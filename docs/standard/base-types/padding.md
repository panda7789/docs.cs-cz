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
ms.openlocfilehash: 83d4b348c4de537d9a71363d34898a50a6a74cb3
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84290393"
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="fbc74-102">Vyplňování řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="fbc74-102">Padding Strings in .NET</span></span>

<span data-ttu-id="fbc74-103">Použijte jednu z následujících <xref:System.String> metod pro vytvoření nového řetězce, který se skládá z původního řetězce, který je doplněn počátečními nebo koncovými znaky na určenou celkovou délku.</span><span class="sxs-lookup"><span data-stu-id="fbc74-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="fbc74-104">Znak odsazení může být mezerou nebo zadaným znakem.</span><span class="sxs-lookup"><span data-stu-id="fbc74-104">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="fbc74-105">Výsledný řetězec je pravděpodobně zarovnán vpravo nebo vlevo.</span><span class="sxs-lookup"><span data-stu-id="fbc74-105">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="fbc74-106">Pokud je délka původního řetězce již rovna nebo větší než požadovaná celková délka, metody odsazení vrátí původní řetězec beze změny; Další informace naleznete v oddílech **vrátí** v částech dvou přetížení <xref:System.String.PadLeft%2A?displayProperty=nameWithType> <xref:System.String.PadRight%2A?displayProperty=nameWithType> metod a.</span><span class="sxs-lookup"><span data-stu-id="fbc74-106">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="fbc74-107">Název metody</span><span class="sxs-lookup"><span data-stu-id="fbc74-107">Method name</span></span>|<span data-ttu-id="fbc74-108">Použití</span><span class="sxs-lookup"><span data-stu-id="fbc74-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="fbc74-109">Vyplní řetězec úvodními znaky o zadanou celkovou délku.</span><span class="sxs-lookup"><span data-stu-id="fbc74-109">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="fbc74-110">Vyplní řetězec koncovými znaky o zadanou celkovou délku.</span><span class="sxs-lookup"><span data-stu-id="fbc74-110">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="fbc74-111">PadLeft</span><span class="sxs-lookup"><span data-stu-id="fbc74-111">PadLeft</span></span>  
 <span data-ttu-id="fbc74-112"><xref:System.String.PadLeft%2A?displayProperty=nameWithType>Metoda vytvoří nový řetězec zřetězením dostatečného znaku přední plochy do původního řetězce, aby bylo možné dosáhnout zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="fbc74-112">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="fbc74-113"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType>Metoda používá prázdné znaky jako ohraničující znak a <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> Metoda umožňuje zadat vlastní ohraničující znak.</span><span class="sxs-lookup"><span data-stu-id="fbc74-113">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="fbc74-114">Následující příklad kódu používá <xref:System.String.PadLeft%2A> metodu k vytvoření nového řetězce, který je dvacet znaků dlouhé.</span><span class="sxs-lookup"><span data-stu-id="fbc74-114">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="fbc74-115">Příklad zobrazí " `--------Hello World!` " do konzoly.</span><span class="sxs-lookup"><span data-stu-id="fbc74-115">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="fbc74-116">PadRight</span><span class="sxs-lookup"><span data-stu-id="fbc74-116">PadRight</span></span>  
 <span data-ttu-id="fbc74-117"><xref:System.String.PadRight%2A?displayProperty=nameWithType>Metoda vytvoří nový řetězec zřetězením dostatek koncových znaků do původního řetězce pro dosažení zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="fbc74-117">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="fbc74-118"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType>Metoda používá prázdné znaky jako ohraničující znak a <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> Metoda umožňuje zadat vlastní ohraničující znak.</span><span class="sxs-lookup"><span data-stu-id="fbc74-118">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="fbc74-119">Následující příklad kódu používá <xref:System.String.PadRight%2A> metodu k vytvoření nového řetězce, který je dvacet znaků dlouhé.</span><span class="sxs-lookup"><span data-stu-id="fbc74-119">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="fbc74-120">Příklad zobrazí " `Hello World!--------` " do konzoly.</span><span class="sxs-lookup"><span data-stu-id="fbc74-120">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="fbc74-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="fbc74-121">See also</span></span>

- [<span data-ttu-id="fbc74-122">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="fbc74-122">Basic String Operations</span></span>](basic-string-operations.md)

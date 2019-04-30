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
ms.openlocfilehash: 3f58e1c3a9e42f48ecc219a2db1649051f9ca20b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61811531"
---
# <a name="padding-strings-in-net"></a><span data-ttu-id="e85fc-102">Doplňování řetězců v .NET</span><span class="sxs-lookup"><span data-stu-id="e85fc-102">Padding Strings in .NET</span></span>

<span data-ttu-id="e85fc-103">Použijte jednu z následujících <xref:System.String> metody k vytvoření nového řetězce, který se skládá z původního řetězce, který je vyplněna úvodní a koncové znaky na zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="e85fc-103">Use one of the following <xref:System.String> methods to create a new string that consists of an original string that is padded with leading or trailing characters to a specified total length.</span></span> <span data-ttu-id="e85fc-104">Znak odsazení může být mezera nebo je zadaný znak.</span><span class="sxs-lookup"><span data-stu-id="e85fc-104">The padding character can be a space or a specified character.</span></span> <span data-ttu-id="e85fc-105">Výsledný řetězec se zdá být zarovnaný doprava nebo doleva.</span><span class="sxs-lookup"><span data-stu-id="e85fc-105">The resulting string appears to be either right-aligned or left-aligned.</span></span> <span data-ttu-id="e85fc-106">Pokud délka původního řetězce je již roven nebo větší než požadovaný celková délka, odsazení metody vrací původního řetězce beze změny; Další informace najdete v tématu **vrátí** oddíly dvě přetížení <xref:System.String.PadLeft%2A?displayProperty=nameWithType> a <xref:System.String.PadRight%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="e85fc-106">If the original string's length is already equal to or greater than the desired total length, the padding methods return the original string unchanged; for more information, see the **Returns** sections of the two overloads of the <xref:System.String.PadLeft%2A?displayProperty=nameWithType> and <xref:System.String.PadRight%2A?displayProperty=nameWithType> methods.</span></span>
  
|<span data-ttu-id="e85fc-107">Název metody</span><span class="sxs-lookup"><span data-stu-id="e85fc-107">Method name</span></span>|<span data-ttu-id="e85fc-108">Použití</span><span class="sxs-lookup"><span data-stu-id="e85fc-108">Use</span></span>|  
|-----------------|---------|  
|<xref:System.String.PadLeft%2A?displayProperty=nameWithType>|<span data-ttu-id="e85fc-109">Vyplní řetězec s počátečními znaky na zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="e85fc-109">Pads a string with leading characters to a specified total length.</span></span>|  
|<xref:System.String.PadRight%2A?displayProperty=nameWithType>|<span data-ttu-id="e85fc-110">Vyplní řetězec s koncové znaky na zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="e85fc-110">Pads a string with trailing characters to a specified total length.</span></span>|  
  
## <a name="padleft"></a><span data-ttu-id="e85fc-111">padLeft</span><span class="sxs-lookup"><span data-stu-id="e85fc-111">PadLeft</span></span>  
 <span data-ttu-id="e85fc-112"><xref:System.String.PadLeft%2A?displayProperty=nameWithType> Metoda vytvoří nový řetězec zřetězením dostatek přední znaků na původní řetězec k dosažení zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="e85fc-112">The <xref:System.String.PadLeft%2A?displayProperty=nameWithType> method creates a new string by concatenating enough leading pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="e85fc-113"><xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> Metoda používá prázdný znak jako znak odsazení a <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metoda vám umožňuje určit vlastní odsazení znaku.</span><span class="sxs-lookup"><span data-stu-id="e85fc-113">The <xref:System.String.PadLeft%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadLeft%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="e85fc-114">Následující příklad kódu používá <xref:System.String.PadLeft%2A> metodu pro vytvoření nového řetězce, který je 20 znaků.</span><span class="sxs-lookup"><span data-stu-id="e85fc-114">The following code example uses the <xref:System.String.PadLeft%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="e85fc-115">V příkladu se zobrazí "`--------Hello World!`" do konzoly.</span><span class="sxs-lookup"><span data-stu-id="e85fc-115">The example displays "`--------Hello World!`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#3)]
 [!code-csharp[Conceptual.String.BasicOps#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#3)]
 [!code-vb[Conceptual.String.BasicOps#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#3)]  
  
## <a name="padright"></a><span data-ttu-id="e85fc-116">PadRight –</span><span class="sxs-lookup"><span data-stu-id="e85fc-116">PadRight</span></span>  
 <span data-ttu-id="e85fc-117"><xref:System.String.PadRight%2A?displayProperty=nameWithType> Metoda vytvoří nový řetězec zřetězením dostatek koncových znaků na původní řetězec k dosažení zadané celkové délky.</span><span class="sxs-lookup"><span data-stu-id="e85fc-117">The <xref:System.String.PadRight%2A?displayProperty=nameWithType> method creates a new string by concatenating enough trailing pad characters to an original string to achieve a specified total length.</span></span> <span data-ttu-id="e85fc-118"><xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> Metoda používá prázdný znak jako znak odsazení a <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> metoda vám umožňuje určit vlastní odsazení znaku.</span><span class="sxs-lookup"><span data-stu-id="e85fc-118">The <xref:System.String.PadRight%28System.Int32%29?displayProperty=nameWithType> method uses white space as the padding character and the <xref:System.String.PadRight%28System.Int32%2CSystem.Char%29?displayProperty=nameWithType> method enables you to specify your own padding character.</span></span>  
  
 <span data-ttu-id="e85fc-119">Následující příklad kódu používá <xref:System.String.PadRight%2A> metodu pro vytvoření nového řetězce, který je 20 znaků.</span><span class="sxs-lookup"><span data-stu-id="e85fc-119">The following code example uses the <xref:System.String.PadRight%2A> method to create a new string that is twenty characters long.</span></span> <span data-ttu-id="e85fc-120">V příkladu se zobrazí "`Hello World!--------`" do konzoly.</span><span class="sxs-lookup"><span data-stu-id="e85fc-120">The example displays "`Hello World!--------`" to the console.</span></span>  
  
 [!code-cpp[Conceptual.String.BasicOps#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.string.basicops/cpp/padding.cpp#4)]
 [!code-csharp[Conceptual.String.BasicOps#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.string.basicops/cs/padding.cs#4)]
 [!code-vb[Conceptual.String.BasicOps#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.string.basicops/vb/padding.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e85fc-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e85fc-121">See also</span></span>

- [<span data-ttu-id="e85fc-122">Základní operace s řetězci</span><span class="sxs-lookup"><span data-stu-id="e85fc-122">Basic String Operations</span></span>](../../../docs/standard/base-types/basic-string-operations.md)

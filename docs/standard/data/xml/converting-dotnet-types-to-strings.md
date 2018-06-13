---
title: Převádění typů rozhraní .NET Framework na řetězce
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1e9b22a4bc876e9b02ec0da0439682082d2d706
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33568768"
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="365f0-102">Převádění typů rozhraní .NET Framework na řetězce</span><span class="sxs-lookup"><span data-stu-id="365f0-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="365f0-103">Pokud chcete převést typ rozhraní .NET Framework na řetězec, použijte **ToString** metoda.</span><span class="sxs-lookup"><span data-stu-id="365f0-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="365f0-104">**ToString** metoda vrátí řetězcovou reprezentaci předaný typ.</span><span class="sxs-lookup"><span data-stu-id="365f0-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="365f0-105">Následující tabulka uvádí typy rozhraní .NET Framework, které vrací řetězec ve formátu, který se mapuje na specifikacích schématu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="365f0-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="365f0-106">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="365f0-106">.NET Framework type</span></span>|<span data-ttu-id="365f0-107">Typ řetězec vrácený</span><span class="sxs-lookup"><span data-stu-id="365f0-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="365f0-108">Boolean</span><span class="sxs-lookup"><span data-stu-id="365f0-108">Boolean</span></span>|<span data-ttu-id="365f0-109">"PRAVDA", "Nepravda"</span><span class="sxs-lookup"><span data-stu-id="365f0-109">"true", "false"</span></span>|  
|<span data-ttu-id="365f0-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="365f0-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="365f0-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="365f0-111">"INF"</span></span>|  
|<span data-ttu-id="365f0-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="365f0-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="365f0-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="365f0-113">"-INF"</span></span>|  
|<span data-ttu-id="365f0-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="365f0-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="365f0-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="365f0-115">"INF"</span></span>|  
|<span data-ttu-id="365f0-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="365f0-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="365f0-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="365f0-117">"-INF"</span></span>|  
|<span data-ttu-id="365f0-118">DateTime</span><span class="sxs-lookup"><span data-stu-id="365f0-118">DateTime</span></span>|<span data-ttu-id="365f0-119">Formát je rrrr-MM-ddTHH:mm:sszzzzzz a jeho podmnožin.</span><span class="sxs-lookup"><span data-stu-id="365f0-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="365f0-120">Časový interval</span><span class="sxs-lookup"><span data-stu-id="365f0-120">Timespan</span></span>|<span data-ttu-id="365f0-121">Formát je PnYnMnTnHnMnS, například `P2Y10M15DT10H30M20S` je trvání 10hours 2 roky, 10 měsíců, 15 dní, 30 minut a 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="365f0-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="365f0-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="365f0-122">See Also</span></span>  
 [<span data-ttu-id="365f0-123">Převod datových typů XML</span><span class="sxs-lookup"><span data-stu-id="365f0-123">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)  
 [<span data-ttu-id="365f0-124">Převádění řetězců na datové typy rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="365f0-124">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)

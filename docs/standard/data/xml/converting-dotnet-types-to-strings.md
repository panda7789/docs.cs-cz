---
title: Převádění typů rozhraní .NET Framework na řetězce
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98ebc9248b0585295adf12e04dece0fef654c2e8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953982"
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="8de35-102">Převádění typů rozhraní .NET Framework na řetězce</span><span class="sxs-lookup"><span data-stu-id="8de35-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="8de35-103">Pokud chcete převést na řetězec, typ rozhraní .NET Framework, použijte **ToString** metody.</span><span class="sxs-lookup"><span data-stu-id="8de35-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="8de35-104">**ToString** metoda vrátí řetězcovou reprezentaci objektu předaný typ.</span><span class="sxs-lookup"><span data-stu-id="8de35-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="8de35-105">Následující tabulka uvádí typy rozhraní .NET Framework, které vrací řetězec ve formátu, který se mapuje na specifikace schématu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="8de35-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="8de35-106">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8de35-106">.NET Framework type</span></span>|<span data-ttu-id="8de35-107">Vrátí typ String</span><span class="sxs-lookup"><span data-stu-id="8de35-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="8de35-108">Boolean</span><span class="sxs-lookup"><span data-stu-id="8de35-108">Boolean</span></span>|<span data-ttu-id="8de35-109">"PRAVDA", "Nepravda"</span><span class="sxs-lookup"><span data-stu-id="8de35-109">"true", "false"</span></span>|  
|<span data-ttu-id="8de35-110">Single.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="8de35-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="8de35-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="8de35-111">"INF"</span></span>|  
|<span data-ttu-id="8de35-112">Single.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="8de35-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="8de35-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="8de35-113">"-INF"</span></span>|  
|<span data-ttu-id="8de35-114">Double.PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="8de35-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="8de35-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="8de35-115">"INF"</span></span>|  
|<span data-ttu-id="8de35-116">Double.NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="8de35-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="8de35-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="8de35-117">"-INF"</span></span>|  
|<span data-ttu-id="8de35-118">DateTime</span><span class="sxs-lookup"><span data-stu-id="8de35-118">DateTime</span></span>|<span data-ttu-id="8de35-119">Formát je rrrr-MM-ddTHH:mm:sszzzzzz a její podskupiny.</span><span class="sxs-lookup"><span data-stu-id="8de35-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="8de35-120">Časový interval</span><span class="sxs-lookup"><span data-stu-id="8de35-120">Timespan</span></span>|<span data-ttu-id="8de35-121">Formát je PnYnMnTnHnMnS, například `P2Y10M15DT10H30M20S` je po dobu 2 let, 10 měsíců, 15 dnů, 10hours 30 minut a 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="8de35-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8de35-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8de35-122">See also</span></span>

- [<span data-ttu-id="8de35-123">Převod datových typů XML</span><span class="sxs-lookup"><span data-stu-id="8de35-123">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [<span data-ttu-id="8de35-124">Převádění řetězců na datové typy rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="8de35-124">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)

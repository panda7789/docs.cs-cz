---
title: Převádění typů rozhraní .NET Framework na řetězce
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: a63e0175f6660967eb4aa678c6731d353e44e2d5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711074"
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="2f8f5-102">Převádění typů rozhraní .NET Framework na řetězce</span><span class="sxs-lookup"><span data-stu-id="2f8f5-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="2f8f5-103">Pokud chcete převést .NET Framework typ na řetězec, použijte metodu **ToString** .</span><span class="sxs-lookup"><span data-stu-id="2f8f5-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="2f8f5-104">Metoda **ToString** vrátí řetězcovou reprezentaci typu předaného.</span><span class="sxs-lookup"><span data-stu-id="2f8f5-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="2f8f5-105">V následující tabulce jsou uvedeny typy .NET Framework, které vracejí řetězec ve formátu, který se mapuje na specifikace schématu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="2f8f5-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="2f8f5-106">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2f8f5-106">.NET Framework type</span></span>|<span data-ttu-id="2f8f5-107">Vrácený typ řetězce</span><span class="sxs-lookup"><span data-stu-id="2f8f5-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="2f8f5-108">Boolean</span><span class="sxs-lookup"><span data-stu-id="2f8f5-108">Boolean</span></span>|<span data-ttu-id="2f8f5-109">"pravda", "NEPRAVDA"</span><span class="sxs-lookup"><span data-stu-id="2f8f5-109">"true", "false"</span></span>|  
|<span data-ttu-id="2f8f5-110">Single. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="2f8f5-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="2f8f5-111">"INF"</span><span class="sxs-lookup"><span data-stu-id="2f8f5-111">"INF"</span></span>|  
|<span data-ttu-id="2f8f5-112">Single. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="2f8f5-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="2f8f5-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="2f8f5-113">"-INF"</span></span>|  
|<span data-ttu-id="2f8f5-114">Double. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="2f8f5-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="2f8f5-115">"INF"</span><span class="sxs-lookup"><span data-stu-id="2f8f5-115">"INF"</span></span>|  
|<span data-ttu-id="2f8f5-116">Double. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="2f8f5-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="2f8f5-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="2f8f5-117">"-INF"</span></span>|  
|<span data-ttu-id="2f8f5-118">Datum a čas</span><span class="sxs-lookup"><span data-stu-id="2f8f5-118">DateTime</span></span>|<span data-ttu-id="2f8f5-119">Formát je RRRR-MM-ddTHH: mm: sszzzzzz a jeho podmnožiny.</span><span class="sxs-lookup"><span data-stu-id="2f8f5-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="2f8f5-120">Časový rozsah</span><span class="sxs-lookup"><span data-stu-id="2f8f5-120">Timespan</span></span>|<span data-ttu-id="2f8f5-121">Formát je PnYnMnTnHnMnS, například `P2Y10M15DT10H30M20S` má délku 2 roky, 10 měsíců, 15 dní, 10hours, 30 minut a 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="2f8f5-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2f8f5-122">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2f8f5-122">See also</span></span>

- [<span data-ttu-id="2f8f5-123">Převod datových typů XML</span><span class="sxs-lookup"><span data-stu-id="2f8f5-123">Conversion of XML Data Types</span></span>](../../../../docs/standard/data/xml/conversion-of-xml-data-types.md)
- [<span data-ttu-id="2f8f5-124">Převádění řetězců na datové typy rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2f8f5-124">Converting Strings to .NET Framework Data Types</span></span>](../../../../docs/standard/data/xml/converting-strings-to-dotnet-data-types.md)

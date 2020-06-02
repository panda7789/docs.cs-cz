---
title: Převádění typů rozhraní .NET Framework na řetězce
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: dc2e2b65-f623-4dc3-938b-d2a054d6832c
ms.openlocfilehash: d232fb0e3ea4cf3189294d6e6f43ae9270417407
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287815"
---
# <a name="converting-net-framework-types-to-strings"></a><span data-ttu-id="5f691-102">Převádění typů rozhraní .NET Framework na řetězce</span><span class="sxs-lookup"><span data-stu-id="5f691-102">Converting .NET Framework Types to Strings</span></span>
<span data-ttu-id="5f691-103">Pokud chcete převést .NET Framework typ na řetězec, použijte metodu **ToString** .</span><span class="sxs-lookup"><span data-stu-id="5f691-103">If you want to convert a .NET Framework type to a string, use the **ToString** method.</span></span> <span data-ttu-id="5f691-104">Metoda **ToString** vrátí řetězcovou reprezentaci typu předaného.</span><span class="sxs-lookup"><span data-stu-id="5f691-104">The **ToString** method returns a string representation of the type passed in.</span></span> <span data-ttu-id="5f691-105">V následující tabulce jsou uvedeny typy .NET Framework, které vracejí řetězec ve formátu, který se mapuje na specifikace schématu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="5f691-105">The following table lists the .NET Framework types that return a string in a format that maps to the XML Schema (XSD) specifications.</span></span>  
  
|<span data-ttu-id="5f691-106">Typ rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5f691-106">.NET Framework type</span></span>|<span data-ttu-id="5f691-107">Vrácený typ řetězce</span><span class="sxs-lookup"><span data-stu-id="5f691-107">String type returned</span></span>|  
|-------------------------|--------------------------|  
|<span data-ttu-id="5f691-108">Logická hodnota</span><span class="sxs-lookup"><span data-stu-id="5f691-108">Boolean</span></span>|<span data-ttu-id="5f691-109">"pravda", "NEPRAVDA"</span><span class="sxs-lookup"><span data-stu-id="5f691-109">"true", "false"</span></span>|  
|<span data-ttu-id="5f691-110">Single. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="5f691-110">Single.PositiveInfinity</span></span>|<span data-ttu-id="5f691-111">SOUBORŮ</span><span class="sxs-lookup"><span data-stu-id="5f691-111">"INF"</span></span>|  
|<span data-ttu-id="5f691-112">Single. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="5f691-112">Single.NegativeInfinity</span></span>|<span data-ttu-id="5f691-113">"-INF"</span><span class="sxs-lookup"><span data-stu-id="5f691-113">"-INF"</span></span>|  
|<span data-ttu-id="5f691-114">Double. PositiveInfinity</span><span class="sxs-lookup"><span data-stu-id="5f691-114">Double.PositiveInfinity</span></span>|<span data-ttu-id="5f691-115">SOUBORŮ</span><span class="sxs-lookup"><span data-stu-id="5f691-115">"INF"</span></span>|  
|<span data-ttu-id="5f691-116">Double. NegativeInfinity</span><span class="sxs-lookup"><span data-stu-id="5f691-116">Double.NegativeInfinity</span></span>|<span data-ttu-id="5f691-117">"-INF"</span><span class="sxs-lookup"><span data-stu-id="5f691-117">"-INF"</span></span>|  
|<span data-ttu-id="5f691-118">DateTime</span><span class="sxs-lookup"><span data-stu-id="5f691-118">DateTime</span></span>|<span data-ttu-id="5f691-119">Formát je RRRR-MM-ddTHH: mm: sszzzzzz a jeho podmnožiny.</span><span class="sxs-lookup"><span data-stu-id="5f691-119">Format is yyyy-MM-ddTHH:mm:sszzzzzz and its subsets.</span></span>|  
|<span data-ttu-id="5f691-120">Časový interval</span><span class="sxs-lookup"><span data-stu-id="5f691-120">Timespan</span></span>|<span data-ttu-id="5f691-121">Formát je PnYnMnTnHnMnS, například `P2Y10M15DT10H30M20S` je doba 2 roky, 10 měsíců, 15 dní, 10hours, 30 minut a 20 sekund.</span><span class="sxs-lookup"><span data-stu-id="5f691-121">Format is PnYnMnTnHnMnS, for example, `P2Y10M15DT10H30M20S` is a duration of 2 years, 10 months, 15 days, 10hours, 30 minutes and 20 seconds.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5f691-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f691-122">See also</span></span>

- [<span data-ttu-id="5f691-123">Převod datových typů XML</span><span class="sxs-lookup"><span data-stu-id="5f691-123">Conversion of XML Data Types</span></span>](conversion-of-xml-data-types.md)
- [<span data-ttu-id="5f691-124">Převádění řetězců na datové typy rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="5f691-124">Converting Strings to .NET Framework Data Types</span></span>](converting-strings-to-dotnet-data-types.md)

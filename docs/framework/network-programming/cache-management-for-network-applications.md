---
title: Správa mezipaměti pro síťové aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 7e131963999db3e3d5e0e6f3fa110da36e6452a1
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048878"
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="186ce-102">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="186ce-102">Cache Management for Network Applications</span></span>
<span data-ttu-id="186ce-103">Toto téma a související dílčí témata popisují ukládání do mezipaměti pro <xref:System.Net.WebClient>prostředky získané pomocí tříd, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>a. <xref:System.Net.FtpWebRequest></span><span class="sxs-lookup"><span data-stu-id="186ce-103">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="186ce-104">Mezipaměť poskytuje dočasné úložiště prostředků, které požadovala aplikace.</span><span class="sxs-lookup"><span data-stu-id="186ce-104">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="186ce-105">Pokud aplikace požádá o stejný prostředek více než jednou, může být prostředek vrácen z mezipaměti, takže nebude mít na serveru nárok na jejich opětovné vyžádání.</span><span class="sxs-lookup"><span data-stu-id="186ce-105">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="186ce-106">Ukládání do mezipaměti může zlepšit výkon aplikace tím, že zkracuje dobu potřebnou k získání požadovaného prostředku.</span><span class="sxs-lookup"><span data-stu-id="186ce-106">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="186ce-107">Ukládání do mezipaměti může také snížit zatížení sítě tím, že se sníží počet cest k serveru.</span><span class="sxs-lookup"><span data-stu-id="186ce-107">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="186ce-108">I když ukládání do mezipaměti zvyšuje výkon, zvyšuje riziko, že prostředek vrácený do aplikace je zastaralý, což znamená, že se neshoduje s prostředkem, který by byl odeslán serverem, pokud se ukládání do mezipaměti nepoužívalo.</span><span class="sxs-lookup"><span data-stu-id="186ce-108">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="186ce-109">Ukládání do mezipaměti může umožňovat neoprávněným uživatelům nebo procesům číst citlivá data.</span><span class="sxs-lookup"><span data-stu-id="186ce-109">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="186ce-110">Ověřená odpověď, která je uložena v mezipaměti, může být načtena z mezipaměti bez další autorizace.</span><span class="sxs-lookup"><span data-stu-id="186ce-110">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="186ce-111">Pokud je povoleno ukládání do mezipaměti, <xref:System.Net.WebRequest.CachePolicy%2A> přejděte <xref:System.Net.Cache.RequestCacheLevel.BypassCache> na <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> nebo a zakažte ukládání do mezipaměti pro tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="186ce-111">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="186ce-112">Kvůli problémům se zabezpečením není ukládání do **mezipaměti doporučováno** pro scénáře střední vrstvy.</span><span class="sxs-lookup"><span data-stu-id="186ce-112">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="186ce-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="186ce-113">In This Section</span></span>  
 [<span data-ttu-id="186ce-114">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="186ce-114">Cache Policy</span></span>](cache-policy.md)  
 <span data-ttu-id="186ce-115">Vysvětluje, co je zásada mezipaměti a jak ji definovat.</span><span class="sxs-lookup"><span data-stu-id="186ce-115">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="186ce-116">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="186ce-116">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)  
 <span data-ttu-id="186ce-117">Definuje každý typ zásad mezipaměti na základě umístění dostupných pro prostředky http a HTTPS (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="186ce-117">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="186ce-118">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="186ce-118">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)  
 <span data-ttu-id="186ce-119">V této části najdete popis kritérií, která lze použít k přizpůsobení zásad mezipaměti založeného na čase.</span><span class="sxs-lookup"><span data-stu-id="186ce-119">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="186ce-120">Konfigurace mezipaměti v síťových aplikacích</span><span class="sxs-lookup"><span data-stu-id="186ce-120">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)  
 <span data-ttu-id="186ce-121">Popisuje způsob, jak programově vytvářet zásady mezipaměti a požadavky, které používají ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="186ce-121">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="186ce-122">Reference</span><span class="sxs-lookup"><span data-stu-id="186ce-122">Reference</span></span>  
 <xref:System.Net.Cache>  
 <span data-ttu-id="186ce-123">Definuje typy a výčty používané k definování zásad mezipaměti pro prostředky získané pomocí <xref:System.Net.WebRequest>tříd, <xref:System.Net.HttpWebRequest>a <xref:System.Net.FtpWebRequest> .</span><span class="sxs-lookup"><span data-stu-id="186ce-123">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>

---
title: Správa mezipaměti pro síťové aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 7e131963999db3e3d5e0e6f3fa110da36e6452a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71048878"
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="a4480-102">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="a4480-102">Cache Management for Network Applications</span></span>
<span data-ttu-id="a4480-103">Toto téma a související dílčí témata popisují ukládání <xref:System.Net.WebClient> <xref:System.Net.WebRequest>prostředků <xref:System.Net.HttpWebRequest>získaných pomocí tříd , , a <xref:System.Net.FtpWebRequest> tříd.</span><span class="sxs-lookup"><span data-stu-id="a4480-103">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="a4480-104">Mezipaměť poskytuje dočasné úložiště prostředků, které byly požadovány aplikací.</span><span class="sxs-lookup"><span data-stu-id="a4480-104">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="a4480-105">Pokud aplikace požaduje stejný prostředek více než jednou, prostředek může být vrácena z mezipaměti, aby se zabránilo režii opětovného vyžádání ze serveru.</span><span class="sxs-lookup"><span data-stu-id="a4480-105">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="a4480-106">Ukládání do mezipaměti může zlepšit výkon aplikace zkrácením času potřebného k získání požadovaného prostředku.</span><span class="sxs-lookup"><span data-stu-id="a4480-106">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="a4480-107">Ukládání do mezipaměti může také snížit provoz v síti snížením počtu cest na server.</span><span class="sxs-lookup"><span data-stu-id="a4480-107">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="a4480-108">Při ukládání do mezipaměti zlepšuje výkon, zvyšuje riziko, že prostředek vrácený do aplikace je zastaralý, což znamená, že není totožný s prostředek, který by byly odeslány serverem, pokud ukládání do mezipaměti nebyly používány.</span><span class="sxs-lookup"><span data-stu-id="a4480-108">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="a4480-109">Ukládání do mezipaměti může umožnit neoprávněným uživatelům nebo procesům číst citlivá data.</span><span class="sxs-lookup"><span data-stu-id="a4480-109">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="a4480-110">Ověřená odpověď, která je uložena v mezipaměti, může být načtena z mezipaměti bez další autorizace.</span><span class="sxs-lookup"><span data-stu-id="a4480-110">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="a4480-111">Pokud je ukládání do mezipaměti <xref:System.Net.Cache.RequestCacheLevel.BypassCache> <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> povoleno, změňte na <xref:System.Net.WebRequest.CachePolicy%2A> nebo zakázat ukládání do mezipaměti pro tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="a4480-111">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="a4480-112">Z důvodu obav o zabezpečení ukládání do mezipaměti se **nedoporučuje** pro scénáře střední vrstvy.</span><span class="sxs-lookup"><span data-stu-id="a4480-112">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a4480-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a4480-113">In This Section</span></span>  
 [<span data-ttu-id="a4480-114">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="a4480-114">Cache Policy</span></span>](cache-policy.md)  
 <span data-ttu-id="a4480-115">Vysvětluje, co je zásada mezipaměti a jak ji definovat.</span><span class="sxs-lookup"><span data-stu-id="a4480-115">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="a4480-116">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="a4480-116">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)  
 <span data-ttu-id="a4480-117">Definuje každý typ zásad mezipaměti založených na umístění, které jsou k dispozici pro prostředky protokolu HTTP a https .)</span><span class="sxs-lookup"><span data-stu-id="a4480-117">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="a4480-118">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="a4480-118">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)  
 <span data-ttu-id="a4480-119">Popisuje kritéria, která lze použít k přizpůsobení zásad mezipaměti založené na čase.</span><span class="sxs-lookup"><span data-stu-id="a4480-119">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="a4480-120">Konfigurace ukládání do mezipaměti v síťových aplikacích</span><span class="sxs-lookup"><span data-stu-id="a4480-120">Configuring Caching in Network Applications</span></span>](configuring-caching-in-network-applications.md)  
 <span data-ttu-id="a4480-121">Popisuje, jak programově vytvořit zásady mezipaměti a požadavky, které používají ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="a4480-121">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="a4480-122">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="a4480-122">Reference</span></span>  
 <xref:System.Net.Cache>  
 <span data-ttu-id="a4480-123">Definuje typy a výčty používané k definování zásad mezipaměti <xref:System.Net.HttpWebRequest>pro <xref:System.Net.FtpWebRequest> prostředky získané pomocí <xref:System.Net.WebRequest>, a tříd.</span><span class="sxs-lookup"><span data-stu-id="a4480-123">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>

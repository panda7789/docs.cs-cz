---
title: Správa mezipaměti pro síťové aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: c2b27f3516169ee7b90eaa27fbf22ec02fb638fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391674"
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="f4a2d-102">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="f4a2d-102">Cache Management for Network Applications</span></span>
<span data-ttu-id="f4a2d-103">Toto téma a jeho souvisejících dílčí témata popisují ukládání do mezipaměti pro prostředků získaných pomocí <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, a <xref:System.Net.FtpWebRequest> třídy.</span><span class="sxs-lookup"><span data-stu-id="f4a2d-103">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="f4a2d-104">Mezipaměť poskytuje dočasné úložiště prostředků, která vyžadovala aplikace.</span><span class="sxs-lookup"><span data-stu-id="f4a2d-104">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="f4a2d-105">Pokud aplikace vyžaduje stejného zdroje více než jednou, mohou být vráceny prostředek z mezipaměti, není zpomalován režií znovu požadovat ze serveru.</span><span class="sxs-lookup"><span data-stu-id="f4a2d-105">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="f4a2d-106">Ukládání do mezipaměti můžete zlepšit výkon aplikací snížením čas potřebný k získání požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="f4a2d-106">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="f4a2d-107">Ukládání do mezipaměti může také snížit zatížení sítě snížením počtu cest k serveru.</span><span class="sxs-lookup"><span data-stu-id="f4a2d-107">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="f4a2d-108">Při ukládání do mezipaměti zvyšuje výkon, jeho hodnota se zvyšuje riziko, že prostředek vrátí do aplikace je zastaralé, což znamená, že není stejný jako prostředek, který by byly odeslány server v případě ukládání do mezipaměti nebyly používán.</span><span class="sxs-lookup"><span data-stu-id="f4a2d-108">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="f4a2d-109">Ukládání do mezipaměti může povolit neoprávněnými uživateli a procesy, které slouží ke čtení citlivá data.</span><span class="sxs-lookup"><span data-stu-id="f4a2d-109">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="f4a2d-110">Ověřená odpověď, který je uložený v mezipaměti může načíst z mezipaměti bez další autorizace.</span><span class="sxs-lookup"><span data-stu-id="f4a2d-110">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="f4a2d-111">Pokud je povoleno ukládání do mezipaměti, změňte <xref:System.Net.WebRequest.CachePolicy%2A> k <xref:System.Net.Cache.RequestCacheLevel.BypassCache> nebo <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> zakázání ukládání do mezipaměti pro tuto žádost.</span><span class="sxs-lookup"><span data-stu-id="f4a2d-111">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="f4a2d-112">Ukládání do mezipaměti je z důvodu zabezpečení se **není** doporučeno pro scénáře střední vrstvy.</span><span class="sxs-lookup"><span data-stu-id="f4a2d-112">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f4a2d-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f4a2d-113">In This Section</span></span>  
 [<span data-ttu-id="f4a2d-114">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="f4a2d-114">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 <span data-ttu-id="f4a2d-115">Vysvětluje, jaké zásady mezipaměti je a jak definovat jeden.</span><span class="sxs-lookup"><span data-stu-id="f4a2d-115">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="f4a2d-116">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="f4a2d-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 <span data-ttu-id="f4a2d-117">Definuje každý typ zásady na základě umístění mezipaměti, které jsou k dispozici pro protokol HTTP (http a https) prostředky.</span><span class="sxs-lookup"><span data-stu-id="f4a2d-117">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="f4a2d-118">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="f4a2d-118">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 <span data-ttu-id="f4a2d-119">Popisuje kritéria, která slouží k přizpůsobení zásady mezipaměti založené na čase.</span><span class="sxs-lookup"><span data-stu-id="f4a2d-119">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="f4a2d-120">Konfigurace mezipaměti v síťových aplikacích</span><span class="sxs-lookup"><span data-stu-id="f4a2d-120">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 <span data-ttu-id="f4a2d-121">Popisuje postup vytváření zásad mezipaměti a požadavky, které používají ukládání do mezipaměti prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="f4a2d-121">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f4a2d-122">Odkaz</span><span class="sxs-lookup"><span data-stu-id="f4a2d-122">Reference</span></span>  
 <xref:System.Net.Cache>  
 <span data-ttu-id="f4a2d-123">Definuje typy a výčty používaný k definování zásady mezipaměti pro prostředků získaných pomocí <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, a <xref:System.Net.FtpWebRequest> třídy.</span><span class="sxs-lookup"><span data-stu-id="f4a2d-123">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>

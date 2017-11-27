---
title: "Správa mezipaměti pro síťové aplikace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b960942d17e402b333354bbd932cf63d11b1209f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="231ea-102">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="231ea-102">Cache Management for Network Applications</span></span>
<span data-ttu-id="231ea-103">Toto téma a jeho souvisejících dílčí témata popisují ukládání do mezipaměti pro prostředků získaných pomocí <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, a <xref:System.Net.FtpWebRequest> třídy.</span><span class="sxs-lookup"><span data-stu-id="231ea-103">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="231ea-104">Mezipaměť poskytuje dočasné úložiště prostředků, která vyžadovala aplikace.</span><span class="sxs-lookup"><span data-stu-id="231ea-104">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="231ea-105">Pokud aplikace vyžaduje stejného zdroje více než jednou, mohou být vráceny prostředek z mezipaměti, není zpomalován režií znovu požadovat ze serveru.</span><span class="sxs-lookup"><span data-stu-id="231ea-105">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="231ea-106">Ukládání do mezipaměti můžete zlepšit výkon aplikací snížením čas potřebný k získání požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="231ea-106">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="231ea-107">Ukládání do mezipaměti může také snížit zatížení sítě snížením počtu cest k serveru.</span><span class="sxs-lookup"><span data-stu-id="231ea-107">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="231ea-108">Při ukládání do mezipaměti zvyšuje výkon, jeho hodnota se zvyšuje riziko, že prostředek vrátí do aplikace je zastaralé, což znamená, že není stejný jako prostředek, který by byly odeslány server v případě ukládání do mezipaměti nebyly používán.</span><span class="sxs-lookup"><span data-stu-id="231ea-108">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="231ea-109">Ukládání do mezipaměti může povolit neoprávněnými uživateli a procesy, které slouží ke čtení citlivá data.</span><span class="sxs-lookup"><span data-stu-id="231ea-109">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="231ea-110">Ověřená odpověď, který je uložený v mezipaměti může načíst z mezipaměti bez další autorizace.</span><span class="sxs-lookup"><span data-stu-id="231ea-110">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="231ea-111">Pokud je povoleno ukládání do mezipaměti, změňte <xref:System.Net.WebRequest.CachePolicy%2A> k <xref:System.Net.Cache.RequestCacheLevel.BypassCache> nebo <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> zakázání ukládání do mezipaměti pro tuto žádost.</span><span class="sxs-lookup"><span data-stu-id="231ea-111">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="231ea-112">Ukládání do mezipaměti je z důvodu zabezpečení se **není** doporučeno pro scénáře střední vrstvy.</span><span class="sxs-lookup"><span data-stu-id="231ea-112">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="231ea-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="231ea-113">In This Section</span></span>  
 [<span data-ttu-id="231ea-114">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="231ea-114">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 <span data-ttu-id="231ea-115">Vysvětluje, jaké zásady mezipaměti je a jak definovat jeden.</span><span class="sxs-lookup"><span data-stu-id="231ea-115">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="231ea-116">Na základě umístění mezipaměti zásad</span><span class="sxs-lookup"><span data-stu-id="231ea-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 <span data-ttu-id="231ea-117">Definuje každý typ zásady na základě umístění mezipaměti, které jsou k dispozici pro protokol HTTP (http a https) prostředky.</span><span class="sxs-lookup"><span data-stu-id="231ea-117">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="231ea-118">Zásady založené na čase mezipaměti</span><span class="sxs-lookup"><span data-stu-id="231ea-118">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 <span data-ttu-id="231ea-119">Popisuje kritéria, která slouží k přizpůsobení zásady mezipaměti založené na čase.</span><span class="sxs-lookup"><span data-stu-id="231ea-119">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="231ea-120">Konfigurace ukládání do mezipaměti v síťových aplikací</span><span class="sxs-lookup"><span data-stu-id="231ea-120">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 <span data-ttu-id="231ea-121">Popisuje postup vytváření zásad mezipaměti a požadavky, které používají ukládání do mezipaměti prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="231ea-121">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="231ea-122">Odkaz</span><span class="sxs-lookup"><span data-stu-id="231ea-122">Reference</span></span>  
 <xref:System.Net.Cache>  
 <span data-ttu-id="231ea-123">Definuje typy a výčty používaný k definování zásady mezipaměti pro prostředků získaných pomocí <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, a <xref:System.Net.FtpWebRequest> třídy.</span><span class="sxs-lookup"><span data-stu-id="231ea-123">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>

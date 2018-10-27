---
title: Správa mezipaměti pro síťové aplikace
ms.date: 03/30/2017
helpviewer_keywords:
- cache [.NET Framework], network applications
- network resources, caching
- Internet, caching
ms.assetid: fc258a40-f370-434f-ae09-4a8cb11ddaeb
ms.openlocfilehash: 265b4e451ebb76dbabe0d3e0df065504a3891f32
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50049123"
---
# <a name="cache-management-for-network-applications"></a><span data-ttu-id="d5f37-102">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="d5f37-102">Cache Management for Network Applications</span></span>
<span data-ttu-id="d5f37-103">Toto téma a další související části popisují, ukládání do mezipaměti pro prostředky získané s použitím <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, a <xref:System.Net.FtpWebRequest> třídy.</span><span class="sxs-lookup"><span data-stu-id="d5f37-103">This topic and its related subtopics describe caching for resources obtained using the <xref:System.Net.WebClient>, <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>  
  
 <span data-ttu-id="d5f37-104">Mezipaměť poskytuje dočasného úložiště prostředků, které bylo vyžádáno aplikací.</span><span class="sxs-lookup"><span data-stu-id="d5f37-104">A cache provides temporary storage of resources that have been requested by an application.</span></span> <span data-ttu-id="d5f37-105">Pokud aplikace požaduje více než jednou. stejný prostředek, prostředek mohou být vráceny z mezipaměti, není zpomalován režií na znovu vyžádat ze serveru.</span><span class="sxs-lookup"><span data-stu-id="d5f37-105">If an application requests the same resource more than once, the resource can be returned from the cache, avoiding the overhead of re-requesting it from the server.</span></span> <span data-ttu-id="d5f37-106">Ukládání do mezipaměti může zlepšit výkon aplikace tím, že snižuje čas potřebný k získání požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="d5f37-106">Caching can improve application performance by reducing the time required to get a requested resource.</span></span> <span data-ttu-id="d5f37-107">Ukládání do mezipaměti může také snížit síťový provoz snížením počtu zpráv se serverem.</span><span class="sxs-lookup"><span data-stu-id="d5f37-107">Caching can also decrease network traffic by reducing the number of trips to the server.</span></span> <span data-ttu-id="d5f37-108">Při ukládání do mezipaměti zvyšuje výkon, jeho hodnota se zvyšuje riziko, že prostředek vrátil do aplikace je zastaralé, což znamená, že není stejný jako prostředek, který by se odeslaly server v případě ukládání do mezipaměti nebyly používá.</span><span class="sxs-lookup"><span data-stu-id="d5f37-108">While caching improves performance, it increases the risk that the resource returned to the application is stale, meaning that it is not identical to the resource that would have been sent by the server if caching were not in use.</span></span>  
  
 <span data-ttu-id="d5f37-109">Neoprávnění uživatelé nebo procesy čtení citlivých dat můžou povolit ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d5f37-109">Caching may allow unauthorized users or processes to read sensitive data.</span></span> <span data-ttu-id="d5f37-110">Ověřená odpověď, která se uloží do mezipaměti může načíst z mezipaměti bez další oprávnění.</span><span class="sxs-lookup"><span data-stu-id="d5f37-110">An authenticated response that is cached may be retrieved from the cache without an additional authorization.</span></span> <span data-ttu-id="d5f37-111">Pokud je povoleno ukládání do mezipaměti, změňte na <xref:System.Net.WebRequest.CachePolicy%2A> k <xref:System.Net.Cache.RequestCacheLevel.BypassCache> nebo <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> zakázat ukládání do mezipaměti pro tento požadavek.</span><span class="sxs-lookup"><span data-stu-id="d5f37-111">If caching is enabled, change to <xref:System.Net.WebRequest.CachePolicy%2A> to <xref:System.Net.Cache.RequestCacheLevel.BypassCache> or <xref:System.Net.Cache.RequestCacheLevel.NoCacheNoStore> to disable caching for this request.</span></span>  
  
 <span data-ttu-id="d5f37-112">Ukládání do mezipaměti je z bezpečnostních důvodů **není** doporučuje pro scénáře střední vrstvy.</span><span class="sxs-lookup"><span data-stu-id="d5f37-112">Due to security concerns, caching is **not** recommended for middle tier scenarios.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="d5f37-113">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d5f37-113">In This Section</span></span>  
 [<span data-ttu-id="d5f37-114">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="d5f37-114">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)  
 <span data-ttu-id="d5f37-115">Vysvětluje, jaké zásady mezipaměti je a jak definovat jeden.</span><span class="sxs-lookup"><span data-stu-id="d5f37-115">Explains what a cache policy is and how to define one.</span></span>  
  
 [<span data-ttu-id="d5f37-116">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="d5f37-116">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)  
 <span data-ttu-id="d5f37-117">Definuje jednotlivé typy zásad mezipaměti na základě umístění k dispozici pro protokol HTTP (http a https) zdroje.</span><span class="sxs-lookup"><span data-stu-id="d5f37-117">Defines each type of location-based cache policy available for Hypertext Transfer Protocol (http and https) resources.</span></span>  
  
 [<span data-ttu-id="d5f37-118">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="d5f37-118">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)  
 <span data-ttu-id="d5f37-119">Popisuje kritéria, která slouží k přizpůsobení zásad mezipaměti na základě času.</span><span class="sxs-lookup"><span data-stu-id="d5f37-119">Describes the criteria that can be used to customize a time-based cache policy.</span></span>  
  
 [<span data-ttu-id="d5f37-120">Konfigurace mezipaměti v síťových aplikacích</span><span class="sxs-lookup"><span data-stu-id="d5f37-120">Configuring Caching in Network Applications</span></span>](../../../docs/framework/network-programming/configuring-caching-in-network-applications.md)  
 <span data-ttu-id="d5f37-121">Popisuje, jak prostřednictvím kódu programu vytvořit zásady mezipaměti a požadavky, které využívají ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="d5f37-121">Describes how to programmatically create cache policies and requests that use caching.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="d5f37-122">Odkaz</span><span class="sxs-lookup"><span data-stu-id="d5f37-122">Reference</span></span>  
 <xref:System.Net.Cache>  
 <span data-ttu-id="d5f37-123">Definuje typy a výčty, které slouží k definování zásad mezipaměti pro prostředky získané s použitím <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, a <xref:System.Net.FtpWebRequest> třídy.</span><span class="sxs-lookup"><span data-stu-id="d5f37-123">Defines the types and enumerations used to define cache policies for resources obtained using the <xref:System.Net.WebRequest>, <xref:System.Net.HttpWebRequest>, and <xref:System.Net.FtpWebRequest> classes.</span></span>

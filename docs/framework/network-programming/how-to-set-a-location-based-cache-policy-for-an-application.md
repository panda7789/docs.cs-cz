---
title: 'Postupy: Nastavení zásad mezipaměti na základě umístění pro aplikaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- explicitly defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
ms.openlocfilehash: 150198c2bda220e4b37981e461e19b8e4e30e483
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048125"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="9a64d-102">Postupy: Nastavení zásad mezipaměti na základě umístění pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="9a64d-102">How to: Set a Location-Based Cache Policy for an Application</span></span>
<span data-ttu-id="9a64d-103">Zásady mezipaměti na základě umístění umožňují aplikaci explicitně definovat chování ukládání do mezipaměti na základě umístění požadovaného prostředku.</span><span class="sxs-lookup"><span data-stu-id="9a64d-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="9a64d-104">Toto téma ukazuje, jak nastavit zásady mezipaměti programově.</span><span class="sxs-lookup"><span data-stu-id="9a64d-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="9a64d-105">Informace o nastavení zásad pro aplikaci pomocí konfiguračních souborů naleznete v tématu [ \<RequestCaching > element (nastavení sítě)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="9a64d-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="9a64d-106">Nastavení zásad mezipaměti na základě umístění pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="9a64d-106">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="9a64d-107">Vytvořte objekt <xref:System.Net.Cache.HttpRequestCachePolicy>nebo. <xref:System.Net.Cache.RequestCachePolicy></span><span class="sxs-lookup"><span data-stu-id="9a64d-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="9a64d-108">Nastavte objekt zásad jako výchozí pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="9a64d-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="9a64d-109">Nastavení zásad, které přebírají požadované prostředky z mezipaměti</span><span class="sxs-lookup"><span data-stu-id="9a64d-109">To set a policy that takes requested resources from a cache</span></span>  
  
- <span data-ttu-id="9a64d-110">Vytvořte zásadu, která provede požadované prostředky z mezipaměti, pokud je k dispozici, a v opačném případě odešle požadavky na server nastavením úrovně mezipaměti <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>na.</span><span class="sxs-lookup"><span data-stu-id="9a64d-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="9a64d-111">Požadavek může splnit jakákoli mezipaměť mezi klientem a serverem, včetně vzdálených mezipamětí.</span><span class="sxs-lookup"><span data-stu-id="9a64d-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
    ```csharp  
    public static void UseCacheIfAvailable()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
            (HttpRequestCacheLevel.CacheIfAvailable);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub UseCacheIfAvailable()  
        Dim policy As New HttpRequestCachePolicy _  
             (HttpRequestCacheLevel.CacheIfAvailable)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="9a64d-112">Nastavení zásad, které zabrání v poskytnutí prostředků do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="9a64d-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
- <span data-ttu-id="9a64d-113">Vytvořte zásadu, která zabrání libovolné mezipaměti v poskytnutí požadovaných prostředků nastavením úrovně mezipaměti na <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span><span class="sxs-lookup"><span data-stu-id="9a64d-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="9a64d-114">Tato úroveň zásad odstraní prostředek z místní mezipaměti, pokud je přítomen, a označuje vzdálené mezipaměti, které by měly také odebrat prostředek.</span><span class="sxs-lookup"><span data-stu-id="9a64d-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseCache()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.NoCacheNoStore);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.NoCacheNoStore)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="9a64d-115">Nastavení zásad, které vrátí požadované prostředky pouze v případě, že jsou v místní mezipaměti</span><span class="sxs-lookup"><span data-stu-id="9a64d-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
- <span data-ttu-id="9a64d-116">Vytvořte zásadu, která bude vracet požadované prostředky pouze v případě, že jsou v místní mezipaměti nastavením úrovně mezipaměti na <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span><span class="sxs-lookup"><span data-stu-id="9a64d-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="9a64d-117">Pokud požadovaný prostředek není v mezipaměti, <xref:System.Net.WebException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="9a64d-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
    ```csharp  
    public static void OnlyUseCache()  
    {  
        HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.CacheOnly);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub OnlyUseCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.CacheOnly)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="9a64d-118">Nastavení zásad, které brání místní mezipaměti v zásobování prostředků</span><span class="sxs-lookup"><span data-stu-id="9a64d-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
- <span data-ttu-id="9a64d-119">Vytvořte zásadu, která zabrání v ukládání požadovaných prostředků do místní mezipaměti nastavením úrovně mezipaměti na <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span><span class="sxs-lookup"><span data-stu-id="9a64d-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="9a64d-120">Pokud se požadovaný prostředek nachází v přechodné mezipaměti a úspěšně se znovu ověří, mezilehlá mezipaměť může dodat požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="9a64d-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
    ```csharp  
    public static void DoNotUseLocalCache()  
    {  
     HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.Refresh);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub DoNotUseLocalCache()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Refresh)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="9a64d-121">Nastavení zásad, které zabrání v ukládání požadovaných prostředků do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="9a64d-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
- <span data-ttu-id="9a64d-122">Vytvořte zásadu, která zabrání libovolné mezipaměti v poskytnutí požadovaných prostředků nastavením úrovně mezipaměti na <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span><span class="sxs-lookup"><span data-stu-id="9a64d-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="9a64d-123">Prostředek vrácený serverem může být uložený v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="9a64d-123">The resource returned by the server can be stored in the cache.</span></span>  
  
    ```csharp  
    public static void SendToServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy   
            (HttpRequestCacheLevel.Reload);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub SendToServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Reload)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="9a64d-124">Nastavení zásady, která umožní, aby jakákoli mezipaměť poskytovala požadované prostředky, pokud prostředek na serveru není novější než kopie v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="9a64d-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
- <span data-ttu-id="9a64d-125">Vytvořte zásadu, která umožňuje, aby jakákoli mezipaměť poskytovala požadované prostředky, pokud prostředek na serveru není novější než kopie uložená v mezipaměti nastavením úrovně mezipaměti na <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span><span class="sxs-lookup"><span data-stu-id="9a64d-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
    ```csharp  
    public static void CheckServer()  
    {  
    HttpRequestCachePolicy policy = new HttpRequestCachePolicy  
             (HttpRequestCacheLevel.Revalidate);  
        HttpWebRequest.DefaultCachePolicy = policy;  
    }  
    ```  
  
    ```vb  
    Public Shared Sub CheckServer()  
        Dim policy As New HttpRequestCachePolicy _  
            (HttpRequestCacheLevel.Revalidate)  
        HttpWebRequest.DefaultCachePolicy = policy  
    End Sub  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9a64d-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a64d-126">See also</span></span>

- [<span data-ttu-id="9a64d-127">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="9a64d-127">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="9a64d-128">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="9a64d-128">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="9a64d-129">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="9a64d-129">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="9a64d-130">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="9a64d-130">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="9a64d-131">\<requestCaching – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="9a64d-131">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)

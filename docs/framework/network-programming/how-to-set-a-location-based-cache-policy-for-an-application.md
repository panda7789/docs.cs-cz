---
title: 'Postupy: Nastavení zásad mezipaměti na základě místa pro aplikaci'
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
ms.openlocfilehash: 6fe569e781b005461ea41e3d6b90859666f9601a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180783"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="71f12-102">Postupy: Nastavení zásad mezipaměti na základě místa pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="71f12-102">How to: Set a Location-Based Cache Policy for an Application</span></span>
<span data-ttu-id="71f12-103">Zásady mezipaměti založené na umístění umožňují aplikaci explicitně definovat chování ukládání do mezipaměti na základě umístění požadovaného prostředku.</span><span class="sxs-lookup"><span data-stu-id="71f12-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="71f12-104">Toto téma ukazuje nastavení zásad mezipaměti programově.</span><span class="sxs-lookup"><span data-stu-id="71f12-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="71f12-105">Informace o nastavení zásad pro aplikaci používající konfigurační soubory naleznete v [ \<tématu requestCaching> Element (Network Settings).](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="71f12-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="71f12-106">Nastavení zásad mezipaměti založené na umístění pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="71f12-106">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="71f12-107">Vytvořte <xref:System.Net.Cache.RequestCachePolicy> <xref:System.Net.Cache.HttpRequestCachePolicy> nebo objekt.</span><span class="sxs-lookup"><span data-stu-id="71f12-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="71f12-108">Nastavte objekt zásad jako výchozí pro doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="71f12-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="71f12-109">Nastavení zásady, která přebírá požadované prostředky z mezipaměti</span><span class="sxs-lookup"><span data-stu-id="71f12-109">To set a policy that takes requested resources from a cache</span></span>  
  
- <span data-ttu-id="71f12-110">Vytvořte zásadu, která převezme požadované prostředky z mezipaměti, pokud je k dispozici, <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>a jinak odešle požadavky na server nastavením úrovně mezipaměti na .</span><span class="sxs-lookup"><span data-stu-id="71f12-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="71f12-111">Požadavek může splnit libovolná mezipaměť mezi klientem a serverem, včetně vzdálených mezipamětí.</span><span class="sxs-lookup"><span data-stu-id="71f12-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="71f12-112">Nastavení zásady, která brání jakékoli mezipaměti v poskytování prostředků</span><span class="sxs-lookup"><span data-stu-id="71f12-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
- <span data-ttu-id="71f12-113">Vytvořte zásadu, která zabrání jakékoli mezipaměti v poskytování <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>požadovaných prostředků nastavením úrovně mezipaměti na .</span><span class="sxs-lookup"><span data-stu-id="71f12-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="71f12-114">Tato úroveň zásad odebere prostředek z místní mezipaměti, pokud je k dispozici, a označuje vzdálené mezipaměti, že by měly také odebrat prostředek.</span><span class="sxs-lookup"><span data-stu-id="71f12-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="71f12-115">Nastavení zásady, která vrací požadované prostředky pouze v případě, že jsou v místní mezipaměti</span><span class="sxs-lookup"><span data-stu-id="71f12-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
- <span data-ttu-id="71f12-116">Vytvořte zásadu, která vrátí požadované prostředky pouze v případě, <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>že jsou v místní mezipaměti nastavením úrovně mezipaměti na .</span><span class="sxs-lookup"><span data-stu-id="71f12-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="71f12-117">Pokud požadovaný prostředek není v mezipaměti, je vyvolána <xref:System.Net.WebException> výjimka.</span><span class="sxs-lookup"><span data-stu-id="71f12-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="71f12-118">Nastavení zásady, která brání místní mezipaměti v poskytování prostředků</span><span class="sxs-lookup"><span data-stu-id="71f12-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
- <span data-ttu-id="71f12-119">Vytvořte zásadu, která zabrání místní mezipaměti v poskytování <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>požadovaných prostředků nastavením úrovně mezipaměti na .</span><span class="sxs-lookup"><span data-stu-id="71f12-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="71f12-120">Pokud je požadovaný prostředek v mezilehlé mezipaměti a je úspěšně znovu ověřen, může mezilehlá mezipaměť poskytnout požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="71f12-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="71f12-121">Nastavení zásady, která brání jakékoli mezipaměti v poskytování požadovaných prostředků</span><span class="sxs-lookup"><span data-stu-id="71f12-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
- <span data-ttu-id="71f12-122">Vytvořte zásadu, která zabrání jakékoli mezipaměti v poskytování <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>požadovaných prostředků nastavením úrovně mezipaměti na .</span><span class="sxs-lookup"><span data-stu-id="71f12-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="71f12-123">Prostředek vrácený serverem může být uložen v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="71f12-123">The resource returned by the server can be stored in the cache.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="71f12-124">Nastavení zásady, která umožňuje jakékoli mezipaměti zadávat požadované prostředky, pokud prostředek na serveru není novější než kopie uložená v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="71f12-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
- <span data-ttu-id="71f12-125">Vytvořte zásadu, která umožní jakékoli mezipaměti zadávat požadované prostředky, pokud prostředek na serveru <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>není novější než kopie uložená v mezipaměti, a to nastavením úrovně mezipaměti na .</span><span class="sxs-lookup"><span data-stu-id="71f12-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="71f12-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="71f12-126">See also</span></span>

- [<span data-ttu-id="71f12-127">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="71f12-127">Cache Management for Network Applications</span></span>](cache-management-for-network-applications.md)
- [<span data-ttu-id="71f12-128">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="71f12-128">Cache Policy</span></span>](cache-policy.md)
- [<span data-ttu-id="71f12-129">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="71f12-129">Location-Based Cache Policies</span></span>](location-based-cache-policies.md)
- [<span data-ttu-id="71f12-130">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="71f12-130">Time-Based Cache Policies</span></span>](time-based-cache-policies.md)
- [<span data-ttu-id="71f12-131">\<requestCaching> Element (Nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="71f12-131">\<requestCaching> Element (Network Settings)</span></span>](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)

---
title: 'Postupy: Nastavení zásad mezipaměti na základě umístění pro aplikaci'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- expliciting defining cache behavior
- location-based cache policies
- local cache
- request cache policies
- cache [.NET Framework], location-based policies
ms.assetid: 683bb88e-3411-4f46-9686-3411b6ba511c
ms.openlocfilehash: 06d458828c77f61e03d18f635ec00f6a7267bab8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61642474"
---
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="43a07-102">Postupy: Nastavení zásad mezipaměti na základě umístění pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="43a07-102">How to: Set a Location-Based Cache Policy for an Application</span></span>
<span data-ttu-id="43a07-103">Zásady mezipaměti na základě polohy umožnit aplikaci k explicitnímu definování chování ukládání do mezipaměti na základě umístění požadovaného prostředku.</span><span class="sxs-lookup"><span data-stu-id="43a07-103">Location-based cache policies allow an application to explicitly define caching behavior based on the location of the requested resource.</span></span> <span data-ttu-id="43a07-104">Toto téma popisuje nastavení zásad mezipaměti prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="43a07-104">This topic demonstrates setting the cache policy programmatically.</span></span> <span data-ttu-id="43a07-105">Informace o nastavení zásad pro aplikace pomocí konfiguračních souborů naleznete v tématu [ \<requestCaching – > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span><span class="sxs-lookup"><span data-stu-id="43a07-105">For information on setting the policy for an application using the configuration files, see [\<requestCaching> Element (Network Settings)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).</span></span>  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a><span data-ttu-id="43a07-106">Nastavení zásad mezipaměti na základě umístění pro aplikaci</span><span class="sxs-lookup"><span data-stu-id="43a07-106">To set a location-based cache policy for an application</span></span>  
  
1. <span data-ttu-id="43a07-107">Vytvoření <xref:System.Net.Cache.RequestCachePolicy> nebo <xref:System.Net.Cache.HttpRequestCachePolicy> objektu.</span><span class="sxs-lookup"><span data-stu-id="43a07-107">Create a <xref:System.Net.Cache.RequestCachePolicy> or <xref:System.Net.Cache.HttpRequestCachePolicy> object.</span></span>  
  
2. <span data-ttu-id="43a07-108">Nastavte jako výchozí pro doménu aplikace objektu zásad.</span><span class="sxs-lookup"><span data-stu-id="43a07-108">Set the policy object as the default for the application domain.</span></span>  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a><span data-ttu-id="43a07-109">Chcete-li nastavit zásadu, která má požadované prostředky z mezipaměti</span><span class="sxs-lookup"><span data-stu-id="43a07-109">To set a policy that takes requested resources from a cache</span></span>  
  
- <span data-ttu-id="43a07-110">Vytvořit zásadu, která přebírá požadované prostředky z mezipaměti, pokud je k dispozici a v opačném případě zasílá požadavky na server, pomocí nastavení mezipaměti na úrovni <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span><span class="sxs-lookup"><span data-stu-id="43a07-110">Create a policy that takes requested resources from a cache if available, and otherwise, sends requests to the server, by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>.</span></span> <span data-ttu-id="43a07-111">Žádost lze splnit všechny mezipaměti mezi klientem a serverem, včetně vzdáleného mezipamětí.</span><span class="sxs-lookup"><span data-stu-id="43a07-111">A request can be fulfilled by any cache between the client and server, including remote caches.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a><span data-ttu-id="43a07-112">Chcete-li nastavit zásadu, která brání všechny mezipaměti poskytující prostředky</span><span class="sxs-lookup"><span data-stu-id="43a07-112">To set a policy that prevents any cache from supplying resources</span></span>  
  
- <span data-ttu-id="43a07-113">Vytvořit zásadu, která brání poskytnutí požadovaných prostředků tak, že nastavíte mezipaměti úrovně pro všechny mezipaměti <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span><span class="sxs-lookup"><span data-stu-id="43a07-113">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>.</span></span> <span data-ttu-id="43a07-114">Tato úroveň zásad odebere prostředek z místní mezipaměti, pokud je k dispozici a tak vzdálené mezipaměti informaci, že se mělo odstranit také na prostředek.</span><span class="sxs-lookup"><span data-stu-id="43a07-114">This policy level removes the resource from the local cache if it is present and indicates to remote caches that they should also remove the resource.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a><span data-ttu-id="43a07-115">Chcete-li nastavit zásadu, která vrátí požadované prostředky pouze v případě, že jsou v místní mezipaměti</span><span class="sxs-lookup"><span data-stu-id="43a07-115">To set a policy that returns requested resources only if they are in the local cache</span></span>  
  
- <span data-ttu-id="43a07-116">Vytvořit zásadu, která vrátí požadované prostředky pouze v případě, že jsou v místní mezipaměti pomocí nastavení mezipaměti na úrovni <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span><span class="sxs-lookup"><span data-stu-id="43a07-116">Create a policy that returns requested resources only if they are in the local cache by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>.</span></span> <span data-ttu-id="43a07-117">Pokud požadovaný prostředek není v mezipaměti, <xref:System.Net.WebException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="43a07-117">If the requested resource is not in the cache, a <xref:System.Net.WebException> exception is thrown.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a><span data-ttu-id="43a07-118">Chcete-li nastavit zásadu, která brání poskytující prostředky místní mezipaměti</span><span class="sxs-lookup"><span data-stu-id="43a07-118">To set a policy that prevents the local cache from supplying resources</span></span>  
  
- <span data-ttu-id="43a07-119">Vytvořit zásadu, která brání poskytnutí požadovaných prostředků podle nastavení úrovně do mezipaměti v místní mezipaměti <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span><span class="sxs-lookup"><span data-stu-id="43a07-119">Create a policy that prevents the local cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>.</span></span> <span data-ttu-id="43a07-120">Pokud požadovaný prostředek je v zprostředkující mezipaměti a úspěšně ověřit, zprostředkující mezipaměti můžete zadat požadovaný prostředek.</span><span class="sxs-lookup"><span data-stu-id="43a07-120">If the requested resource is in an intermediate cache and is successfully revalidated, the intermediate cache can supply the requested resource.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a><span data-ttu-id="43a07-121">Chcete-li nastavit zásadu, která brání všechny mezipaměti zadáním požadované prostředky</span><span class="sxs-lookup"><span data-stu-id="43a07-121">To set a policy that prevents any cache from supplying requested resources</span></span>  
  
- <span data-ttu-id="43a07-122">Vytvořit zásadu, která brání poskytnutí požadovaných prostředků tak, že nastavíte mezipaměti úrovně pro všechny mezipaměti <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span><span class="sxs-lookup"><span data-stu-id="43a07-122">Create a policy that prevents any cache from supplying requested resources by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>.</span></span> <span data-ttu-id="43a07-123">Prostředek vrácená serverem mohou být uloženy v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="43a07-123">The resource returned by the server can be stored in the cache.</span></span>  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a><span data-ttu-id="43a07-124">Chcete-li nastavit zásadu, která umožňuje všechny mezipaměti slouží k poskytování požadované prostředky, pokud prostředek na serveru není novější než kopie v mezipaměti</span><span class="sxs-lookup"><span data-stu-id="43a07-124">To set a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy</span></span>  
  
- <span data-ttu-id="43a07-125">Vytvořit zásadu, která umožňuje všechny mezipaměti slouží k poskytování požadované prostředky, pokud prostředek na serveru není novější než kopie v mezipaměti pomocí nastavení mezipaměti na úrovni <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span><span class="sxs-lookup"><span data-stu-id="43a07-125">Create a policy that allows any cache to supply requested resources if the resource on the server is not newer than the cached copy by setting the cache level to <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43a07-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="43a07-126">See also</span></span>

- [<span data-ttu-id="43a07-127">Správa mezipaměti pro síťové aplikace</span><span class="sxs-lookup"><span data-stu-id="43a07-127">Cache Management for Network Applications</span></span>](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [<span data-ttu-id="43a07-128">Zásady mezipaměti</span><span class="sxs-lookup"><span data-stu-id="43a07-128">Cache Policy</span></span>](../../../docs/framework/network-programming/cache-policy.md)
- [<span data-ttu-id="43a07-129">Zásady mezipaměti na základě místa</span><span class="sxs-lookup"><span data-stu-id="43a07-129">Location-Based Cache Policies</span></span>](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [<span data-ttu-id="43a07-130">Zásady mezipaměti na základě času</span><span class="sxs-lookup"><span data-stu-id="43a07-130">Time-Based Cache Policies</span></span>](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [<span data-ttu-id="43a07-131">\<requestCaching – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="43a07-131">\<requestCaching> Element (Network Settings)</span></span>](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)

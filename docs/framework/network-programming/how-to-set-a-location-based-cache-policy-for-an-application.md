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
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a>Postupy: Nastavení zásad mezipaměti na základě umístění pro aplikaci
Zásady mezipaměti na základě umístění umožňují aplikaci explicitně definovat chování ukládání do mezipaměti na základě umístění požadovaného prostředku. Toto téma ukazuje, jak nastavit zásady mezipaměti programově. Informace o nastavení zásad pro aplikaci pomocí konfiguračních souborů naleznete v tématu [ \<RequestCaching > element (nastavení sítě)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a>Nastavení zásad mezipaměti na základě umístění pro aplikaci  
  
1. Vytvořte objekt <xref:System.Net.Cache.HttpRequestCachePolicy>nebo. <xref:System.Net.Cache.RequestCachePolicy>  
  
2. Nastavte objekt zásad jako výchozí pro doménu aplikace.  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a>Nastavení zásad, které přebírají požadované prostředky z mezipaměti  
  
- Vytvořte zásadu, která provede požadované prostředky z mezipaměti, pokud je k dispozici, a v opačném případě odešle požadavky na server nastavením úrovně mezipaměti <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>na. Požadavek může splnit jakákoli mezipaměť mezi klientem a serverem, včetně vzdálených mezipamětí.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a>Nastavení zásad, které zabrání v poskytnutí prostředků do mezipaměti  
  
- Vytvořte zásadu, která zabrání libovolné mezipaměti v poskytnutí požadovaných prostředků nastavením úrovně mezipaměti na <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>. Tato úroveň zásad odstraní prostředek z místní mezipaměti, pokud je přítomen, a označuje vzdálené mezipaměti, které by měly také odebrat prostředek.  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a>Nastavení zásad, které vrátí požadované prostředky pouze v případě, že jsou v místní mezipaměti  
  
- Vytvořte zásadu, která bude vracet požadované prostředky pouze v případě, že jsou v místní mezipaměti nastavením úrovně mezipaměti na <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>. Pokud požadovaný prostředek není v mezipaměti, <xref:System.Net.WebException> je vyvolána výjimka.  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a>Nastavení zásad, které brání místní mezipaměti v zásobování prostředků  
  
- Vytvořte zásadu, která zabrání v ukládání požadovaných prostředků do místní mezipaměti nastavením úrovně mezipaměti na <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>. Pokud se požadovaný prostředek nachází v přechodné mezipaměti a úspěšně se znovu ověří, mezilehlá mezipaměť může dodat požadovaný prostředek.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a>Nastavení zásad, které zabrání v ukládání požadovaných prostředků do mezipaměti  
  
- Vytvořte zásadu, která zabrání libovolné mezipaměti v poskytnutí požadovaných prostředků nastavením úrovně mezipaměti na <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>. Prostředek vrácený serverem může být uložený v mezipaměti.  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a>Nastavení zásady, která umožní, aby jakákoli mezipaměť poskytovala požadované prostředky, pokud prostředek na serveru není novější než kopie v mezipaměti  
  
- Vytvořte zásadu, která umožňuje, aby jakákoli mezipaměť poskytovala požadované prostředky, pokud prostředek na serveru není novější než kopie uložená v mezipaměti nastavením úrovně mezipaměti na <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Správa mezipaměti pro síťové aplikace](cache-management-for-network-applications.md)
- [Zásady mezipaměti](cache-policy.md)
- [Zásady mezipaměti na základě místa](location-based-cache-policies.md)
- [Zásady mezipaměti na základě času](time-based-cache-policies.md)
- [\<requestCaching – element > (nastavení sítě)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)

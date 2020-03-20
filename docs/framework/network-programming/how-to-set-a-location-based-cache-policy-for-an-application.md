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
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a>Postupy: Nastavení zásad mezipaměti na základě místa pro aplikaci
Zásady mezipaměti založené na umístění umožňují aplikaci explicitně definovat chování ukládání do mezipaměti na základě umístění požadovaného prostředku. Toto téma ukazuje nastavení zásad mezipaměti programově. Informace o nastavení zásad pro aplikaci používající konfigurační soubory naleznete v [ \<tématu requestCaching> Element (Network Settings).](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a>Nastavení zásad mezipaměti založené na umístění pro aplikaci  
  
1. Vytvořte <xref:System.Net.Cache.RequestCachePolicy> <xref:System.Net.Cache.HttpRequestCachePolicy> nebo objekt.  
  
2. Nastavte objekt zásad jako výchozí pro doménu aplikace.  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a>Nastavení zásady, která přebírá požadované prostředky z mezipaměti  
  
- Vytvořte zásadu, která převezme požadované prostředky z mezipaměti, pokud je k dispozici, <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>a jinak odešle požadavky na server nastavením úrovně mezipaměti na . Požadavek může splnit libovolná mezipaměť mezi klientem a serverem, včetně vzdálených mezipamětí.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a>Nastavení zásady, která brání jakékoli mezipaměti v poskytování prostředků  
  
- Vytvořte zásadu, která zabrání jakékoli mezipaměti v poskytování <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>požadovaných prostředků nastavením úrovně mezipaměti na . Tato úroveň zásad odebere prostředek z místní mezipaměti, pokud je k dispozici, a označuje vzdálené mezipaměti, že by měly také odebrat prostředek.  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a>Nastavení zásady, která vrací požadované prostředky pouze v případě, že jsou v místní mezipaměti  
  
- Vytvořte zásadu, která vrátí požadované prostředky pouze v případě, <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>že jsou v místní mezipaměti nastavením úrovně mezipaměti na . Pokud požadovaný prostředek není v mezipaměti, je vyvolána <xref:System.Net.WebException> výjimka.  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a>Nastavení zásady, která brání místní mezipaměti v poskytování prostředků  
  
- Vytvořte zásadu, která zabrání místní mezipaměti v poskytování <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>požadovaných prostředků nastavením úrovně mezipaměti na . Pokud je požadovaný prostředek v mezilehlé mezipaměti a je úspěšně znovu ověřen, může mezilehlá mezipaměť poskytnout požadovaný prostředek.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a>Nastavení zásady, která brání jakékoli mezipaměti v poskytování požadovaných prostředků  
  
- Vytvořte zásadu, která zabrání jakékoli mezipaměti v poskytování <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>požadovaných prostředků nastavením úrovně mezipaměti na . Prostředek vrácený serverem může být uložen v mezipaměti.  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a>Nastavení zásady, která umožňuje jakékoli mezipaměti zadávat požadované prostředky, pokud prostředek na serveru není novější než kopie uložená v mezipaměti  
  
- Vytvořte zásadu, která umožní jakékoli mezipaměti zadávat požadované prostředky, pokud prostředek na serveru <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>není novější než kopie uložená v mezipaměti, a to nastavením úrovně mezipaměti na .  
  
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
  
## <a name="see-also"></a>Viz také

- [Správa mezipaměti pro síťové aplikace](cache-management-for-network-applications.md)
- [Zásady mezipaměti](cache-policy.md)
- [Zásady mezipaměti na základě místa](location-based-cache-policies.md)
- [Zásady mezipaměti na základě času](time-based-cache-policies.md)
- [\<requestCaching> Element (Nastavení sítě)](../configure-apps/file-schema/network/requestcaching-element-network-settings.md)

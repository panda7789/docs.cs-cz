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
# <a name="how-to-set-a-location-based-cache-policy-for-an-application"></a>Postupy: Nastavení zásad mezipaměti na základě umístění pro aplikaci
Zásady mezipaměti na základě polohy umožnit aplikaci k explicitnímu definování chování ukládání do mezipaměti na základě umístění požadovaného prostředku. Toto téma popisuje nastavení zásad mezipaměti prostřednictvím kódu programu. Informace o nastavení zásad pro aplikace pomocí konfiguračních souborů naleznete v tématu [ \<requestCaching – > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md).  
  
### <a name="to-set-a-location-based-cache-policy-for-an-application"></a>Nastavení zásad mezipaměti na základě umístění pro aplikaci  
  
1. Vytvoření <xref:System.Net.Cache.RequestCachePolicy> nebo <xref:System.Net.Cache.HttpRequestCachePolicy> objektu.  
  
2. Nastavte jako výchozí pro doménu aplikace objektu zásad.  
  
### <a name="to-set-a-policy-that-takes-requested-resources-from-a-cache"></a>Chcete-li nastavit zásadu, která má požadované prostředky z mezipaměti  
  
- Vytvořit zásadu, která přebírá požadované prostředky z mezipaměti, pokud je k dispozici a v opačném případě zasílá požadavky na server, pomocí nastavení mezipaměti na úrovni <xref:System.Net.Cache.HttpRequestCacheLevel.CacheIfAvailable>. Žádost lze splnit všechny mezipaměti mezi klientem a serverem, včetně vzdáleného mezipamětí.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-resources"></a>Chcete-li nastavit zásadu, která brání všechny mezipaměti poskytující prostředky  
  
- Vytvořit zásadu, která brání poskytnutí požadovaných prostředků tak, že nastavíte mezipaměti úrovně pro všechny mezipaměti <xref:System.Net.Cache.HttpRequestCacheLevel.NoCacheNoStore>. Tato úroveň zásad odebere prostředek z místní mezipaměti, pokud je k dispozici a tak vzdálené mezipaměti informaci, že se mělo odstranit také na prostředek.  
  
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
  
### <a name="to-set-a-policy-that-returns-requested-resources-only-if-they-are-in-the-local-cache"></a>Chcete-li nastavit zásadu, která vrátí požadované prostředky pouze v případě, že jsou v místní mezipaměti  
  
- Vytvořit zásadu, která vrátí požadované prostředky pouze v případě, že jsou v místní mezipaměti pomocí nastavení mezipaměti na úrovni <xref:System.Net.Cache.HttpRequestCacheLevel.CacheOnly>. Pokud požadovaný prostředek není v mezipaměti, <xref:System.Net.WebException> je vyvolána výjimka.  
  
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
  
### <a name="to-set-a-policy-that-prevents-the-local-cache-from-supplying-resources"></a>Chcete-li nastavit zásadu, která brání poskytující prostředky místní mezipaměti  
  
- Vytvořit zásadu, která brání poskytnutí požadovaných prostředků podle nastavení úrovně do mezipaměti v místní mezipaměti <xref:System.Net.Cache.HttpRequestCacheLevel.Refresh>. Pokud požadovaný prostředek je v zprostředkující mezipaměti a úspěšně ověřit, zprostředkující mezipaměti můžete zadat požadovaný prostředek.  
  
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
  
### <a name="to-set-a-policy-that-prevents-any-cache-from-supplying-requested-resources"></a>Chcete-li nastavit zásadu, která brání všechny mezipaměti zadáním požadované prostředky  
  
- Vytvořit zásadu, která brání poskytnutí požadovaných prostředků tak, že nastavíte mezipaměti úrovně pro všechny mezipaměti <xref:System.Net.Cache.HttpRequestCacheLevel.Reload>. Prostředek vrácená serverem mohou být uloženy v mezipaměti.  
  
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
  
### <a name="to-set-a-policy-that-allows-any-cache-to-supply-requested-resources-if-the-resource-on-the-server-is-not-newer-than-the-cached-copy"></a>Chcete-li nastavit zásadu, která umožňuje všechny mezipaměti slouží k poskytování požadované prostředky, pokud prostředek na serveru není novější než kopie v mezipaměti  
  
- Vytvořit zásadu, která umožňuje všechny mezipaměti slouží k poskytování požadované prostředky, pokud prostředek na serveru není novější než kopie v mezipaměti pomocí nastavení mezipaměti na úrovni <xref:System.Net.Cache.HttpRequestCacheLevel.Revalidate>.  
  
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

- [Správa mezipaměti pro síťové aplikace](../../../docs/framework/network-programming/cache-management-for-network-applications.md)
- [Zásady mezipaměti](../../../docs/framework/network-programming/cache-policy.md)
- [Zásady mezipaměti na základě místa](../../../docs/framework/network-programming/location-based-cache-policies.md)
- [Zásady mezipaměti na základě času](../../../docs/framework/network-programming/time-based-cache-policies.md)
- [\<requestCaching – > – Element (nastavení sítě)](../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)

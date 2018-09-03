---
title: Správa připojení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Internet, connections
- HTTP, classes for connecting
- requesting data from Internet, connections
- sending data, connections
- receiving data, connections
- ServicePoint class, about ServicePoint class
- response to Internet request, connections
- connections [.NET Framework], classes
- network resources, connections
- downloading Internet resources, connections
- ServicePointManager class, about ServicePointManager class
ms.assetid: 9b3d3de7-189f-4f7d-81ae-9c29c441aaaa
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 29077a1c0f2b803270adb730e0d810143095e709
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43484977"
---
# <a name="managing-connections"></a>Správa připojení
Aplikace, které používají protokol HTTP pro připojení k datovým prostředkům můžete použít rozhraní .NET Framework <xref:System.Net.ServicePoint> a <xref:System.Net.ServicePointManager> třídy ke správě připojení k Internetu a aby to pomohl ostatním dosažení optimálního škálování a výkon.  
  
 **ServicePoint** třída poskytuje aplikace s koncovým bodem, do které můžete připojit aplikaci pro přístup k internetovým prostředkům. Každý **ServicePoint** informacemi, že pomáhá optimalizovat připojení pomocí internetového serveru při sdílení informací o optimalizaci mezi připojení ke zlepšení výkonu.  
  
 Každý **ServicePoint** je identifikován podle identifikátor URI (Uniform Resource) a jsou rozdělené do kategorií podle schéma identifikátor a fragmentům hostitele identifikátoru URI. Například stejné **ServicePoint** instance by požadavky poskytovat identifikátory URI `http://www.contoso.com/index.htm` a `http://www.contoso.com/news.htm?date=today` protože mají stejný identifikátor schématu (http) a fragmentů hostitele (`www.contoso.com`). Pokud má aplikace již trvalé připojení k serveru `www.contoso.com`, použije toto připojení k načtení obou požadavků, takže není nutné vytvořit dvě připojení.  
  
 **Třída ServicePointManager** je statická třída, která spravuje vytváření a ničení **ServicePoint** instancí. **Třída ServicePointManager** vytvoří **ServicePoint** když aplikace požádá o prostředek Internet, který se nenachází v kolekci stávajících **ServicePoint** instance. **ServicePoint** instancí jsou zničeny při překročení jejich maximální doba nečinnosti, nebo když se počet stávajících **ServicePoint** překračuje maximální počet instancí **ServicePoint**instancí aplikace. Můžete řídit, výchozí maximální doba nečinnosti a maximální počet **ServicePoint** instance tak, že nastavíte <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> a <xref:System.Net.ServicePointManager.MaxServicePoints%2A> vlastnosti **Třída ServicePointManager**.  
  
 Počet připojení mezi klientem a serverem, které může mít výrazný dopad na propustnost aplikace. Ve výchozím nastavení aplikace s využitím <xref:System.Net.HttpWebRequest> třída používá maximálně dvě trvalé připojení k danému serveru, ale můžete nastavit maximální počet připojení na základě jednotlivých aplikací.  
  
> [!NOTE]
>  Specifikace protokolu HTTP/1.1 omezuje počet připojení z aplikace do dvou připojení na serveru.  
  
 Optimální počet připojení, které závisí na skutečných podmínek, ve kterých je aplikace spuštěná. Zvýšení počtu připojení aplikace k dispozici nemusí mít vliv na výkon aplikace. Pokud chcete zjistit dopad další připojení, spuštění testů výkonu při různých počet připojení. Můžete změnit počet připojení, které aplikace používá tak, že změníte statické <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> vlastnost **Třída ServicePointManager** třídy při inicializaci aplikace, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 Změna **ServicePointManager.DefaultConnectionLimit** vlastnost nemá vliv na dříve inicializován **ServicePoint** instancí. Následující kód ukazuje změnu limitu připojení na existující **ServicePoint** pro server `http://www.contoso.com` na hodnotu uloženou v `newLimit`.  
  
```csharp  
Uri uri = new Uri("http://www.contoso.com/");  
ServicePoint sp = ServicePointManager.FindServicePoint(uri);  
sp.ConnectionLimit = newLimit;  
```  
  
```vb  
Dim uri As New Uri("http://www.contoso.com/")  
Dim sp As ServicePoint = ServicePointManager.FindServicePoint(uri)  
sp.ConnectionLimit = newLimit  
```  
  
## <a name="see-also"></a>Viz také  
 [Seskupení připojení](../../../docs/framework/network-programming/connection-grouping.md)  
 [Použití aplikačních protokolů](../../../docs/framework/network-programming/using-application-protocols.md)

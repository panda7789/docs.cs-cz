---
title: Správa připojení
description: Přečtěte si, jak aplikace, které používají protokol HTTP pro datové prostředky, můžou ke správě připojení používat třídy .NET Framework ServicePoint a Třída ServicePointManager.
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
ms.openlocfilehash: 124dff1b104e323b929d13f73cf17d740e747c32
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84502285"
---
# <a name="managing-connections"></a>Správa připojení
Aplikace, které používají protokol HTTP pro připojení k datovým prostředkům, mohou pomocí .NET Framework <xref:System.Net.ServicePoint> a <xref:System.Net.ServicePointManager> tříd spravovat připojení k Internetu a pomáhat jim dosáhnout optimálního škálování a výkonu.  
  
 Třída **ServicePoint** poskytuje aplikaci s koncovým bodem, ke kterému se může aplikace připojit a získat přístup k internetovým prostředkům. Každý **ServicePoint** obsahuje informace, které pomáhají optimalizovat připojení k internetovému serveru, a to sdílením informací o optimalizaci mezi připojeními za účelem zvýšení výkonu.  
  
 Jednotlivé **ServicePoint** jsou označeny identifikátorem URI (Uniform Resource Identifier) a jsou zařazeny do kategorií podle identifikátoru schématu a fragmentů hostitele identifikátoru URI. Například stejná instance **ServicePoint** poskytne žádosti identifikátorům URI `http://www.contoso.com/index.htm` a `http://www.contoso.com/news.htm?date=today` protože mají stejný identifikátor schématu (http) a fragmenty hostitele ( `www.contoso.com` ). Pokud už aplikace má trvalé připojení k serveru `www.contoso.com` , používá toto připojení k načtení obou požadavků, takže není potřeba vytvářet dvě připojení.  
  
 **Třída ServicePointManager** je statická třída, která spravuje vytváření a zničení instancí **ServicePoint** . **Třída ServicePointManager** vytvoří **ServicePoint** , když aplikace požádá o internetový prostředek, který není v kolekci existujících instancí **ServicePoint** . Instance **ServicePoint** jsou zničené, když překročí maximální dobu nečinnosti, nebo když počet stávajících instancí **ServicePoint** překračuje maximální počet instancí **ServicePoint** pro aplikaci. Nastavením **ServicePoint** <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> <xref:System.Net.ServicePointManager.MaxServicePoints%2A> vlastností a v **Třída ServicePointManager**můžete řídit výchozí maximální dobu nečinnosti a maximální počet instancí ServicePoint.  
  
 Počet připojení mezi klientem a serverem může výrazně ovlivnit propustnost aplikace. Ve výchozím nastavení aplikace, která používá <xref:System.Net.HttpWebRequest> třídu, používá maximálně dvě trvalá připojení k danému serveru, ale můžete nastavit maximální počet připojení na základě jednotlivých aplikací.  
  
> [!NOTE]
> Specifikace HTTP/1.1 omezuje počet připojení z aplikace na dvě připojení na jeden server.  
  
 Optimální počet připojení závisí na skutečných podmínkách, v nichž je aplikace spuštěna. Zvýšení počtu připojení, která jsou k dispozici pro aplikaci, nemusí mít vliv na výkon aplikace. Chcete-li zjistit dopad dalších připojení, spusťte testy výkonu při proměnlivosti počtu připojení. Počet připojení, která aplikace používá, můžete změnit tak, že změníte statickou <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> vlastnost třídy **Třída ServicePointManager** při inicializaci aplikace, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 Změna vlastnosti **Třída ServicePointManager. DefaultConnectionLimit** nemá vliv na dřív inicializované instance **ServicePoint** . Následující kód ukazuje změnu limitu připojení pro existující **ServicePoint** serveru `http://www.contoso.com` na hodnotu uloženou v `newLimit` .  
  
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
  
## <a name="see-also"></a>Viz také:

- [Seskupení připojení](connection-grouping.md)
- [Použití aplikačních protokolů](using-application-protocols.md)

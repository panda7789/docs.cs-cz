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
ms.openlocfilehash: 11c17c6893800fce8bbff8f49b3a207c161bcdfa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "71047637"
---
# <a name="managing-connections"></a>Správa připojení
Aplikace, které používají protokol HTTP k připojení k <xref:System.Net.ServicePoint> datovým prostředkům, mohou ke správě připojení k Internetu pomocí <xref:System.Net.ServicePointManager> rozhraní .NET Framework a tříd y a pomáhají jim dosáhnout optimálního rozsahu a výkonu.  
  
 Třída **ServicePoint** poskytuje aplikaci koncový bod, ke kterému se aplikace může připojit k přístupu k internetovým prostředkům. Každý **ServicePoint** obsahuje informace, které pomáhají optimalizovat připojení s internetovým serverem sdílením informací o optimalizaci mezi připojeními ke zlepšení výkonu.  
  
 Každý **ServicePoint** je identifikován identifikátorem URI (Uniform Resource Identifier) a je rozdělen do kategorií podle identifikátoru schématu a fragmentů hostitele identifikátoru URI. Například stejná instance **ServicePoint** by poskytovala `http://www.contoso.com/index.htm` požadavky `http://www.contoso.com/news.htm?date=today` na identifikátory URI a protože mají stejný`www.contoso.com`identifikátor schématu (http) a fragmenty hostitele ( ). Pokud aplikace již má trvalé připojení `www.contoso.com`k serveru , používá toto připojení k načtení obou požadavků, aby se zabránilo nutnosti vytvořit dvě připojení.  
  
 **ServicePointManager** je statická třída, která spravuje vytváření a ničení instancí **ServicePoint.** **ServicePointManager** vytvoří **ServicePoint,** když aplikace požaduje internetový prostředek, který není v kolekci existujících instancí **ServicePoint.** **Instance ServicePoint** jsou zničeny, pokud překročily maximální dobu nečinnosti nebo pokud počet existujících instancí **ServicePoint** překročí maximální počet instancí **ServicePoint** pro aplikaci. Můžete řídit výchozí maximální dobu nečinnosti a maximální počet instancí <xref:System.Net.ServicePointManager.MaxServicePoints%2A> **ServicePoint** nastavením <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> vlastnosti a na **ServicePointManager**.  
  
 Počet připojení mezi klientem a serverem může mít dramatický dopad na propustnost aplikace. Ve výchozím nastavení aplikace <xref:System.Net.HttpWebRequest> používající třídu používá maximálně dvě trvalá připojení k danému serveru, ale můžete nastavit maximální počet připojení pro aplikaci.  
  
> [!NOTE]
> Specifikace HTTP/1.1 omezuje počet připojení z aplikace na dvě připojení na server.  
  
 Optimální počet připojení závisí na skutečných podmínkách, ve kterých je aplikace spuštěna. Zvýšení počtu připojení, která jsou k dispozici pro aplikaci, nemusí mít vliv na výkon aplikace. Chcete-li zjistit dopad více připojení, spusťte testy výkonu při směšení počtu připojení. Počet připojení, která aplikace používá, můžete změnit <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> statickou vlastnost ve třídě **ServicePointManager** při inicializaci aplikace, jak je znázorněno v následujícím příkladu kódu.  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 Změna vlastnosti **ServicePointManager.DefaultConnectionLimit** nemá vliv na dříve inicializované instance **Služby ServicePoint.** Následující kód ukazuje změnu limitu připojení na existující `http://www.contoso.com` **ServicePoint** pro `newLimit`server na hodnotu uloženou v aplikaci .  
  
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

- [Seskupení připojení](connection-grouping.md)
- [Použití aplikačních protokolů](using-application-protocols.md)

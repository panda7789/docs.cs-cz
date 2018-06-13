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
ms.openlocfilehash: 8702f2329b262fc5c5965ae49365d46ba34091d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391170"
---
# <a name="managing-connections"></a>Správa připojení
Aplikace, které používají protokol HTTP pro připojení k prostředkům dat můžete použít rozhraní .NET Framework <xref:System.Net.ServicePoint> a <xref:System.Net.ServicePointManager> třídy ke správě připojení k Internetu a pomáhá jim dosáhnout optimálního škálování a výkon.  
  
 **Servisním místem** třída poskytuje aplikace s koncovým bodem, který lze aplikace připojí k přístup k internetovým prostředkům. Každý **servisním místem** obsahuje informace, že pomáhá optimalizovat připojení pomocí internetového serveru pomocí sdílení informací optimalizace mezi připojení ke zlepšení výkonu.  
  
 Každý **servisním místem** je identifikován pomocí identifikátor URI (Uniform Resource) a je zařazený do kategorie podle fragmenty identifikátor a hostitele schéma identifikátoru URI. Například stejné **servisním místem** instance by poskytnout požadavky identifikátory URI http://www.contoso.com/index.htm a http://www.contoso.com/news.htm?date=today vzhledem k tomu, že mají stejný identifikátor schématu (http) a hostitele fragmenty (www.contoso.com). Pokud aplikace už má trvalé připojení k serveru www.contoso.com, používá toto připojení k načtení oba požadavky, takže není nutné vytvořit dvě připojení.  
  
 **ServicePointManager –** je statická třída, která spravuje vytváření a zničení **servisním místem** instance. **ServicePointManager –** vytvoří **servisním místem** při aplikace požádá o prostředek Internet, který není v kolekci existující **servisním místem** instance. **Servisním místem** instance jsou zničen čas překročení jejich maximální doby nečinnosti nebo pokud je to číslo existující **servisním místem** překračuje maximální počet instancí **servisním místem**instancí aplikace. Můžete ovládat maximální dobu výchozí nečinnosti a maximální počet **servisním místem** instance podle nastavení <xref:System.Net.ServicePointManager.MaxServicePointIdleTime%2A> a <xref:System.Net.ServicePointManager.MaxServicePoints%2A> vlastnosti **ServicePointManager –**.  
  
 Počet připojení mezi klientem a serverem může mít výrazný dopad na propustnost aplikace. Ve výchozím nastavení aplikace pomocí <xref:System.Net.HttpWebRequest> třída používá maximálně dvě trvalé připojení k danému serveru, ale můžete nastavit maximální počet připojení na základě jednotlivých aplikací.  
  
> [!NOTE]
>  Specifikace protokolu HTTP/1.1 omezí počet připojení z aplikace do dvě připojení na server.  
  
 Optimální počet připojení závisí na skutečné podmínky, ve kterých je aplikace spuštěná. Zvýšením počtu připojení aplikace k dispozici nemusí ovlivnit výkon aplikace. Pokud chcete zjistit dopad více připojení, spusťte testy výkonu a budeme obměňovat počet připojení. Můžete změnit počet připojení, které aplikace používá změnou statických <xref:System.Net.ServicePointManager.DefaultConnectionLimit%2A> vlastnost **ServicePointManager –** třídy v inicializace aplikací, jak znázorňuje následující ukázka kódu.  
  
```csharp  
// Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4;  
```  
  
```vb  
' Set the maximum number of connections per server to 4.  
ServicePointManager.DefaultConnectionLimit = 4  
```  
  
 Změna **ServicePointManager.DefaultConnectionLimit** vlastnost nemá vliv na dříve inicializovaného **servisním místem** instance. Následující kód ukazuje, změna limitu připojení na existujícím **servisním místem** pro server http://www.contoso.com k s hodnotou uloženou v `newLimit`.  
  
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

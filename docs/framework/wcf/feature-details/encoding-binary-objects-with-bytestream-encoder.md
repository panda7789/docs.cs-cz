---
title: "Kódování binárních objektů pomocí kodéru ByteStream"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d1516731181a7e60445ce19752c3bb1835cb5897
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a>Kódování binárních objektů pomocí kodéru ByteStream
Odesílání a příjmu Nezpracovaná binární data s [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] je konfigurován pomocí <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.  
  
## <a name="byte-stream-message-encoder-architecture"></a>Architektura kodér zpráv datového proudu bajtů  
 Kodér zprávy v binární používané [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nemá žádné zařízení pro zpracování, ověřování nebo identifikace základní binární data ve zprávě. Datový balíček je kódovaný do souboru XML, odeslané, obdržel a dekódovat. Kodér zpracovává data po předávány k přenosu a předtím, než odešle zprávu do fronty zpráv. Funkčně, binární kodér zabalí zprávu data v `<binary>` prvky pro odesílání a odebere elementy po doručení zprávy.  
  
## <a name="using-the-byte-stream-message-encoder"></a>Pomocí kodéru zpráv datového proudu bajtů  
 Následující příklad ukazuje kontraktu služby, který implementuje kodér bajtů datového proudu zpráv.  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 Následující příklad ukazuje službu volaná.  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 V případě používání služby, který implementuje zpráva infrastruktury (třeba směrovač), je zpráva zpracována bez kontroly, ověřování nebo jinak interakci se zprávou, jak je znázorněno v následujícím příkladu.  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a>Scénáře  
 Kodér datového proudu bajtů je užitečné v následujících scénářích.  
  
-   Přenos ve formátu JPEG mezi počítači pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. V tomto scénáři image budou doručeny prostřednictvím přenosu z vnějšího zdroje a data odeslána bude nezpracovaná bajtů, které tvoří bitovou kopii. Služba bude přijímat binární data a umožňuje zobrazit obrázek.  
  
-   Čtení informací z fronty zpráv a její zpracování. Zpráva bude číst ze Správce fronty zpráv a předána do kanálu zprávu fronty ke zpracování. Kanál zprávy fronty bude fungovat jako správce front v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanál zásobníku.  
  
 V případě odesílání zprávy přes kanál fronty zpráv, odesílatel nemá žádnou kontrolu nad bajtů přijatých ze správce front. Pokud proces přijímající bez možnosti čtení nezpracované bajtů, bude přijímat zprávy, jako chybně formátována a nebude zpracován; předpokládá se, že proces přijímající budou mít funkce překladu přijatých bajtů zpět do použitelného formátu.

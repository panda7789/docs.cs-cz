---
title: Kódování binárních objektů pomocí kodéru ByteStream
ms.date: 03/30/2017
ms.assetid: 020ee981-c889-4b12-a3ea-91823ef46444
ms.openlocfilehash: 9619fdf6979833c30159e1ea02b3f8d6b98a6629
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856502"
---
# <a name="encoding-binary-objects-with-bytestream-encoder"></a>Kódování binárních objektů pomocí kodéru ByteStream
Odesílání a příjem Nezpracovaná binární data Windows Communication Foundation (WCF) je nakonfigurovaný nástrojem <xref:System.ServiceModel.Channels.ByteStreamMessageEncodingBindingElement>.  
  
## <a name="byte-stream-message-encoder-architecture"></a>Architektura kodér zprávy Stream bajtů  
 Kodér binárních zpráv používá WCF nemá žádné zařízení pro zpracování, ověřování nebo identifikace základní binární data ve zprávě. Balíček dat překóduje se na XML, odeslání, přijetí a dekódovat. Kodér zpracuje data po předávaný přenosu a před odesláním zprávy do fronty zpráv. Funkčně binárního kodéru zabalí data zprávy v `<binary>` prvky pro odesílání a odebere prvky po doručení zprávy.  
  
## <a name="using-the-byte-stream-message-encoder"></a>Pomocí kodéru zpráv Stream bajtů  
 Následující příklad ukazuje kontraktu služby, který implementuje kodéru zpráv datového proudu bajtů.  
  
```csharp  
[OperationContract]  
Void Myfunction(Stream stream);  
```  
  
 Následující příklad ukazuje vyvolání služby.  
  
```csharp  
proxy.MyFunction(stream);  
```  
  
 V případě použití služby, který implementuje infrastrukturu zprávy (jako jsou směrovače), je zpracovat zprávu bez kontroly, ověřování nebo jinak interakci s touto zprávou, jak je znázorněno v následujícím příkladu.  
  
```csharp  
[OperationContract]  
void ProcessMessage(Message message) ;  
```  
  
## <a name="scenarios"></a>Scénáře  
 Kodér Stream bajt je užitečná v následujících scénářích.  
  
- Obrázek JPEG přenosu mezi počítače pomocí technologie WCF. V tomto scénáři image dorazí prostřednictvím přenos z externího zdroje a data odesílají bude nezpracovaná bajtů, které tvoří bitovou kopii. Služba bude přijímat binární data a zobrazit obrázek.  
  
- Čtení informací z fronty zpráv a její zpracování. Zpráva bude číst z správce fronty zpráv a předané do kanálu zpráv fronty ke zpracování. Kanál zpráva fronty bude fungovat jako správce fronty v zásobníku kanál WCF.  
  
 V případě odesílání zprávy přes kanál fronty zpráv, odesílatel nemá žádnou kontrolu nad bajtů přijatých ze Správce fronty. Pokud přijímající procesu nemá žádné funkce pro čtení nezpracovaných bajtů, zprávy budou přijata chybně formátovány a nebudou zpracovány; předpokládá se, že přijímající proces bude mít funkce z překladu přijatých bajtů zpět do použitelného formátu.

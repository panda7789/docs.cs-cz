---
title: 'Postupy: Povolení streamování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: 1d1eaa1ebf41ef86478dda795b3b199239cd37b4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184933"
---
# <a name="how-to-enable-streaming"></a>Postupy: Povolení streamování
Windows Communication Foundation (WCF) můžete odesílat zprávy pomocí ukládání do vyrovnávací paměti nebo datových proudových přenosů. Ve výchozím režimu přenosu do vyrovnávací paměti musí být zpráva zcela doručena, aby ji příjemce mohl přečíst. V režimu přenosu datových proudů může příjemce začít zpracovávat zprávu před úplným doručením. Režim streamování je užitečný, pokud jsou informace, které jsou předány, zdlouhavé a mohou být zpracovány sériově. Režim streamování je také užitečné, když je zpráva příliš velká, aby byla zcela uložena do vyrovnávací paměti.  
  
 Chcete-li povolit `OperationContract` streamování, definujte správně a povolte streamování na úrovni přenosu.  
  
### <a name="to-stream-data"></a>Chcete-li streamovat data  
  
1. Chcete-li streamovat data, musí služba pro službu `OperationContract` splňovat dva požadavky:  
  
    1. Parametr, který obsahuje data, která mají být streamována, musí být jediným parametrem v metodě. Například pokud vstupní zpráva je ten, který má být datový proud, operace musí mít přesně jeden vstupní parametr. Podobně pokud výstupní zpráva má být datový proud, operace musí mít přesně jeden výstupní parametr nebo vrácenou hodnotu.  
  
    2. Alespoň jeden z typů parametru a vrácené <xref:System.IO.Stream> <xref:System.ServiceModel.Channels.Message>hodnoty <xref:System.Xml.Serialization.IXmlSerializable>musí být buď , nebo .  
  
     Následuje příklad smlouvy pro streamovaná data.  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     Operace `GetStream` obdrží některá vstupní data `string`ve vyrovnávací paměti jako , `Stream`která je uložena do vyrovnávací paměti, a vrátí datový proud . Naopak `UploadStream` bere v `Stream` (streamované) a `bool` vrátí (ve vyrovnávací paměti). `EchoStream`bere a `Stream` vrací a je příkladem operace, jejíž vstupní a výstupní zprávy jsou oba datového proudu. Nakonec `GetReversedStream` trvá žádné vstupy `Stream` a vrátí (streamed).  
  
2. Streamování musí být povolena na vazby. Můžete nastavit `TransferMode` vlastnost, která může trvat jednu z následujících hodnot:  
  
    1. `Buffered`,  
  
    2. `Streamed`, který umožňuje streamování komunikace v obou směrech.  
  
    3. `StreamedRequest`, který umožňuje streamování pouze požadavku.  
  
    4. `StreamedResponse`, který umožňuje streamování pouze odpovědi.  
  
     Zpřístupňuje `BasicHttpBinding` `TransferMode` vlastnost na vazbu, `NetTcpBinding` `NetNamedPipeBinding`stejně jako a . Vlastnost `TransferMode` lze také nastavit na prvek vazby přenosu a použít ve vlastní vazbě.  
  
     Následující ukázky ukazují, `TransferMode` jak nastavit podle kódu a změnou konfiguračního souboru. Ukázky také nastavit `maxReceivedMessageSize` vlastnost 64 MB, který umístí omezení na maximální přípustnou velikost zpráv při příjmu. Výchozí `maxReceivedMessageSize` hodnota je 64 kB, což je obvykle příliš nízká pro scénáře streamování. Nastavte toto nastavení kvóty podle potřeby v závislosti na maximální velikosti zpráv, které vaše aplikace očekává přijímat. Všimněte `maxBufferSize` si také, že řídí maximální velikost, která je ve vyrovnávací paměti a nastavte ji odpovídajícím způsobem.  
  
    1. Následující fragment konfigurace z ukázky ukazuje `TransferMode` nastavení vlastnosti `basicHttpBinding` na streamování na a vlastní vazbě HTTP.  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]
  
    2. Následující fragment kódu ukazuje nastavení `TransferMode` vlastnosti streamování `basicHttpBinding` na a vlastní vazbě HTTP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3. Následující fragment kódu ukazuje nastavení `TransferMode` vlastnosti streamování na vlastní vazbě TCP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3. Operace `GetStream`, `UploadStream`a `EchoStream` všechny se zabývají odesíláním dat přímo ze souboru nebo ukládáním přijatých dat přímo do souboru. Následující kód je `GetStream`pro .  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a>Psaní vlastního datového proudu  
  
1. Chcete-li provést speciální zpracování na každém bloku datového proudu, jak je <xref:System.IO.Stream>odesílán nebo přijímán, odvodit vlastní třídu datového proudu z . Jako příklad vlastního datového proudu následující `GetReversedStream` kód obsahuje `ReverseStream` metodu a třídu.  
  
     `GetReversedStream`vytvoří a vrátí novou `ReverseStream`instanci . Skutečné zpracování se stane při `ReverseStream` čtení systému z objektu. Metoda `ReverseStream.Read` přečte část bajtů z podkladového souboru, obrátí je a vrátí stornované bajty. Tato metoda neobrátí celý obsah souboru; obrátí jeden kus bajtů najednou. Tento příklad ukazuje, jak můžete provádět zpracování datového proudu jako obsah je čtení nebo zápis z datového proudu.  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [Objemná data a streamování](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
- [Datový proud](../../../../docs/framework/wcf/samples/stream.md)

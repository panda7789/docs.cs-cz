---
title: 'Postupy: Povolení streamování'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: 0d8428487c3c320a634914b99219e23befb70d55
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59312160"
---
# <a name="how-to-enable-streaming"></a>Postupy: Povolení streamování
Windows Communication Foundation (WCF) můžete odesílání zpráv s použitím přenosy ve vyrovnávací paměti nebo datovým proudem. Ve výchozím režimu přenosu ukládány do vyrovnávací paměti zprávy musí být zcela doručována předtím, než příjemce může číst. V režimu přenosu datového proudu, můžete začít příjemce zprávu zpracovat, než úplně doručení. Režim tvorby datového proudu je užitečné, když informace, které je předáno příliš dlouhý a může být zpracována sériově. Režim tvorby datového proudu je také užitečné, pokud zpráva je příliš velký, aby se zcela ukládány do vyrovnávací paměti.  
  
 Pokud chcete povolit streamování, definujte `OperationContract` odpovídajícím způsobem a umožňoval vysílání datového proudu na úrovni přenosu.  
  
### <a name="to-stream-data"></a>Pro streamování dat  
  
1. Pro streamování dat `OperationContract` pro službu musí splňovat dva požadavky:  
  
    1.  Parametr, který obsahuje data, která mají být Streamovat musí být jediný parametr v metodě. Například pokud vstupní zprávy je ten, který má být datovým proudem, operace musí mít přesně jeden vstupní parametr. Podobně při odesílání zprávy výstup operace musí mít právě jeden výstupní parametr nebo návratovou hodnotu.  
  
    2.  Nejméně jeden z typů parametrů a návratové hodnoty musí být buď <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, nebo <xref:System.Xml.Serialization.IXmlSerializable>.  
  
     Následuje příklad smlouvy pro streamovaná data.  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     `GetStream` Operace přijímá některá data ve vyrovnávací paměti vstupního jako `string`, je uložená do vyrovnávací paměti a vrátí `Stream`, které streamuje. Naopak `UploadStream` přijímá `Stream` (streamování) a vrátí `bool` (ukládány do vyrovnávací paměti). `EchoStream` přijímá a vrací `Stream` je příkladem operace, vstupní a výstupní zprávy jsou obě streamování. Nakonec `GetReversedStream` žádné vstupy přijímá a vrací `Stream` (streamování).  
  
2. Datový proud musí být povolené na vazbu. Můžete nastavit `TransferMode` vlastnost, která můžete provést jednu z následujících hodnot:  
  
    1.  `Buffered`,  
  
    2.  `Streamed`, která umožňuje streamování komunikaci v obou směrech.  
  
    3.  `StreamedRequest`, která umožňuje streamování pouze žádosti.  
  
    4.  `StreamedResponse`, což umožňuje streamování pouze odpovědi.  
  
     `BasicHttpBinding` Zpřístupňuje `TransferMode` vlastnost pro vazbu, stejně jako `NetTcpBinding` a `NetNamedPipeBinding`. `TransferMode` Vlastnosti také můžete nastavit na element vazby přenosu a používaných pro vlastní vazbu.  
  
     Následující ukázky ukazují, jak nastavit `TransferMode` kódu a změnou konfiguračního souboru. Ukázky také obě nastaveny `maxReceivedMessageSize` vlastnost 64 MB, který nahradí zakončení na maximální povolenou velikost zprávy na příjem. Výchozí hodnota `maxReceivedMessageSize` je 64 KB, což je obvykle příliš nízká pro streamování scénáře. Nastavte toto nastavení kvót podle potřeby v závislosti na maximální velikost zprávy, které vaše aplikace očekává. Všimněte si také, `maxBufferSize` určuje maximální velikost, která je uložená do vyrovnávací paměti a odpovídajícím způsobem nastavit.  
  
    1.  Následující fragment kódu konfigurace ze vzorku zobrazuje nastavení `TransferMode` vlastnost streamování na `basicHttpBinding` a vlastních vazeb protokolu HTTP.  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]   
  
    2.  Následující fragment kódu ukazuje nastavení `TransferMode` vlastnost streamování na `basicHttpBinding` a vlastních vazeb protokolu HTTP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3.  Následující fragment kódu ukazuje nastavení `TransferMode` vlastnost streamování pro vlastní vazbu protokolu TCP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3. Operace `GetStream`, `UploadStream`, a `EchoStream` všechna řešení odesílat data přímo ze souboru nebo uložení přijatá data přímo do souboru. Následující kód je pro `GetStream`.  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a>Psaní vlastního datového proudu  
  
1. Speciální zpracování na každý blok datového proudu současně s odesíláním ho nebo přijme, odvoďte třídu vlastního datového proudu z <xref:System.IO.Stream>. Jako příklad vlastního datového proudu, obsahuje následující kód `GetReversedStream` metoda a `ReverseStream` třída-.  
  
     `GetReversedStream` vytvoří a vrátí novou instanci třídy `ReverseStream`. Vlastní zpracování se stane, jak systém přečte z `ReverseStream` objektu. `ReverseStream.Read` Metoda čte blok bajtů ze základního souboru, obrátí je a potom vrátí obrácený bajtů. Tato metoda zpětné celý soubor obsahu; jeden blok bajtů se obrátí najednou. Tento příklad ukazuje, jak můžete provádět zpracování datového proudu jako obsah se ještě na číst nebo zapisovat z datového proudu.  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Objemná data a streamování](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)
- [Stream](../../../../docs/framework/wcf/samples/stream.md)

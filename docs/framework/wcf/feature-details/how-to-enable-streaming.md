---
title: "Postupy: Povolení streamování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b75fe67d99fa611f248c8d5dbb779f47e2bc717d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-streaming"></a>Postupy: Povolení streamování
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]můžete odesílat zprávy pomocí ve vyrovnávací paměti nebo přenášené datovými proudy přenosů. Ve výchozím režimu přenosu do vyrovnávací paměti zprávy musí být zcela doručována předtím, než příjemce může číst. Při streamování režim přenosu, můžete začít příjemce zprávu zpracovat, než je zcela doručit. Streamování režimu je užitečné, když informace, které se předá je náročná a může být zpracována sériově. Streamování režimu je také užitečné, pokud zpráva je moc velká, aby se zcela do vyrovnávací paměti.  
  
 Chcete-li povolit, streamování, definovat `OperationContract` správně a umožňoval vysílání datového proudu na úrovni přenosu.  
  
### <a name="to-stream-data"></a>K datům datového proudu  
  
1.  K datům datového proudu `OperationContract` pro službu musí být splněny dva požadavky:  
  
    1.  Parametr, který obsahuje data, která mají být prostřednictvím datového proudu musí být parametr pouze v metodě. Například pokud je vstupní zpráva má Streamovat, operaci musí mít přesně jeden vstupní parametr. Podobně pokud zpráva výstup je odesílání, operaci musí mít právě jednu výstupní parametr nebo návratovou hodnotu.  
  
    2.  Alespoň jeden z typů parametr a návratové hodnoty musí být buď <xref:System.IO.Stream>, <xref:System.ServiceModel.Channels.Message>, nebo <xref:System.Xml.Serialization.IXmlSerializable>.  
  
     Následuje příklad kontraktu pro datové proudy.  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     `GetStream` Operace přijímá některé z vyrovnávací paměti vstupní data jako `string`, která je uložená do vyrovnávací paměti a vrátí `Stream`, který datového proudu. Na druhé straně `UploadStream` přebírá `Stream` (streamování) a vrátí `bool` (uložená do vyrovnávací paměti). `EchoStream`provede a vrátí `Stream` je příkladem operace, jejichž vstup a výstup zprávy jsou obě streamování. Nakonec `GetReversedStream` přebere žádné vstupy a vrátí `Stream` (streamování).  
  
2.  Streamování musí být povolené na vazby. Můžete nastavit `TransferMode` vlastnosti, které můžete provést jednu z následujících hodnot:  
  
    1.  `Buffered`,  
  
    2.  `Streamed`, která umožňuje streamování komunikace v obou směrech.  
  
    3.  `StreamedRequest`, která umožňuje streamování jenom žádosti.  
  
    4.  `StreamedResponse`, která umožňuje streamování pouze odpovědi.  
  
     `BasicHttpBinding` Zpřístupní `TransferMode` vlastnost vazby, jak to dělá `NetTcpBinding` a `NetNamedPipeBinding`. `TransferMode` Vlastnosti také můžete nastavit v prvku vazby přenosu a použít v vlastní vazby.  
  
     Následující ukázky ukazují, jak nastavit `TransferMode` kódem a změnou konfiguračního souboru. Ukázky také obě nastaveny `maxReceivedMessageSize` vlastnost 64 MB, který nahradí zakončení na maximální povolenou velikost zprávy na přijímat. Výchozí hodnota `maxReceivedMessageSize` je 64 KB, který je obvykle příliš nízká pro streamování scénáře. Tato kvóta nastavení podle potřeby v závislosti na maximální velikost zprávy, které vaše aplikace očekává. Všimněte si také, že `maxBufferSize` určuje maximální velikost, která je uložená do vyrovnávací paměti a nastavte ji odpovídajícím způsobem.  
  
    1.  Následující fragment konfigurace z ukázky ukazuje nastavení `TransferMode` vlastnost streamování na `basicHttpBinding` a vlastní vazby HTTP.  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]   
  
    2.  Následující fragment kódu ukazuje nastavení `TransferMode` vlastnost streamování na `basicHttpBinding` a vlastní vazby HTTP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3.  Následující fragment kódu ukazuje nastavení `TransferMode` vlastnost streamování na vlastní vazby protokolu TCP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3.  Operace `GetStream`, `UploadStream`, a `EchoStream` všechny řešení odesílání dat přímo ze souboru nebo ukládání dat přijatých přímo do souboru. Následující kód je pro `GetStream`.  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a>Psaní vlastních datového proudu  
  
1.  Pro zvláštní zpracování na každého bloku datový proud jako odesílání nemusí být přijata, odvození třídy vlastního datového proudu z <xref:System.IO.Stream>. Jako příklad vlastního datového proudu, obsahuje následující kód `GetReversedStream` metoda a `ReverseStream` třída-.  
  
     `GetReversedStream`vytvoří a vrátí novou instanci třídy `ReverseStream`. Vlastní zpracování se stane, protože systém přečte z `ReverseStream` objektu. `ReverseStream.Read` Metoda čte blok bajtů z podkladový soubor, obrátí je a pak vrátí odstínech bajtů. Tato metoda reverse není celý soubor obsahu; současně se obrátí jeden blok bajtů. Tento příklad ukazuje, jak můžete provádět zpracování datového proudu, jak se obsah pro čtení nebo zapsat z datového proudu.  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Objemná data a streamování](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 [Stream](../../../../docs/framework/wcf/samples/stream.md)

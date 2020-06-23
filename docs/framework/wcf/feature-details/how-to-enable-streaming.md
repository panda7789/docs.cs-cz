---
title: 'Postupy: Povolení streamování'
description: Naučte se, jak povolit streamované zprávy ve službě WCF namísto výchozích přenosů ve vyrovnávací paměti, které je potřeba před zpracováním úplně přijmout.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 6ca2cf4b-c7a1-49d8-a79b-843a90556ba4
ms.openlocfilehash: 538fd8634094aa6fbf097ddb94469d7bca749a63
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247023"
---
# <a name="how-to-enable-streaming"></a>Postupy: Povolení streamování
Windows Communication Foundation (WCF) může odesílat zprávy pomocí vyrovnávacích pamětí nebo přenosů přes datový proud. Ve výchozím režimu přenosu do vyrovnávací paměti musí být zpráva zcela doručena předtím, než ji příjemce může přečíst. V režimu přenosu datového proudu může příjemce zahájit zpracování zprávy před úplným doručením. Režim streamování je užitečný v případě, že předávané informace jsou zdlouhavé a dají se zpracovat sériově. Režim streamování je vhodný také v případě, že je zpráva příliš velká a nemůže být zcela ukládána do vyrovnávací paměti.  
  
 Pokud chcete streamování povolit, definujte `OperationContract` odpovídajícím způsobem a povolte streamování na úrovni přenosu.  
  
### <a name="to-stream-data"></a>Pro streamování dat  
  
1. Pro streamování dat `OperationContract` musí služba pro službu splňovat dvě požadavky:  
  
    1. Parametr, který obsahuje data, která mají být datovým proudem, musí být jediným parametrem v metodě. Pokud je vstupní zpráva například ta, která se má streamovat, musí mít operace přesně jeden vstupní parametr. Podobně platí, že pokud má být výstupní zpráva streamovaná, operace musí mít buď přesně jeden výstupní parametr, nebo návratovou hodnotu.  
  
    2. Nejméně jeden z typů parametrů a návratová hodnota musí být buď <xref:System.IO.Stream> , <xref:System.ServiceModel.Channels.Message> nebo <xref:System.Xml.Serialization.IXmlSerializable> .  
  
     Následuje příklad smlouvy pro streamovaná data.  
  
     [!code-csharp[c_HowTo_EnableStreaming#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#1)]
     [!code-vb[c_HowTo_EnableStreaming#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#1)]  
  
     `GetStream`Operace přijme některá vstupní data ve vyrovnávací paměti jako `string` , která jsou ukládána do vyrovnávací paměti, a vrátí `Stream` , který je datovým proudem. Naopak `UploadStream` přebírá `Stream` (streamuje) a vrací `bool` (Buffered). `EchoStream`přijímá a vrací `Stream` a je příkladem operace, jejíž vstupní a výstupní zprávy jsou přenášeny datovým proudem. Nakonec `GetReversedStream` neprovede žádné vstupy a vrátí `Stream` (streamované).  
  
2. Ve vazbě musí být povoleno streamování. Nastavili jste `TransferMode` vlastnost, která může mít jednu z následujících hodnot:  
  
    1. `Buffered`,  
  
    2. `Streamed`, což umožňuje komunikaci streamování v obou směrech.  
  
    3. `StreamedRequest`, což umožňuje streamování pouze požadavku.  
  
    4. `StreamedResponse`, což umožňuje streamování jenom odpovědi.  
  
     `BasicHttpBinding`Vlastnost zpřístupňuje `TransferMode` vlastnost vazby, jak to dělá `NetTcpBinding` a `NetNamedPipeBinding` . `TransferMode`Vlastnost lze také nastavit na elementu vazby přenosu a použít ve vlastní vazbě.  
  
     Následující ukázky ukazují, jak nastavit `TransferMode` kód a změnit konfigurační soubor. V ukázkách se také nastaví `maxReceivedMessageSize` vlastnost na 64 MB, která umístí limit na maximální povolenou velikost zpráv při příjmu. Výchozí hodnota `maxReceivedMessageSize` je 64 KB, což je obvykle příliš nízké pro scénáře streamování. Nastavení této kvóty nastavte podle potřeby v závislosti na maximální velikosti zpráv, které aplikace očekává přijmout. Všimněte si také, že `maxBufferSize` ovládací prvky mají maximální velikost, která je ukládána do vyrovnávací paměti, a patřičně ji nastavte.  
  
    1. Následující fragment kódu konfigurace z příkladu ukazuje nastavení `TransferMode` vlastnosti pro streamování na `basicHttpBinding` a vlastní vazbu HTTP.  
  
         [!code-xml[c_HowTo_EnableStreaming#103](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/common/app.config#103)]
  
    2. Následující fragment kódu ukazuje nastavení `TransferMode` vlastnosti na streamování v `basicHttpBinding` a vlastní vazby HTTP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#2)]
         [!code-vb[c_HowTo_EnableStreaming_code#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#2)]  
  
    3. Následující fragment kódu ukazuje nastavení `TransferMode` vlastnosti na streamování ve vlastní vazbě protokolu TCP.  
  
         [!code-csharp[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming_code/cs/c_howto_enablestreaming_code.cs#3)]
         [!code-vb[c_HowTo_EnableStreaming_code#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming_code/vb/c_howto_enablestreaming_code.vb#3)]  
  
3. Operace `GetStream` , `UploadStream` a `EchoStream` se týkají odesílání dat přímo ze souboru nebo ukládání přijatých dat přímo do souboru. Následující kód je pro `GetStream` .  
  
     [!code-csharp[c_HowTo_EnableStreaming#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#4)]
     [!code-vb[c_HowTo_EnableStreaming#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#4)]  
  
### <a name="writing-a-custom-stream"></a>Zápis vlastního datového proudu  
  
1. Chcete-li provést speciální zpracování pro každý blok datového proudu při jeho posílání nebo přijímání, odvodit vlastní třídu Stream z <xref:System.IO.Stream> . Jako příklad vlastního datového proudu obsahuje následující kód `GetReversedStream` metodu a `ReverseStream` třídu –.  
  
     `GetReversedStream`Vytvoří a vrátí novou instanci `ReverseStream` . Ke skutečnému zpracování dojde, když systém čte z `ReverseStream` objektu. `ReverseStream.Read`Metoda načte blok bajtů z podkladového souboru, obrátí je a potom vrátí obrácené bajty. Tato metoda nevrátí celý obsah souboru. v jednom okamžiku vrátí jeden blok bajtů. Tento příklad ukazuje, jak lze provádět zpracování datového proudu při čtení a zápisu obsahu z datového proudu.  
  
     [!code-csharp[c_HowTo_EnableStreaming#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_enablestreaming/cs/service.cs#2)]
     [!code-vb[c_HowTo_EnableStreaming#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_enablestreaming/vb/service.vb#2)]  
  
## <a name="see-also"></a>Viz také

- [Objemná data a streamování](large-data-and-streaming.md)
- [Datový proud](../samples/stream.md)

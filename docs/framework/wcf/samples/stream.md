---
title: Stream
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: c16f12e6fb122fbba7dc46abb26859be49c08f74
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662592"
---
# <a name="stream"></a>Stream
Stream ukázce použití streamování komunikace režim přenosu. Služba zpřístupňuje několik operací, které odesílání a příjem streamů. Tato ukázka je v místním prostředí. Klient a služba se o programy konzoly.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Windows Communication Foundation (WCF) můžou komunikovat ve dvou režimech přenos – ve vyrovnávací paměti nebo datových proudů. Ve výchozím režimu přenosu ve vyrovnávací paměti zprávy musí být zcela doručována předtím, než příjemce může číst. V režim tvorby datového proudu přenosu můžete začít příjemce zprávu zpracovat, než úplně doručení. Režim tvorby datového proudu je užitečné, když informace, které je předáno příliš dlouhý a může být zpracována sériově. Režim tvorby datového proudu je také užitečné, pokud zpráva je příliš velký, aby se zcela ukládány do vyrovnávací paměti.  
  
## <a name="streaming-and-service-contracts"></a>Streamování a kontrakty služeb  
 Streamování je něco, co vzít v úvahu při navrhování kontraktu služby. Pokud operace přijímá nebo vrací velké množství dat, měli byste zvážit, tato data, aby se zabránilo vysoké využití paměti z důvodu ukládání do vyrovnávací paměti zpráv vstupních nebo výstupních datových proudů. Pro streamování dat, parametr, který obsahuje, data musí být jediným parametrem ve zprávě. Například pokud vstupní zprávy je ten, který má být datovým proudem, operace musí mít přesně jeden vstupní parametr. Podobně při odesílání zprávy výstup operace musí mít právě jeden výstupní parametr nebo návratovou hodnotu. V případě, parametr nebo návratovou hodnotu typu musí být buď `Stream`, `Message`, nebo `IXmlSerializable`. Tady je kontrakt služby používané v tomto příkladu datových proudů.  
  
```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IStreamingSample  
{  
    [OperationContract]  
    Stream GetStream(string data);  
    [OperationContract]  
    bool UploadStream(Stream stream);  
    [OperationContract]  
    Stream EchoStream(Stream stream);  
    [OperationContract]  
    Stream GetReversedStream();  
  
}  
```  
  
 `GetStream` Operace přijímá vstupní data jako řetězec, který je uložená do vyrovnávací paměti a vrátí `Stream`, které streamuje. Naopak `UploadStream` přijímá `Stream` (streamování) a vrátí `bool` (ukládány do vyrovnávací paměti). `EchoStream` přijímá a vrací `Stream` je příkladem operace, vstupní a výstupní zprávy jsou obě streamování. Nakonec `GetReversedStream` žádné vstupy přijímá a vrací `Stream` (streamování).  
  
## <a name="enabling-streamed-transfers"></a>Povolení streamovaná přenosy  
 Definování kontraktů operace, jak je uvedeno výše poskytuje datové proudy na úrovni modelu programování. Chcete-li zrušit existuje přenos stále ukládá do vyrovnávací paměti obsah celé zprávy. Pokud chcete povolit přenos streamování, vyberte režim přenosu na element vazby přenosu. Má element vazby `TransferMode` vlastnost, která může být nastaven na `Buffered`, `Streamed`, `StreamedRequest`, nebo `StreamedResponse`. Nastavení režimu převodu na `Streamed` umožňuje streamování komunikace v obou směrech. Nastavení režimu převodu na `StreamedRequest` nebo `StreamedResponse` umožňuje streamování komunikace v požadavku nebo odpovědi, v uvedeném pořadí.  
  
 `basicHttpBinding` Zpřístupňuje `TransferMode` vlastnost pro vazbu, stejně jako `NetTcpBinding` a `NetNamedPipeBinding`. Pro další přenosy musíte vytvořit vlastní vazby pro nastavení režimu převodu.  
  
 Následující kód z ukázkového konfigurace zobrazuje nastavení `TransferMode` vlastnost streamování na `basicHttpBinding` a vlastních vazeb protokolu HTTP:  
  
```xml  
<!-- An example basicHttpBinding using streaming. -->  
<basicHttpBinding>  
  <binding name="HttpStreaming" maxReceivedMessageSize="67108864"  
           transferMode="Streamed"/>  
</basicHttpBinding>  
<!-- An example customBinding using HTTP and streaming.-->  
<customBinding>  
  <binding name="Soap12">  
    <textMessageEncoding messageVersion="Soap12WSAddressing10" />  
    <httpTransport transferMode="Streamed"  
                   maxReceivedMessageSize="67108864"/>  
  </binding>  
</customBinding>  
```  
  
 Kromě nastavení `transferMode` k `Streamed`, předchozí konfiguračních sad kód `maxReceivedMessageSize` 64 MB. Jako mechanismus ochrany před mobilními `maxReceivedMessageSize` zobrazit zakončení na maximální povolenou velikost zprávy v místech. Výchozí hodnota `maxReceivedMessageSize` je 64 KB, což je obvykle příliš nízká pro streamování scénáře.  
  
## <a name="processing-data-as-it-is-streamed"></a>Zpracování dat, jako je streamování  
 Operace `GetStream`, `UploadStream` a `EchoStream` všechna řešení odesílat data přímo ze souboru nebo uložení přijatá data přímo do souboru. Ale v některých případech je požadavek na odeslání nebo příjem velkých objemů dat a provádět některé zpracování na bloky dat se ještě odeslány nebo přijaty. Jedním ze způsobů takových situacích je napsat vlastní datový proud (třída, která je odvozena z <xref:System.IO.Stream>), který zpracovává data, jako je číst nebo zapisovat. `GetReversedStream` Operace a `ReverseStream` třídy jsou příkladem.  
  
 `GetReversedStream` vytvoří a vrátí novou instanci třídy `ReverseStream`. Vlastní zpracování se stane, jak systém přečte od `ReverseStream` objektu. `ReverseStream.Read` Implementace čte blok bajtů ze základního souboru, obrátí je a potom vrátí obrácený bajtů. Toto zpětné celý soubor obsahu; jeden blok bajtů se obrátí najednou. Toto je příklad, chcete-li zobrazit, jak můžete provádět zpracování datového proudu jako obsah se číst nebo zapisovat z a do datového proudu.  
  
```csharp
class ReverseStream : Stream  
{  
  
    FileStream inStream;  
    internal ReverseStream(string filePath)  
    {  
        //Opens the file and places a StreamReader around it.  
        inStream = File.OpenRead(filePath);  
    }  
  
    // Other methods removed for brevity.  
  
    public override int Read(byte[] buffer, int offset, int count)  
    {  
        int countRead=inStream.Read(buffer, offset,count);  
        ReverseBuffer(buffer, offset, countRead);  
        return countRead;  
    }  
  
    public override void Close()  
    {  
        inStream.Close();  
        base.Close();  
    }  
    protected override void Dispose(bool disposing)  
    {  
        inStream.Dispose();  
        base.Dispose(disposing);  
    }  
    void ReverseBuffer(byte[] buffer, int offset, int count)  
    {  
        int i, j;  
        for (i = offset, j = offset + count - 1; i < j; i++, j--)  
        {  
            byte currenti = buffer[i];  
            buffer[i] = buffer[j];  
            buffer[j] = currenti;  
        }  
  
    }  
}  
```  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
 Ke spuštění ukázky, nejdřív sestavte službu a klienta podle pokynů na konci tohoto dokumentu. Potom spusťte službu a klienta ve dvou různých konzoly windows. Když se klient spustí, čeká až stisknete ENTER, když se tato služba je připravena. Klient pak zavolá metodu `GetStream()`, `UploadStream()` a `GetReversedStream()` nejprve přes protokol HTTP a pak přes protokol TCP. Tady je příklad výstupu ze služby, za nímž následuje příklad výstupu z klienta:  
  
 Výstup služby:  
  
```console  
The streaming service is ready.  
Press <ENTER> to terminate service.  
  
Saving to file D:\...\uploadedfile  
......................  
File D:\...\uploadedfile saved  
Saving to file D:\...\uploadedfile  
...............  
File D:\...\uploadedfile saved  
```  
  
 Výstup klienta:  
  
```console  
Press <ENTER> when service is ready  
------ Using HTTP ------   
Calling GetStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
......................  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
------ Using Custom HTTP ------  
Calling GetStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
Calling UploadStream()  
Calling GetReversedStream()  
Saving to file D:\...\clientfile  
...............  
Wrote 33405 bytes to stream  
  
File D:\...\clientfile saved  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Pokud používáte Svcutil.exe k opětovnému vytvoření konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly klientský kód.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
  
## <a name="see-also"></a>Viz také:

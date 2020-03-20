---
title: Datový proud
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: f22339ca298f053fa636cc37281276051c70f6d6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183319"
---
# <a name="stream"></a>Datový proud
Stream ukázka ukazuje použití přenosu datového proudu režimu komunikace. Služba zveřejňuje několik operací, které odesílají a přijímají datové proudy. Tato ukázka je hostována samostatně. Klient i služba jsou konzolové programy.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Windows Communication Foundation (WCF) může komunikovat ve dvou režimech přenosu – ve vyrovnávací paměti nebo streamování. Ve výchozím režimu přenosu ve vyrovnávací paměti musí být zpráva zcela doručena, aby ji příjemce mohl přečíst. V režimu přenosu datových proudů může příjemce začít zpracovávat zprávu před úplným doručením. Režim streamování je užitečný, pokud jsou informace, které jsou předány, zdlouhavé a mohou být zpracovány sériově. Režim streamování je také užitečné, když je zpráva příliš velká, aby byla zcela uložena do vyrovnávací paměti.  
  
## <a name="streaming-and-service-contracts"></a>Smlouvy o streamování a poskytování služeb  
 Streamování je něco, co je třeba vzít v úvahu při navrhování smlouvy o poskytování služeb. Pokud operace přijímá nebo vrací velké množství dat, měli byste zvážit streamování těchto dat, abyste se vyhnuli vysokému využití paměti z důvodu ukládání vstupních nebo výstupních zpráv do vyrovnávací paměti. Chcete-li streamovat data, musí být parametr, který tato data obsahuje, jediným parametrem ve zprávě. Například pokud vstupní zpráva je ten, který má být datový proud, operace musí mít přesně jeden vstupní parametr. Podobně pokud výstupní zpráva má být datový proud, operace musí mít přesně jeden výstupní parametr nebo vrácenou hodnotu. V obou případech musí být parametr nebo `Stream` `Message`typ `IXmlSerializable`vrácené hodnoty buď , nebo . Následuje smlouva o poskytování služeb použitá v této ukázce streamování.  
  
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
  
 Operace `GetStream` obdrží některá vstupní data jako řetězec, který je `Stream`do vyrovnávací paměti a vrátí , který je přenášen datovým proudem. Naopak `UploadStream` bere v `Stream` (streamed) a `bool` vrátí (ve vyrovnávací paměti). `EchoStream`bere a `Stream` vrací a je příkladem operace, jejíž vstupní a výstupní zprávy jsou oba datového proudu. Nakonec `GetReversedStream` trvá žádné vstupy `Stream` a vrátí (streamed).  
  
## <a name="enabling-streamed-transfers"></a>Povolení datových proudů přenosů  
 Definování smluv operace, jak bylo popsáno výše, poskytuje streamování na úrovni programovacího modelu. Pokud zastavíte tam, přenos stále vyrovnávací paměti celý obsah zprávy. Chcete-li povolit přenos datových proudů, vyberte režim přenosu na prvek vazby přenosu. Element vazby `TransferMode` má vlastnost, kterou `Buffered` `Streamed`lze `StreamedRequest`nastavit `StreamedResponse`na , , nebo . Nastavení režimu `Streamed` přenosu na umožňuje streamování komunikace v obou směrech. Nastavení režimu `StreamedRequest` přenosu `StreamedResponse` na nebo umožňuje streamování komunikace pouze v požadavku nebo odpovědi, resp.  
  
 Zpřístupňuje `basicHttpBinding` `TransferMode` vlastnost na vazbu `NetTcpBinding` `NetNamedPipeBinding`jako a . Pro ostatní přenosy je nutné vytvořit vlastní vazbu pro nastavení režimu přenosu.  
  
 Následující konfigurační kód z `TransferMode` ukázky ukazuje `basicHttpBinding` nastavení vlastnosti na streamování na a vlastní vazbě HTTP:  
  
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
  
 Kromě nastavení `transferMode` na `Streamed`, předchozí konfigurační kód nastaví `maxReceivedMessageSize` 64 MB. Jako obranný mechanismus umístí `maxReceivedMessageSize` omezení na maximální přípustnou velikost zpráv při příjmu. Výchozí `maxReceivedMessageSize` hodnota je 64 kB, což je obvykle příliš nízká pro scénáře streamování.  
  
## <a name="processing-data-as-it-is-streamed"></a>Zpracování dat tak, jak jsou streamována  
 Operace `GetStream` `UploadStream` a `EchoStream` všechny se zabývají odesíláním dat přímo ze souboru nebo ukládáním přijatých dat přímo do souboru. V některých případech však existuje požadavek na odesílání nebo přijímání velkého množství dat a provádění některých zpracování na blocích dat při odesílání nebo přijímání. Jedním ze způsobů, jak řešit tyto scénáře je napsat <xref:System.IO.Stream>vlastní datový proud (třída, která je odvozena z ) , který zpracovává data, jak je čtení nebo zápis. Operace `GetReversedStream` a `ReverseStream` třída jsou příkladem tohoto.  
  
 `GetReversedStream`vytvoří a vrátí novou `ReverseStream`instanci . Skutečné zpracování se stane při `ReverseStream` čtení systému z tohoto objektu. Implementace `ReverseStream.Read` přečte část bajtů z podkladového souboru, obrátí je a vrátí stornované bajty. Tím se neobrátí celý obsah souboru; obrátí jeden kus bajtů najednou. Toto je příklad, který ukazuje, jak můžete provádět zpracování datového proudu při čtení nebo zápisu obsahu z datového proudu a do datového proudu.  
  
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
 Chcete-li spustit ukázku, nejprve sestavte službu i klienta podle pokynů na konci tohoto dokumentu. Potom spusťte službu a klienta ve dvou různých oknech konzoly. Když se klient spustí, čeká, až stisknete klávesu ENTER, jakmile bude služba připravena. Klient pak volá `GetStream()`metody `UploadStream()` `GetReversedStream()` a nejprve přes HTTP a potom přes TCP. Zde je příklad výstupu ze služby následovaný ukázkovým výstupem z klienta:  
  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Pokud používáte Svcutil.exe k obnovení konfigurace pro tuto ukázku, nezapomeňte upravit název koncového bodu v konfiguraci klienta tak, aby odpovídalkódu klienta.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  

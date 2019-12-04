---
title: Stream
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: d4166ac0258001b3e4eb0b8ece0f5163863359a4
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716662"
---
# <a name="stream"></a>Stream
Ukázka streamu demonstruje použití komunikace režimu přenosu datového proudu. Služba zveřejňuje několik operací, které odesílají a přijímají streamy. Tato ukázka je v místním prostředí hostovaná. Klient i služba jsou konzolové programy.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Windows Communication Foundation (WCF) může komunikovat ve dvou režimech přenosu – ve vyrovnávací paměti nebo streamování. Ve výchozím režimu přenosu do vyrovnávací paměti musí být zpráva zcela doručena předtím, než ji příjemce může přečíst. V režimu přenosu datových proudů může příjemce zahájit zpracování zprávy před úplným doručením. Režim streamování je užitečný v případě, že předávané informace jsou zdlouhavé a dají se zpracovat sériově. Režim streamování je vhodný také v případě, že je zpráva příliš velká a nemůže být zcela ukládána do vyrovnávací paměti.  
  
## <a name="streaming-and-service-contracts"></a>Streamování a kontrakty služeb  
 Streamování je něco, co je potřeba vzít v úvahu při návrhu kontraktu služby. Pokud operace přijme nebo vrátí velké objemy dat, měli byste zvážit streamování těchto dat, aby se zabránilo vysokému využití paměti kvůli ukládání vstupních nebo výstupních zpráv do vyrovnávací paměti. Pro streamování dat musí být parametr, který obsahuje tato data, jediným parametrem ve zprávě. Pokud je vstupní zpráva například ta, která se má streamovat, musí mít operace přesně jeden vstupní parametr. Podobně platí, že pokud má být výstupní zpráva streamovaná, operace musí mít buď přesně jeden výstupní parametr, nebo návratovou hodnotu. V obou případech musí být parametr nebo návratový typ hodnoty buď `Stream`, `Message`nebo `IXmlSerializable`. Níže je uvedené kontrakt služby použitý v této ukázce streamování.  
  
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
  
 Operace `GetStream` přijímá některá vstupní data jako řetězec, který je uložen do vyrovnávací paměti a vrací `Stream`, která je vysílána do datového proudu. Naopak `UploadStream` přebírá v `Stream` (streamované) a vrací `bool` (ve vyrovnávací paměti). `EchoStream` přebírá a vrací `Stream` a je příkladem operace, jejíž vstupní a výstupní zprávy jsou přenášeny datovým proudem. Nakonec `GetReversedStream` nepřevádí žádné vstupy a vrátí `Stream` (streamované).  
  
## <a name="enabling-streamed-transfers"></a>Povolení přenosů odeslaných datovým proudem  
 Definování kontraktů operací, jak je popsáno výše, poskytuje streamování na úrovni programovacího modelu. Pokud tam zastavíte, přenos bude ukládat celý obsah zprávy do vyrovnávací paměti. Chcete-li povolit streamování přenosu, vyberte režim přenosu na elementu vazby přenosu. Element Binding má vlastnost `TransferMode`, kterou lze nastavit na `Buffered`, `Streamed`, `StreamedRequest`nebo `StreamedResponse`. Nastavení režimu přenosu na `Streamed` povolí komunikaci streamování v obou směrech. Nastavení režimu přenosu na `StreamedRequest` nebo `StreamedResponse` povolí komunikaci streamování pouze v žádosti nebo odpovědi.  
  
 `basicHttpBinding` zpřístupňuje vlastnost `TransferMode` ve vazbě jako `NetTcpBinding` a `NetNamedPipeBinding`. Pro jiné přenosy je nutné vytvořit vlastní vazbu pro nastavení režimu přenosu.  
  
 Následující konfigurační kód z ukázky ukazuje nastavení vlastnosti `TransferMode` na streamování v `basicHttpBinding` a vlastní vazby HTTP:  
  
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
  
 Kromě nastavení `transferMode` `Streamed`, předchozí konfigurační kód nastaví `maxReceivedMessageSize` na 64 MB. Jako mechanismus ochrany `maxReceivedMessageSize` umístí limit maximální povolené velikosti zpráv při příjmu. Výchozí `maxReceivedMessageSize` je 64 KB, což je obvykle příliš nízké pro scénáře streamování.  
  
## <a name="processing-data-as-it-is-streamed"></a>Zpracování dat při streamování  
 Provozní `GetStream`, `UploadStream` a `EchoStream` se zabývat odesláním dat přímo ze souboru nebo uložení přijatých dat přímo do souboru. V některých případech však existuje požadavek na odeslání nebo přijetí velkých objemů dat a provádění určitého zpracování datových bloků dat při jejich posílání nebo přijímání. Jedním ze způsobů, jak tyto scénáře vyřešit, je napsat vlastní datový proud (třída odvozená z <xref:System.IO.Stream>), která zpracovává data při čtení nebo zápisu. Příkladem je `GetReversedStream` operace a `ReverseStream` třídy.  
  
 `GetReversedStream` vytvoří a vrátí novou instanci `ReverseStream`. Ke skutečnému zpracování dojde, když systém čte z tohoto objektu `ReverseStream`. Implementace `ReverseStream.Read` čte blok bajtů z podkladového souboru, obrátí je a potom vrátí obrácené bajty. Tím se nevrátí celý obsah souboru. v jednom okamžiku vrátí jeden blok bajtů. Toto je příklad, který ukazuje, jak lze provádět zpracování datového proudu při čtení nebo zápisu obsahu z a do datového proudu.  
  
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
 Chcete-li spustit ukázku, nejprve Sestavte službu i klienta podle pokynů na konci tohoto dokumentu. Pak spusťte službu a klienta ve dvou různých oknech konzoly. Po spuštění klienta počká, až bude služba připravena, po stisknutí klávesy ENTER. Klient pak zavolá metody `GetStream()`, `UploadStream()` a `GetReversedStream()` nejdříve přes protokol HTTP a potom přes protokol TCP. Tady je příklad výstupu služby následovaný ukázkovým výstupem z klienta:  
  
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
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
> Pokud pro obnovení konfigurace této ukázky používáte Svcutil. exe, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídal kódu klienta.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  

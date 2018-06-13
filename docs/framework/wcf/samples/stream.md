---
title: Stream
ms.date: 03/30/2017
ms.assetid: 58a3db81-20ab-4627-bf31-39d30b70b4fe
ms.openlocfilehash: 96b77d0135a4dac1dcb8406a1b9a1372d0c4a35d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33508212"
---
# <a name="stream"></a>Stream
Ukázkový datový proud demonstruje použití streamování přenosu režimu komunikace. Služba zpřístupňuje několik operací, které odesílat a přijímat datové proudy. Tato ukázka se hostuje sama. Klient a služba jsou programy konzoly.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Windows Communication Foundation (WCF) může komunikovat ve dvou režimech přenos – ve vyrovnávací paměti nebo streamování. Ve výchozím režimu přenosu ve vyrovnávací paměti zprávy musí být zcela doručována předtím, než příjemce může číst. V režimu datového přenosu můžete začít příjemce zprávu zpracovat, než je zcela doručit. Streamování režimu je užitečné, když informace, které se předá je náročná a může být zpracována sériově. Streamování režimu je také užitečné, pokud zpráva je moc velká, aby se zcela do vyrovnávací paměti.  
  
## <a name="streaming-and-service-contracts"></a>Streaming kontraktů a kontraktů služby  
 Streamování je něco zvážit při návrhu kontraktu služby. Pokud operace obdrží nebo vrátí velké objemy dat, měli byste zvážit, tato data, aby se zabránilo využití velkého množství paměti z důvodu ukládání do vyrovnávací paměti zpráv vstupních nebo výstupních datových proudů. K datům datového proudu, parametr, který obsahuje, že data musí být parametr pouze ve zprávě. Například pokud je vstupní zpráva má Streamovat, operaci musí mít přesně jeden vstupní parametr. Podobně pokud zpráva výstup je odesílání, operaci musí mít právě jednu výstupní parametr nebo návratovou hodnotu. V případě, parametr nebo return hodnotě typ musí být buď `Stream`, `Message`, nebo `IXmlSerializable`. Zde je použit v této ukázce streamování kontrakt služby.  
  
```  
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
  
 `GetStream` Operace přijímá některé vstupní data jako řetězec, který je uloží do vyrovnávací paměti a vrátí `Stream`, který je prostřednictvím datového proudu. Naopak `UploadStream` přebírá `Stream` (streamování) a vrátí `bool` (uložená do vyrovnávací paměti). `EchoStream` provede a vrátí `Stream` je příkladem operace, jejichž vstup a výstup zprávy jsou obě streamování. Nakonec `GetReversedStream` přebere žádné vstupy a vrátí `Stream` (streamování).  
  
## <a name="enabling-streamed-transfers"></a>Povolení přenášené datovými proudy přenosů  
 Definování kontraktů operaci výše popsané poskytuje streamování na úrovni modelu programování. Pokud zastavíte existuje, přenos stále ukládá do vyrovnávací paměti obsahu celé zprávy. Pokud chcete povolit přenos streamování, vyberte režim přenosu u prvku vazby přenosu. Obsahuje prvku vazby `TransferMode` vlastnost, která může být nastaven na `Buffered`, `Streamed`, `StreamedRequest`, nebo `StreamedResponse`. Nastavení režimu přenosu `Streamed` umožňuje streamování komunikace v obou směrech. Nastavení režimu přenosu `StreamedRequest` nebo `StreamedResponse` umožňuje streamování komunikaci v požadavek nebo odpověď, a to v uvedeném pořadí.  
  
 `basicHttpBinding` Zpřístupní `TransferMode` vlastnost vazby stejně `NetTcpBinding` a `NetNamedPipeBinding`. Pro ostatní přenosy musíte vytvořit vlastní vazby nastavit režim přenosu.  
  
 Následující kód konfigurace z ukázky ukazuje nastavení `TransferMode` vlastnost streamování na `basicHttpBinding` a vlastní vazby HTTP:  
  
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
  
 Kromě nastavení `transferMode` k `Streamed`, předchozí sady konfigurace kódu `maxReceivedMessageSize` na 64 MB. Jako mechanismus obrany `maxReceivedMessageSize` přijímat zakončení na maximální povolenou velikost zprávy v místech. Výchozí hodnota `maxReceivedMessageSize` je 64 KB, který je obvykle příliš nízká pro streamování scénáře.  
  
## <a name="processing-data-as-it-is-streamed"></a>Zpracování dat, jako je streamování  
 Operace `GetStream`, `UploadStream` a `EchoStream` všechny řešení odesílání dat přímo ze souboru nebo ukládání dat přijatých přímo do souboru. Ale v některých případech je potřeba odesílat nebo přijímat velké objemy dat a provedení některých zpracování na bloky dat, jako je právě odesílané nebo přijímané. Jeden způsob, jak vyřešit takových scénářů je napsat vlastní datový proud (třídy odvozené z <xref:System.IO.Stream>), zpracovává data, jako je číst nebo zapisovat. `GetReversedStream` Operace a `ReverseStream` třídy jsou příklady.  
  
 `GetReversedStream` vytvoří a vrátí novou instanci třídy `ReverseStream`. Vlastní zpracování se stane, protože systém přečte z tohoto `ReverseStream` objektu. `ReverseStream.Read` Implementace čte blok bajtů z podkladový soubor, obrátí je a pak vrátí odstínech bajtů. Toto není reverse celý soubor obsahu; současně se obrátí jeden blok bajtů. Jedná se o příklad zobrazit, jak můžete provádět zpracování datového proudu, jak se obsah číst nebo zapisovat z a do datového proudu.  
  
```  
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
 Ke spuštění ukázky, nejprve vytvořte službu a klienta podle následujících pokynů na konci tohoto dokumentu. Spusťte službu a klienta ve dvou různých konzoly windows. Když se klient spustí, se zobrazí výzvu k stiskněte klávesu ENTER, pokud služba je připravena. Klient pak zavolá metodu `GetStream()`, `UploadStream()` a `GetReversedStream()` nejprve přes protokol HTTP a pak přes protokol TCP. Tady je příklad výstup ze služby následuje příklad výstupu z klienta:  
  
 Výstup služby:  
  
```  
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
  
```  
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
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!NOTE]
>  Pokud používáte Svcutil.exe znovu vygenerovat konfigurace pro tuto ukázku, nezapomeňte změnit název koncového bodu v konfiguraci klienta tak, aby odpovídaly kódu klienta.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Stream`  
  
## <a name="see-also"></a>Viz také

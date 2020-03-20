---
title: Kódování MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: 83dbe9e51da1cc9e55bfffb862e2601d70fc7695
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144380"
---
# <a name="mtom-encoding"></a>Kódování MTOM
Tato ukázka ukazuje použití kódování zprávy mechanismus optimalizace přenosu zpráv (MTOM) s WSHttpBinding. MTOM je mechanismus pro přenos velkých binárních příloh s SOAP zprávy jako nezpracované bajty, umožňující menší zprávy.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 Ve výchozím nastavení wshttpbinding odesílá a přijímá zprávy jako normální textový XML. Chcete-li povolit odesílání a `messageEncoding` přijímání zpráv MTOM, nastavte atribut na konfiguraci vazby (jako `MessageEncoding` v následujícím příkladu kódu) nebo přímo na vazbě pomocí vlastnosti. Služba nebo klient nyní může odesílat a přijímat zprávy MTOM.  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 Kodér MTOM může optimalizovat pole bajtů a datových proudů. V této ukázce `Stream` operace používá parametr a proto může být optimalizována.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 Smlouva zvolená pro tento vzorek přenáší binární data do služby a přijímá počet bajtů odeslaných jako vrácená hodnota. Když je služba nainstalována a klient je spuštěn, vytiskne číslo 1000, což znamená, že bylo přijato všech 1000 bajtů. Zbývající část výstupu obsahuje optimalizované a neoptimalizované velikosti zpráv pro různé datové části.  
  
```console
Output:  
1000  
  
Text encoding with a 100 byte payload: 433  
MTOM encoding with a 100 byte payload: 912  
  
Text encoding with a 1000 byte payload: 1633  
MTOM encoding with a 1000 byte payload: 2080  
  
Text encoding with a 10000 byte payload: 13633  
MTOM encoding with a 10000 byte payload: 11080  
  
Text encoding with a 100000 byte payload: 133633  
MTOM encoding with a 100000 byte payload: 101080  
  
Text encoding with a 1000000 byte payload: 1333633  
MTOM encoding with a 1000000 byte payload: 1001080  
  
Press <ENTER> to terminate client.  
```  
  
 Účelem použití MTOM je optimalizovat přenos velkých binárních datových částí. Odesílání zprávy SOAP pomocí MTOM má znatelnou režii pro malé binární datové části, ale stane se velké úspory při jejich růstu přes několik tisíc bajtů. Důvodem je, že normální text XML kóduje binární data pomocí Base64, který vyžaduje čtyři znaky pro každé tři bajty a zvyšuje velikost dat o jednu třetinu. MTOM je schopen přenášet binární data jako nezpracované bajty, ukládání kódování / dekódování čas a výsledné je menší zprávy. Práh několika tisíc bajtů je malý ve srovnání s dnešními obchodními dokumenty a digitálními fotografiemi.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  

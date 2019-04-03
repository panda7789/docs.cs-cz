---
title: Kódování MTOM
ms.date: 03/30/2017
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
ms.openlocfilehash: aa24a8f8553ceb035e5fc9c0c6094b1279711674
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58839831"
---
# <a name="mtom-encoding"></a>Kódování MTOM
Tento příklad ukazuje použití kódování s WSHttpBinding zprávy zpráv přenosu optimalizace mechanismus (MTOM). MTOM je mechanismus pro předávání velké binární jejich přílohy pomocí zprávy protokolu SOAP jako nezpracovaný bajtů, umožňuje menší zprávy.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 Ve výchozím nastavení, odešle WSHttpBinding a přijaté zprávy jako normální text XML. Pokud chcete povolit posílat a přijímat zprávy MTOM, nastavte `messageEncoding` atribut u vazby konfigurace (viz následující příklad kódu), nebo přímo u vazby pomocí `MessageEncoding` vlastnost. Služba nebo klient teď můžete odesílat a přijímat zprávy MTOM.  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 Kodér MTOM můžete optimalizovat pole bajtů a datových proudů. V této ukázce se používá operaci `Stream` parametrů a proto se dá optimalizovat.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 Kontrakt pro tuto ukázku zvolili přenáší binárních dat ve službě a přijímá počet bajtů odeslat jako návratovou hodnotu. Když je služba nainstalována a klient je spuštěn, vytiskne číslo 1 000, což znamená, že byly přijaty všechny 1 000 bajtů. Zbývající část ve výstupu zobrazit seznam velikostí optimalizované a neoptimalizované zprávu pro různé datové části.  
  
```  
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
  
 Účelem použití MTOM je k optimalizaci přenosu velké binární datové části. Odeslání zprávy protokolu SOAP pomocí MTOM má znatelný režijní náklady pro malé binární datové části, ale změní na velké úspory, pokud se jejich průběhu několika tisíc bajtů. Důvodem je, že normální text XML zakóduje binární data pomocí kódování Base64, který vyžaduje čtyři znaky pro každých třech bajtech a zvýší množství dat o jednu třetinu. Výsledkem je menší zprávy MTOM je moct přenášet binárních dat jako nezpracovaný bajtů, úspory času kódování/dekódování. Prahové hodnoty několika tisíc bajtů je malé ve srovnání s dnešní firemní dokumenty a digitální fotografie.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  

---
title: Kódování MTOM
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 820e316f-4ee1-4eb5-ae38-b6a536e8a14f
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d826b5f2973ac451b3943fd78b661093906c72ad
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2018
---
# <a name="mtom-encoding"></a>Kódování MTOM
Tento příklad znázorňuje použití kódování s WSHttpBinding zprávy zpráva přenosu optimalizace mechanismus (MTOM). MTOM je mechanismus pro přenos velkých binární příloh protokolu SOAP zprávy nezpracovaná bajtů, umožňuje pro menší zprávy.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\MTOM`  
  
 Ve výchozím nastavení, odešle WSHttpBinding a přijaté zprávy jako běžný text XML. Chcete-li povolit odesílání a přijímání zpráv MTOM, nastavte `messageEncoding` atribut v konfiguraci vazby (jako v následujícím příkladu kódu), nebo přímo na vazbu pomocí `MessageEncoding` vlastnost. Služba nebo klienta můžete nyní odesílat a přijímat zprávy MTOM.  
  
```xml  
<wsHttpBinding>  
  <binding name="WSHttpBinding_IUpload" messageEncoding="Mtom" />  
</wsHttpBinding>  
```  
  
 Kodér MTOM můžete optimalizovat pole bajtů a datových proudů. V této ukázce používá operaci `Stream` parametr a proto může být optimalizované.  

```csharp
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
  public interface IUpload  
  {  
      [OperationContract]  
      int Upload(Stream data);  
  }  
```
  
 Kontrakt zvolené pro tuto ukázku odesílá binární data do služby a získá počet bajtů odesílané jako návratovou hodnotu. Když je služba nainstalována a klient je spuštěn, vytiskne číslo 1 000, což znamená, že bylo přijato všechny 1 000 bajtů. Zbývající část výstupu uvádí zprávy optimalizovaným a Neaktivní optimalizované velikosti pro různé datové části.  
  
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
  
 Účelem pro používání MTOM je za účelem optimalizace přenos velkých binární datové části. Odesílání protokolu SOAP zprávy pomocí MTOM má znatelné režijní náklady pro malé binární datové části, ale změní skvělé úspory, pokud jejich výskytu prostřednictvím několika tisíc bajtů. Důvodem je, že běžného textu XML zakóduje binární data pomocí Base64, který vyžaduje čtyři znaky pro každé tři bajtů a zvyšuje velikost dat o jednu třetinu. MTOM je schopen přenášet binární data nezpracovaná bajtů, což šetří čas kódování a dekódování a výsledná je menší zprávy. Prahové hodnoty několika tisíc bajtů je malé ve srovnání s dnešní obchodní dokumenty a digitální fotografie.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
3.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také

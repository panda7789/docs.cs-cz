---
title: Trasa podle textu
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: 3f6be962db2d07bef3a7adc714e9f4e72d621d37
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59172312"
---
# <a name="route-by-body"></a>Trasa podle textu
Tento příklad ukazuje, jak implementovat službu, která přijímá zprávy objekty s žádnou akci SOAP. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje. Služba implementuje jediného `Calculate` operace, která přijímá <xref:System.ServiceModel.Channels.Message> požadavku parametr a vrátí <xref:System.ServiceModel.Channels.Message> odpovědi.  
  
 V této ukázce klient je konzolová aplikace (.exe) a služba je hostována ve službě IIS.  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Ukázce odeslání zprávy na základě obsahu těla. Integrované zpráva odeslání mechanismus modelu služby Windows Communication Foundation (WCF) je založen na zprávu akce. Existují však mnoho existující webové služby, které definují všechny své operace s akcí = "". Není možné vytvářet službě založené na souboru WSDL, který udržuje odeslání žádosti o zprávy založené na informace o akci. V této ukázce kontraktu služby, který je založen na WSDL (jazyka WSDL je součástí, která je součástí vzorku. Service.wsdl). Kontrakt služby je kalkulačky, podobný tomu použitému v [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Ale `[OperationContract]` Určuje `Action=""` pro všechny operace.  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples"),    
                 XmlSerializerFormat, DispatchByBodyBehavior]  
    public interface ICalculator  
    {  
        [OperationContract(Action="")]  
        double Add(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Subtract(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Multiply(double n1, double n2);  
        [OperationContract(Action = "")]  
        double Divide(double n1, double n2);  
    }  
```  
  
 Daný kontrakt služby vyžaduje vlastní chování `DispatchByBodyBehavior` aby byly povolené zprávy k odeslání mezi operacemi. Toto chování odeslání inicializuje `DispatchByBodyElementOperationSelector` selektor vlastní operace s tabulkou názvy operací s klíči QName obálky odpovídajících prvků. `DispatchByBodyElementOperationSelector` vypadá v počáteční značce prvního podřízeného obsahu a vybere operace pomocí tabulky už jsme zmínili.  
  
 Klient používá automaticky generovaný z WSDL exportovali pomocí služby proxy [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 Vzhledem k tomu, že mají akce všechny operace prázdný nemá žádný vliv na kód klienta, s výjimkou parametry akce v proxy serveru automaticky generovány.  
  
 Klientský kód provede několik výpočtů. Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně Klient vypnutí klient.  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  

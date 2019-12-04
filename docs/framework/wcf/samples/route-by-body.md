---
title: Trasa podle textu
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: 5b6a9ec6c862e501e6d04c27391a601a7cf6e66a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716374"
---
# <a name="route-by-body"></a>Trasa podle textu
Tato ukázka předvádí, jak implementovat službu, která přijímá objekty zpráv s jakoukoli akcí SOAP. Tato ukázka je založená na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) , která implementuje službu kalkulačky. Služba implementuje jednu operaci `Calculate`, která přijímá parametr žádosti <xref:System.ServiceModel.Channels.Message> a vrátí odpověď <xref:System.ServiceModel.Channels.Message>.  
  
 V této ukázce je klient Konzolová aplikace (. exe) a služba je hostovaná ve službě IIS.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Ukázka znázorňuje odeslání zprávy na základě obsahu těla. Integrovaný mechanismus odeslání zprávy modelu služby Windows Communication Foundation (WCF) je založen na akcích zprávy. Existuje však mnoho existujících webových služeb, které definují všechny své operace pomocí akce = "". Není možné vytvořit službu založenou na jazyce WSDL, která zajišťuje odesílání zpráv s požadavky na základě informací o akci. Tato ukázka demonstruje kontrakt služby, který je založen na jazyce WSDL (WSDL je obsažen v souboru Service. WSDL, který je součástí ukázky). Kontrakt služby je kalkulačka, podobně jako ta, která se používá v [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). `[OperationContract]` však určuje `Action=""` pro všechny operace.  
  
```csharp  
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
  
 U kontraktu vyžaduje služba `DispatchByBodyBehavior` vlastní chování odeslání, aby bylo možné mezi operacemi odesílat zprávy. Toto chování při odeslání inicializuje selektor `DispatchByBodyElementOperationSelector` vlastní operace s tabulkou názvů operací, na které se odkazuje pomocí QName odpovídajících prvků obálky. `DispatchByBodyElementOperationSelector` se podívá na počáteční značku prvního podřízeného objektu a vybere operaci s výše zmíněnou tabulkou.  
  
 Klient používá proxy automaticky generovaný ze třídy WSDL exportované službou pomocí [nástroje Svcutil. exe](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
```console  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 Fakt, že akce všech operací nejsou prázdné, nemá žádný vliv na kód klienta, s výjimkou parametrů akce v automaticky generovaném proxy serveru.  
  
 Kód klienta provádí několik výpočtů. Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.  
  
```console
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  

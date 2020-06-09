---
title: Trasa podle textu
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: 146baf806f4922f5e3ddd92a762772786e61d443
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84594592"
---
# <a name="route-by-body"></a>Trasa podle textu
Tato ukázka předvádí, jak implementovat službu, která přijímá objekty zpráv s jakoukoli akcí SOAP. Tato ukázka je založená na [Začínáme](getting-started-sample.md) , která implementuje službu kalkulačky. Služba implementuje jednu `Calculate` operaci, která přijme <xref:System.ServiceModel.Channels.Message> parametr žádosti a vrátí <xref:System.ServiceModel.Channels.Message> odpověď.  
  
 V této ukázce je klient Konzolová aplikace (. exe) a služba je hostovaná ve službě IIS.  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Ukázka znázorňuje odeslání zprávy na základě obsahu těla. Integrovaný mechanismus odeslání zprávy modelu služby Windows Communication Foundation (WCF) je založen na akcích zprávy. Existuje však mnoho existujících webových služeb, které definují všechny své operace pomocí akce = "". Není možné vytvořit službu založenou na jazyce WSDL, která zajišťuje odesílání zpráv s požadavky na základě informací o akci. Tato ukázka demonstruje kontrakt služby, který je založen na jazyce WSDL (WSDL je obsažen v souboru Service. WSDL, který je součástí ukázky). Kontrakt služby je kalkulačka, podobně jako ta, která se používá v [Začínáme](getting-started-sample.md). Nicméně `[OperationContract]` Určuje `Action=""` pro všechny operace.  
  
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
  
 Vzhledem k tomu, že služba vyžaduje vlastní chování odesílání, `DispatchByBodyBehavior` aby bylo možné mezi operacemi odesílat zprávy. Toto chování při zpracování inicializuje `DispatchByBodyElementOperationSelector` selektor vlastních operací s tabulkou názvů operací, které jsou na základě QName odpovídajících prvků obálky. `DispatchByBodyElementOperationSelector`vyhledá počáteční značku prvního podřízeného textu a vybere operaci pomocí výše zmíněné tabulky.  
  
 Klient používá proxy automaticky generovaný ze třídy WSDL exportované službou pomocí [nástroje Svcutil. exe](../servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
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
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  

---
title: Trasa podle textu
ms.date: 03/30/2017
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
ms.openlocfilehash: c3f4b19e646a6a9716d2264a3969b339208c60a1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144185"
---
# <a name="route-by-body"></a>Trasa podle textu
Tato ukázka ukazuje, jak implementovat službu, která přijímá objekty zprávy s jakoukoli akcí SOAP. Tato ukázka je založena na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje službu kalkulačky. Služba implementuje `Calculate` jednu operaci, <xref:System.ServiceModel.Channels.Message> která přijímá <xref:System.ServiceModel.Channels.Message> parametr požadavku a vrací odpověď.  
  
 V této ukázce je klient konzolovou aplikací (.exe) a služba je hostována ve službě IIS.  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
 Ukázka ukazuje odeslání zprávy na základě obsahu těla. Vestavěný Windows Communication Foundation (WCF) mechanismus odesílání zpráv modelu služby je založen na akcích zprávy. Existuje však mnoho existujících webových služeb, které definují všechny své operace s Action="". Není možné vytvořit službu založenou na WSDL, která udržuje odesílání zpráv požadavků na základě informací akce. Tato ukázka ukazuje servisní smlouvy, která je založena na WSDL (WSDL je obsažen v Service.wsdl, který je součástí vzorku). Servisní smlouva je Kalkulačka, podobná té, která se používá v [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Nicméně `[OperationContract]` určuje `Action=""` pro všechny operace.  
  
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
  
 Dané smlouvy, služba vyžaduje vlastní `DispatchByBodyBehavior` odeslání chování povolit zprávy, které mají být odesílány mezi operacemi. Toto chování odeslání inicializuje `DispatchByBodyElementOperationSelector` vlastní selektor operace s tabulkou názvů operací zakódovaných QName příslušných prvků obálky. `DispatchByBodyElementOperationSelector`vyhledá počáteční značku první podřízené položky těla a vybere operaci pomocí výše uvedené tabulky.  
  
 Klient používá proxy automaticky generovaný z WSDL exportované službou pomocí [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
```console  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 Skutečnost, že akce všech operací jsou prázdné nemá žádný vliv na kód klienta, s výjimkou Action parametry v automaticky generované proxy.  
  
 Kód klienta provádí několik výpočtů. Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi. Stisknutím klávesy ENTER v okně klienta vypněte klienta.  
  
```console
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  

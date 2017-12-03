---
title: Trasa podle textu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 07a6fc3b-c360-42e0-b663-3d0f22cf4502
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 09e274bcbc1995dcd6b2c21e0114aa4a865f4129
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="route-by-body"></a>Trasa podle textu
Tento příklad znázorňuje způsob implementace služba, která přijímá zprávy objekty s žádnou akci protokolu SOAP. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje. Služba implementuje jedné `Calculate` operace, která přijímá <xref:System.ServiceModel.Channels.Message> požadavků parametr a vrátí <xref:System.ServiceModel.Channels.Message> odpovědi.  
  
 V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná ve službě IIS.  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
 Ukázka ukazuje odesílání zpráv na základě obsahu textu. Integrované [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] mechanismu odesílání zpráv model služby je na základě zprávy akce. Existují však mnoho existujících webových služeb, které definují všechny své operace pomocí akce = "". Není možné vytvořit služby založené na jazyce WSDL, který udržuje odeslání zprávy s požadavky na informace o akci. Tento příklad znázorňuje kontraktu služby, která je založena na WSDL (schématu WSDL je součástí Service.wsdl, který se dodává s ukázkou). Kontrakt služby je kalkulačky, podobně jako používaný v [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Ale `[OperationContract]` Určuje `Action=""` pro všechny operace.  
  
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
  
 Zadána kontraktu služby vyžaduje vlastní odesílání chování `DispatchByBodyBehavior` umožňující zpráv, které mají být odeslány mezi operacemi. Toto chování odesílání inicializuje `DispatchByBodyElementOperationSelector` selektor vlastní operace s tabulkou názvů operace s klíči QName elementů příslušných obálku. `DispatchByBodyElementOperationSelector`u počáteční značky prvního podřízeného obsahu vyhledá a vybere operaci v tabulce výše.  
  
 Klient používá automaticky generovaný z WSDL exportovali pomocí služby proxy [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
```  
svcutil.exe  /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples /uxs http://localhost/servicemodelsamples/service.svc?wsdl /out:generatedProxy.cs  
```  
  
 Skutečnost, že akce všechny operace jsou prázdné nemá žádný vliv na kód klienta, s výjimkou parametrů akce v automaticky generovaných proxy.  
  
 Kód klienta provede několik výpočtů. Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně klienta vypnout klienta.  
  
```  
Add(100, 15.99) = 115.99  
Subtract(145, 76.54) = 68.46  
Multiply(9, 81.25) = 731.25  
Divide(22, 7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Interop\RouteByBody`  
  
## <a name="see-also"></a>Viz také

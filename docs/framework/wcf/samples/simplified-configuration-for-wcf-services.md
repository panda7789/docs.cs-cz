---
title: Zjednodušená konfigurace pro služby WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 80e2ac83ec0e07176d6afe6d34c63fb4d8e836d1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="simplified-configuration-for-wcf-services"></a>Zjednodušená konfigurace pro služby WCF
Tento příklad ukazuje, jak implementovat a nastavení typické služby a klienta pomocí služby Windows Communication Foundation (WCF). Tato ukázka je základem pro všechny ostatní vzorky základní technologie.  
  
 Tato služba, která zpřístupňuje koncový bod pro komunikaci se službou, používá zjednodušená konfigurace v [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]. Před verzí [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], koncový bod je obvykle definováno v konfiguračním souboru (Web.config), jak je znázorněno v následujícím příkladu kódu konfigurace.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright ©) Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <services>  
      <service name="Microsoft.Samples.GettingStarted.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <endpoint address="" binding="basicHttpBinding" contract="ICalculator"/>  
        <endpoint address="mex" binding="mexHttpBinding" contract="IMetadataExchange"/>  
      </service>  
    </services>  
  </system.serviceModel>  
</configuration>  
```  
  
 V [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], `<service>` prvek je volitelný. Pokud služby nedefinuje žádné koncové body, koncový bod pro každou základní adresa a kontrakt implementována jsou přidány do služby. Základní adresa je přidán do názvu kontraktu určit koncový bod a vazba je dáno schéma adresy. Následující příklad kódu ukazuje zjednodušené konfigurační soubor. Podle konfigurace, služba je přístupná na http://localhost/servicemodelsamples/service.svc klientem na stejném počítači. Pro klienty ve vzdálených počítačích pro přístup ke službě musí zadat název plně kvalifikované domény místo localhost. Služba nevystavuje metadata ve výchozím nastavení. Jako takový službu Zapne <xref:System.ServiceModel.Description.ServiceMetadataBehavior> chování.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<!-- Copyright © Microsoft Corporation.  All Rights Reserved. -->  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="">  
          <serviceMetadata httpGetEnabled="True"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavte řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku pomocí následujících kroků:  
  
    1.  Klikněte pravým tlačítkem **služby** projektu a vyberte **nastavit jako spouštěný projekt**, stiskněte **Ctrl + F5**.  
  
    2.  Počkejte, až bude výstup konzoly potvrdí, že služba nahoru a spuštěna.  
  
    3.  Klikněte pravým tlačítkem **klienta** projektu a vyberte **nastavit jako spouštěný projekt**, stiskněte **Ctrl + F5**.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Viz také  
 [Ukázky správy AppFabric](http://go.microsoft.com/fwlink/?LinkId=193960)  
 [Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)

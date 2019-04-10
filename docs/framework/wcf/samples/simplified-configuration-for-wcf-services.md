---
title: Zjednodušená konfigurace pro služby WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 47af8dcba35ba31f25597c946596b0cbcac93b4d
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59304256"
---
# <a name="simplified-configuration-for-wcf-services"></a>Zjednodušená konfigurace pro služby WCF
Tento příklad ukazuje, jak implementovat a konfigurovat typické službu a klienta s použitím Windows Communication Foundation (WCF). Tato ukázka představuje základ pro všechny další ukázky základní technologii.  
  
 Tato služba, která zpřístupňuje koncový bod pro komunikaci se službou, využívá zjednodušenou konfiguraci v [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)]. Před verzí [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], koncový bod je obvykle definováno v souboru konfigurace (Web.config), jak je znázorněno v následujícím příkladu kódu konfigurace.  
  
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
  
 V [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)], `<service>` element je volitelné. Když služba nedefinuje žádné koncové body, koncový bod pro každou základní adresu a implementovat kontrakt jsou přidány do služby. Základní adresa je připojeným k názvu kontraktu určit koncový bod a vazbu určuje schéma adres. Následující příklad kódu ukazuje zjednodušený konfigurační soubor. Podle konfigurace, služba může získat přístup na adrese `http://localhost/servicemodelsamples/service.svc` klientem na stejném počítači. Pro klienty ve vzdálených počítačích pro přístup ke službě musí se zadat název plně kvalifikované domény místo localhost. Služba nevystavuje metadata ve výchozím nastavení. V důsledku toho služba Zapne <xref:System.ServiceModel.Description.ServiceMetadataBehavior> chování.  
  
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
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Abyste mohli sestavit řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Spusťte ukázku pomocí následujících kroků:  
  
    1.  Klikněte pravým tlačítkem myši **služby** projektu a vyberte **nastavit jako spouštěný projekt**, stiskněte klávesu **Ctrl + F5**.  
  
    2.  Vyčkat, než bude výstup konzoly potvrzení, zda je služba nahoru a spouštění.  
  
    3.  Klikněte pravým tlačítkem myši **klienta** projektu a vyberte **nastavit jako spouštěný projekt**, stiskněte klávesu **Ctrl + F5**.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Viz také:

- [Ukázky správy AppFabric](https://go.microsoft.com/fwlink/?LinkId=193960)
- [Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)

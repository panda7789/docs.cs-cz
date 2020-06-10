---
title: Zjednodušená konfigurace pro služby WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: 61720fff957bfe7a13da1d7498487342b2ee234c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84584100"
---
# <a name="simplified-configuration-for-wcf-services"></a>Zjednodušená konfigurace pro služby WCF
Tato ukázka předvádí, jak implementovat a nakonfigurovat typickou službu a klienta pomocí Windows Communication Foundation (WCF). Tato ukázka je základem pro všechny ostatní základní ukázkové technologie.  
  
 Tato služba, která zpřístupňuje koncový bod pro komunikaci se službou, používá zjednodušenou konfiguraci v .NET Framework 4. Před .NET Framework 4 je koncový bod obvykle definován v konfiguračním souboru (Web. config), jak je znázorněno v následujícím příkladu kódu konfigurace.  
  
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
  
 V .NET Framework 4 `<service>` je element volitelný. Pokud služba nedefinuje žádné koncové body, do služby se přidají koncový bod pro každou základní adresu a implementaci smlouvy. Základní adresa se připojí k názvu kontraktu a určí koncový bod a vazba je určena schématem adres. Následující příklad kódu ukazuje zjednodušený konfigurační soubor. Jak je nakonfigurováno, může být služba k dispozici `http://localhost/servicemodelsamples/service.svc` klientovi ve stejném počítači. Aby mohli klienti na vzdálených počítačích přistupovat ke službě, je třeba zadat plně kvalifikovaný název domény namísto localhost. Služba ve výchozím nastavení nevystavuje metadata. V takovém případě služba toto chování zapne <xref:System.ServiceModel.Description.ServiceMetadataBehavior> .  
  
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
  
### <a name="to-use-this-sample"></a>Použití této ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Při sestavování řešení postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Spusťte ukázku pomocí následujících kroků:  
  
    1. Klikněte pravým tlačítkem myši na projekt **služby** a vyberte **nastavit jako spouštěný projekt**a potom stiskněte klávesy **CTRL + F5**.  
  
    2. Počkejte na výstup konzoly s potvrzením, že je služba spuštěná.  
  
    3. Klikněte pravým tlačítkem myši na projekt **klienta** a vyberte **nastavit jako spouštěný projekt**a potom stiskněte klávesy **CTRL + F5**.  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Viz také

- [Ukázky správy technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))
- [Zjednodušená konfigurace](../simplified-configuration.md)

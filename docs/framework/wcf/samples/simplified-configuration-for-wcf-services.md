---
title: Zjednodušená konfigurace pro služby WCF
ms.date: 03/30/2017
ms.assetid: 1e39ec25-18a3-4fdc-b6a3-9dfafbd60112
ms.openlocfilehash: f3c4df5ae3fe5426c8b26142807f16b60db001c6
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183356"
---
# <a name="simplified-configuration-for-wcf-services"></a>Zjednodušená konfigurace pro služby WCF
Tato ukázka ukazuje, jak implementovat a nakonfigurovat typické služby a klienta pomocí Windows Communication Foundation (WCF). Tento vzorek je základem pro všechny ostatní základní vzorky technologie.  
  
 Tato služba, která zveřejňuje koncový bod pro komunikaci se službou, používá zjednodušenou konfiguraci v rozhraní .NET Framework 4. Před rozhraním .NET Framework 4 je koncový bod obvykle definován v konfiguračním souboru (Web.config), jak je znázorněno v následujícím příkladu konfiguračního kódu.  
  
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
  
 V rozhraní .NET `<service>` Framework 4 je prvek volitelný. Pokud služba nedefinuje žádné koncové body, koncový bod pro každou základní adresu a implementovanou smlouvu jsou přidány do služby. Základní adresa je připojena k názvu smlouvy k určení koncového bodu a vazba je určena schématem adresy. Následující příklad kódu ukazuje zjednodušený konfigurační soubor. Podle konfigurace, služba může být `http://localhost/servicemodelsamples/service.svc` přístupná klientem ve stejném počítači. Pro klienty ve vzdálených počítačích pro přístup ke službě musí být zadán plně kvalifikovaný název domény namísto localhost. Služba nezveřejňuje metadata ve výchozím nastavení. Jako takové služba zapne <xref:System.ServiceModel.Description.ServiceMetadataBehavior> chování.  
  
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
  
### <a name="to-use-this-sample"></a>Chcete-li použít tento vzorek  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Ukázku spusťte takto:  
  
    1. Klepněte pravým tlačítkem myši na projekt **servisu** a vyberte **příkaz Nastavit jako projekt spuštění**a stiskněte **kombinaci kláves Ctrl+F5**.  
  
    2. Počkejte na výstup konzoly potvrzující, že služba je v provozu.  
  
    3. Klepněte pravým tlačítkem myši na **projekt Klient** a vyberte příkaz Nastavit jako **počáteční projekt**a stiskněte **kombinaci kláves Ctrl+F5**.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\ConfigSimplificationIn40`  
  
## <a name="see-also"></a>Viz také

- [Ukázky správy appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383405(v=azure.10))
- [Zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md)

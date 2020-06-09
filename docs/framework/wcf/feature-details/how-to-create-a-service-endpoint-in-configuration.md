---
title: 'Postupy: Vytvoření koncového bodu služby v konfiguraci'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 56b29da0c147eb9e73a08e2875e33e384da729ed
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598915"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a>Postupy: Vytvoření koncového bodu služby v konfiguraci
Koncové body poskytují klientům přístup k funkcím, které nabízí služba Windows Communication Foundation (WCF). Můžete definovat jeden nebo více koncových bodů pro službu pomocí kombinace relativních a absolutních adres koncového bodu, nebo pokud nedefinujete žádné koncové body služby, modul runtime pro vás standardně poskytne výchozí hodnoty. V tomto tématu se dozvíte, jak přidat koncové body pomocí konfiguračního souboru, který obsahuje relativní i absolutní adresy.  
  
## <a name="example"></a>Příklad  
 Následující konfigurace služby určuje základní adresu a pět koncových bodů.  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <services>  
    <!-- This section is optional with the default configuration introduced in .NET Framework 4. -->  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <endpoint address=""  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="/test"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="http://localhost:8001/hello/servicemodelsamples"  
                  binding="wsHttpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
                  binding="netTcpBinding"  
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />  
        <!-- the mex endpoint is another relative address exposed at   
             http://localhost:8000/ServiceModelSamples/service/mex -->  
        <endpoint address="mex"  
                  binding="mexHttpBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```  
  
## <a name="example"></a>Příklad  
 Základní adresa je určena pomocí `add` elementu v části Služba/Hostitel/adres BaseAddresses, jak je znázorněno v následující ukázce.  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a>Příklad  
 První definice koncového bodu zobrazená v následujícím příkladu určuje relativní adresu, což znamená, že adresa koncového bodu je kombinací základní adresy a relativní adresy podle pravidel složení identifikátoru URI (Uniform Resource Identifier). Relativní adresa je prázdná (""), takže adresa koncového bodu je stejná jako základní adresa. Skutečná adresa koncového bodu je `http://localhost:8000/servicemodelsamples/service` .  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Příklad  
 Druhá definice koncového bodu také určuje relativní adresu, jak je znázorněno v následující ukázkové konfiguraci. Relativní adresa "test" se připojí k základní adrese. Skutečná adresa koncového bodu je `http://localhost:8000/servicemodelsamples/service/test` .  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Příklad  
 Třetí definice koncového bodu určuje absolutní adresu, jak je znázorněno v následující ukázkové konfiguraci. Základní adresa nehraje v adrese žádnou roli. Skutečná adresa koncového bodu je `http://localhost:8001/hello/servicemodelsamples` .  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Příklad  
 Čtvrtá adresa koncového bodu určuje absolutní adresu a jiný přenos – TCP. Základní adresa nehraje v adrese žádnou roli. Skutečná adresa koncového bodu je NET. TCP://localhost: 9000/servicemodelsamples/service.  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Příklad  
 Chcete-li použít výchozí koncové body poskytované modulem runtime, nezadávejte koncové body služby buď v kódu, nebo v konfiguračním souboru. V tomto příkladu modul runtime vytvoří výchozí koncové body při otevření služby. Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](../simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../samples/simplified-configuration-for-wcf-services.md).  
  
```xml  
<configuration>  
  
  <appSettings>  
    <!-- use appSetting to configure base address provided by host -->  
    <add key="baseAddress" value="http://localhost:8000/servicemodelsamples/service" />  
  </appSettings>  
  
  <system.serviceModel>  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  
  </system.serviceModel>  
  
</configuration>  
```

---
title: 'Postupy: vytvoření koncového bodu služby v konfiguraci'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 63a40576b805952197cec5af2f89a5dc4b5d3545
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850593"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a>Postupy: vytvoření koncového bodu služby v konfiguraci
Koncové body mají klienti obdržet přístup k funkcím, které nabízí služba Windows Communication Foundation (WCF). Můžete definovat jeden nebo víc koncových bodů služby pomocí kombinace relativní a absolutní koncový bod adresy, nebo pokud nejsou definovány žádné koncové body služby, modul runtime, poskytuje některé ve výchozím nastavení za vás. Toto téma ukazuje, jak přidat koncové body pomocí konfiguračního souboru, které obsahují relativní a absolutní adresu.  
  
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
    <!-- This section is optional with the default configuration introduced  
         in .NET Framework 4. -->  
      <service  
          name="Microsoft.ServiceModel.Samples.CalculatorService">  
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
 Základní adresa je zadána pomocí `add` element v rámci služby/hostitele/baseAddresses, jak je znázorněno v následujícím příkladu.  
  
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
 První definice koncového bodu je znázorněno v následujícím příkladu určuje relativní adresa, což znamená, že adresa koncového bodu je kombinací základní adresu a relativní adresu dle pravidel složení identifikátor URI (Uniform Resource). Relativní adresa je prázdná (""), takže adresu koncového bodu je stejný jako základní adresu. Adresa skutečný koncový bod je `http://localhost:8000/servicemodelsamples/service`.  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Příklad  
 Druhá definice koncového bodu také určuje relativní adresa, jak je znázorněno v následující ukázková konfigurace. Relativní adresa "test", se připojí k základní adrese. Adresa skutečný koncový bod je `http://localhost:8000/servicemodelsamples/service/test`.  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Příklad  
 Třetí definice koncového bodu určuje absolutní adresu, jak je znázorněno v následující ukázková konfigurace. Základní adresa hraje žádná role v adrese. Adresa skutečný koncový bod je `http://localhost:8001/hello/servicemodelsamples`.  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Příklad  
 Na čtvrté adresu koncového bodu určuje absolutní adresu a různé přenosové – TCP. Základní adresa hraje žádná role v adrese. Adresa skutečný koncový bod je NET.TCP://localhost: 9000/servicemodelsamples/služby.  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a>Příklad  
 Pokud chcete použít výchozí koncové body poskytovaný modulem runtime, nezadávejte žádné koncové body služby v kódu nebo konfiguračního souboru. V tomto příkladu modul runtime vytvoří výchozí koncové body při otevření služby. Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).  
  
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

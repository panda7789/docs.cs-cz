---
title: 'Postupy: Vytvoření koncového bodu služby v konfiguraci'
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 63a40576b805952197cec5af2f89a5dc4b5d3545
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61787644"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="73414-102">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="73414-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="73414-103">Koncové body mají klienti obdržet přístup k funkcím, které nabízí služba Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="73414-103">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="73414-104">Můžete definovat jeden nebo víc koncových bodů služby pomocí kombinace relativní a absolutní koncový bod adresy, nebo pokud nejsou definovány žádné koncové body služby, modul runtime, poskytuje některé ve výchozím nastavení za vás.</span><span class="sxs-lookup"><span data-stu-id="73414-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="73414-105">Toto téma ukazuje, jak přidat koncové body pomocí konfiguračního souboru, které obsahují relativní a absolutní adresu.</span><span class="sxs-lookup"><span data-stu-id="73414-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="73414-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="73414-106">Example</span></span>  
 <span data-ttu-id="73414-107">Následující konfigurace služby určuje základní adresu a pět koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="73414-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="73414-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="73414-108">Example</span></span>  
 <span data-ttu-id="73414-109">Základní adresa je zadána pomocí `add` element v rámci služby/hostitele/baseAddresses, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="73414-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="73414-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="73414-110">Example</span></span>  
 <span data-ttu-id="73414-111">První definice koncového bodu je znázorněno v následujícím příkladu určuje relativní adresa, což znamená, že adresa koncového bodu je kombinací základní adresu a relativní adresu dle pravidel složení identifikátor URI (Uniform Resource).</span><span class="sxs-lookup"><span data-stu-id="73414-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="73414-112">Relativní adresa je prázdná (""), takže adresu koncového bodu je stejný jako základní adresu.</span><span class="sxs-lookup"><span data-stu-id="73414-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="73414-113">Adresa skutečný koncový bod je `http://localhost:8000/servicemodelsamples/service`.</span><span class="sxs-lookup"><span data-stu-id="73414-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="73414-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="73414-114">Example</span></span>  
 <span data-ttu-id="73414-115">Druhá definice koncového bodu také určuje relativní adresa, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="73414-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="73414-116">Relativní adresa "test", se připojí k základní adrese.</span><span class="sxs-lookup"><span data-stu-id="73414-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="73414-117">Adresa skutečný koncový bod je `http://localhost:8000/servicemodelsamples/service/test`.</span><span class="sxs-lookup"><span data-stu-id="73414-117">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="73414-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="73414-118">Example</span></span>  
 <span data-ttu-id="73414-119">Třetí definice koncového bodu určuje absolutní adresu, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="73414-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="73414-120">Základní adresa hraje žádná role v adrese.</span><span class="sxs-lookup"><span data-stu-id="73414-120">The base address plays no role in the address.</span></span> <span data-ttu-id="73414-121">Adresa skutečný koncový bod je `http://localhost:8001/hello/servicemodelsamples`.</span><span class="sxs-lookup"><span data-stu-id="73414-121">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="73414-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="73414-122">Example</span></span>  
 <span data-ttu-id="73414-123">Na čtvrté adresu koncového bodu určuje absolutní adresu a různé přenosové – TCP.</span><span class="sxs-lookup"><span data-stu-id="73414-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="73414-124">Základní adresa hraje žádná role v adrese.</span><span class="sxs-lookup"><span data-stu-id="73414-124">The base address plays no role in the address.</span></span> <span data-ttu-id="73414-125">Adresa skutečný koncový bod je NET.TCP://localhost: 9000/servicemodelsamples/služby.</span><span class="sxs-lookup"><span data-stu-id="73414-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="73414-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="73414-126">Example</span></span>  
 <span data-ttu-id="73414-127">Pokud chcete použít výchozí koncové body poskytovaný modulem runtime, nezadávejte žádné koncové body služby v kódu nebo konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="73414-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="73414-128">V tomto příkladu modul runtime vytvoří výchozí koncové body při otevření služby.</span><span class="sxs-lookup"><span data-stu-id="73414-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="73414-129">Další informace o výchozí koncové body, vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="73414-129">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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

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
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="705c9-102">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="705c9-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="705c9-103">Koncové body poskytují klientům přístup k funkcím, které nabízí služba Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="705c9-103">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="705c9-104">Můžete definovat jeden nebo více koncových bodů pro službu pomocí kombinace relativních a absolutních adres koncového bodu, nebo pokud nedefinujete žádné koncové body služby, modul runtime pro vás standardně poskytne výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="705c9-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="705c9-105">V tomto tématu se dozvíte, jak přidat koncové body pomocí konfiguračního souboru, který obsahuje relativní i absolutní adresy.</span><span class="sxs-lookup"><span data-stu-id="705c9-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="705c9-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="705c9-106">Example</span></span>  
 <span data-ttu-id="705c9-107">Následující konfigurace služby určuje základní adresu a pět koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="705c9-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="705c9-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="705c9-108">Example</span></span>  
 <span data-ttu-id="705c9-109">Základní adresa je určena pomocí `add` elementu v části Služba/Hostitel/adres BaseAddresses, jak je znázorněno v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="705c9-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="705c9-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="705c9-110">Example</span></span>  
 <span data-ttu-id="705c9-111">První definice koncového bodu zobrazená v následujícím příkladu určuje relativní adresu, což znamená, že adresa koncového bodu je kombinací základní adresy a relativní adresy podle pravidel složení identifikátoru URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="705c9-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="705c9-112">Relativní adresa je prázdná (""), takže adresa koncového bodu je stejná jako základní adresa.</span><span class="sxs-lookup"><span data-stu-id="705c9-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="705c9-113">Skutečná adresa koncového bodu je `http://localhost:8000/servicemodelsamples/service` .</span><span class="sxs-lookup"><span data-stu-id="705c9-113">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="705c9-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="705c9-114">Example</span></span>  
 <span data-ttu-id="705c9-115">Druhá definice koncového bodu také určuje relativní adresu, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="705c9-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="705c9-116">Relativní adresa "test" se připojí k základní adrese.</span><span class="sxs-lookup"><span data-stu-id="705c9-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="705c9-117">Skutečná adresa koncového bodu je `http://localhost:8000/servicemodelsamples/service/test` .</span><span class="sxs-lookup"><span data-stu-id="705c9-117">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="705c9-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="705c9-118">Example</span></span>  
 <span data-ttu-id="705c9-119">Třetí definice koncového bodu určuje absolutní adresu, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="705c9-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="705c9-120">Základní adresa nehraje v adrese žádnou roli.</span><span class="sxs-lookup"><span data-stu-id="705c9-120">The base address plays no role in the address.</span></span> <span data-ttu-id="705c9-121">Skutečná adresa koncového bodu je `http://localhost:8001/hello/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="705c9-121">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="705c9-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="705c9-122">Example</span></span>  
 <span data-ttu-id="705c9-123">Čtvrtá adresa koncového bodu určuje absolutní adresu a jiný přenos – TCP.</span><span class="sxs-lookup"><span data-stu-id="705c9-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="705c9-124">Základní adresa nehraje v adrese žádnou roli.</span><span class="sxs-lookup"><span data-stu-id="705c9-124">The base address plays no role in the address.</span></span> <span data-ttu-id="705c9-125">Skutečná adresa koncového bodu je NET. TCP://localhost: 9000/servicemodelsamples/service.</span><span class="sxs-lookup"><span data-stu-id="705c9-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="705c9-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="705c9-126">Example</span></span>  
 <span data-ttu-id="705c9-127">Chcete-li použít výchozí koncové body poskytované modulem runtime, nezadávejte koncové body služby buď v kódu, nebo v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="705c9-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="705c9-128">V tomto příkladu modul runtime vytvoří výchozí koncové body při otevření služby.</span><span class="sxs-lookup"><span data-stu-id="705c9-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="705c9-129">Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](../simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="705c9-129">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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

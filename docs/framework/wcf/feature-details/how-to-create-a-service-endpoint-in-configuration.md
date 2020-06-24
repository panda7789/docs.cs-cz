---
title: 'Postupy: Vytvoření koncového bodu služby v konfiguraci'
description: Naučte se, jak přidat koncové body pro službu WCF pomocí konfiguračního souboru, který obsahuje relativní i absolutní adresy.
ms.date: 06/16/2016
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
ms.openlocfilehash: 184bcb5f7f3e83f12608757b55bbb4d57be58f7d
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247062"
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="938b4-103">Postupy: Vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="938b4-103">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="938b4-104">Koncové body poskytují klientům přístup k funkcím, které nabízí služba Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="938b4-104">Endpoints provide clients with access to the functionality a Windows Communication Foundation (WCF) service offers.</span></span> <span data-ttu-id="938b4-105">Můžete definovat jeden nebo více koncových bodů pro službu pomocí kombinace relativních a absolutních adres koncového bodu, nebo pokud nedefinujete žádné koncové body služby, modul runtime pro vás standardně poskytne výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="938b4-105">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="938b4-106">V tomto tématu se dozvíte, jak přidat koncové body pomocí konfiguračního souboru, který obsahuje relativní i absolutní adresy.</span><span class="sxs-lookup"><span data-stu-id="938b4-106">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="938b4-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="938b4-107">Example</span></span>  
 <span data-ttu-id="938b4-108">Následující konfigurace služby určuje základní adresu a pět koncových bodů.</span><span class="sxs-lookup"><span data-stu-id="938b4-108">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="938b4-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="938b4-109">Example</span></span>  
 <span data-ttu-id="938b4-110">Základní adresa je určena pomocí `add` elementu v části Služba/Hostitel/adres BaseAddresses, jak je znázorněno v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="938b4-110">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="938b4-111">Příklad</span><span class="sxs-lookup"><span data-stu-id="938b4-111">Example</span></span>  
 <span data-ttu-id="938b4-112">První definice koncového bodu zobrazená v následujícím příkladu určuje relativní adresu, což znamená, že adresa koncového bodu je kombinací základní adresy a relativní adresy podle pravidel složení identifikátoru URI (Uniform Resource Identifier).</span><span class="sxs-lookup"><span data-stu-id="938b4-112">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="938b4-113">Relativní adresa je prázdná (""), takže adresa koncového bodu je stejná jako základní adresa.</span><span class="sxs-lookup"><span data-stu-id="938b4-113">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="938b4-114">Skutečná adresa koncového bodu je `http://localhost:8000/servicemodelsamples/service` .</span><span class="sxs-lookup"><span data-stu-id="938b4-114">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service`.</span></span>  
  
```xml  
<endpoint address=""
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="938b4-115">Příklad</span><span class="sxs-lookup"><span data-stu-id="938b4-115">Example</span></span>  
 <span data-ttu-id="938b4-116">Druhá definice koncového bodu také určuje relativní adresu, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="938b4-116">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="938b4-117">Relativní adresa "test" se připojí k základní adrese.</span><span class="sxs-lookup"><span data-stu-id="938b4-117">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="938b4-118">Skutečná adresa koncového bodu je `http://localhost:8000/servicemodelsamples/service/test` .</span><span class="sxs-lookup"><span data-stu-id="938b4-118">The actual endpoint address is `http://localhost:8000/servicemodelsamples/service/test`.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="938b4-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="938b4-119">Example</span></span>  
 <span data-ttu-id="938b4-120">Třetí definice koncového bodu určuje absolutní adresu, jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="938b4-120">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="938b4-121">Základní adresa nehraje v adrese žádnou roli.</span><span class="sxs-lookup"><span data-stu-id="938b4-121">The base address plays no role in the address.</span></span> <span data-ttu-id="938b4-122">Skutečná adresa koncového bodu je `http://localhost:8001/hello/servicemodelsamples` .</span><span class="sxs-lookup"><span data-stu-id="938b4-122">The actual endpoint address is `http://localhost:8001/hello/servicemodelsamples`.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="938b4-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="938b4-123">Example</span></span>  
 <span data-ttu-id="938b4-124">Čtvrtá adresa koncového bodu určuje absolutní adresu a jiný přenos – TCP.</span><span class="sxs-lookup"><span data-stu-id="938b4-124">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="938b4-125">Základní adresa nehraje v adrese žádnou roli.</span><span class="sxs-lookup"><span data-stu-id="938b4-125">The base address plays no role in the address.</span></span> <span data-ttu-id="938b4-126">Skutečná adresa koncového bodu je NET. TCP://localhost: 9000/servicemodelsamples/service.</span><span class="sxs-lookup"><span data-stu-id="938b4-126">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="938b4-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="938b4-127">Example</span></span>  
 <span data-ttu-id="938b4-128">Chcete-li použít výchozí koncové body poskytované modulem runtime, nezadávejte koncové body služby buď v kódu, nebo v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="938b4-128">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="938b4-129">V tomto příkladu modul runtime vytvoří výchozí koncové body při otevření služby.</span><span class="sxs-lookup"><span data-stu-id="938b4-129">In this example, the runtime creates the default endpoints when the service is opened.</span></span> <span data-ttu-id="938b4-130">Další informace o výchozích koncových bodech, vazbách a chování najdete v tématu [zjednodušená konfigurace](../simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="938b4-130">For more information about default endpoints, bindings, and behaviors, see [Simplified Configuration](../simplified-configuration.md) and [Simplified Configuration for WCF Services](../samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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

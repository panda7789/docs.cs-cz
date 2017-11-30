---
title: "Postupy: vytvoření koncového bodu služby v konfiguraci"
ms.custom: 
ms.date: 06/16/2016
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f474e25d-2a27-4f31-84c5-395c442b8e70
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bf9b6eed2ce4270c9faecc27cb4626a155eb4a6c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-create-a-service-endpoint-in-configuration"></a><span data-ttu-id="5caa2-102">Postupy: vytvoření koncového bodu služby v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="5caa2-102">How to: Create a Service Endpoint in Configuration</span></span>
<span data-ttu-id="5caa2-103">Koncové body mají klienti přístup k funkci [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] nabídky služeb.</span><span class="sxs-lookup"><span data-stu-id="5caa2-103">Endpoints provide clients with access to the functionality a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service offers.</span></span> <span data-ttu-id="5caa2-104">Můžete definovat jeden nebo více koncových bodů pro službu pomocí kombinace adresy koncových bodů relativní a absolutní, nebo pokud nejsou definovány žádné koncové body služby, modul runtime, obsahuje některé ve výchozím nastavení za vás.</span><span class="sxs-lookup"><span data-stu-id="5caa2-104">You can define one or more endpoints for a service by using a combination of relative and absolute endpoint addresses, or if you do not define any service endpoints, the runtime provides some by default for you.</span></span> <span data-ttu-id="5caa2-105">Toto téma ukazuje, jak přidat koncové body pomocí konfiguračního souboru, které obsahují relativní a absolutní adresy.</span><span class="sxs-lookup"><span data-stu-id="5caa2-105">This topic shows how to add endpoints using a configuration file that contain both relative and absolute addresses.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5caa2-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="5caa2-106">Example</span></span>  
 <span data-ttu-id="5caa2-107">Následující konfigurace služby určuje základní adresu a pět koncové body.</span><span class="sxs-lookup"><span data-stu-id="5caa2-107">The following service configuration specifies a base address and five endpoints.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="5caa2-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="5caa2-108">Example</span></span>  
 <span data-ttu-id="5caa2-109">Základní adresa je zadán pomocí `add` prvek, v rámci služby nebo hostitele nebo baseAddresses, jak znázorňuje následující ukázka.</span><span class="sxs-lookup"><span data-stu-id="5caa2-109">The base address is specified using the `add` element, under service/host/baseAddresses, as shown in the following sample.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
```  
  
## <a name="example"></a><span data-ttu-id="5caa2-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="5caa2-110">Example</span></span>  
 <span data-ttu-id="5caa2-111">První koncový bod definice znázorňuje následující ukázka určuje relativní adresu, která znamená, že adresa koncového bodu je kombinací základní adresu a relativní adresy následující pravidla složení identifikátor URI (Uniform Resource).</span><span class="sxs-lookup"><span data-stu-id="5caa2-111">The first endpoint definition shown in the following sample specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of Uniform Resource Identifier (URI) composition.</span></span> <span data-ttu-id="5caa2-112">Relativní adresa je prázdná (""), takže adresa koncového bodu je stejný jako základní adresu.</span><span class="sxs-lookup"><span data-stu-id="5caa2-112">The relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="5caa2-113">Adresa skutečný koncový bod je http://localhost: 8000/servicemodelsamples nebo služby.</span><span class="sxs-lookup"><span data-stu-id="5caa2-113">The actual endpoint address is http://localhost:8000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address=""   
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="5caa2-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="5caa2-114">Example</span></span>  
 <span data-ttu-id="5caa2-115">Druhý definice služby endpoint také určuje relativní adresu, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5caa2-115">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span> <span data-ttu-id="5caa2-116">Relativní adresu "test", připojí se k základní adresu.</span><span class="sxs-lookup"><span data-stu-id="5caa2-116">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="5caa2-117">Adresa skutečný koncový bod je http://localhost: 8000/servicemodelsamples/service/testování.</span><span class="sxs-lookup"><span data-stu-id="5caa2-117">The actual endpoint address is http://localhost:8000/servicemodelsamples/service/test.</span></span>  
  
```xml  
<endpoint address="/test"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="5caa2-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="5caa2-118">Example</span></span>  
 <span data-ttu-id="5caa2-119">Třetí definice služby endpoint určuje absolutní adresu, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="5caa2-119">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span> <span data-ttu-id="5caa2-120">Základní adresa hraje žádný atribut role v adrese.</span><span class="sxs-lookup"><span data-stu-id="5caa2-120">The base address plays no role in the address.</span></span> <span data-ttu-id="5caa2-121">Adresa skutečný koncový bod je http://localhost:8001/hello nebo servicemodelsamples.</span><span class="sxs-lookup"><span data-stu-id="5caa2-121">The actual endpoint address is http://localhost:8001/hello/servicemodelsamples.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
    binding="wsHttpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="5caa2-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="5caa2-122">Example</span></span>  
 <span data-ttu-id="5caa2-123">Čtvrtý adresa koncového bodu určuje absolutní adresu a různé přenosové – TCP.</span><span class="sxs-lookup"><span data-stu-id="5caa2-123">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="5caa2-124">Základní adresa hraje žádný atribut role v adrese.</span><span class="sxs-lookup"><span data-stu-id="5caa2-124">The base address plays no role in the address.</span></span> <span data-ttu-id="5caa2-125">Adresa skutečný koncový bod je net.tcp://localhost: 9000/servicemodelsamples nebo služby.</span><span class="sxs-lookup"><span data-stu-id="5caa2-125">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<endpoint address="net.tcp://localhost:9000/servicemodelsamples/service"  
    binding="netTcpBinding"  
    contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
## <a name="example"></a><span data-ttu-id="5caa2-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="5caa2-126">Example</span></span>  
 <span data-ttu-id="5caa2-127">Chcete-li použít výchozí koncové body poskytované modulem runtime, nezadávejte žádné koncové body služby v kódu nebo konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="5caa2-127">To use the default endpoints provided by the runtime, do not specify any service endpoints in either the code or the configuration file.</span></span> <span data-ttu-id="5caa2-128">Modul runtime vytvoří v tomto příkladu jsou výchozí koncové body po otevření služby.</span><span class="sxs-lookup"><span data-stu-id="5caa2-128">In this example, the runtime creates the default endpoints when the service is opened.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="5caa2-129">výchozí koncové body, vazby a chování, viz [zjednodušená konfigurace](../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="5caa2-129"> default endpoints, bindings, and behaviors, see [Simplified Configuration](../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
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

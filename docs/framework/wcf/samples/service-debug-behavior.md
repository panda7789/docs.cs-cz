---
title: Chování ladění služby
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 2f2eefb01e66efddea05116f640a60defe78de1b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664722"
---
# <a name="service-debug-behavior"></a><span data-ttu-id="e3398-102">Chování ladění služby</span><span class="sxs-lookup"><span data-stu-id="e3398-102">Service Debug Behavior</span></span>
<span data-ttu-id="e3398-103">Tato ukázka předvádí, jak lze konfigurovat nastavení chování ladění služby.</span><span class="sxs-lookup"><span data-stu-id="e3398-103">This sample demonstrates how service debug behavior settings can be configured.</span></span> <span data-ttu-id="e3398-104">Vzorek je založen na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje `ICalculator` kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="e3398-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="e3398-105">Tato ukázka explicitně definuje chování ladění služby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="e3398-105">This sample explicitly defines service debug behavior in the configuration file.</span></span> <span data-ttu-id="e3398-106">To je možné provést imperativně v kódu.</span><span class="sxs-lookup"><span data-stu-id="e3398-106">It can also be done imperatively in code.</span></span>  
  
 <span data-ttu-id="e3398-107">V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="e3398-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3398-108">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="e3398-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="e3398-109">Soubor Web.config pro server se definuje chování ladění služby povolit stránku nápovědy a zpracování výjimek, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e3398-109">The Web.config file for the server defines the service debug behavior to enable the help page and exception handling as shown in the following sample.</span></span>  
  
```xml  
<behaviors>  
     <serviceBehaviors>  
         <behavior name="CalculatorServiceBehavior">  
         <!-- WARNING: Setting includeExceptionDetailInFaults = "True" could result in leaking secured server information to the client.-->  
         <!-- Please set this to false when deploying -->  
             <serviceDebug includeExceptionDetailInFaults="True" httpHelpPageEnabled="True"/>  
         </behavior>  
     </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="e3398-110">[\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) je prvek konfigurace, který umožňuje změnit vlastnosti chování ladění služby.</span><span class="sxs-lookup"><span data-stu-id="e3398-110">[\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) is the configuration element that allows changing the service debug behavior properties.</span></span> <span data-ttu-id="e3398-111">Uživatel může upravit toto chování a dosáhnout následující:</span><span class="sxs-lookup"><span data-stu-id="e3398-111">The user can modify this behavior to achieve the following:</span></span>  
  
- <span data-ttu-id="e3398-112">To umožňuje službě vrátit jakoukoliv výjimku, která je vyvolána kódem aplikace, i v případě, že výjimka není deklarován pomocí <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="e3398-112">This allows the service to return any exception that is thrown by the application code even if the exception is not declared using the <xref:System.ServiceModel.FaultContractAttribute>.</span></span> <span data-ttu-id="e3398-113">To se provádí nastavením `includeExceptionDetailInFaults` k `true`.</span><span class="sxs-lookup"><span data-stu-id="e3398-113">It is done by setting `includeExceptionDetailInFaults` to `true`.</span></span> <span data-ttu-id="e3398-114">Toto nastavení je užitečné při ladění v případech, kde je serveru vyvolání neočekávané výjimky.</span><span class="sxs-lookup"><span data-stu-id="e3398-114">This setting is useful when debugging cases where the server is throwing an unexpected exception.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="e3398-115">Není bezpečné zapnout toto nastavení v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="e3398-115">It is not secure to turn this setting on in a production environment.</span></span> <span data-ttu-id="e3398-116">Server neočekávané výjimky může mít některé informace, která není určená pro klienta a proto nastavení `includeExceptionDetailsInFaults` k `true` může vést úniku informací.</span><span class="sxs-lookup"><span data-stu-id="e3398-116">An unexpected server exception may have some information that is not intended for the client and so setting `includeExceptionDetailsInFaults` to `true` might result in an information leak.</span></span>  
  
- <span data-ttu-id="e3398-117">[ \<ServiceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) také umožňuje uživatelům povolit nebo zakázat na stránce nápovědy.</span><span class="sxs-lookup"><span data-stu-id="e3398-117">The [\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) also allows a user to enable or disable the help page.</span></span> <span data-ttu-id="e3398-118">Každá služba Volitelně můžete zveřejnit stránce nápovědy, který obsahuje informace o službě včetně koncový bod pro získání WSDL pro službu.</span><span class="sxs-lookup"><span data-stu-id="e3398-118">Each service can optionally expose a help page that contains information about the service including the endpoint to get WSDL for the service.</span></span> <span data-ttu-id="e3398-119">To se dá nastavit tak, že nastavíte `httpHelpPageEnabled` k `true`.</span><span class="sxs-lookup"><span data-stu-id="e3398-119">This can be enabled by setting `httpHelpPageEnabled` to `true`.</span></span> <span data-ttu-id="e3398-120">To umožňuje na stránce nápovědy, který se má vrátit požadavek GET na základní adresu služby.</span><span class="sxs-lookup"><span data-stu-id="e3398-120">This enables the help page to be returned to a GET request to the base address of the service.</span></span> <span data-ttu-id="e3398-121">Tuto adresu můžete změnit nastavením jiný atribut `httpHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="e3398-121">You can change this address by setting another attribute `httpHelpPageUrl`.</span></span> <span data-ttu-id="e3398-122">Lze zvýšit tím zabezpečení pomocí protokolu HTTPS místo protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="e3398-122">You can make this secure by using HTTPS instead of HTTP.</span></span> <span data-ttu-id="e3398-123">To můžete udělat tak, že nastavíte `httpsHelpPageEnabled` a `httpsHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="e3398-123">This can be done by setting `httpsHelpPageEnabled` and `httpsHelpPageUrl`.</span></span>  
  
 <span data-ttu-id="e3398-124">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="e3398-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="e3398-125">První tři operace (přidání, odečíst a násobení) musí být úspěšný.</span><span class="sxs-lookup"><span data-stu-id="e3398-125">The first three operations (Add, Subtract and Multiply) must succeed.</span></span> <span data-ttu-id="e3398-126">Poslední operace ("dělení") se nezdaří s dělení nulovou výjimky.</span><span class="sxs-lookup"><span data-stu-id="e3398-126">The last operation ("divide") fails with a division by zero exception.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="e3398-127">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="e3398-127">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="e3398-128">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e3398-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="e3398-129">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e3398-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="e3398-130">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="e3398-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e3398-131">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="e3398-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e3398-132">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="e3398-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e3398-133">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="e3398-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e3398-134">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="e3398-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  

---
title: Chování ladění služby
ms.date: 03/30/2017
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
ms.openlocfilehash: 67ae8cf72baf2d6a54010a05ca4c5e047120617a
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044747"
---
# <a name="service-debug-behavior"></a><span data-ttu-id="b322e-102">Chování ladění služby</span><span class="sxs-lookup"><span data-stu-id="b322e-102">Service Debug Behavior</span></span>

<span data-ttu-id="b322e-103">Tato ukázka předvádí, jak lze nakonfigurovat nastavení chování ladění služby.</span><span class="sxs-lookup"><span data-stu-id="b322e-103">This sample demonstrates how service debug behavior settings can be configured.</span></span> <span data-ttu-id="b322e-104">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), která implementuje `ICalculator` kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="b322e-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="b322e-105">Tato ukázka explicitně definuje chování ladění služby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="b322e-105">This sample explicitly defines service debug behavior in the configuration file.</span></span> <span data-ttu-id="b322e-106">Může být také provedeno imperativně v kódu.</span><span class="sxs-lookup"><span data-stu-id="b322e-106">It can also be done imperatively in code.</span></span>

<span data-ttu-id="b322e-107">V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="b322e-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>

> [!NOTE]
> <span data-ttu-id="b322e-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="b322e-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>

<span data-ttu-id="b322e-109">Soubor Web. config pro Server definuje chování ladění služby, aby bylo možné povolit stránku a zpracování výjimek stránky s nápovědu, jak je znázorněno v následující ukázce.</span><span class="sxs-lookup"><span data-stu-id="b322e-109">The Web.config file for the server defines the service debug behavior to enable the help page and exception handling as shown in the following sample.</span></span>

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

<span data-ttu-id="b322e-110">serviceDebug > je prvek konfigurace, který umožňuje změnit vlastnosti chování ladění služby. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)</span><span class="sxs-lookup"><span data-stu-id="b322e-110">[\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) is the configuration element that allows changing the service debug behavior properties.</span></span> <span data-ttu-id="b322e-111">Uživatel může toto chování změnit, aby bylo možné provést následující akce:</span><span class="sxs-lookup"><span data-stu-id="b322e-111">The user can modify this behavior to achieve the following:</span></span>

- <span data-ttu-id="b322e-112">To umožňuje službě vracet všechny výjimky, které jsou vyvolány kódem aplikace, i v případě, že výjimka není deklarována <xref:System.ServiceModel.FaultContractAttribute>pomocí.</span><span class="sxs-lookup"><span data-stu-id="b322e-112">This allows the service to return any exception that is thrown by the application code even if the exception is not declared using the <xref:System.ServiceModel.FaultContractAttribute>.</span></span> <span data-ttu-id="b322e-113">Je prováděna nastavením `includeExceptionDetailInFaults` na `true`.</span><span class="sxs-lookup"><span data-stu-id="b322e-113">It is done by setting `includeExceptionDetailInFaults` to `true`.</span></span> <span data-ttu-id="b322e-114">Toto nastavení je užitečné při ladění případů, kdy server vyvolává neočekávanou výjimku.</span><span class="sxs-lookup"><span data-stu-id="b322e-114">This setting is useful when debugging cases where the server is throwing an unexpected exception.</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="b322e-115">Toto nastavení v produkčním prostředí není bezpečné zapnout.</span><span class="sxs-lookup"><span data-stu-id="b322e-115">It is not secure to turn this setting on in a production environment.</span></span> <span data-ttu-id="b322e-116">Neočekávaná výjimka serveru může obsahovat některé informace, které nejsou určené pro klienta, a nastavení `includeExceptionDetailsInFaults` , které `true` by mohlo vést k úniku informací.</span><span class="sxs-lookup"><span data-stu-id="b322e-116">An unexpected server exception may have some information that is not intended for the client and so setting `includeExceptionDetailsInFaults` to `true` might result in an information leak.</span></span>

- <span data-ttu-id="b322e-117">ServiceDebug > také umožňuje uživateli povolit nebo zakázat stránku s jeho pomocí. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md)</span><span class="sxs-lookup"><span data-stu-id="b322e-117">The [\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) also allows a user to enable or disable the help page.</span></span> <span data-ttu-id="b322e-118">Každá služba může volitelně vystavit stránku s nápovědu obsahující informace o službě, včetně koncového bodu pro získání WSDL pro službu.</span><span class="sxs-lookup"><span data-stu-id="b322e-118">Each service can optionally expose a help page that contains information about the service including the endpoint to get WSDL for the service.</span></span> <span data-ttu-id="b322e-119">To lze povolit nastavením `httpHelpPageEnabled` na. `true`</span><span class="sxs-lookup"><span data-stu-id="b322e-119">This can be enabled by setting `httpHelpPageEnabled` to `true`.</span></span> <span data-ttu-id="b322e-120">Tím umožníte, aby se stránka s Nápověda vrátila do žádosti o získání základní adresy služby.</span><span class="sxs-lookup"><span data-stu-id="b322e-120">This enables the help page to be returned to a GET request to the base address of the service.</span></span> <span data-ttu-id="b322e-121">Tuto adresu můžete změnit nastavením jiného atributu `httpHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="b322e-121">You can change this address by setting another attribute `httpHelpPageUrl`.</span></span> <span data-ttu-id="b322e-122">Toto zabezpečení můžete provést pomocí protokolu HTTPS místo HTTP.</span><span class="sxs-lookup"><span data-stu-id="b322e-122">You can make this secure by using HTTPS instead of HTTP.</span></span> <span data-ttu-id="b322e-123">To se dá udělat nastavením `httpsHelpPageEnabled` a. `httpsHelpPageUrl`</span><span class="sxs-lookup"><span data-stu-id="b322e-123">This can be done by setting `httpsHelpPageEnabled` and `httpsHelpPageUrl`.</span></span>

<span data-ttu-id="b322e-124">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="b322e-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b322e-125">První tři operace (sčítání, odečítání a násobení) musí být úspěšné.</span><span class="sxs-lookup"><span data-stu-id="b322e-125">The first three operations (Add, Subtract and Multiply) must succeed.</span></span> <span data-ttu-id="b322e-126">Poslední operace ("dělení") se nezdařila s oddělenou výjimkou dělení nulou.</span><span class="sxs-lookup"><span data-stu-id="b322e-126">The last operation ("divide") fails with a division by zero exception.</span></span>

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b322e-127">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="b322e-127">To set up, build, and run the sample</span></span>

1. <span data-ttu-id="b322e-128">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b322e-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>

2. <span data-ttu-id="b322e-129">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b322e-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>

3. <span data-ttu-id="b322e-130">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="b322e-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b322e-131">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="b322e-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b322e-132">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="b322e-132">Check for the following (default) directory before continuing.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> <span data-ttu-id="b322e-133">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="b322e-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b322e-134">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="b322e-134">This sample is located in the following directory.</span></span>
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`

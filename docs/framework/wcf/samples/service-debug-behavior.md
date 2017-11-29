---
title: "Chování ladění služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d8fd3fb-dc39-427a-8235-336a7e7162ba
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 04520eda9fe7ce2cd461e094fe2cec76d52ccc7d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="service-debug-behavior"></a><span data-ttu-id="43e87-102">Chování ladění služby</span><span class="sxs-lookup"><span data-stu-id="43e87-102">Service Debug Behavior</span></span>
<span data-ttu-id="43e87-103">Tento příklad znázorňuje, jak lze nakonfigurovat nastavení chování ladění služby.</span><span class="sxs-lookup"><span data-stu-id="43e87-103">This sample demonstrates how service debug behavior settings can be configured.</span></span> <span data-ttu-id="43e87-104">Ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md), který implementuje `ICalculator` kontrakt služby.</span><span class="sxs-lookup"><span data-stu-id="43e87-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="43e87-105">Tato ukázka explicitně definuje chování ladění služby v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="43e87-105">This sample explicitly defines service debug behavior in the configuration file.</span></span> <span data-ttu-id="43e87-106">Je možné také ji provést imperativní v kódu.</span><span class="sxs-lookup"><span data-stu-id="43e87-106">It can also be done imperatively in code.</span></span>  
  
 <span data-ttu-id="43e87-107">V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="43e87-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43e87-108">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="43e87-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="43e87-109">Soubor Web.config pro server definuje chování ladění služby povolit stránku nápovědy a výjimek, jak znázorňuje následující ukázka.</span><span class="sxs-lookup"><span data-stu-id="43e87-109">The Web.config file for the server defines the service debug behavior to enable the help page and exception handling as shown in the following sample.</span></span>  
  
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
  
 <span data-ttu-id="43e87-110">[\<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) je konfigurace elementu, který umožňuje změnit vlastnosti chování ladění služby.</span><span class="sxs-lookup"><span data-stu-id="43e87-110">[\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) is the configuration element that allows changing the service debug behavior properties.</span></span> <span data-ttu-id="43e87-111">Uživatele můžete upravit toto chování cíle jsou následující:</span><span class="sxs-lookup"><span data-stu-id="43e87-111">The user can modify this behavior to achieve the following:</span></span>  
  
-   <span data-ttu-id="43e87-112">To umožňuje službě vrátit jakékoli výjimky vyvolané kódem aplikace i v případě, že výjimka není deklarovaný pomocí <xref:System.ServiceModel.FaultContractAttribute>.</span><span class="sxs-lookup"><span data-stu-id="43e87-112">This allows the service to return any exception that is thrown by the application code even if the exception is not declared using the <xref:System.ServiceModel.FaultContractAttribute>.</span></span> <span data-ttu-id="43e87-113">Se provádí nastavením `includeExceptionDetailInFaults` k `true`.</span><span class="sxs-lookup"><span data-stu-id="43e87-113">It is done by setting `includeExceptionDetailInFaults` to `true`.</span></span> <span data-ttu-id="43e87-114">Toto nastavení je užitečné při ladění případech, kde je serveru došlo k neočekávané výjimce.</span><span class="sxs-lookup"><span data-stu-id="43e87-114">This setting is useful when debugging cases where the server is throwing an unexpected exception.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="43e87-115">Není zabezpečený zapnout toto nastavení v produkčním prostředí.</span><span class="sxs-lookup"><span data-stu-id="43e87-115">It is not secure to turn this setting on in a production environment.</span></span> <span data-ttu-id="43e87-116">Výjimku neočekávané server může mít některé informace, která není určená pro klienta a tak nastavení `includeExceptionDetailsInFaults` k `true` může vést k tomu dojde k úniku informací.</span><span class="sxs-lookup"><span data-stu-id="43e87-116">An unexpected server exception may have some information that is not intended for the client and so setting `includeExceptionDetailsInFaults` to `true` might result in an information leak.</span></span>  
  
-   <span data-ttu-id="43e87-117">[ \<ServiceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) také umožňuje uživatelům povolit nebo zakázat tuto stránku nápovědy.</span><span class="sxs-lookup"><span data-stu-id="43e87-117">The [\<serviceDebug>](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) also allows a user to enable or disable the help page.</span></span> <span data-ttu-id="43e87-118">Každé služby můžete volitelně vystavit stránku nápovědy, která obsahuje informace o službě včetně koncový bod získat WSDL pro službu.</span><span class="sxs-lookup"><span data-stu-id="43e87-118">Each service can optionally expose a help page that contains information about the service including the endpoint to get WSDL for the service.</span></span> <span data-ttu-id="43e87-119">To se dá nastavit nastavením `httpHelpPageEnabled` k `true`.</span><span class="sxs-lookup"><span data-stu-id="43e87-119">This can be enabled by setting `httpHelpPageEnabled` to `true`.</span></span> <span data-ttu-id="43e87-120">To umožňuje stránku nápovědy a vrátit požadavek GET na adresu základní služby.</span><span class="sxs-lookup"><span data-stu-id="43e87-120">This enables the help page to be returned to a GET request to the base address of the service.</span></span> <span data-ttu-id="43e87-121">Tuto adresu můžete změnit nastavením jiný atribut `httpHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="43e87-121">You can change this address by setting another attribute `httpHelpPageUrl`.</span></span> <span data-ttu-id="43e87-122">Můžete nastavit to zabezpečené pomocí protokolu HTTPS místo protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="43e87-122">You can make this secure by using HTTPS instead of HTTP.</span></span> <span data-ttu-id="43e87-123">To můžete provést nastavením `httpsHelpPageEnabled` a `httpsHelpPageUrl`.</span><span class="sxs-lookup"><span data-stu-id="43e87-123">This can be done by setting `httpsHelpPageEnabled` and `httpsHelpPageUrl`.</span></span>  
  
 <span data-ttu-id="43e87-124">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="43e87-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="43e87-125">První tři operace (přidání, odečtena a násobení) musí být úspěšné.</span><span class="sxs-lookup"><span data-stu-id="43e87-125">The first three operations (Add, Subtract and Multiply) must succeed.</span></span> <span data-ttu-id="43e87-126">Poslední operace ("Rozděl") se nezdaří s dělení nulové výjimkou.</span><span class="sxs-lookup"><span data-stu-id="43e87-126">The last operation ("divide") fails with a division by zero exception.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="43e87-127">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="43e87-127">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="43e87-128">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43e87-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="43e87-129">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43e87-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="43e87-130">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="43e87-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="43e87-131">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="43e87-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="43e87-132">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="43e87-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="43e87-133">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="43e87-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="43e87-134">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="43e87-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\ServiceDebug`  
  
## <a name="see-also"></a><span data-ttu-id="43e87-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="43e87-135">See Also</span></span>

---
title: "Spolehlivá relace WS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c07130715b0416e7a8603b46a1c39c2f22dd7d2e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ws-reliable-session"></a><span data-ttu-id="01b35-102">Spolehlivá relace WS</span><span class="sxs-lookup"><span data-stu-id="01b35-102">WS Reliable Session</span></span>
<span data-ttu-id="01b35-103">Tento příklad znázorňuje použití spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="01b35-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="01b35-104">Spolehlivé relace poskytuje podporu pro spolehlivé zasílání zpráv a relací.</span><span class="sxs-lookup"><span data-stu-id="01b35-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="01b35-105">Spolehlivé zasílání zpráv opakování komunikace při selhání a umožňuje záruky doručení zadat, jako je například doručení zpráv v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="01b35-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="01b35-106">Relace uchování stavu pro klienty mezi volání.</span><span class="sxs-lookup"><span data-stu-id="01b35-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="01b35-107">Ukázka implementuje relace pro zachování stavu klienta a určuje záruky doručení v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="01b35-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="01b35-108">Ukázky může být již nainstalována na váš počítač.</span><span class="sxs-lookup"><span data-stu-id="01b35-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="01b35-109">Před pokračováním zkontrolovat na následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="01b35-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="01b35-110">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="01b35-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="01b35-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="01b35-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="01b35-112">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="01b35-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="01b35-113">Spolehlivá relace funkcí jsou povolené a nakonfigurované v konfiguračních souborech aplikace pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="01b35-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="01b35-114">V této ukázce služba je hostovaná v Internetové informační služby (IIS) a klient je konzolová aplikace (.exe).</span><span class="sxs-lookup"><span data-stu-id="01b35-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="01b35-115">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="01b35-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="01b35-116">Ukázce se používá `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="01b35-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="01b35-117">Vazba je zadána v konfiguračních souborech pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="01b35-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="01b35-118">Typ vazby je zadaný v elementu koncový bod `binding` atributu, jak je znázorněno v následující ukázka konfigurace.</span><span class="sxs-lookup"><span data-stu-id="01b35-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="01b35-119">Obsahuje koncový bod `bindingConfiguration` atribut, který odkazuje na vazbu konfigurace s názvem "Binding1."</span><span class="sxs-lookup"><span data-stu-id="01b35-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="01b35-120">Konfigurace vazeb umožňuje spolehlivé relace nastavením `enabled` atribut [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) k `true`.</span><span class="sxs-lookup"><span data-stu-id="01b35-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="01b35-121">Záruky doručení pro seřazené relace jsou řízeny nastavením seřazené atribut `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="01b35-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="01b35-122">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="01b35-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="01b35-123">Třída implementuje implementace služby <xref:System.ServiceModel.InstanceContextMode.PerSession> zřizování instancí udržovat samostatné třídy instance pro jednotlivé klienty, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="01b35-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  
  
```  
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```  
  
 <span data-ttu-id="01b35-124">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="01b35-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="01b35-125">Stisknutím klávesy ENTER v okně klienta vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="01b35-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="01b35-126">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="01b35-126">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="01b35-127">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="01b35-127">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="01b35-128">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="01b35-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="01b35-129">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="01b35-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="01b35-130">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="01b35-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01b35-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="01b35-131">See Also</span></span>

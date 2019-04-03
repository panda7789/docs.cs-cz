---
title: Spolehlivá relace WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: c4e238cbc3b99209e88bb56c73097f25e56ccdfb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814481"
---
# <a name="ws-reliable-session"></a><span data-ttu-id="96da3-102">Spolehlivá relace WS</span><span class="sxs-lookup"><span data-stu-id="96da3-102">WS Reliable Session</span></span>
<span data-ttu-id="96da3-103">Tento příklad ukazuje použití spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="96da3-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="96da3-104">Spolehlivé relace poskytovat podporu pro spolehlivé zasílání zpráv a relací.</span><span class="sxs-lookup"><span data-stu-id="96da3-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="96da3-105">Spolehlivé zasílání zpráv se pokusí znovu navázat komunikaci s selhání a umožňuje záruky doručení zadání, jako je například v pořadí doručení zpráv.</span><span class="sxs-lookup"><span data-stu-id="96da3-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="96da3-106">Relace uchování stavu pro klienty mezi voláními.</span><span class="sxs-lookup"><span data-stu-id="96da3-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="96da3-107">Ukázka implementuje relací pro zachování stavu klienta a určuje záruky doručení v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="96da3-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="96da3-108">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="96da3-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="96da3-109">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="96da3-109">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="96da3-110">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="96da3-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="96da3-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="96da3-111">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="96da3-112">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) službu kalkulačky, která implementuje.</span><span class="sxs-lookup"><span data-stu-id="96da3-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="96da3-113">Spolehlivé relace funkce jsou povolené a nakonfigurované v konfiguračních souborech aplikace pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="96da3-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="96da3-114">V této ukázce služba je hostována v Internetové informační služby (IIS) a klient je konzolová aplikace (.exe).</span><span class="sxs-lookup"><span data-stu-id="96da3-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="96da3-115">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="96da3-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="96da3-116">Ukázka používá `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="96da3-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="96da3-117">Vazba je zadán v konfiguračních souborech pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="96da3-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="96da3-118">Typ vazby je zadaný v elementu koncového bodu `binding` atributu, jak je znázorněno v následující ukázková konfigurace.</span><span class="sxs-lookup"><span data-stu-id="96da3-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"   
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="96da3-119">Obsahuje koncový bod `bindingConfiguration` atribut, který odkazuje na konfiguraci vazby s názvem "Binding1."</span><span class="sxs-lookup"><span data-stu-id="96da3-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="96da3-120">Konfigurace vazby umožňuje spolehlivé relace tak, že nastavíte `enabled` atribut [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) k `true`.</span><span class="sxs-lookup"><span data-stu-id="96da3-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="96da3-121">Záruky doručení pro uspořádaný relace jsou řízeny nastavením atribut uspořádaný `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="96da3-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="96da3-122">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="96da3-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="96da3-123">Třída implementuje implementace služby <xref:System.ServiceModel.InstanceContextMode.PerSession> vytvoření instance udržovat samostatné třídy instanci pro každého klienta, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="96da3-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="96da3-124">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="96da3-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="96da3-125">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="96da3-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="96da3-126">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="96da3-126">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="96da3-127">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="96da3-127">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="96da3-128">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="96da3-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="96da3-129">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="96da3-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="96da3-130">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="96da3-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  

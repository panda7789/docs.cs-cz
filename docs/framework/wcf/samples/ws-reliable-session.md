---
title: Spolehlivá relace WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 8898dfedc6ba7deceb5a6e6856b7c7e6ad79d047
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143496"
---
# <a name="ws-reliable-session"></a><span data-ttu-id="0db22-102">Spolehlivá relace WS</span><span class="sxs-lookup"><span data-stu-id="0db22-102">WS Reliable Session</span></span>
<span data-ttu-id="0db22-103">Tato ukázka ukazuje použití spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="0db22-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="0db22-104">Spolehlivé relace poskytují podporu pro spolehlivé zasílání zpráv a relací.</span><span class="sxs-lookup"><span data-stu-id="0db22-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="0db22-105">Spolehlivé zasílání zpráv opakuje komunikaci o selhání a umožňuje zajištění doručení, které mají být zadány, jako je například doručení zpráv v pořadí.</span><span class="sxs-lookup"><span data-stu-id="0db22-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="0db22-106">Relace udržovat stav pro klienty mezi voláními.</span><span class="sxs-lookup"><span data-stu-id="0db22-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="0db22-107">Ukázka implementuje relace pro udržování stavu klienta a určuje záruky doručení v pořadí.</span><span class="sxs-lookup"><span data-stu-id="0db22-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="0db22-108">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="0db22-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0db22-109">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="0db22-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="0db22-110">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="0db22-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0db22-111">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="0db22-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="0db22-112">Tato ukázka je založena na [Začínáme,](../../../../docs/framework/wcf/samples/getting-started-sample.md) který implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="0db22-112">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="0db22-113">Spolehlivé funkce relace jsou povoleny a konfigurovány v konfiguračních souborech aplikace pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="0db22-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="0db22-114">V této ukázce je služba hostována v Internetové informační službě (IIS) a klient je konzolová aplikace (.exe).</span><span class="sxs-lookup"><span data-stu-id="0db22-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0db22-115">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="0db22-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0db22-116">Ukázka používá `wsHttpBinding`.</span><span class="sxs-lookup"><span data-stu-id="0db22-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="0db22-117">Vazba je určena v konfiguračních souborech pro klienta i službu.</span><span class="sxs-lookup"><span data-stu-id="0db22-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="0db22-118">Typ vazby je určen v atributu prvku koncového `binding` bodu, jak je znázorněno v následující konfiguraci ukázky.</span><span class="sxs-lookup"><span data-stu-id="0db22-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="0db22-119">Koncový bod obsahuje `bindingConfiguration` atribut, který odkazuje na konfiguraci vazby s názvem "Binding1.".</span><span class="sxs-lookup"><span data-stu-id="0db22-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="0db22-120">Konfigurace vazby umožňuje spolehlivé `enabled` relace nastavením atributu `true` [ \<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) na .</span><span class="sxs-lookup"><span data-stu-id="0db22-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="0db22-121">Záruky doručení pro objednané relace jsou `true` řízeny nastavením objednaného atributu nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="0db22-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="0db22-122">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="0db22-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="0db22-123">Třída implementace služby <xref:System.ServiceModel.InstanceContextMode.PerSession> implementuje instance udržovat samostatnou instanci třídy pro každého klienta, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="0db22-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="0db22-124">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="0db22-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0db22-125">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="0db22-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0db22-126">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="0db22-126">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0db22-127">Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="0db22-127">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="0db22-128">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0db22-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="0db22-129">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0db22-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="0db22-130">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0db22-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  

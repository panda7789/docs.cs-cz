---
title: Spolehlivá relace WS
ms.date: 03/30/2017
helpviewer_keywords:
- Reliable session
ms.assetid: 86e914f2-060b-432b-bd17-333695317745
ms.openlocfilehash: 68123ba9a273bf2c1eaa7b3747930ebca386064b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84589692"
---
# <a name="ws-reliable-session"></a><span data-ttu-id="f0865-102">Spolehlivá relace WS</span><span class="sxs-lookup"><span data-stu-id="f0865-102">WS Reliable Session</span></span>
<span data-ttu-id="f0865-103">Tato ukázka demonstruje použití spolehlivých relací.</span><span class="sxs-lookup"><span data-stu-id="f0865-103">This sample demonstrates the use of reliable sessions.</span></span> <span data-ttu-id="f0865-104">Spolehlivé relace poskytují podporu pro spolehlivé zasílání zpráv a relací.</span><span class="sxs-lookup"><span data-stu-id="f0865-104">Reliable sessions provide support for reliable messaging and sessions.</span></span> <span data-ttu-id="f0865-105">Spolehlivé zasílání zpráv zopakuje komunikaci při selhání a umožňuje zadat záruky doručování, například doručení zpráv v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f0865-105">Reliable messaging retries communication on failure and allows delivery assurances to be specified, such as in-order arrival of messages.</span></span> <span data-ttu-id="f0865-106">Relace uchovávají stav pro klienty mezi voláními.</span><span class="sxs-lookup"><span data-stu-id="f0865-106">Sessions maintain state for clients between calls.</span></span> <span data-ttu-id="f0865-107">Ukázka implementuje relace pro udržování stavu klienta a určuje záruku doručení v daném pořadí.</span><span class="sxs-lookup"><span data-stu-id="f0865-107">The sample implements sessions for maintaining client state and specifies in-order delivery assurances.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="f0865-108">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="f0865-108">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f0865-109">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="f0865-109">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="f0865-110">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="f0865-110">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f0865-111">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="f0865-111">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsReliableSession`  
  
 <span data-ttu-id="f0865-112">Tato ukázka je založená na [Začínáme](getting-started-sample.md) , která implementuje službu kalkulačky.</span><span class="sxs-lookup"><span data-stu-id="f0865-112">This sample is based on the [Getting Started](getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="f0865-113">Funkce spolehlivé relace jsou povolené a nakonfigurované v konfiguračních souborech aplikací pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="f0865-113">The reliable session features are enabled and configured in the application configuration files for the client and service.</span></span>  
  
 <span data-ttu-id="f0865-114">V této ukázce je služba hostovaná ve službě Internetová informační služba (IIS) a klient je Konzolová aplikace (. exe).</span><span class="sxs-lookup"><span data-stu-id="f0865-114">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="f0865-115">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="f0865-115">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="f0865-116">Ukázka používá `wsHttpBinding` .</span><span class="sxs-lookup"><span data-stu-id="f0865-116">The sample uses the `wsHttpBinding`.</span></span> <span data-ttu-id="f0865-117">Vazba je určena v konfiguračních souborech pro klienta i službu.</span><span class="sxs-lookup"><span data-stu-id="f0865-117">The binding is specified in the configuration files for both the client and service.</span></span> <span data-ttu-id="f0865-118">Typ vazby je zadán v atributu elementu koncového bodu `binding` , jak je znázorněno v následující ukázkové konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="f0865-118">The binding type is specified in the endpoint element’s `binding` attribute as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address=""  
          binding="wsHttpBinding"  
          bindingConfiguration="Binding1"
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="f0865-119">Koncový bod obsahuje `bindingConfiguration` atribut, který odkazuje na konfiguraci vazby s názvem "Binding1".</span><span class="sxs-lookup"><span data-stu-id="f0865-119">The endpoint contains a `bindingConfiguration` attribute that references a binding configuration named "Binding1."</span></span> <span data-ttu-id="f0865-120">Konfigurace vazby umožňuje spolehlivé relace nastavením `enabled` atributu [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) na `true` .</span><span class="sxs-lookup"><span data-stu-id="f0865-120">The binding configuration enables reliable sessions by setting the `enabled` attribute of the [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) to `true`.</span></span> <span data-ttu-id="f0865-121">Záruky doručení pro seřazené relace jsou ovládány nastavením seřazeného atributu na `true` nebo `false` .</span><span class="sxs-lookup"><span data-stu-id="f0865-121">Delivery assurances for ordered sessions are controlled by setting the ordered attribute to `true` or `false`.</span></span> <span data-ttu-id="f0865-122">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="f0865-122">The default is `true`.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding name="Binding1">  
            <reliableSession enabled="true" />  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="f0865-123">Třída implementace služby implementuje vytváření <xref:System.ServiceModel.InstanceContextMode.PerSession> instancí pro udržování samostatné instance třídy pro každého klienta, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="f0865-123">The service implementation class implements <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing to maintain a separate class instance for each client, as shown in the following sample code.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)] public class CalculatorService : ICalculator  
{  
    ...  
}  
```
  
 <span data-ttu-id="f0865-124">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="f0865-124">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="f0865-125">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="f0865-125">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="f0865-126">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="f0865-126">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="f0865-127">Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.</span><span class="sxs-lookup"><span data-stu-id="f0865-127">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="f0865-128">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f0865-128">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="f0865-129">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f0865-129">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="f0865-130">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="f0865-130">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  

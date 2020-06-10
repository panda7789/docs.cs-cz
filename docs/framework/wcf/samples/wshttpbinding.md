---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: a78eac52095d3f647efdacc9104a75e46651f389
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596368"
---
# <a name="wshttpbinding"></a><span data-ttu-id="feb59-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="feb59-102">WSHttpBinding</span></span>
<span data-ttu-id="feb59-103">Tato ukázka předvádí, jak implementovat typickou službu a typický klient pomocí Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="feb59-103">This sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="feb59-104">Tato ukázka se skládá z programu klientské konzoly (Client. exe) a knihovny služeb hostované službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="feb59-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="feb59-105">Služba implementuje kontrakt definující způsob komunikace požadavek-odpověď.</span><span class="sxs-lookup"><span data-stu-id="feb59-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="feb59-106">Kontrakt je definován `ICalculator` rozhraním, které zpřístupňuje matematické operace (sčítání, odčítání, násobení a dělení).</span><span class="sxs-lookup"><span data-stu-id="feb59-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="feb59-107">Klient provádí synchronní požadavky na určitou matematickou operaci a služba odpovídá výsledku.</span><span class="sxs-lookup"><span data-stu-id="feb59-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="feb59-108">Aktivita klienta se zobrazí v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="feb59-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="feb59-109">Ukázky už můžou být na vašem počítači nainstalované.</span><span class="sxs-lookup"><span data-stu-id="feb59-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="feb59-110">Než budete pokračovat, vyhledejte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="feb59-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="feb59-111">Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek.</span><span class="sxs-lookup"><span data-stu-id="feb59-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="feb59-112">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="feb59-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> <span data-ttu-id="feb59-113">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="feb59-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="feb59-114">Tato ukázka zveřejňuje `ICalculator` kontrakt pomocí [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="feb59-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="feb59-115">Konfigurace této vazby byla rozšířena v souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="feb59-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
```xml
<bindings>  
  <wsHttpBinding>  
    <!--The following is the expanded configuration section for a-->  
    <!--WSHttpBinding. Each property is configured with the default-->
    <!--value. See the ReliableSession, TransactionFlow, -->  
    <!--TransportSecurity, and MessageSecurity samples in the WS -->  
    <!--directory to learn how to configure these features. -->  
    <binding name="Binding1"  
              bypassProxyOnLocal="false"
              transactionFlow="false"
              hostNameComparisonMode="StrongWildcard"  
              maxBufferPoolSize="524288"
              maxReceivedMessageSize="65536"  
              messageEncoding="Text"
              textEncoding="utf-8"
              useDefaultWebProxy="true"  
              allowCookies="false">  
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"  
                       enabled="false" />  
      <security mode="Message">  
        <message clientCredentialType="Windows"
                 negotiateServiceCredential="true"  
                 algorithmSuite="Default"
                 establishSecurityContext="true" />  
      </security>  
    </binding>  
  </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="feb59-116">Na základním `binding` prvku `maxReceivedMessageSize` hodnota vám umožní nakonfigurovat maximální velikost příchozí zprávy (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="feb59-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="feb59-117">`hostNameComparisonMode`Hodnota umožňuje nakonfigurovat, jestli se má název hostitele považovat za při demultiplexování zprávy službě.</span><span class="sxs-lookup"><span data-stu-id="feb59-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="feb59-118">`messageEncoding`Hodnota umožňuje nakonfigurovat, zda má být pro zprávy použit text nebo kódování MTOM.</span><span class="sxs-lookup"><span data-stu-id="feb59-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="feb59-119">`textEncoding`Hodnota umožňuje nakonfigurovat kódování znaků pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="feb59-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="feb59-120">`bypassProxyOnLocal`Hodnota umožňuje nakonfigurovat, jestli se má používat proxy server HTTP pro místní komunikaci.</span><span class="sxs-lookup"><span data-stu-id="feb59-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="feb59-121">`transactionFlow`Hodnota určuje, zda je aktuální transakce předávána (Pokud je operace konfigurovaná pro tok transakce).</span><span class="sxs-lookup"><span data-stu-id="feb59-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="feb59-122">U [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) elementu je povolená logická hodnota nakonfiguruje, jestli jsou povolené spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="feb59-122">On the [\<reliableSession>](../../configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="feb59-123">`ordered`Hodnota určuje, zda je zachováváno řazení zpráv.</span><span class="sxs-lookup"><span data-stu-id="feb59-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="feb59-124">`inactivityTimeout`Hodnota určuje, jak dlouho může být relace nečinná, než bude chyba.</span><span class="sxs-lookup"><span data-stu-id="feb59-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="feb59-125">Na rozhraní [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `mode` určuje hodnota, který režim zabezpečení má být použit.</span><span class="sxs-lookup"><span data-stu-id="feb59-125">On the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="feb59-126">V této ukázce se používá zabezpečení zpráv, což je důvod, proč [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) je specifikován v [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="feb59-126">In this sample, messages security is being used, which is why the [\<message>](../../configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="feb59-127">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="feb59-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="feb59-128">V okně klienta stiskněte klávesu ENTER pro vypnutí klienta.</span><span class="sxs-lookup"><span data-stu-id="feb59-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="feb59-129">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="feb59-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="feb59-130">Pomocí následujícího příkazu nainstalujte ASP.NET 4,0.</span><span class="sxs-lookup"><span data-stu-id="feb59-130">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="feb59-131">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="feb59-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="feb59-132">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="feb59-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="feb59-133">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="feb59-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  

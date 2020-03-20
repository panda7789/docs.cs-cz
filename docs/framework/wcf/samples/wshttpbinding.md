---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: c54cbf1fe881ef2ce5dffb0bc0c6dac4049135b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143366"
---
# <a name="wshttpbinding"></a><span data-ttu-id="5b6d3-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="5b6d3-102">WSHttpBinding</span></span>
<span data-ttu-id="5b6d3-103">Tato ukázka ukazuje, jak implementovat typické služby a typické klienta pomocí Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="5b6d3-103">This sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="5b6d3-104">Tato ukázka se skládá z programu klientské konzole (client.exe) a knihovny služeb hostované internetovou informační službou (IIS).</span><span class="sxs-lookup"><span data-stu-id="5b6d3-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="5b6d3-105">Služba implementuje smlouvu, která definuje vzor komunikace požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="5b6d3-106">Kontrakt je definován `ICalculator` rozhraním, které zveřejňuje matematické operace (sčítání, odčítání, násobení a dělení).</span><span class="sxs-lookup"><span data-stu-id="5b6d3-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="5b6d3-107">Klient provádí synchronní požadavky na danou operaci matematiky a odpovědi služby s výsledkem.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="5b6d3-108">Aktivita klienta je viditelná v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5b6d3-109">Ukázky mohou být již nainstalovány v počítači.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="5b6d3-110">Před pokračováním zkontrolujte následující (výchozí) adresář.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-110">Check for the following (default) directory before continuing.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> <span data-ttu-id="5b6d3-111">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="5b6d3-112">Tato ukázka je umístěna v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-112">This sample is located in the following directory.</span></span>  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
> <span data-ttu-id="5b6d3-113">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="5b6d3-114">Tato ukázka `ICalculator` zveřejňuje smlouvy pomocí [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="5b6d3-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="5b6d3-115">Konfigurace této vazby byla rozšířena v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
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
  
 <span data-ttu-id="5b6d3-116">Na základní `binding` prvek `maxReceivedMessageSize` hodnota umožňuje nakonfigurovat maximální velikost příchozí zprávy (v bajtů).</span><span class="sxs-lookup"><span data-stu-id="5b6d3-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="5b6d3-117">Hodnota `hostNameComparisonMode` umožňuje nakonfigurovat, zda je název hostitele považován při de-multiplexování zpráv do služby.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="5b6d3-118">Hodnota `messageEncoding` umožňuje nakonfigurovat, zda chcete pro zprávy použít kódování textu nebo mtom.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="5b6d3-119">Hodnota `textEncoding` umožňuje konfigurovat kódování znaků pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="5b6d3-120">Hodnota `bypassProxyOnLocal` umožňuje nakonfigurovat, zda chcete použít proxy server HTTP pro místní komunikaci.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="5b6d3-121">Hodnota `transactionFlow` konfiguruje, zda je aktuální transakce tok (pokud je operace nakonfigurována pro tok transakce).</span><span class="sxs-lookup"><span data-stu-id="5b6d3-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="5b6d3-122">U prvku [ \<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) nakonfiguruje povolená logická hodnota, zda jsou povoleny spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-122">On the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="5b6d3-123">Hodnota `ordered` konfiguruje, zda je zachováno řazení zpráv.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="5b6d3-124">Hodnota `inactivityTimeout` konfiguruje, jak dlouho může být relace nečinná před chybou.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="5b6d3-125">V [ \<>zabezpečení ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) `mode` hodnota konfiguruje, který režim zabezpečení by měl být použit.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-125">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="5b6d3-126">V této ukázce se používá zabezpečení zpráv, což je důvod, proč je [ \<zpráva>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) zadána [ \< ](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)uvnitř>zabezpečení .</span><span class="sxs-lookup"><span data-stu-id="5b6d3-126">In this sample, messages security is being used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="5b6d3-127">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="5b6d3-128">Stisknutím klávesy ENTER v okně klienta vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```console  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="5b6d3-129">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="5b6d3-129">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="5b6d3-130">Nainstalujte ASP.NET 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="5b6d3-130">Install ASP.NET 4.0 using the following command.</span></span>  
  
    ```console
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2. <span data-ttu-id="5b6d3-131">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5b6d3-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3. <span data-ttu-id="5b6d3-132">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5b6d3-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4. <span data-ttu-id="5b6d3-133">Chcete-li spustit ukázku v konfiguraci jednoho nebo více počítačů, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="5b6d3-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  

---
title: WSHttpBinding
ms.date: 03/30/2017
helpviewer_keywords:
- WS Profile binding
ms.assetid: 22d85b19-0135-4141-9179-a0e9c343ad73
ms.openlocfilehash: 333fe946f82d7bee92f5d29f079eb262297cdf8f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556584"
---
# <a name="wshttpbinding"></a><span data-ttu-id="676c3-102">WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="676c3-102">WSHttpBinding</span></span>
<span data-ttu-id="676c3-103">Tento příklad ukazuje, jak implementovat typické služby a typické klienta pomocí Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="676c3-103">This sample demonstrates how to implement a typical service and a typical client using Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="676c3-104">Tento příklad se skládá z programu konzoly klienta (client.exe) a knihovna služby hostované v Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="676c3-104">This sample consists of a client console program (client.exe) and a service library hosted by Internet Information Services (IIS).</span></span> <span data-ttu-id="676c3-105">Služba implementuje kontrakt, který definuje vzor komunikace požadavek odpověď.</span><span class="sxs-lookup"><span data-stu-id="676c3-105">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="676c3-106">Smlouva je definován `ICalculator` rozhraní, které zveřejňuje matematických operací (Přidat odečíst, násobení a dělení).</span><span class="sxs-lookup"><span data-stu-id="676c3-106">The contract is defined by the `ICalculator` interface, which exposes math operations (add, subtract, multiply, and divide).</span></span> <span data-ttu-id="676c3-107">Klient podá synchronní žádosti a odpovědi služby s výsledkem dané matematické operace.</span><span class="sxs-lookup"><span data-stu-id="676c3-107">The client makes synchronous requests to a given math operation and the service replies with the result.</span></span> <span data-ttu-id="676c3-108">Činnost klienta je vidět v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="676c3-108">Client activity is visible in the console window.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="676c3-109">Vzorky mohou již být nainstalováno na svém počítači.</span><span class="sxs-lookup"><span data-stu-id="676c3-109">The samples may already be installed on your machine.</span></span> <span data-ttu-id="676c3-110">Před pokračováním zkontrolujte následující adresář (výchozí).</span><span class="sxs-lookup"><span data-stu-id="676c3-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="676c3-111">Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky.</span><span class="sxs-lookup"><span data-stu-id="676c3-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="676c3-112">Tato ukázka se nachází v následujícím adresáři.</span><span class="sxs-lookup"><span data-stu-id="676c3-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\WS\wsHttp`  
  
> [!NOTE]
>  <span data-ttu-id="676c3-113">Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="676c3-113">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="676c3-114">Tato ukázka poskytuje `ICalculator` smlouvy pomocí [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="676c3-114">This sample exposes the `ICalculator` contract using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="676c3-115">Došlo k rozbalení konfiguraci této vazby v souboru Web.config.</span><span class="sxs-lookup"><span data-stu-id="676c3-115">The configuration of this binding has been expanded in the Web.config file.</span></span>  
  
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
  
 <span data-ttu-id="676c3-116">V základní třídě `binding` elementu, `maxReceivedMessageSize` hodnota umožňuje nakonfigurovat maximální velikost příchozí zprávy (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="676c3-116">On the base `binding` element, the `maxReceivedMessageSize` value lets you configure the maximum size of an incoming message (in bytes).</span></span> <span data-ttu-id="676c3-117">`hostNameComparisonMode` Hodnota umožňuje nakonfigurovat, jestli název hostitele je považován za multiplexingu rušit při zprávy do služby.</span><span class="sxs-lookup"><span data-stu-id="676c3-117">The `hostNameComparisonMode` value lets you configure whether the hostname is considered when de-multiplexing messages to the service.</span></span> <span data-ttu-id="676c3-118">`messageEncoding` Hodnota vám umožní nakonfigurovat, jestli se má používat Text nebo MTOM kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="676c3-118">The `messageEncoding` value lets you configure whether to use Text or MTOM encoding for messages.</span></span> <span data-ttu-id="676c3-119">`textEncoding` Hodnota vám umožní nakonfigurovat kódování znaků pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="676c3-119">The `textEncoding` value lets you configure the character encoding for messages.</span></span> <span data-ttu-id="676c3-120">`bypassProxyOnLocal` Hodnota vám umožní nakonfigurovat, jestli se má používat proxy server HTTP pro místní komunikace.</span><span class="sxs-lookup"><span data-stu-id="676c3-120">The `bypassProxyOnLocal` value lets you configure whether to use an HTTP proxy for local communication.</span></span> <span data-ttu-id="676c3-121">`transactionFlow` Hodnota konfiguruje, zda se aktuální transakce je naplněn (Pokud je operace je nakonfigurována pro tok transakcí).</span><span class="sxs-lookup"><span data-stu-id="676c3-121">The `transactionFlow` value configures whether the current transaction is flowed (if an operation is configured for transaction flow).</span></span>  
  
 <span data-ttu-id="676c3-122">Na [ \<reliableSession >](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, povolené logická hodnota konfiguruje, zda jsou povoleny spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="676c3-122">On the [\<reliableSession>](../../../../docs/framework/configure-apps/file-schema/wcf/reliablesession.md) element, the enabled Boolean value configures whether reliable sessions are enabled.</span></span> <span data-ttu-id="676c3-123">`ordered` Hodnota konfiguruje, zda zpráva pořadí je zachováno.</span><span class="sxs-lookup"><span data-stu-id="676c3-123">The `ordered` value configures whether message ordering is preserved.</span></span> <span data-ttu-id="676c3-124">`inactivityTimeout` Hodnota konfiguruje, jak dlouho může být relace nečinná, než se došlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="676c3-124">The `inactivityTimeout` value configures how long a session can be idle before being faulted.</span></span>  
  
 <span data-ttu-id="676c3-125">Na [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), `mode` hodnota konfiguruje, který režim zabezpečení by měl sloužit.</span><span class="sxs-lookup"><span data-stu-id="676c3-125">On the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md), the `mode` value configures which security mode should be used.</span></span> <span data-ttu-id="676c3-126">V této ukázce zabezpečení zprávy se používá, což je důvod, proč [ \<zpráva >](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) je zadat v rámci [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="676c3-126">In this sample, messages security is being used, which is why the [\<message>](../../../../docs/framework/configure-apps/file-schema/wcf/message-of-wshttpbinding.md) is specified inside the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md).</span></span>  
  
 <span data-ttu-id="676c3-127">Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="676c3-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="676c3-128">Stisknutím klávesy ENTER v okně Klient vypnutí klient.</span><span class="sxs-lookup"><span data-stu-id="676c3-128">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="676c3-129">Chcete-li nastavit, sestavte a spusťte ukázku</span><span class="sxs-lookup"><span data-stu-id="676c3-129">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="676c3-130">Nainstalujte [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 pomocí následujícího příkazu.</span><span class="sxs-lookup"><span data-stu-id="676c3-130">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="676c3-131">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="676c3-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="676c3-132">K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="676c3-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="676c3-133">Spusťte ukázku v konfiguraci s jedním nebo více počítačů, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="676c3-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="676c3-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="676c3-134">See also</span></span>

---
title: Zabezpečení zpráv – Windows
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
ms.openlocfilehash: f46eb12078082614cd6cdc75b7bc7eedb7c94de9
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69930433"
---
# <a name="message-security-windows"></a><span data-ttu-id="53168-102">Zabezpečení zpráv – Windows</span><span class="sxs-lookup"><span data-stu-id="53168-102">Message Security Windows</span></span>
<span data-ttu-id="53168-103">Tato ukázka předvádí, jak nakonfigurovat <xref:System.ServiceModel.WSHttpBinding> vazbu na použití zabezpečení na úrovni zprávy s ověřováním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="53168-103">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span> <span data-ttu-id="53168-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="53168-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="53168-105">V této ukázce je služba hostovaná ve službě Internetová informační služba (IIS) a klient je Konzolová aplikace (. exe).</span><span class="sxs-lookup"><span data-stu-id="53168-105">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="53168-106">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="53168-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="53168-107">Výchozím zabezpečením [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) je zabezpečení zpráv pomocí ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="53168-107">The default security for the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) is message security using Windows authentication.</span></span> <span data-ttu-id="53168-108">Konfigurační soubory v této ukázce explicitně nastavily `mode` atribut [ \<> zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) na `Message` a `clientCredentialType` atribut na `Windows`.</span><span class="sxs-lookup"><span data-stu-id="53168-108">The configuration files in this sample explicitly set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) to `Message` and the `clientCredentialType` attribute to `Windows`.</span></span> <span data-ttu-id="53168-109">Tyto hodnoty jsou výchozími hodnotami pro tuto vazbu, ale byly explicitně nakonfigurovány, jak je znázorněno v následující ukázkové konfiguraci k předvedení jejich použití.</span><span class="sxs-lookup"><span data-stu-id="53168-109">These values are the default values for this binding, but they have been explicitly configured, as shown in the following sample configuration to demonstrate their use.</span></span>  
  
```xml  
<bindings>  
    <wsHttpBinding>  
        <binding>  
            <security mode="Message">  
                <message clientCredentialType="Windows"/>  
            </security>  
        </binding>  
    </wsHttpBinding>  
</bindings>  
```  
  
 <span data-ttu-id="53168-110">Konfigurace koncového bodu klienta se skládá z absolutní adresy koncového bodu služby, vazby a kontraktu.</span><span class="sxs-lookup"><span data-stu-id="53168-110">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="53168-111">Vazba klienta je nakonfigurovaná s odpovídajícími `securityMode` a `authenticationMode`.</span><span class="sxs-lookup"><span data-stu-id="53168-111">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span>  
  
```xml  
<system.serviceModel>  
  <client>  
    <endpoint address=  
            "http://localhost/servicemodelsamples/service.svc"   
            binding="wsHttpBinding"   
            bindingConfiguration="Binding1"   
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  </client>  
  
  <bindings>  
    <wsHttpBinding>  
      <!-- The default security for the WSHttpBinding is -->  
      <!-- Message security using Windows authentication. -->  
      <!-- This configuration explicitly defines the security mode -->  
      <!-- as Message and the clientCredentialType as Windows -->  
      <!-- for demonstration purposes. -->  
      <binding name="Binding1">  
        <security mode="Message">  
          <message clientCredentialType="Windows"/>  
        </security>  
      </binding>  
    </wsHttpBinding>  
  </bindings>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="53168-112">Zdrojový kód služby byl upraven, aby ukázal, jak <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> lze použít k přístupu k identitě volajícího.</span><span class="sxs-lookup"><span data-stu-id="53168-112">The service source code has been modified to demonstrate how the <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> can be used to access the identity of the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="53168-113">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="53168-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="53168-114">První metoda se nazývá – `GetCallerIdentity` vrátí název identity volajícího zpátky klientovi.</span><span class="sxs-lookup"><span data-stu-id="53168-114">The first method called - `GetCallerIdentity` - returns the name of the caller identity back to the client.</span></span> <span data-ttu-id="53168-115">Ukončete klienta stisknutím klávesy ENTER v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="53168-115">Press ENTER in the console window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="53168-116">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="53168-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="53168-117">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="53168-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="53168-118">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="53168-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="53168-119">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="53168-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  

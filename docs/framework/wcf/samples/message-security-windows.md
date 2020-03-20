---
title: Zabezpečení zpráv – Windows
ms.date: 03/30/2017
helpviewer_keywords:
- WS Security
ms.assetid: d2221d1c-c9cb-48d1-b044-a3b4445c7f05
ms.openlocfilehash: 8706eee341dd1a5852efae0aad5195e09f62fec4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183498"
---
# <a name="message-security-windows"></a><span data-ttu-id="925fc-102">Zabezpečení zpráv – Windows</span><span class="sxs-lookup"><span data-stu-id="925fc-102">Message Security Windows</span></span>
<span data-ttu-id="925fc-103">Tato ukázka ukazuje, <xref:System.ServiceModel.WSHttpBinding> jak nakonfigurovat vazbu pro použití zabezpečení na úrovni zprávy s ověřováním systému Windows.</span><span class="sxs-lookup"><span data-stu-id="925fc-103">This sample demonstrates how to configure a <xref:System.ServiceModel.WSHttpBinding> binding to use message-level security with Windows authentication.</span></span> <span data-ttu-id="925fc-104">Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="925fc-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="925fc-105">V této ukázce je služba hostována v Internetové informační službě (IIS) a klient je konzolová aplikace (.exe).</span><span class="sxs-lookup"><span data-stu-id="925fc-105">In this sample, the service is hosted in Internet Information Services (IIS) and the client is a console application (.exe).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="925fc-106">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="925fc-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="925fc-107">Výchozí zabezpečení [ \<pro>wsHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) je zabezpečení zpráv pomocí ověřování systému Windows.</span><span class="sxs-lookup"><span data-stu-id="925fc-107">The default security for the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) is message security using Windows authentication.</span></span> <span data-ttu-id="925fc-108">Konfigurační soubory v `mode` této ukázce `Message` explicitně nastavují atribut>[ \<zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) a `clientCredentialType` atribut `Windows`.</span><span class="sxs-lookup"><span data-stu-id="925fc-108">The configuration files in this sample explicitly set the `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md) to `Message` and the `clientCredentialType` attribute to `Windows`.</span></span> <span data-ttu-id="925fc-109">Tyto hodnoty jsou výchozí hodnoty pro tuto vazbu, ale byly explicitně nakonfigurovány, jak je znázorněno v následující ukázkové konfiguraci k prokázání jejich použití.</span><span class="sxs-lookup"><span data-stu-id="925fc-109">These values are the default values for this binding, but they have been explicitly configured, as shown in the following sample configuration to demonstrate their use.</span></span>  
  
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
  
 <span data-ttu-id="925fc-110">Konfigurace koncového bodu klienta se skládá z absolutní adresy pro koncový bod služby, vazbu a smlouvu.</span><span class="sxs-lookup"><span data-stu-id="925fc-110">The client endpoint configuration consists of an absolute address for the service endpoint, the binding, and the contract.</span></span> <span data-ttu-id="925fc-111">Vazby klienta je `securityMode` nakonfigurován s příslušnou a `authenticationMode`.</span><span class="sxs-lookup"><span data-stu-id="925fc-111">The client binding is configured with the appropriate `securityMode` and `authenticationMode`.</span></span>  
  
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
  
 <span data-ttu-id="925fc-112">Zdrojový kód služby byl upraven <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> tak, aby demonstroval, jak lze použít pro přístup k identitě volajícího.</span><span class="sxs-lookup"><span data-stu-id="925fc-112">The service source code has been modified to demonstrate how the <xref:System.ServiceModel.OperationContext.ServiceSecurityContext%2A> can be used to access the identity of the caller.</span></span>  

```csharp
public string GetCallerIdentity()  
{  
    // The Windows identity of the caller can be accessed on the ServiceSecurityContext.WindowsIdentity.  
    return OperationContext.Current.ServiceSecurityContext.WindowsIdentity.Name;  
}  
```

 <span data-ttu-id="925fc-113">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="925fc-113">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="925fc-114">První metoda s `GetCallerIdentity` názvem - - vrátí název volající identity zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="925fc-114">The first method called - `GetCallerIdentity` - returns the name of the caller identity back to the client.</span></span> <span data-ttu-id="925fc-115">Stisknutím klávesy ENTER v okně konzoly vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="925fc-115">Press ENTER in the console window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="925fc-116">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="925fc-116">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="925fc-117">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="925fc-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="925fc-118">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="925fc-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="925fc-119">Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="925fc-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  

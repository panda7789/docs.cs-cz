---
title: Autorizace přístupu k operacím služby
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: a0ea82c876b3bd8c2a3218f84399fbb69e1d0080
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932501"
---
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="00492-102">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="00492-102">Authorizing Access to Service Operations</span></span>
<span data-ttu-id="00492-103">Tato ukázka předvádí, <xref:System.Security.Permissions.PrincipalPermissionAttribute> [ \<jak použít > serviceAuthorization](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) k povolení použití atributu k autorizaci přístupu k operacím služby.</span><span class="sxs-lookup"><span data-stu-id="00492-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="00492-104">Tato ukázka je založená na ukázce [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) .</span><span class="sxs-lookup"><span data-stu-id="00492-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) sample.</span></span> <span data-ttu-id="00492-105">Služba a klient se nakonfigurují pomocí [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="00492-105">The service and client are configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="00492-106">`Message` `clientCredentialType`Atribut> zabezpečení byl nastaven na hodnotu a byl nastaven na `Windows`hodnotu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) `mode`</span><span class="sxs-lookup"><span data-stu-id="00492-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="00492-107"><xref:System.Security.Permissions.PrincipalPermissionAttribute> Je použit pro každou metodu služby a slouží k omezení přístupu ke každé operaci.</span><span class="sxs-lookup"><span data-stu-id="00492-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="00492-108">Pro přístup k jednotlivým operacím volající musí být správcem systému Windows.</span><span class="sxs-lookup"><span data-stu-id="00492-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="00492-109">V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="00492-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="00492-110">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="00492-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="00492-111">Konfigurační soubor služby používá [ \<> serviceAuthorization](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) k nastavení `principalPermissionMode` atributu:</span><span class="sxs-lookup"><span data-stu-id="00492-111">The service configuration file uses the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior>   
      <!-- The serviceAuthorization behavior sets the  
           principalPermissionMode to UseWindowsGroups.  
           This puts a WindowsPrincipal on the current thread when a   
           service is invoked. -->  
      <serviceAuthorization principalPermissionMode="UseWindowsGroups" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="00492-112">Nastavení, `principalPermissionMode` které `UseWindowsGroups` povolí použití <xref:System.Security.Permissions.PrincipalPermissionAttribute> v závislosti na názvech skupin systému Windows.</span><span class="sxs-lookup"><span data-stu-id="00492-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="00492-113"><xref:System.Security.Permissions.PrincipalPermissionAttribute> Je použita na každou operaci, aby bylo vyžadováno, aby volající byl součástí skupiny správců systému Windows, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="00492-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="00492-114">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="00492-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="00492-115">Klient úspěšně komunikuje s každou operací, pokud je spuštěn pod účtem, který je součástí skupiny správců. v opačném případě přístup je odepřen.</span><span class="sxs-lookup"><span data-stu-id="00492-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="00492-116">Pokud chcete experimentovat s chybou autorizace, spusťte klienta pod účtem, který není součástí skupiny správců.</span><span class="sxs-lookup"><span data-stu-id="00492-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="00492-117">Ukončete klienta stisknutím klávesy ENTER v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="00492-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="00492-118">Služba může být upozorněna na selhání autorizace implementací <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span><span class="sxs-lookup"><span data-stu-id="00492-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="00492-119">Viz [rozšíření kontroly nad zpracováním chyb a vytváření sestav](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) pro informace `IErrorHandler`o implementaci.</span><span class="sxs-lookup"><span data-stu-id="00492-119">See [Extending Control Over Error Handling and Reporting](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="00492-120">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="00492-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="00492-121">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="00492-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="00492-122">Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="00492-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="00492-123">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="00492-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  

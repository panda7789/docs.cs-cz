---
title: "Autorizace přístupu k operacím služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
caps.latest.revision: "23"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: cfa1eefa9f7bd940baf3796d92ac7b49e0f9843e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="895dd-102">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="895dd-102">Authorizing Access to Service Operations</span></span>
<span data-ttu-id="895dd-103">Tento příklad znázorňuje způsob použití [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) povolit používání <xref:System.Security.Permissions.PrincipalPermissionAttribute> atribut k autorizaci přístupu k operacím služby.</span><span class="sxs-lookup"><span data-stu-id="895dd-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="895dd-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md) ukázka.</span><span class="sxs-lookup"><span data-stu-id="895dd-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) sample.</span></span> <span data-ttu-id="895dd-105">Klienta a služby jsou konfigurováni pomocí [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="895dd-105">The service and client are configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="895dd-106">`mode` Atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) byla nastavena na `Message` a `clientCredentialType` byla nastavena na `Windows`.</span><span class="sxs-lookup"><span data-stu-id="895dd-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="895dd-107"><xref:System.Security.Permissions.PrincipalPermissionAttribute> Je použít pro každou metodu služby a slouží k omezení přístupu na každou operaci.</span><span class="sxs-lookup"><span data-stu-id="895dd-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="895dd-108">Volající musí být správcem systému Windows pro přístup k jednotlivých operací.</span><span class="sxs-lookup"><span data-stu-id="895dd-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="895dd-109">V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="895dd-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="895dd-110">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="895dd-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="895dd-111">Konfigurační soubor služby používá [ \<serviceAuthorization >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) nastavit `principalPermissionMode` atribut:</span><span class="sxs-lookup"><span data-stu-id="895dd-111">The service configuration file uses the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
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
  
 <span data-ttu-id="895dd-112">Nastavení `principalPermissionMode` k `UseWindowsGroups` umožňuje použití <xref:System.Security.Permissions.PrincipalPermissionAttribute> podle názvů skupin systému Windows.</span><span class="sxs-lookup"><span data-stu-id="895dd-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="895dd-113"><xref:System.Security.Permissions.PrincipalPermissionAttribute> Se použijí na každou operaci tak, aby vyžadovala volajícího, aby být součástí skupiny administrators systému Windows, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="895dd-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```  
[PrincipalPermission(SecurityAction.Demand,   
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="895dd-114">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="895dd-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="895dd-115">Klient úspěšně komunikuje s každou operaci, pokud je spuštěn pod účtem, který je součástí skupiny Administrators; jinak byl odepřen přístup.</span><span class="sxs-lookup"><span data-stu-id="895dd-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="895dd-116">A experimentovat s selhání autorizace, spusťte klienta pod účtem, který není součástí skupiny Administrators.</span><span class="sxs-lookup"><span data-stu-id="895dd-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="895dd-117">Stisknutím klávesy ENTER v okně konzoly vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="895dd-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="895dd-118">Službu můžete informováni o selhání ověřování implementací <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span><span class="sxs-lookup"><span data-stu-id="895dd-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="895dd-119">V tématu [rozšíření řízení přes zpracování chyb a generování sestav](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) informace o implementaci `IErrorHandler`.</span><span class="sxs-lookup"><span data-stu-id="895dd-119">See [Extending Control Over Error Handling and Reporting](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="895dd-120">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="895dd-120">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="895dd-121">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="895dd-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="895dd-122">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="895dd-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="895dd-123">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="895dd-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="895dd-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="895dd-124">See Also</span></span>

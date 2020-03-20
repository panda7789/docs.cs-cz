---
title: Autorizace přístupu k operacím služby
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, authorizing access sample
- Authorizing Access To Service Operations Sample [Windows Communication Foundation]
- authorization, Windows Communication Foundation sample
ms.assetid: ddcfdaa5-8b2e-4e13-bd85-887209dc6328
ms.openlocfilehash: c2ad6977674666ef65df1ea4cfe58cfd4bff8b69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183929"
---
# <a name="authorizing-access-to-service-operations"></a><span data-ttu-id="0223c-102">Autorizace přístupu k operacím služby</span><span class="sxs-lookup"><span data-stu-id="0223c-102">Authorizing Access to Service Operations</span></span>
<span data-ttu-id="0223c-103">Tento příklad ukazuje, jak používat [ \<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) <xref:System.Security.Permissions.PrincipalPermissionAttribute> povolit použití atributu povolit přístup k operacím služby.</span><span class="sxs-lookup"><span data-stu-id="0223c-103">This sample demonstrates how to use the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to enable use of the <xref:System.Security.Permissions.PrincipalPermissionAttribute> attribute to authorize access to service operations.</span></span> <span data-ttu-id="0223c-104">Tato ukázka je založena na [ukázce Začínáme.](../../../../docs/framework/wcf/samples/getting-started-sample.md)</span><span class="sxs-lookup"><span data-stu-id="0223c-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) sample.</span></span> <span data-ttu-id="0223c-105">Služba a klient jsou konfigurovány [ \<pomocí wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="0223c-105">The service and client are configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="0223c-106">Atribut `mode` [ \<>zabezpečení](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) byl nastaven `Message` na `clientCredentialType` a byl `Windows`nastaven na .</span><span class="sxs-lookup"><span data-stu-id="0223c-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="0223c-107">Použije <xref:System.Security.Permissions.PrincipalPermissionAttribute> se pro každou metodu služby a slouží k omezení přístupu ke každé operaci.</span><span class="sxs-lookup"><span data-stu-id="0223c-107">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each service method and used to restrict access to each operation.</span></span> <span data-ttu-id="0223c-108">Volající musí být správce systému Windows pro přístup ke každé operaci.</span><span class="sxs-lookup"><span data-stu-id="0223c-108">The caller must be a Windows administrator to access each operation.</span></span>  
  
 <span data-ttu-id="0223c-109">V této ukázce je klient konzolovou aplikací (.exe) a služba je hostována internetovou informační službou (IIS).</span><span class="sxs-lookup"><span data-stu-id="0223c-109">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0223c-110">Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="0223c-110">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0223c-111">Konfigurační soubor služby používá `principalPermissionMode` k nastavení atributu [ \<>serviceAuthorization:](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md)</span><span class="sxs-lookup"><span data-stu-id="0223c-111">The service configuration file uses the [\<serviceAuthorization>](../../../../docs/framework/configure-apps/file-schema/wcf/serviceauthorization-element.md) to set the `principalPermissionMode` attribute:</span></span>  
  
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
  
 <span data-ttu-id="0223c-112">Nastavení `principalPermissionMode` na `UseWindowsGroups` umožňuje použití <xref:System.Security.Permissions.PrincipalPermissionAttribute> na základě názvů skupin systému Windows.</span><span class="sxs-lookup"><span data-stu-id="0223c-112">Setting the `principalPermissionMode` to `UseWindowsGroups` enables the use of <xref:System.Security.Permissions.PrincipalPermissionAttribute> based on Windows group names.</span></span>  
  
 <span data-ttu-id="0223c-113">Použití <xref:System.Security.Permissions.PrincipalPermissionAttribute> pro každou operaci vyžaduje volající ho být součástí skupiny správců systému Windows, jak je znázorněno v následujícím ukázkovém kódu.</span><span class="sxs-lookup"><span data-stu-id="0223c-113">The <xref:System.Security.Permissions.PrincipalPermissionAttribute> is applied to each operation to require the caller to be part of the Windows administrators group, as shown in the following sample code.</span></span>  
  
```csharp
[PrincipalPermission(SecurityAction.Demand,
                             Role = "Builtin\\Administrators")]  
public double Add(double n1, double n2)  
{  
    double result = n1 + n2;  
    return result;  
}  
```  
  
 <span data-ttu-id="0223c-114">Při spuštění ukázky jsou v okně klientské konzole zobrazeny požadavky na operaci a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="0223c-114">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="0223c-115">Klient úspěšně komunikuje s každou operací, pokud je spuštěn pod účtem, který je součástí skupiny Administrators; v opačném případě je přístup odepřen.</span><span class="sxs-lookup"><span data-stu-id="0223c-115">The client successfully communicates with each operation if it is running under an account that is part of the Administrators group; otherwise, access is denied.</span></span> <span data-ttu-id="0223c-116">Chcete-li experimentovat s chybou autorizace, spusťte klienta pod účtem, který není součástí skupiny Administrators.</span><span class="sxs-lookup"><span data-stu-id="0223c-116">To experiment with authorization failure, run the client under an account that is not part of the Administrators group.</span></span> <span data-ttu-id="0223c-117">Stisknutím klávesy ENTER v okně konzoly vypněte klienta.</span><span class="sxs-lookup"><span data-stu-id="0223c-117">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="0223c-118">Služba může být upozorněna na chyby <xref:System.ServiceModel.Dispatcher.IErrorHandler>autorizace implementací .</span><span class="sxs-lookup"><span data-stu-id="0223c-118">A service can be notified of authorization failures by implementing an <xref:System.ServiceModel.Dispatcher.IErrorHandler>.</span></span> <span data-ttu-id="0223c-119">Informace o implementaci naleznete v tématu Rozšíření `IErrorHandler` [kontroly nad zpracováním chyb a vytvářením sestav.](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md)</span><span class="sxs-lookup"><span data-stu-id="0223c-119">See [Extending Control Over Error Handling and Reporting](../../../../docs/framework/wcf/samples/extending-control-over-error-handling-and-reporting.md) for information about implementing `IErrorHandler`.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0223c-120">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="0223c-120">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="0223c-121">Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0223c-121">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="0223c-122">Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0223c-122">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="0223c-123">Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="0223c-123">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  

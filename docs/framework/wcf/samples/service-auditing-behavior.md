---
title: Chování auditování služby
ms.date: 03/30/2017
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
ms.openlocfilehash: bfe13146a7f7cdec648a82a34c34077ec5466809
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599929"
---
# <a name="service-auditing-behavior"></a><span data-ttu-id="3fb0c-102">Chování auditování služby</span><span class="sxs-lookup"><span data-stu-id="3fb0c-102">Service Auditing Behavior</span></span>
<span data-ttu-id="3fb0c-103">Tato ukázka předvádí, jak použít <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> k povolení auditování událostí zabezpečení během operací služby.</span><span class="sxs-lookup"><span data-stu-id="3fb0c-103">This sample demonstrates how to use the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to enable auditing of security events during service operations.</span></span> <span data-ttu-id="3fb0c-104">Tato ukázka je založena na [Začínáme](getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="3fb0c-104">This sample is based on the [Getting Started](getting-started-sample.md).</span></span> <span data-ttu-id="3fb0c-105">Služba a klient byly nakonfigurovány pomocí nástroje [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) .</span><span class="sxs-lookup"><span data-stu-id="3fb0c-105">The service and client have been configured using the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="3fb0c-106">`mode`Atribut [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) byl nastaven na hodnotu `Message` a `clientCredentialType` byl nastaven na hodnotu `Windows` .</span><span class="sxs-lookup"><span data-stu-id="3fb0c-106">The `mode` attribute of the [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="3fb0c-107">V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).</span><span class="sxs-lookup"><span data-stu-id="3fb0c-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3fb0c-108">Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="3fb0c-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="3fb0c-109">Konfigurační soubor služby používá `serviceSecurityAudit` prvek ke konfiguraci auditování.</span><span class="sxs-lookup"><span data-stu-id="3fb0c-109">The service configuration file uses the `serviceSecurityAudit` element to configure auditing.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      ...  
<!-- serviceSecurityAudit allows specification of audit location   
     and whether to audit success, failure or both. This service   
     logs success and failure of messageAuthentication   
     to the default location -->  
     <serviceSecurityAudit auditLogLocation ="Default" messageAuthenticationAuditLevel = "SuccessOrFailure" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="3fb0c-110">Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="3fb0c-110">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="3fb0c-111">Ukončete klienta stisknutím klávesy ENTER v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="3fb0c-111">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="3fb0c-112">Výsledné protokoly auditu můžete zobrazit spuštěním Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="3fb0c-112">The resulting audit logs can be seen by running the Event Viewer.</span></span> <span data-ttu-id="3fb0c-113">Ve výchozím nastavení v systému Windows XP lze události auditu zobrazit v aplikačním protokolu, zatímco v systému Windows Server 2003 a Windows Vista, události auditu lze zobrazit v protokolu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3fb0c-113">By default, on Windows XP the audit events can be seen in the Application Log while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="3fb0c-114">V systémech Windows Server 2008 a Windows 7 se události auditu zobrazují v protokolech aplikací a služeb.</span><span class="sxs-lookup"><span data-stu-id="3fb0c-114">On Windows Server 2008 and Windows 7, the audit events can be seen in the Applications and Services logs.</span></span> <span data-ttu-id="3fb0c-115">Umístění událostí auditu lze zadat nastavením `auditLogLocation` atributu "Application" nebo "Security".</span><span class="sxs-lookup"><span data-stu-id="3fb0c-115">The location of audit events can be specified by setting the `auditLogLocation` attribute to "Application" or "Security".</span></span> <span data-ttu-id="3fb0c-116">Další informace najdete v tématu [Postupy: auditování událostí zabezpečení](../feature-details/how-to-audit-wcf-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="3fb0c-116">For more information, see [How to: Audit Security Events](../feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="3fb0c-117">Pokud jsou události zapisovány do protokolu zabezpečení, LocalSecurityPolicy-> povolit přístup k objektům by měl být nastaven na hodnotu "úspěch" a "selhání".</span><span class="sxs-lookup"><span data-stu-id="3fb0c-117">If the events are written in the Security Log the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="3fb0c-118">Při prohlížení protokolu událostí je zdrojem událostí auditu "ServiceModel audit 3.0.0.0".</span><span class="sxs-lookup"><span data-stu-id="3fb0c-118">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="3fb0c-119">Záznamy auditu ověřování zprávy mají kategorii "MessageAuthentication", zatímco záznamy auditu autorizací služeb mají kategorii "ServiceAuthorization".</span><span class="sxs-lookup"><span data-stu-id="3fb0c-119">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of "ServiceAuthorization".</span></span>  
  
 <span data-ttu-id="3fb0c-120">Události auditu ověřování zpráv se týkají ohledu na to, zda byla zpráva zfalšována, zda vypršela platnost zprávy a zda se může klient ověřit ve službě.</span><span class="sxs-lookup"><span data-stu-id="3fb0c-120">Message authentication audit events cover whether the message was tampered with, whether the message has expired, and whether the client can authenticate to the service.</span></span> <span data-ttu-id="3fb0c-121">Poskytují informace o tom, zda bylo ověření úspěšné nebo neúspěšné, spolu s identitou klienta, a koncovým bodem, na který byla zpráva odeslána, spolu s akcí přidruženou ke zprávě.</span><span class="sxs-lookup"><span data-stu-id="3fb0c-121">They provide information about whether the authentication succeeded or failed along with the identity of the client, and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="3fb0c-122">Události auditu autorizace služby se týkají autorizačního rozhodnutí, které udělal Správce autorizací služby.</span><span class="sxs-lookup"><span data-stu-id="3fb0c-122">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="3fb0c-123">Poskytují informace o tom, zda autorizace byla úspěšná nebo neúspěšná, spolu s identitou klienta, koncový bod, na který byla zpráva odeslána, akce přidružená ke zprávě, identifikátor autorizačního kontextu, který byl vygenerován z příchozí zprávy, a typ Správce autorizací, který učinil rozhodnutí o přístupu.</span><span class="sxs-lookup"><span data-stu-id="3fb0c-123">They provide information about whether authorization succeeded or failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message, and the type of the authorization manager that made the access decision.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="3fb0c-124">Nastavení, sestavení a spuštění ukázky</span><span class="sxs-lookup"><span data-stu-id="3fb0c-124">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="3fb0c-125">Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3fb0c-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2. <span data-ttu-id="3fb0c-126">Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3fb0c-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](building-the-samples.md).</span></span>  
  
3. <span data-ttu-id="3fb0c-127">Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="3fb0c-127">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fb0c-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="3fb0c-128">See also</span></span>

- [<span data-ttu-id="3fb0c-129">Auditování</span><span class="sxs-lookup"><span data-stu-id="3fb0c-129">Auditing</span></span>](../feature-details/auditing-security-events.md)
- [<span data-ttu-id="3fb0c-130">Postupy: Auditování událostí zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3fb0c-130">How to: Audit Security Events</span></span>](../feature-details/how-to-audit-wcf-security-events.md)

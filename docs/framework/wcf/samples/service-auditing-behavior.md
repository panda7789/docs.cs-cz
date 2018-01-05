---
title: "Chování auditování služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 140793e41be012a777dbfa4bf66528612ab33da7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="service-auditing-behavior"></a><span data-ttu-id="25985-102">Chování auditování služby</span><span class="sxs-lookup"><span data-stu-id="25985-102">Service Auditing Behavior</span></span>
<span data-ttu-id="25985-103">Tento příklad znázorňuje způsob použití <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> povolení auditování událostí zabezpečení během operací služby.</span><span class="sxs-lookup"><span data-stu-id="25985-103">This sample demonstrates how to use the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to enable auditing of security events during service operations.</span></span> <span data-ttu-id="25985-104">Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span><span class="sxs-lookup"><span data-stu-id="25985-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="25985-105">Klienta a služby jsou nakonfigurované pomocí [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="25985-105">The service and client have been configured using the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="25985-106">`mode` Atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) byla nastavena na `Message` a `clientCredentialType` byla nastavena na `Windows`.</span><span class="sxs-lookup"><span data-stu-id="25985-106">The `mode` attribute of the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) has been set to `Message` and `clientCredentialType` has been set to `Windows`.</span></span> <span data-ttu-id="25985-107">V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).</span><span class="sxs-lookup"><span data-stu-id="25985-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="25985-108">V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.</span><span class="sxs-lookup"><span data-stu-id="25985-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="25985-109">Konfigurační soubor služby používá `serviceSecurityAudit` element konfigurace auditování.</span><span class="sxs-lookup"><span data-stu-id="25985-109">The service configuration file uses the `serviceSecurityAudit` element to configure auditing.</span></span>  
  
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
  
 <span data-ttu-id="25985-110">Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta.</span><span class="sxs-lookup"><span data-stu-id="25985-110">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="25985-111">Stisknutím klávesy ENTER v okně konzoly vypnout klienta.</span><span class="sxs-lookup"><span data-stu-id="25985-111">Press ENTER in the console window to shut down the client.</span></span>  
  
 <span data-ttu-id="25985-112">Výsledný protokoly auditu je možné zobrazit pomocí prohlížeče událostí.</span><span class="sxs-lookup"><span data-stu-id="25985-112">The resulting audit logs can be seen by running the Event Viewer.</span></span> <span data-ttu-id="25985-113">Ve výchozím nastavení se zobrazí události auditu v protokolu aplikace při na Windows Server 2003 a Windows Vista, Windows XP se zobrazí události auditu v protokolu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="25985-113">By default, on Windows XP the audit events can be seen in the Application Log while on Windows Server 2003 and Windows Vista, the audit events can be seen in the Security Log.</span></span> <span data-ttu-id="25985-114">Na Windows Server 2008 a Windows 7 se zobrazí události auditu v protokoly aplikací a služeb.</span><span class="sxs-lookup"><span data-stu-id="25985-114">On Windows Server 2008 and Windows 7, the audit events can be seen in the Applications and Services logs.</span></span> <span data-ttu-id="25985-115">Umístění události auditu lze zadat nastavením `auditLogLocation` atribut "Aplikace" nebo "Zabezpečení".</span><span class="sxs-lookup"><span data-stu-id="25985-115">The location of audit events can be specified by setting the `auditLogLocation` attribute to "Application" or "Security".</span></span> <span data-ttu-id="25985-116">Další informace najdete v tématu [postup: události auditu zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="25985-116">For more information, see [How to: Audit Security Events](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).</span></span> <span data-ttu-id="25985-117">Pokud události se zapisují do protokolu zabezpečení LocalSecurityPolicy -> Povolit přístup k objektu by měla být nastavena pro "ÚSPĚCH" a "Selhání".</span><span class="sxs-lookup"><span data-stu-id="25985-117">If the events are written in the Security Log the LocalSecurityPolicy-> Enable Object Access should be set for "Success" and "Failure".</span></span>  
  
 <span data-ttu-id="25985-118">Při vyhledávání v protokolu událostí, zdroj událostí auditu je "ServiceModel auditu 3.0.0.0".</span><span class="sxs-lookup"><span data-stu-id="25985-118">When looking at the event log, the source of the audit events is "ServiceModel Audit 3.0.0.0".</span></span> <span data-ttu-id="25985-119">Záznamů zprávy o auditu ověřování vlastní kategorie "MessageAuthentication", zatímco záznamy auditu autorizace služby, vlastní kategorie "ServiceAuthorization".</span><span class="sxs-lookup"><span data-stu-id="25985-119">Message authentication audit records have a category of "MessageAuthentication" while service authorization audit records have a category of "ServiceAuthorization".</span></span>  
  
 <span data-ttu-id="25985-120">Události auditu ověřování zpráv tématech, zda zpráva bylo manipulováno, jestli vypršela platnost zprávu, a zda může klient ověřit ve službě.</span><span class="sxs-lookup"><span data-stu-id="25985-120">Message authentication audit events cover whether the message was tampered with, whether the message has expired, and whether the client can authenticate to the service.</span></span> <span data-ttu-id="25985-121">Poskytují informace o tom, jestli je ověřování byla úspěšná nebo neúspěšná spolu s identitou klienta a koncový bod zpráva byla odeslána spolu s akce přidružené ke zprávě.</span><span class="sxs-lookup"><span data-stu-id="25985-121">They provide information about whether the authentication succeeded or failed along with the identity of the client, and the endpoint the message was sent to along with the action associated with the message.</span></span>  
  
 <span data-ttu-id="25985-122">Události auditu autorizace služby zahrnují rozhodnutí o autorizaci provedené správcem autorizace služby.</span><span class="sxs-lookup"><span data-stu-id="25985-122">Service authorization audit events cover the authorization decision made by a service authorization manager.</span></span> <span data-ttu-id="25985-123">Poskytují informace o tom, jestli ověření bylo úspěšné, nebo se nezdařilo spolu s identitou klienta, koncový bod zpráva byla odeslána k akci spojený se zprávou, identifikátor autorizační kontext, který se vygeneroval ze příchozí zprávy a typ Správce autorizací, který se rozhodnete přístup.</span><span class="sxs-lookup"><span data-stu-id="25985-123">They provide information about whether authorization succeeded or failed along with the identity of the client, the endpoint the message was sent to, the action associated with the message, the identifier of the authorization context that was generated from the incoming message, and the type of the authorization manager that made the access decision.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="25985-124">Pokud chcete nastavit, sestavit a spustit ukázku</span><span class="sxs-lookup"><span data-stu-id="25985-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="25985-125">Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25985-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="25985-126">Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25985-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="25985-127">Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).</span><span class="sxs-lookup"><span data-stu-id="25985-127">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25985-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="25985-128">See Also</span></span>  
 [<span data-ttu-id="25985-129">Auditování</span><span class="sxs-lookup"><span data-stu-id="25985-129">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [<span data-ttu-id="25985-130">Postupy: Auditování událostí zabezpečení</span><span class="sxs-lookup"><span data-stu-id="25985-130">How to: Audit Security Events</span></span>](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)

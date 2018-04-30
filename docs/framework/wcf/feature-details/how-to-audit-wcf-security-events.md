---
title: 'Postupy: Windows Communication Foundation zabezpečení události auditu'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
caps.latest.revision: 19
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 72eff4af38636577dc9e3b35af1f1155d5ed892c
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="7289f-102">Postupy: Windows Communication Foundation zabezpečení události auditu</span><span class="sxs-lookup"><span data-stu-id="7289f-102">How to: Audit Windows Communication Foundation Security Events</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="7289f-103"> umožňuje protokolovat události zabezpečení do protokolu událostí systému Windows, který lze zobrazit pomocí prohlížeče událostí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="7289f-103"> allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="7289f-104">Toto téma vysvětluje, jak nastavit aplikaci tak, aby protokoluje události zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7289f-104">This topic explains how to set up an application so that it logs security events.</span></span> <span data-ttu-id="7289f-105">Další informace o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] auditování, najdete v části [auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="7289f-105">For more information about [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] auditing, see [Auditing](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="7289f-106">Auditování událostí zabezpečení v kódu</span><span class="sxs-lookup"><span data-stu-id="7289f-106">To audit security events in code</span></span>  
  
1.  <span data-ttu-id="7289f-107">Zadejte umístění protokolu auditování.</span><span class="sxs-lookup"><span data-stu-id="7289f-107">Specify the audit log location.</span></span> <span data-ttu-id="7289f-108">Chcete-li to provést, nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> vlastnost <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> třída na jednu z <xref:System.ServiceModel.AuditLogLocation> hodnoty výčtu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7289f-108">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="7289f-109"><xref:System.ServiceModel.AuditLogLocation> Výčet má tří hodnot: `Application`, `Security`, nebo `Default`.</span><span class="sxs-lookup"><span data-stu-id="7289f-109">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="7289f-110">Hodnota jednoho z protokolů zobrazit v prohlížeči událostí určuje buď protokolu zabezpečení nebo v protokolu aplikace.</span><span class="sxs-lookup"><span data-stu-id="7289f-110">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="7289f-111">Pokud použijete `Default` hodnotu, skutečný protokolu bude záviset na operační systém je aplikace spuštěna v.</span><span class="sxs-lookup"><span data-stu-id="7289f-111">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="7289f-112">Pokud je povoleno auditování a umístění protokolu není určena, výchozí hodnota je `Security` protokolu pro platformy, které podporují zápis do protokolu zabezpečení; jinak bude zapisovat do `Application` protokolu.</span><span class="sxs-lookup"><span data-stu-id="7289f-112">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="7289f-113">Pouze [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wv](../../../../includes/wv-md.md)] podporovat zápis do protokolu zabezpečení ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="7289f-113">Only [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wv](../../../../includes/wv-md.md)] support writing to the Security log by default.</span></span>  
  
2.  <span data-ttu-id="7289f-114">Nastavte typy událostí, které auditování.</span><span class="sxs-lookup"><span data-stu-id="7289f-114">Set up the types of events to audit.</span></span> <span data-ttu-id="7289f-115">Současně můžete auditovat událostí na úrovni služby nebo autorizace úroveň zprávy událostí.</span><span class="sxs-lookup"><span data-stu-id="7289f-115">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="7289f-116">Chcete-li to provést, nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> vlastnost nebo <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> vlastnost na jednu z <xref:System.ServiceModel.AuditLevel> hodnoty výčtu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7289f-116">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3.  <span data-ttu-id="7289f-117">Zadejte, jestli se má potlačit nebo odhalí selhání aplikace týkající se událostí auditování protokolu.</span><span class="sxs-lookup"><span data-stu-id="7289f-117">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="7289f-118">Nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnost, která má buď `true` nebo `false`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7289f-118">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="7289f-119">Výchozí hodnota `SuppressAuditFailure` vlastnost je `true`tak, aby selhání auditovat nemá vliv na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="7289f-119">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="7289f-120">V opačném případě je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="7289f-120">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="7289f-121">Pro všechny úspěšné auditu je zapsán podrobného trasování.</span><span class="sxs-lookup"><span data-stu-id="7289f-121">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="7289f-122">Všechny chyby audit trasování bude zapsáno na úrovni chyby.</span><span class="sxs-lookup"><span data-stu-id="7289f-122">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4.  <span data-ttu-id="7289f-123">Odstraňte existující <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekce chování najít v popisu <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="7289f-123">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="7289f-124">Kolekce chování přistupuje <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> vlastnosti, která zase přistupuje z <xref:System.ServiceModel.ServiceHostBase.Description%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="7289f-124">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="7289f-125">Přidejte nové <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> ke stejné kolekci, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="7289f-125">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="7289f-126">Nastavení auditování v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="7289f-126">To set up auditing in configuration</span></span>  
  
1.  <span data-ttu-id="7289f-127">Chcete-li nastavit auditování v konfiguraci, přidejte [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu, který chcete [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) části souboru web.config.</span><span class="sxs-lookup"><span data-stu-id="7289f-127">To set up auditing in configuration, add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="7289f-128">Pak přidejte [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) elementu a sadu různé atributy, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7289f-128">Then add a [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
    ```xml  
    <behaviors>  
       <behavior name="myAuditBehavior">  
          <serviceSecurityAudit auditLogLocation="Application"  
                suppressAuditFailure="false"   
                serviceAuthorizationAuditLevel="None"   
                messageAuthenticationAuditLevel="SuccessOrFailure" />  
          </behavior>  
    </behaviors>  
    ```  
  
2.  <span data-ttu-id="7289f-129">Chování služby, je nutné zadat, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7289f-129">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
    ```xml  
    <services>  
        <service type="WCS.Samples.Service.Echo"   
        behaviorConfiguration=" myAuditBehavior">  
           <endpoint address=""  
                    binding="wsHttpBinding"  
                    bindingConfiguration="CertificateDefault"   
                    contract="WCS.Samples.Service.IEcho" />  
        </service>  
    </services>  
    ```  
  
## <a name="example"></a><span data-ttu-id="7289f-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="7289f-130">Example</span></span>  
 <span data-ttu-id="7289f-131">Následující kód vytvoří instanci <xref:System.ServiceModel.ServiceHost> a přidává novou <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> jeho kolekce chování.</span><span class="sxs-lookup"><span data-stu-id="7289f-131">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="7289f-132">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="7289f-132">.NET Framework Security</span></span>  
 <span data-ttu-id="7289f-133">Nastavení <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnost `true`, potlačí všechny chyby Generovat audity zabezpečení (Pokud nastavena na `false`, je vyvolána výjimka).</span><span class="sxs-lookup"><span data-stu-id="7289f-133">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="7289f-134">Ale pokud povolíte následující Windows **místní nastavení zabezpečení**vlastnost, způsobí selhání generovat události auditu okamžitě vypnutí systému Windows:</span><span class="sxs-lookup"><span data-stu-id="7289f-134">However, if you enable the following Windows **Local Security Setting**property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="7289f-135">**Audit: Vypnutí systému okamžitě, když se nemůže přihlásit audity zabezpečení**</span><span class="sxs-lookup"><span data-stu-id="7289f-135">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="7289f-136">Pokud chcete nastavit vlastnost, otevřete **místní nastavení zabezpečení** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="7289f-136">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="7289f-137">V části **nastavení zabezpečení**, klikněte na tlačítko **místní zásady**.</span><span class="sxs-lookup"><span data-stu-id="7289f-137">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="7289f-138">Pak klikněte na tlačítko **možnosti zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="7289f-138">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="7289f-139">Pokud <xref:System.ServiceModel.AuditLogLocation> je nastavena na <xref:System.ServiceModel.AuditLogLocation.Security> a **přístup k objektům** není nastavena v **místní zásady zabezpečení**, události auditu budou zapsány do protokolu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7289f-139">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="7289f-140">Všimněte si, že je vrácen bez chyby, ale položky auditu nejsou zapsány do protokolu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7289f-140">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7289f-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="7289f-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [<span data-ttu-id="7289f-142">Auditování</span><span class="sxs-lookup"><span data-stu-id="7289f-142">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)

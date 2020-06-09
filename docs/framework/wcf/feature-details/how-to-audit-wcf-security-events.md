---
title: 'Postupy: auditování událostí zabezpečení Windows Communication Foundation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: 186dd4a7fc2beae848e5cbd167a204352ee6ed4e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601293"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="2f547-102">Postupy: auditování událostí zabezpečení Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="2f547-102">How to: Audit Windows Communication Foundation Security Events</span></span>
<span data-ttu-id="2f547-103">Windows Communication Foundation (WCF) umožňuje protokolovat události zabezpečení do protokolu událostí systému Windows, který lze zobrazit pomocí Prohlížeč událostí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="2f547-103">Windows Communication Foundation (WCF) allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="2f547-104">Toto téma vysvětluje, jak nastavit aplikaci tak, aby protokoloval události zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2f547-104">This topic explains how to set up an application so that it logs security events.</span></span> <span data-ttu-id="2f547-105">Další informace o auditování WCF najdete v tématu [auditování](auditing-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="2f547-105">For more information about WCF auditing, see [Auditing](auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="2f547-106">Auditování událostí zabezpečení v kódu</span><span class="sxs-lookup"><span data-stu-id="2f547-106">To audit security events in code</span></span>  
  
1. <span data-ttu-id="2f547-107">Zadejte umístění protokolu auditu.</span><span class="sxs-lookup"><span data-stu-id="2f547-107">Specify the audit log location.</span></span> <span data-ttu-id="2f547-108">Chcete-li to provést, nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> vlastnost <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> třídy na jednu z <xref:System.ServiceModel.AuditLogLocation> hodnot výčtu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2f547-108">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="2f547-109"><xref:System.ServiceModel.AuditLogLocation>Výčet obsahuje tři hodnoty: `Application` , `Security` , nebo `Default` .</span><span class="sxs-lookup"><span data-stu-id="2f547-109">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="2f547-110">Hodnota určuje jeden z protokolů viditelných v Prohlížeč událostí, buď protokol zabezpečení, nebo protokol aplikace.</span><span class="sxs-lookup"><span data-stu-id="2f547-110">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="2f547-111">Pokud použijete tuto `Default` hodnotu, skutečný protokol bude záviset na operačním systému, ve kterém je aplikace spuštěná.</span><span class="sxs-lookup"><span data-stu-id="2f547-111">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="2f547-112">Pokud je povolené auditování a umístění protokolu není zadané, použije se výchozí `Security` protokol pro platformy, které podporují zápis do protokolu zabezpečení. jinak se zapíše do `Application` protokolu.</span><span class="sxs-lookup"><span data-stu-id="2f547-112">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="2f547-113">Ve výchozím nastavení podporuje systém Windows Server 2003 a systém Windows Vista do protokolu zabezpečení pouze zápis.</span><span class="sxs-lookup"><span data-stu-id="2f547-113">Only Windows Server 2003 and Windows Vista support writing to the Security log by default.</span></span>  
  
2. <span data-ttu-id="2f547-114">Nastavte typy událostí, které se mají auditovat.</span><span class="sxs-lookup"><span data-stu-id="2f547-114">Set up the types of events to audit.</span></span> <span data-ttu-id="2f547-115">Současně můžete auditovat události na úrovni služby nebo události autorizace na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="2f547-115">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="2f547-116">Chcete-li to provést, nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> vlastnost nebo <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> vlastnost na jednu z <xref:System.ServiceModel.AuditLevel> hodnot výčtu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2f547-116">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. <span data-ttu-id="2f547-117">Určete, zda se mají potlačit nebo vystavení selhání aplikace v souvislosti s událostmi auditu protokolu.</span><span class="sxs-lookup"><span data-stu-id="2f547-117">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="2f547-118">Nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnost na buď `true` nebo `false` , jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2f547-118">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="2f547-119">Výchozí `SuppressAuditFailure` vlastnost je `true` , aby nedošlo k neovlivnění selhání pro audit aplikace.</span><span class="sxs-lookup"><span data-stu-id="2f547-119">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="2f547-120">V opačném případě je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="2f547-120">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="2f547-121">U všech úspěšných auditů se zapíše podrobné trasování.</span><span class="sxs-lookup"><span data-stu-id="2f547-121">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="2f547-122">V případě jakéhokoli neúspěšného auditu se trasování zapisuje na úroveň chyby.</span><span class="sxs-lookup"><span data-stu-id="2f547-122">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4. <span data-ttu-id="2f547-123">Odstraní existující <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekce chování nalezené v popisu a <xref:System.ServiceModel.ServiceHost> .</span><span class="sxs-lookup"><span data-stu-id="2f547-123">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="2f547-124">Kolekce chování je k dispozici ve <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> vlastnosti, která je zase k dispozici z <xref:System.ServiceModel.ServiceHostBase.Description%2A> Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2f547-124">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="2f547-125">Pak přidejte novou <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do stejné kolekce, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2f547-125">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="2f547-126">Nastavení auditování v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="2f547-126">To set up auditing in configuration</span></span>  
  
1. <span data-ttu-id="2f547-127">Chcete-li nastavit auditování v konfiguraci, přidejte [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element do [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) oddílu souboru Web. config.</span><span class="sxs-lookup"><span data-stu-id="2f547-127">To set up auditing in configuration, add a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="2f547-128">Pak přidejte [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) element a nastavte různé atributy, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2f547-128">Then add a [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
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
  
2. <span data-ttu-id="2f547-129">Je nutné zadat chování služby, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2f547-129">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="2f547-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="2f547-130">Example</span></span>  
 <span data-ttu-id="2f547-131">Následující kód vytvoří instanci <xref:System.ServiceModel.ServiceHost> třídy a přidá novou <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do kolekce chování.</span><span class="sxs-lookup"><span data-stu-id="2f547-131">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="2f547-132">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="2f547-132">.NET Framework Security</span></span>  
 <span data-ttu-id="2f547-133">Nastavení <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnosti na `true` , potlačí jakékoli selhání při generování auditů zabezpečení (Pokud je nastaveno na `false` výjimku, je vyvolána výjimka).</span><span class="sxs-lookup"><span data-stu-id="2f547-133">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="2f547-134">Pokud ale povolíte následující vlastnost **místního nastavení zabezpečení** systému Windows, selhání při generování událostí auditu způsobí, že se systém Windows okamžitě vypne:</span><span class="sxs-lookup"><span data-stu-id="2f547-134">However, if you enable the following Windows **Local Security Setting** property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="2f547-135">**Audit: Není-li možno protokolovat audity zabezpečení, vypnout okamžitě systém**</span><span class="sxs-lookup"><span data-stu-id="2f547-135">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="2f547-136">Chcete-li nastavit vlastnost, otevřete dialogové okno **místní nastavení zabezpečení** .</span><span class="sxs-lookup"><span data-stu-id="2f547-136">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="2f547-137">V části **nastavení zabezpečení**klikněte na **místní zásady**.</span><span class="sxs-lookup"><span data-stu-id="2f547-137">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="2f547-138">Pak klikněte na **Možnosti zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="2f547-138">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="2f547-139">Pokud je <xref:System.ServiceModel.AuditLogLocation> vlastnost nastavena na hodnotu <xref:System.ServiceModel.AuditLogLocation.Security> a **Audit přístupu k objektům** není nastaven v **místních zásadách zabezpečení**, události auditu nebudou zapsány do protokolu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2f547-139">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="2f547-140">Všimněte si, že se nevrátí žádná chyba, ale záznamy auditu se nezapisují do protokolu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2f547-140">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f547-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f547-141">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [<span data-ttu-id="2f547-142">Auditování</span><span class="sxs-lookup"><span data-stu-id="2f547-142">Auditing</span></span>](auditing-security-events.md)

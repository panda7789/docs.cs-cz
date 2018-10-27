---
title: 'Postupy: auditování událostí zabezpečení aplikace Windows Communication Foundation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: 90169aac0c0c2cac8860b2809467ffa3a27d0e91
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50184735"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="825e5-102">Postupy: auditování událostí zabezpečení aplikace Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="825e5-102">How to: Audit Windows Communication Foundation Security Events</span></span>
<span data-ttu-id="825e5-103">Windows Communication Foundation (WCF) umožňuje protokolovat události zabezpečení do protokolu událostí Windows, který lze zobrazit pomocí prohlížeče událostí Windows.</span><span class="sxs-lookup"><span data-stu-id="825e5-103">Windows Communication Foundation (WCF) allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="825e5-104">Toto téma vysvětluje, jak nastavit aplikaci tak, aby protokoly událostí zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="825e5-104">This topic explains how to set up an application so that it logs security events.</span></span> <span data-ttu-id="825e5-105">Další informace o auditování WCF najdete v tématu [auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="825e5-105">For more information about WCF auditing, see [Auditing](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="825e5-106">Auditování událostí zabezpečení v kódu</span><span class="sxs-lookup"><span data-stu-id="825e5-106">To audit security events in code</span></span>  
  
1.  <span data-ttu-id="825e5-107">Zadejte umístění protokolu auditu.</span><span class="sxs-lookup"><span data-stu-id="825e5-107">Specify the audit log location.</span></span> <span data-ttu-id="825e5-108">Chcete-li to provést, nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> vlastnost <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> třídy do jednoho z <xref:System.ServiceModel.AuditLogLocation> hodnot výčtu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="825e5-108">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="825e5-109"><xref:System.ServiceModel.AuditLogLocation> Výčet má tři hodnoty: `Application`, `Security`, nebo `Default`.</span><span class="sxs-lookup"><span data-stu-id="825e5-109">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="825e5-110">Hodnota jednoho z protokolů zobrazit v prohlížeči událostí určuje buď protokolu zabezpečení nebo v protokolu aplikace.</span><span class="sxs-lookup"><span data-stu-id="825e5-110">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="825e5-111">Pokud používáte `Default` hodnotu, skutečné protokolu bude záviset na aplikace běží na operační systém.</span><span class="sxs-lookup"><span data-stu-id="825e5-111">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="825e5-112">Pokud je povolené auditování a umístění protokolu není zadán, výchozí hodnota je `Security` protokolu pro platformy, které podporují zápis do protokolu zabezpečení; v opačném případě bude zapisovat do `Application` protokolu.</span><span class="sxs-lookup"><span data-stu-id="825e5-112">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="825e5-113">Pouze [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wv](../../../../includes/wv-md.md)] podporovat zápis do protokolu zabezpečení ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="825e5-113">Only [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] and [!INCLUDE[wv](../../../../includes/wv-md.md)] support writing to the Security log by default.</span></span>  
  
2.  <span data-ttu-id="825e5-114">Nastavte typy událostí auditu.</span><span class="sxs-lookup"><span data-stu-id="825e5-114">Set up the types of events to audit.</span></span> <span data-ttu-id="825e5-115">Současně je můžete auditovat události autorizaci na úrovni zpráv nebo událostí na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="825e5-115">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="825e5-116">Chcete-li to provést, nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> vlastnost nebo <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> vlastnost na jednu z <xref:System.ServiceModel.AuditLevel> hodnot výčtu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="825e5-116">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3.  <span data-ttu-id="825e5-117">Určete, zda potlačit nebo zveřejnit chyby týkající se událostí auditování protokolu aplikace.</span><span class="sxs-lookup"><span data-stu-id="825e5-117">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="825e5-118">Nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnost buď `true` nebo `false`, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="825e5-118">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="825e5-119">Výchozí hodnota `SuppressAuditFailure` vlastnost `true`tak, aby selhání auditovat nemá vliv na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="825e5-119">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="825e5-120">V opačném případě je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="825e5-120">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="825e5-121">Všechny úspěšné auditu se zapisují podrobné trasování.</span><span class="sxs-lookup"><span data-stu-id="825e5-121">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="825e5-122">Auditovat všechny chyby trasování bude zapsáno na úrovni chyby.</span><span class="sxs-lookup"><span data-stu-id="825e5-122">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4.  <span data-ttu-id="825e5-123">Odstranit existující <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekce chování, které jsou součástí popis <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="825e5-123">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="825e5-124">Kolekce chování přistupuje <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> vlastnost, která pak přistupuje z <xref:System.ServiceModel.ServiceHostBase.Description%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="825e5-124">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="825e5-125">Pak přidejte nové <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do stejné kolekce, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="825e5-125">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="825e5-126">Nastavení auditování v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="825e5-126">To set up auditing in configuration</span></span>  
  
1.  <span data-ttu-id="825e5-127">Chcete-li nastavit auditování v konfiguraci, přidejte [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) část souboru web.config.</span><span class="sxs-lookup"><span data-stu-id="825e5-127">To set up auditing in configuration, add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="825e5-128">Pak přidejte [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) elementu a nastavte různé atributy, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="825e5-128">Then add a [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
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
  
2.  <span data-ttu-id="825e5-129">Chování služby, je nutné zadat, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="825e5-129">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="825e5-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="825e5-130">Example</span></span>  
 <span data-ttu-id="825e5-131">Následující kód vytvoří instanci <xref:System.ServiceModel.ServiceHost> třídy a přidá nový <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> jeho kolekce chování.</span><span class="sxs-lookup"><span data-stu-id="825e5-131">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="825e5-132">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="825e5-132">.NET Framework Security</span></span>  
 <span data-ttu-id="825e5-133">Nastavení <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnost `true`, potlačí všechny chyby Generovat audity zabezpečení (Pokud nastavena na `false`, je vyvolána výjimka).</span><span class="sxs-lookup"><span data-stu-id="825e5-133">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="825e5-134">Nicméně pokud povolíte následující Windows **místní nastavení zabezpečení** vlastnost, nepovedlo se generovat události auditu způsobí, že Windows vypnout okamžitě:</span><span class="sxs-lookup"><span data-stu-id="825e5-134">However, if you enable the following Windows **Local Security Setting** property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="825e5-135">**Audit: Vypněte okamžitě systém schopen protokolovat audity zabezpečení**</span><span class="sxs-lookup"><span data-stu-id="825e5-135">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="825e5-136">Chcete-li nastavena vlastnost, otevřete **místní nastavení zabezpečení** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="825e5-136">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="825e5-137">V části **nastavení zabezpečení**, klikněte na tlačítko **místní zásady**.</span><span class="sxs-lookup"><span data-stu-id="825e5-137">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="825e5-138">Pak klikněte na tlačítko **možnosti zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="825e5-138">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="825e5-139">Pokud <xref:System.ServiceModel.AuditLogLocation> je nastavena na <xref:System.ServiceModel.AuditLogLocation.Security> a **auditování přístupu k objektům** kódu není nastavený **místní zásady zabezpečení**, události auditu se zapisují do protokolu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="825e5-139">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="825e5-140">Všimněte si, že se vrátí bez chyby, ale položky auditu se zapisují do protokolu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="825e5-140">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="825e5-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="825e5-141">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [<span data-ttu-id="825e5-142">Auditování</span><span class="sxs-lookup"><span data-stu-id="825e5-142">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)

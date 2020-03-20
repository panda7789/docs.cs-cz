---
title: 'Postup: Auditování událostí zabezpečení služby Windows Communication Foundation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: 62d26b24b5d46427c1871fccf48b063c45781beb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185115"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a><span data-ttu-id="d2507-102">Postup: Auditování událostí zabezpečení služby Windows Communication Foundation</span><span class="sxs-lookup"><span data-stu-id="d2507-102">How to: Audit Windows Communication Foundation Security Events</span></span>
<span data-ttu-id="d2507-103">Windows Communication Foundation (WCF) umožňuje protokolovat události zabezpečení do protokolu událostí systému Windows, který lze zobrazit pomocí prohlížeče událostí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d2507-103">Windows Communication Foundation (WCF) allows you to log security events to the Windows event log, which can be viewed using the Windows Event Viewer.</span></span> <span data-ttu-id="d2507-104">Toto téma vysvětluje, jak nastavit aplikaci tak, aby protokolování události zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d2507-104">This topic explains how to set up an application so that it logs security events.</span></span> <span data-ttu-id="d2507-105">Další informace o auditování WCF naleznete v [tématu Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span><span class="sxs-lookup"><span data-stu-id="d2507-105">For more information about WCF auditing, see [Auditing](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).</span></span>  
  
### <a name="to-audit-security-events-in-code"></a><span data-ttu-id="d2507-106">Auditování událostí zabezpečení v kódu</span><span class="sxs-lookup"><span data-stu-id="d2507-106">To audit security events in code</span></span>  
  
1. <span data-ttu-id="d2507-107">Zadejte umístění protokolu auditu.</span><span class="sxs-lookup"><span data-stu-id="d2507-107">Specify the audit log location.</span></span> <span data-ttu-id="d2507-108">Chcete-li to <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> provést, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> nastavte vlastnost třídy na jednu z hodnot výčtu, <xref:System.ServiceModel.AuditLogLocation> jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d2507-108">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> property of the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> class to one of the <xref:System.ServiceModel.AuditLogLocation> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <span data-ttu-id="d2507-109">Výčet <xref:System.ServiceModel.AuditLogLocation> má tři `Application`hodnoty: `Security`, `Default`, nebo .</span><span class="sxs-lookup"><span data-stu-id="d2507-109">The <xref:System.ServiceModel.AuditLogLocation> enumeration has three values: `Application`, `Security`, or `Default`.</span></span> <span data-ttu-id="d2507-110">Hodnota určuje jeden z protokolů viditelných v Prohlížeči událostí, protokol zabezpečení nebo protokol aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2507-110">The value specifies one of the logs visible in the Event Viewer, either the Security log or the Application log.</span></span> <span data-ttu-id="d2507-111">Pokud použijete `Default` hodnotu, bude skutečný protokol záviset na operačním systému, ve které je aplikace spuštěna.</span><span class="sxs-lookup"><span data-stu-id="d2507-111">If you use the `Default` value, the actual log will depend on the operating system the application is running on.</span></span> <span data-ttu-id="d2507-112">Pokud je povoleno auditování a není zadáno umístění `Security` protokolu, výchozí je protokol pro platformy, které podporují zápis do protokolu zabezpečení; v opačném případě zapíše do `Application` protokolu.</span><span class="sxs-lookup"><span data-stu-id="d2507-112">If auditing is enabled and the log location is not specified, the default is the `Security` log for platforms that support writing to the Security log; otherwise, it will write to the `Application` log.</span></span> <span data-ttu-id="d2507-113">Zápis do protokolu zabezpečení ve výchozím nastavení podporují pouze systémy Windows Server 2003 a Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="d2507-113">Only Windows Server 2003 and Windows Vista support writing to the Security log by default.</span></span>  
  
2. <span data-ttu-id="d2507-114">Nastavte typy událostí k auditu.</span><span class="sxs-lookup"><span data-stu-id="d2507-114">Set up the types of events to audit.</span></span> <span data-ttu-id="d2507-115">Můžete současně auditovat události na úrovni služby nebo události autorizace na úrovni zprávy.</span><span class="sxs-lookup"><span data-stu-id="d2507-115">You can simultaneously audit service-level events or message-level authorization events.</span></span> <span data-ttu-id="d2507-116">Chcete-li to <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> provést, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> nastavte vlastnost nebo <xref:System.ServiceModel.AuditLevel> vlastnost na jednu z hodnot výčtu, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d2507-116">To do this, set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> property or the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> property to one of the <xref:System.ServiceModel.AuditLevel> enumeration values, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. <span data-ttu-id="d2507-117">Určete, zda chcete potlačit nebo vystavit selhání aplikace týkající se událostí auditu protokolu.</span><span class="sxs-lookup"><span data-stu-id="d2507-117">Specify whether to suppress or expose failures to the application regarding log audit events.</span></span> <span data-ttu-id="d2507-118">Nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnost buď `true` `false`nebo , jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d2507-118">Set the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to either `true` or `false`, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     <span data-ttu-id="d2507-119">Výchozí `SuppressAuditFailure` vlastnost `true`je , takže selhání auditu nemá vliv na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="d2507-119">The default `SuppressAuditFailure` property is `true`, so that the failure to audit does not affect the application.</span></span> <span data-ttu-id="d2507-120">V opačném případě je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="d2507-120">Otherwise, an exception is thrown.</span></span> <span data-ttu-id="d2507-121">Pro každý úspěšný audit je zapsánpodrobné trasování.</span><span class="sxs-lookup"><span data-stu-id="d2507-121">For any successful audit, a verbose trace is written.</span></span> <span data-ttu-id="d2507-122">Pro jakékoli selhání auditu trasování je zapsána na úrovni Error.</span><span class="sxs-lookup"><span data-stu-id="d2507-122">For any failure to audit, the trace is written at the Error level.</span></span>  
  
4. <span data-ttu-id="d2507-123">Odstranit existující <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekce chování v popisu <xref:System.ServiceModel.ServiceHost>.</span><span class="sxs-lookup"><span data-stu-id="d2507-123">Delete the existing <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> from the collection of behaviors found in the description of a <xref:System.ServiceModel.ServiceHost>.</span></span> <span data-ttu-id="d2507-124">Kolekce chování je přístupná <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> vlastnost, která zase je <xref:System.ServiceModel.ServiceHostBase.Description%2A> přístupná z vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="d2507-124">The behavior collection is accessed by the <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> property, which in turn is accessed from the <xref:System.ServiceModel.ServiceHostBase.Description%2A> property.</span></span> <span data-ttu-id="d2507-125">Pak přidejte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> nové do stejné kolekce, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="d2507-125">Then add the new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to the same collection, as shown in the following code.</span></span>  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a><span data-ttu-id="d2507-126">Nastavení auditování v konfiguraci</span><span class="sxs-lookup"><span data-stu-id="d2507-126">To set up auditing in configuration</span></span>  
  
1. <span data-ttu-id="d2507-127">Chcete-li nastavit auditování v konfiguraci, přidejte prvek [ \<chování>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) do [ \<oddílu chování>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) souboru web.config.</span><span class="sxs-lookup"><span data-stu-id="d2507-127">To set up auditing in configuration, add a [\<behavior>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element to the [\<behaviors>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) section of the web.config file.</span></span> <span data-ttu-id="d2507-128">Potom přidejte [ \<prvek serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) a nastavte různé atributy, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d2507-128">Then add a [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) element and set the various attributes, as shown in the following example.</span></span>  
  
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
  
2. <span data-ttu-id="d2507-129">Je nutné zadat chování pro službu, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="d2507-129">You must specify the behavior for the service, as shown in the following example.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="d2507-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="d2507-130">Example</span></span>  
 <span data-ttu-id="d2507-131">Následující kód vytvoří instanci <xref:System.ServiceModel.ServiceHost> třídy <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> a přidá nové do své kolekce chování.</span><span class="sxs-lookup"><span data-stu-id="d2507-131">The following code creates an instance of the <xref:System.ServiceModel.ServiceHost> class and adds a new <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> to its collection of behaviors.</span></span>  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a><span data-ttu-id="d2507-132">Zabezpečení rozhraní .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d2507-132">.NET Framework Security</span></span>  
 <span data-ttu-id="d2507-133">Nastavení <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnosti `true`na , potlačí jakékoli selhání generování `false`auditů zabezpečení (pokud je nastavena na , je vyvolána výjimka).</span><span class="sxs-lookup"><span data-stu-id="d2507-133">Setting the <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> property to `true`, suppresses any failure to generate security audits (if set to `false`, an exception is thrown).</span></span> <span data-ttu-id="d2507-134">Pokud však povolíte následující vlastnost **Nastavení místního zabezpečení** systému Windows, selhání při generování událostí auditu způsobí okamžité vypnutí systému Windows:</span><span class="sxs-lookup"><span data-stu-id="d2507-134">However, if you enable the following Windows **Local Security Setting** property, a failure to generate audit events will cause Windows to shut down immediately:</span></span>  
  
 <span data-ttu-id="d2507-135">**Audit: Není-li možno protokolovat audity zabezpečení, vypnout okamžitě systém**</span><span class="sxs-lookup"><span data-stu-id="d2507-135">**Audit: Shut down system immediately if unable to log security audits**</span></span>  
  
 <span data-ttu-id="d2507-136">Chcete-li vlastnost nastavit, otevřete dialogové okno **Nastavení místního zabezpečení.**</span><span class="sxs-lookup"><span data-stu-id="d2507-136">To set the property, open the **Local Security Settings** dialog box.</span></span> <span data-ttu-id="d2507-137">V části **Nastavení zabezpečení**klepněte na **položku Místní zásady**.</span><span class="sxs-lookup"><span data-stu-id="d2507-137">Under **Security Settings**, click **Local Policies**.</span></span> <span data-ttu-id="d2507-138">Potom klepněte na **položku Možnosti zabezpečení**.</span><span class="sxs-lookup"><span data-stu-id="d2507-138">Then click **Security Options**.</span></span>  
  
 <span data-ttu-id="d2507-139">Pokud <xref:System.ServiceModel.AuditLogLocation> je vlastnost <xref:System.ServiceModel.AuditLogLocation.Security> nastavena na **a auditování přístupu k objektům** není nastaveno v **místních zásadách zabezpečení**, události auditu nebudou zapsány do protokolu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d2507-139">If the <xref:System.ServiceModel.AuditLogLocation> property is set to <xref:System.ServiceModel.AuditLogLocation.Security> and **Audit Object Access** is not set in the **Local Security Policy**, audit events will not be written to the Security log.</span></span> <span data-ttu-id="d2507-140">Všimněte si, že není vrácena žádná chyba, ale položky auditu nejsou zapsány do protokolu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d2507-140">Note that no failure is returned, but audit entries are not written to the Security log.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2507-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="d2507-141">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [<span data-ttu-id="d2507-142">Auditování</span><span class="sxs-lookup"><span data-stu-id="d2507-142">Auditing</span></span>](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)

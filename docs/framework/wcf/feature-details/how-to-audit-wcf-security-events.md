---
title: "Postupy: Windows Communication Foundation zabezpečení události auditu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
caps.latest.revision: 
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: d3456eb374add7768fa6f2d01bc1b7b610c9577e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Postupy: Windows Communication Foundation zabezpečení události auditu
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]umožňuje protokolovat události zabezpečení do protokolu událostí systému Windows, který lze zobrazit pomocí prohlížeče událostí systému Windows. Toto téma vysvětluje, jak nastavit aplikaci tak, aby protokoluje události zabezpečení. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] auditování, najdete v části [auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
### <a name="to-audit-security-events-in-code"></a>Auditování událostí zabezpečení v kódu  
  
1.  Zadejte umístění protokolu auditování. Chcete-li to provést, nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> vlastnost <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> třída na jednu z <xref:System.ServiceModel.AuditLogLocation> hodnoty výčtu, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <xref:System.ServiceModel.AuditLogLocation> Výčet má tří hodnot: `Application`, `Security`, nebo `Default`. Hodnota jednoho z protokolů zobrazit v prohlížeči událostí určuje buď protokolu zabezpečení nebo v protokolu aplikace. Pokud použijete `Default` hodnotu, skutečný protokolu bude záviset na operační systém je aplikace spuštěna v. Pokud je povoleno auditování a umístění protokolu není určena, výchozí hodnota je `Security` protokolu pro platformy, které podporují zápis do protokolu zabezpečení; jinak bude zapisovat do `Application` protokolu. Pouze [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wv](../../../../includes/wv-md.md)] podporovat zápis do protokolu zabezpečení ve výchozím nastavení.  
  
2.  Nastavte typy událostí, které auditování. Současně můžete auditovat událostí na úrovni služby nebo autorizace úroveň zprávy událostí. Chcete-li to provést, nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> vlastnost nebo <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> vlastnost na jednu z <xref:System.ServiceModel.AuditLevel> hodnoty výčtu, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3.  Zadejte, jestli se má potlačit nebo odhalí selhání aplikace týkající se událostí auditování protokolu. Nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnost, která má buď `true` nebo `false`, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     Výchozí hodnota `SuppressAuditFailure` vlastnost je `true`tak, aby selhání auditovat nemá vliv na aplikaci. V opačném případě je vyvolána výjimka. Pro všechny úspěšné auditu je zapsán podrobného trasování. Všechny chyby audit trasování bude zapsáno na úrovni chyby.  
  
4.  Odstraňte existující <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekce chování najít v popisu <xref:System.ServiceModel.ServiceHost>. Kolekce chování přistupuje <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> vlastnosti, která zase přistupuje z <xref:System.ServiceModel.ServiceHostBase.Description%2A> vlastnost. Přidejte nové <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> ke stejné kolekci, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Nastavení auditování v konfiguraci  
  
1.  Chcete-li nastavit auditování v konfiguraci, přidejte [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu, který chcete [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) části souboru web.config. Pak přidejte [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) elementu a sadu různé atributy, jak je znázorněno v následujícím příkladu.  
  
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
  
2.  Chování služby, je nutné zadat, jak je znázorněno v následujícím příkladu.  
  
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
  
## <a name="example"></a>Příklad  
 Následující kód vytvoří instanci <xref:System.ServiceModel.ServiceHost> a přidává novou <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> jeho kolekce chování.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nastavení <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnost `true`, potlačí všechny chyby Generovat audity zabezpečení (Pokud nastavena na `false`, je vyvolána výjimka). Ale pokud povolíte následující Windows **místní nastavení zabezpečení**vlastnost, způsobí selhání generovat události auditu okamžitě vypnutí systému Windows:  
  
 **Audit: Vypnutí systému okamžitě, když se nemůže přihlásit audity zabezpečení**  
  
 Pokud chcete nastavit vlastnost, otevřete **místní nastavení zabezpečení** dialogové okno. V části **nastavení zabezpečení**, klikněte na tlačítko **místní zásady**. Pak klikněte na tlačítko **možnosti zabezpečení**.  
  
 Pokud <xref:System.ServiceModel.AuditLogLocation> je nastavena na <xref:System.ServiceModel.AuditLogLocation.Security> a **přístup k objektům** není nastavena v **místní zásady zabezpečení**, události auditu budou zapsány do protokolu zabezpečení. Všimněte si, že je vrácen bez chyby, ale položky auditu nejsou zapsány do protokolu zabezpečení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)

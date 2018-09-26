---
title: 'Postupy: auditování událostí zabezpečení aplikace Windows Communication Foundation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
author: BrucePerlerMS
ms.openlocfilehash: 1efd651751e0f81b5125b64f81f7d2087d002d8d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47196275"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Postupy: auditování událostí zabezpečení aplikace Windows Communication Foundation
Windows Communication Foundation (WCF) umožňuje protokolovat události zabezpečení do protokolu událostí Windows, který lze zobrazit pomocí prohlížeče událostí Windows. Toto téma vysvětluje, jak nastavit aplikaci tak, aby protokoly událostí zabezpečení. Další informace o auditování WCF najdete v tématu [auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
### <a name="to-audit-security-events-in-code"></a>Auditování událostí zabezpečení v kódu  
  
1.  Zadejte umístění protokolu auditu. Chcete-li to provést, nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> vlastnost <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> třídy do jednoho z <xref:System.ServiceModel.AuditLogLocation> hodnot výčtu, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     <xref:System.ServiceModel.AuditLogLocation> Výčet má tři hodnoty: `Application`, `Security`, nebo `Default`. Hodnota jednoho z protokolů zobrazit v prohlížeči událostí určuje buď protokolu zabezpečení nebo v protokolu aplikace. Pokud používáte `Default` hodnotu, skutečné protokolu bude záviset na aplikace běží na operační systém. Pokud je povolené auditování a umístění protokolu není zadán, výchozí hodnota je `Security` protokolu pro platformy, které podporují zápis do protokolu zabezpečení; v opačném případě bude zapisovat do `Application` protokolu. Pouze [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wv](../../../../includes/wv-md.md)] podporovat zápis do protokolu zabezpečení ve výchozím nastavení.  
  
2.  Nastavte typy událostí auditu. Současně je můžete auditovat události autorizaci na úrovni zpráv nebo událostí na úrovni služby. Chcete-li to provést, nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> vlastnost nebo <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> vlastnost na jednu z <xref:System.ServiceModel.AuditLevel> hodnot výčtu, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3.  Určete, zda potlačit nebo zveřejnit chyby týkající se událostí auditování protokolu aplikace. Nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnost buď `true` nebo `false`, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     Výchozí hodnota `SuppressAuditFailure` vlastnost `true`tak, aby selhání auditovat nemá vliv na aplikaci. V opačném případě je vyvolána výjimka. Všechny úspěšné auditu se zapisují podrobné trasování. Auditovat všechny chyby trasování bude zapsáno na úrovni chyby.  
  
4.  Odstranit existující <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekce chování, které jsou součástí popis <xref:System.ServiceModel.ServiceHost>. Kolekce chování přistupuje <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> vlastnost, která pak přistupuje z <xref:System.ServiceModel.ServiceHostBase.Description%2A> vlastnost. Pak přidejte nové <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do stejné kolekce, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Nastavení auditování v konfiguraci  
  
1.  Chcete-li nastavit auditování v konfiguraci, přidejte [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) element [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) část souboru web.config. Pak přidejte [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) elementu a nastavte různé atributy, jak je znázorněno v následujícím příkladu.  
  
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
 Následující kód vytvoří instanci <xref:System.ServiceModel.ServiceHost> třídy a přidá nový <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> jeho kolekce chování.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nastavení <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnost `true`, potlačí všechny chyby Generovat audity zabezpečení (Pokud nastavena na `false`, je vyvolána výjimka). Nicméně pokud povolíte následující Windows **místní nastavení zabezpečení** vlastnost, nepovedlo se generovat události auditu způsobí, že Windows vypnout okamžitě:  
  
 **Audit: Vypněte okamžitě systém schopen protokolovat audity zabezpečení**  
  
 Chcete-li nastavena vlastnost, otevřete **místní nastavení zabezpečení** dialogové okno. V části **nastavení zabezpečení**, klikněte na tlačítko **místní zásady**. Pak klikněte na tlačítko **možnosti zabezpečení**.  
  
 Pokud <xref:System.ServiceModel.AuditLogLocation> je nastavena na <xref:System.ServiceModel.AuditLogLocation.Security> a **auditování přístupu k objektům** kódu není nastavený **místní zásady zabezpečení**, události auditu se zapisují do protokolu zabezpečení. Všimněte si, že se vrátí bez chyby, ale položky auditu se zapisují do protokolu zabezpečení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)

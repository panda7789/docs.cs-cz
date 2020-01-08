---
title: 'Postupy: auditování událostí zabezpečení Windows Communication Foundation'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], auditing events
ms.assetid: e71e9587-3336-46a2-9a9e-d72a1743ecec
ms.openlocfilehash: 7071aaf88346ee217226632501ebd6c82cfc1cb8
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346760"
---
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Postupy: auditování událostí zabezpečení Windows Communication Foundation
Windows Communication Foundation (WCF) umožňuje protokolovat události zabezpečení do protokolu událostí systému Windows, který lze zobrazit pomocí Prohlížeč událostí systému Windows. Toto téma vysvětluje, jak nastavit aplikaci tak, aby protokoloval události zabezpečení. Další informace o auditování WCF najdete v tématu [auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
### <a name="to-audit-security-events-in-code"></a>Auditování událostí zabezpečení v kódu  
  
1. Zadejte umístění protokolu auditu. Chcete-li to provést, nastavte vlastnost <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> třídy <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> na jednu z hodnot výčtu <xref:System.ServiceModel.AuditLogLocation>, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     Výčet <xref:System.ServiceModel.AuditLogLocation> má tři hodnoty: `Application`, `Security`nebo `Default`. Hodnota určuje jeden z protokolů viditelných v Prohlížeč událostí, buď protokol zabezpečení, nebo protokol aplikace. Pokud použijete `Default` hodnotu, bude skutečný protokol záviset na operačním systému, ve kterém je aplikace spuštěná. Pokud je povolené auditování a umístění protokolu není zadané, použije se výchozí protokol `Security` pro platformy, které podporují zápis do protokolu zabezpečení. v opačném případě bude zapisovat do protokolu `Application`. Ve výchozím nastavení podporuje systém Windows Server 2003 a systém Windows Vista do protokolu zabezpečení pouze zápis.  
  
2. Nastavte typy událostí, které se mají auditovat. Současně můžete auditovat události na úrovni služby nebo události autorizace na úrovni zprávy. Chcete-li to provést, nastavte vlastnost <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> nebo vlastnost <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> na jednu z hodnot výčtu <xref:System.ServiceModel.AuditLevel>, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. Určete, zda se mají potlačit nebo vystavení selhání aplikace v souvislosti s událostmi auditu protokolu. Vlastnost <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> nastavte buď na `true` nebo `false`, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     Výchozí vlastnost `SuppressAuditFailure` je `true`, aby nedošlo k neovlivnění selhání při auditování aplikace. V opačném případě je vyvolána výjimka. U všech úspěšných auditů se zapíše podrobné trasování. V případě jakéhokoli neúspěšného auditu se trasování zapisuje na úroveň chyby.  
  
4. Odstraní existující <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekce chování nalezené v popisu <xref:System.ServiceModel.ServiceHost>. Kolekce chování je k dispozici pomocí vlastnosti <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A>, která je zase k dispozici z vlastnosti <xref:System.ServiceModel.ServiceHostBase.Description%2A>. Pak přidejte novou <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do stejné kolekce, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Nastavení auditování v konfiguraci  
  
1. Chcete-li nastavit auditování v konfiguraci, přidejte [\<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) elementu do [\<části > chování](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) souboru Web. config. Pak přidejte [\<prvek > serviceSecurityAudit](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) a nastavte různé atributy, jak je znázorněno v následujícím příkladu.  
  
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
  
2. Je nutné zadat chování služby, jak je znázorněno v následujícím příkladu.  
  
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
 Následující kód vytvoří instanci třídy <xref:System.ServiceModel.ServiceHost> a přidá novou <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> do kolekce chování.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nastavení vlastnosti <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> na `true`potlačí jakékoli selhání při generování auditů zabezpečení (Pokud je nastaveno na `false`, je vyvolána výjimka). Pokud ale povolíte následující vlastnost **místního nastavení zabezpečení** systému Windows, selhání při generování událostí auditu způsobí, že se systém Windows okamžitě vypne:  
  
 **Audit: není-li možné protokolovat audity zabezpečení, okamžitě vypnout systém.**  
  
 Chcete-li nastavit vlastnost, otevřete dialogové okno **místní nastavení zabezpečení** . V části **nastavení zabezpečení**klikněte na **místní zásady**. Pak klikněte na **Možnosti zabezpečení**.  
  
 Pokud je vlastnost <xref:System.ServiceModel.AuditLogLocation> nastavena na hodnotu <xref:System.ServiceModel.AuditLogLocation.Security> a **Auditovat přístup k objektům** v **místních zásadách zabezpečení**, události auditu nebudou zapsány do protokolu zabezpečení. Všimněte si, že se nevrátí žádná chyba, ale záznamy auditu se nezapisují do protokolu zabezpečení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)

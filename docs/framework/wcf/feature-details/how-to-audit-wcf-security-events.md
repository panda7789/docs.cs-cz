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
# <a name="how-to-audit-windows-communication-foundation-security-events"></a>Postup: Auditování událostí zabezpečení služby Windows Communication Foundation
Windows Communication Foundation (WCF) umožňuje protokolovat události zabezpečení do protokolu událostí systému Windows, který lze zobrazit pomocí prohlížeče událostí systému Windows. Toto téma vysvětluje, jak nastavit aplikaci tak, aby protokolování události zabezpečení. Další informace o auditování WCF naleznete v [tématu Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md).  
  
### <a name="to-audit-security-events-in-code"></a>Auditování událostí zabezpečení v kódu  
  
1. Zadejte umístění protokolu auditu. Chcete-li to <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A> provést, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> nastavte vlastnost třídy na jednu z hodnot výčtu, <xref:System.ServiceModel.AuditLogLocation> jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[AuditingSecurityEvents#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#2)]
     [!code-vb[AuditingSecurityEvents#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#2)]  
  
     Výčet <xref:System.ServiceModel.AuditLogLocation> má tři `Application`hodnoty: `Security`, `Default`, nebo . Hodnota určuje jeden z protokolů viditelných v Prohlížeči událostí, protokol zabezpečení nebo protokol aplikace. Pokud použijete `Default` hodnotu, bude skutečný protokol záviset na operačním systému, ve které je aplikace spuštěna. Pokud je povoleno auditování a není zadáno umístění `Security` protokolu, výchozí je protokol pro platformy, které podporují zápis do protokolu zabezpečení; v opačném případě zapíše do `Application` protokolu. Zápis do protokolu zabezpečení ve výchozím nastavení podporují pouze systémy Windows Server 2003 a Windows Vista.  
  
2. Nastavte typy událostí k auditu. Můžete současně auditovat události na úrovni služby nebo události autorizace na úrovni zprávy. Chcete-li to <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A> provést, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A> nastavte vlastnost nebo <xref:System.ServiceModel.AuditLevel> vlastnost na jednu z hodnot výčtu, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[AuditingSecurityEvents#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#3)]
     [!code-vb[AuditingSecurityEvents#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#3)]  
  
3. Určete, zda chcete potlačit nebo vystavit selhání aplikace týkající se událostí auditu protokolu. Nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnost buď `true` `false`nebo , jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[AuditingSecurityEvents#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#4)]
     [!code-vb[AuditingSecurityEvents#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#4)]  
  
     Výchozí `SuppressAuditFailure` vlastnost `true`je , takže selhání auditu nemá vliv na aplikaci. V opačném případě je vyvolána výjimka. Pro každý úspěšný audit je zapsánpodrobné trasování. Pro jakékoli selhání auditu trasování je zapsána na úrovni Error.  
  
4. Odstranit existující <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> z kolekce chování v popisu <xref:System.ServiceModel.ServiceHost>. Kolekce chování je přístupná <xref:System.ServiceModel.Description.ServiceDescription.Behaviors%2A> vlastnost, která zase je <xref:System.ServiceModel.ServiceHostBase.Description%2A> přístupná z vlastnosti. Pak přidejte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> nové do stejné kolekce, jak je znázorněno v následujícím kódu.  
  
     [!code-csharp[AuditingSecurityEvents#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#5)]
     [!code-vb[AuditingSecurityEvents#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#5)]  
  
### <a name="to-set-up-auditing-in-configuration"></a>Nastavení auditování v konfiguraci  
  
1. Chcete-li nastavit auditování v konfiguraci, přidejte prvek [ \<chování>](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) do [ \<oddílu chování>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) souboru web.config. Potom přidejte [ \<prvek serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) a nastavte různé atributy, jak je znázorněno v následujícím příkladu.  
  
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
  
2. Je nutné zadat chování pro službu, jak je znázorněno v následujícím příkladu.  
  
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
 Následující kód vytvoří instanci <xref:System.ServiceModel.ServiceHost> třídy <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> a přidá nové do své kolekce chování.  
  
 [!code-csharp[AuditingSecurityEvents#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/auditingsecurityevents/cs/auditingsecurityevents.cs#1)]
 [!code-vb[AuditingSecurityEvents#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/auditingsecurityevents/vb/auditingsecurityevents.vb#1)]  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Nastavení <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnosti `true`na , potlačí jakékoli selhání generování `false`auditů zabezpečení (pokud je nastavena na , je vyvolána výjimka). Pokud však povolíte následující vlastnost **Nastavení místního zabezpečení** systému Windows, selhání při generování událostí auditu způsobí okamžité vypnutí systému Windows:  
  
 **Audit: Není-li možno protokolovat audity zabezpečení, vypnout okamžitě systém**  
  
 Chcete-li vlastnost nastavit, otevřete dialogové okno **Nastavení místního zabezpečení.** V části **Nastavení zabezpečení**klepněte na **položku Místní zásady**. Potom klepněte na **položku Možnosti zabezpečení**.  
  
 Pokud <xref:System.ServiceModel.AuditLogLocation> je vlastnost <xref:System.ServiceModel.AuditLogLocation.Security> nastavena na **a auditování přístupu k objektům** není nastaveno v **místních zásadách zabezpečení**, události auditu nebudou zapsány do protokolu zabezpečení. Všimněte si, že není vrácena žádná chyba, ale položky auditu nejsou zapsány do protokolu zabezpečení.  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.AuditLogLocation%2A>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)

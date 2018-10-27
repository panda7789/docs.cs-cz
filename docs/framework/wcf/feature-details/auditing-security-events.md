---
title: Auditování událostí zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: 70bd756c9de2cf6ffb43479b0b28a6d51340f905
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/26/2018
ms.locfileid: "50048252"
---
# <a name="auditing-security-events"></a>Auditování událostí zabezpečení
Aplikace vytvořené pomocí služby Windows Communication Foundation (WCF) může protokolovat události zabezpečení (úspěch, selhání nebo obě) se tato funkce. Události se zapisují do protokolu událostí systému Windows a lze jej prozkoumat pomocí prohlížeče událostí.  
  
 Auditování poskytuje způsob, jak správce ke zjištění útoku, který má již došlo k chybě nebo probíhá. Kromě toho auditování pomáhá vývojářům ladit problémy související se zabezpečením. Například pokud k chybě v konfiguraci autorizace nebo kontrola zásad omylem odepře přístup k autorizovaným uživatelům, Vývojář můžete rychle zjišťovat a najít příčinu této chyby naleznete v protokolu událostí.  
  
 Další informace o zabezpečení WCF najdete v tématu [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md). Další informace o programování WCF najdete v tématu [základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Úroveň auditování a chování  
 Existují dvě úrovně auditů zabezpečení:  
  
-   Úroveň autorizace služby, ve kterém je volající oprávnění.  
  
-   Úroveň zprávy, ve kterém WCF kontroluje platnost zpráv a ověří volajícího.  
  
 Můžete zkontrolovat obě auditu úrovně o úspěch nebo chybu, která se nazývá *auditu chování*.  
  
## <a name="audit-log-location"></a>Umístění protokolu auditu  
 Jakmile určíte úroveň auditování a chování služby, můžete vy (nebo správcem) zadejte umístění protokolu auditu. Tři možnosti jsou: výchozí, aplikace a zabezpečení. Při zadání výchozí skutečné protokolu závisí na systém, který používáte a určuje, zda systém podporuje zápis do protokolu zabezpečení. Další informace najdete v části "Operační systém" dále v tomto tématu.  
  
 Zapsat do protokolu zabezpečení vyžaduje `SeAuditPrivilege`. Ve výchozím nastavení pouze místní systém a Network Service účty mají toto oprávnění. Ke správě funkcí protokolu zabezpečení `read` a `delete` vyžaduje `SeSecurityPrivilege`. Ve výchozím nastavení pouze správci mají toto oprávnění.  
  
 Naproti tomu může ověřeným uživatelům číst a zapisovat do protokolu aplikace. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] zápisy auditovat události do protokolu aplikací ve výchozím nastavení. Protokol může také obsahovat osobní informace, které jsou viditelné pro všechny ověřené uživatele.  
  
## <a name="suppressing-audit-failures"></a>Potlačení chyby auditu  
 Další možností při auditování se, jestli se má potlačit jakékoli neúspěšný audit. Ve výchozím nastavení selhání audit nemá vliv na aplikaci. V případě potřeby však můžete nastavit možnost `false`, což způsobuje vyvolání výjimky.  
  
## <a name="programming-auditing"></a>Auditování programování  
 Chování auditování můžete programově nebo prostřednictvím konfigurace.  
  
### <a name="auditing-classes"></a>Auditování třídy  
 Následující tabulka popisuje třídy a vlastnosti pro program auditování chování.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Povolí nastavení možností pro auditování jako chování služby.|  
|<xref:System.ServiceModel.AuditLogLocation>|Výčet k určení, které k zápisu do protokolu. Možné hodnoty jsou výchozí, aplikace a zabezpečení. Při výběru výchozí operačního systému určuje umístění skutečného protokolu. V části "Aplikace nebo zabezpečení protokolu událostí podle výběru" dále v tomto tématu.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|Určuje, jaké typy událostí ověření zprávy se auditují na úrovni zprávy. Možnosti jsou `None`, `Failure`, `Success`, a `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Určuje, jaké typy událostí autorizace služby se auditují na úrovni služby. Možnosti jsou `None`, `Failure`, `Success`, a `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Určuje, co se stane na žádosti klientů při auditování se nezdaří. Například pokud služba pokusí se zapsat do protokolu zabezpečení, ale nemá `SeAuditPrivilege`. Výchozí hodnota `true` označuje, že chyby jsou ignorovány a žádost klienta se zpracují normálně.|  
  
 Příklad nastavení aplikace k zaznamenání událostí auditu najdete v tématu [postupy: auditování událostí zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Konfigurace  
 Konfigurace můžete použít také k určení chování auditování tak, že přidáte [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) pod [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md). Je nutné přidat prvek v části [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) jak je znázorněno v následujícím kódu.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <behavior>  
        <!— auditLogLocation="Application" or "Security" -—>  
        <serviceSecurityAudit  
                  auditLogLocation="Application"  
                  suppressAuditFailure="true"  
                  serviceAuthorizationAuditLevel="Failure"  
                  messageAuthenticationAuditLevel="SuccessOrFailure" />   
      </behavior>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 Pokud je povolené auditování a `auditLogLocation` není zadán, výchozí název protokolu je "Zabezpečení" protokolu pro platformu podporující zápis do protokolu zabezpečení; v opačném případě je protokol "Aplikace". Pouze [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wv](../../../../includes/wv-md.md)] operační systémy podporují zápis do protokolu zabezpečení. Další informace najdete v části "Operační systém" dále v tomto tématu.  
  
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Pokud uživatel se zlými úmysly ví, že je povolené auditování, že útočník odeslat neplatná zprávy, které způsobují auditu má být proveden zápis. Pokud je tímto způsobem protokolu auditu, selhání auditování systému. Chcete-li tento problém zmírnit, nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnost `true` a použití vlastností v prohlížeči událostí pro řízení chování auditování. Další informace najdete v tématu Článek Microsoft Support na zobrazení a správu protokolů událostí s použitím prohlížeče události ve Windows XP k dispozici na [zobrazení a správě protokolů událostí v prohlížeči událostí ve Windows XP](https://go.microsoft.com/fwlink/?LinkId=89150).  
  
 Události auditu, které se zapisují do protokolu aplikací na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] jsou viditelné pro všechny ověřené uživatele.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Volba mezi aplikací a protokolů událostí zabezpečení  
 Následující tabulka obsahuje informace, které vám pomůžou zvolit, jestli se má přihlásit do protokolu událostí zabezpečení nebo aplikace.  
  
#### <a name="operating-system"></a>Operační systém  
  
|Systém|Protokolu aplikace|Protokol zabezpečení|  
|------------|---------------------|------------------|  
|[!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] nebo novější|Podporováno|Nepodporováno|  
|[!INCLUDE[ws2003sp1](../../../../includes/ws2003sp1-md.md)] a [!INCLUDE[wv](../../../../includes/wv-md.md)]|Podporováno|Musí mít kontext vlákna `SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Další faktory  
 Kromě operačního systému následující tabulka popisuje další nastavení, která řídí povolení protokolování.  
  
|faktor|Protokolu aplikace|Protokol zabezpečení|  
|------------|---------------------|------------------|  
|Správa zásad auditu|Nelze použít.|Spolu s konfiguraci protokolu zabezpečení řídí také místní autorita (LSA) zásady zabezpečení. Kategorie "Auditovat přístup k objektům" musí být povolena také.|  
|Výchozí uživatelské prostředí|Všem ověřeným uživatelům můžete zapisovat do aplikačního protokolu, takže žádná další oprávnění krok je nezbytný pro procesy aplikace.|Proces aplikace (objektu context) musí mít `SeAuditPrivilege`.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Postupy: Auditování událostí zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)  
 [\<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
 [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)

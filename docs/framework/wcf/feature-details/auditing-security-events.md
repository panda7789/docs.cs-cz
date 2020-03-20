---
title: Auditování událostí zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: 535f19741ff26e9472ce56ff06b670f7d0523be8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185458"
---
# <a name="auditing-security-events"></a>Auditování událostí zabezpečení
Aplikace vytvořené pomocí windows communication foundation (WCF) můžete protokolovat události zabezpečení (úspěch, selhání, nebo obojí) s funkcí auditování. Události jsou zapsány do protokolu systémových událostí systému Windows a mohou být zkontrolovány pomocí Prohlížeče událostí.  
  
 Auditování poskytuje správci způsob, jak zjistit útok, ke kterému již došlo nebo probíhá. Auditování může navíc vývojáři pomoci ladit problémy související se zabezpečením. Například pokud chyba v konfiguraci autorizace nebo kontrolní zásady omylem odepře přístup oprávněnému uživateli, může vývojář rychle zjistit a izolovat příčinu této chyby kontrolou protokolu událostí.  
  
 Další informace o zabezpečení WCF naleznete v [tématu Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md). Další informace o programování WCF naleznete [v tématu Basic WCF Programming](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Úroveň auditu a chování  
 Existují dvě úrovně bezpečnostních auditů:  
  
- Úroveň autorizace služby, ve které je volající autorizován.  
  
- Úroveň zprávy, ve kterém WCF kontroluje platnost zprávy a ověřuje volajícího.  
  
 Můžete zkontrolovat obě úrovně auditu pro úspěch nebo neúspěch, který se označuje jako *chování auditu*.  
  
## <a name="audit-log-location"></a>Umístění protokolu auditu  
 Jakmile určíte úroveň auditu a chování, můžete vy (nebo správce) určit umístění protokolu auditu. Mezi tři možnosti patří: Výchozí, Aplikace a Zabezpečení. Zadáte-li výchozí, závisí skutečný protokol na tom, který systém používáte a zda systém podporuje zápis do protokolu zabezpečení. Další informace naleznete v části Operační systém dále v tomto tématu.  
  
 Chcete-li zapisovat `SeAuditPrivilege`do protokolu zabezpečení, je třeba, aby program . Ve výchozím nastavení mají toto oprávnění pouze účty místních systémových a síťových služeb. Chcete-li spravovat `read` funkce `delete` protokolu `SeSecurityPrivilege`zabezpečení a vyžaduje . Ve výchozím nastavení mají toto oprávnění pouze správci.  
  
 Naproti tomu ověření uživatelé mohou číst a zapisovat do protokolu aplikace. Systém Windows XP ve výchozím nastavení zapisuje události auditu do protokolu aplikací. Protokol může také obsahovat osobní informace, které jsou viditelné pro všechny ověřené uživatele.  
  
## <a name="suppressing-audit-failures"></a>Potlačení selhání auditu  
 Další možností během auditování je, zda potlačit jakékoli selhání auditu. Ve výchozím nastavení selhání auditu nemá vliv na aplikaci. V případě potřeby však můžete `false`nastavit možnost , která způsobí, že výjimka má být vyvolána.  
  
## <a name="programming-auditing"></a>Programování auditování  
 Chování auditování můžete určit programově nebo prostřednictvím konfigurace.  
  
### <a name="auditing-classes"></a>Auditování tříd  
 Následující tabulka popisuje třídy a vlastnosti používané k programování chování auditování.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Umožňuje nastavení možností auditování jako chování služby.|  
|<xref:System.ServiceModel.AuditLogLocation>|Výčet určit, který protokol zapisovat. Možné hodnoty jsou Výchozí, Aplikace a Zabezpečení. Když vyberete Výchozí, operační systém určuje skutečné umístění protokolu. Viz část "Volba protokolu událostí aplikace nebo zabezpečení" dále v tomto tématu.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|Určuje, které typy událostí ověřování zpráv jsou auditovány na úrovni zprávy. Volby `None`jsou `Failure` `Success`, `SuccessOrFailure`, a .|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Určuje, které typy událostí autorizace služby jsou auditovány na úrovni služby. Volby `None`jsou `Failure` `Success`, `SuccessOrFailure`, a .|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Určuje, co se stane s požadavkem klienta při selhání auditování. Například když se služba pokusí o zápis do protokolu `SeAuditPrivilege`zabezpečení, ale nemá . Výchozí hodnota `true` označuje, že chyby jsou ignorovány a požadavek klienta je zpracován a normálně.|  
  
 Příklad nastavení aplikace pro protokolování událostí auditu naleznete v tématu [How to: Audit Security Events](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Konfigurace  
 Pomocí konfigurace můžete také určit chování auditování přidáním [ \<>serviceSecurityAudit](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) pod [ \<chování>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md). Prvek je nutné přidat pod [ \<>chování,](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) jak je znázorněno v následujícím kódu.  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <behavior>  
        <!-- auditLogLocation="Application" or "Security" -->  
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
  
 Pokud je auditování `auditLogLocation` povoleno a není zadán, výchozí název protokolu protokolu je "Zabezpečení" pro platformu podporující zápis do protokolu zabezpečení; v opačném případě je "Aplikace" log. Zápis do protokolu zabezpečení podporují pouze operační systémy Windows Server 2003 a Windows Vista. Další informace naleznete v části Operační systém dále v tomto tématu.  
  
## <a name="security-considerations"></a>Aspekty zabezpečení  
 Pokud uživatel se zlými úmysly ví, že auditování je povoleno, může útočník odeslat neplatné zprávy, které způsobí zápis položek auditu. Pokud je protokol auditu vyplněn tímto způsobem, systém auditování se nezdaří. Chcete-li to <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> zmírnit, nastavte vlastnost `true` a použijte vlastnosti Prohlížeče událostí k řízení chování auditování.  
  
 Události auditu, které jsou zapsány do protokolu aplikací v systému Windows XP, jsou viditelné pro všechny ověřené uživatele.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Výběr mezi protokoly událostí aplikace a zabezpečení  
 Následující tabulky poskytují informace, které vám pomohou zvolit, zda se chcete přihlásit do aplikace nebo protokolu událostí zabezpečení.  
  
#### <a name="operating-system"></a>Operační systém  
  
|Systémový|Protokol aplikací|Protokol zabezpečení|  
|------------|---------------------|------------------|  
|Aktualizace Windows XP SP2 nebo novější|Podporuje se|Nepodporuje se|  
|Aktualizace Windows Server 2003 SP1 a Windows Vista|Podporuje se|Kontext vlákna musí mít.`SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Další faktory  
 Kromě operačního systému popisuje následující tabulka další nastavení, která řídí povolení protokolování.  
  
|Faktor|Protokol aplikací|Protokol zabezpečení|  
|------------|---------------------|------------------|  
|Správa auditní politiky|Neužívá se.|Spolu s konfigurací je protokol zabezpečení také řízen zásadami místního úřadu zabezpečení (LSA). Kategorie "Auditovat přístup k objektům" musí být také povolena.|  
|Výchozí uživatelské prostředí|Všichni ověření uživatelé mohou zapisovat do protokolu aplikace, takže pro procesy aplikace není potřeba žádný další krok oprávnění.|Proces žádosti (kontext) `SeAuditPrivilege`musí mít .|  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Postupy: Auditování událostí zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
- [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)
- [\<chování>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [Model zabezpečení pro infrastrukturu aplikací pro Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))

---
title: Auditování událostí zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: e4219553f97f272577e8efdeb106b43e5f76ee59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="auditing-security-events"></a>Auditování událostí zabezpečení
Aplikace vytvořené s Windows Communication Foundation (WCF) může protokolovat události zabezpečení (úspěch, chyba nebo obě) se funkci auditování. Události se zapisují do protokolu událostí systému Windows a může být prověřen pomocí prohlížeče událostí.  
  
 Auditování poskytuje způsob, jak správce ke zjištění útoku, který má již došlo k chybě nebo právě probíhá. Kromě toho audit může pomoct vývojář pro ladění problémů souvisejících se zabezpečením. Například pokud k chybě v konfiguraci ověřování nebo Zásady vracení se změnami omylem odepře přístup k autorizovaným uživatelem, Vývojář můžete rychle zjistit a najít příčinu této chyby kontrolou protokolu událostí.  
  
 Další informace o zabezpečení WCF najdete v tématu [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md). Další informace o programování WCF najdete v tématu [základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Úroveň auditování a chování  
 Existují dvě úrovně audity zabezpečení:  
  
-   Úrovně autorizace služby, ve kterém má volající oprávnění.  
  
-   Úroveň zprávy, ve kterém WCF kontroluje platnost zpráv a ověří volajícího.  
  
 Můžete zkontrolovat obě audit úrovně pro úspěch nebo selhání, která se označuje jako *audit chování*.  
  
## <a name="audit-log-location"></a>Umístění protokolu auditování  
 Jakmile určíte, chování a úroveň auditování, můžete zadat umístění pro protokol auditu vy (nebo správce). Zahrnout tři možnosti: výchozí, aplikace a zabezpečení. Když zadáte výchozí, skutečný protokolu závisí na systém, který používáte a jestli systém podporuje zápis do protokolu zabezpečení. Další informace najdete v části "Operační systém" dál v tomto tématu.  
  
 Zápis do protokolu zabezpečení vyžaduje `SeAuditPrivilege`. Ve výchozím nastavení pouze místní systém a Network Service účty mít toto oprávnění. Ke správě funkcí protokolu zabezpečení `read` a `delete` vyžaduje `SeSecurityPrivilege`. Ve výchozím nastavení je toto oprávnění mají pouze správci.  
  
 Naproti tomu ověřené uživatele můžete číst a zapisovat do protokolu aplikace. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] zápisy auditovat události v protokolu aplikací ve výchozím nastavení. Protokol může také obsahovat osobní informace, které jsou viditelné pro všechny ověřené uživatele.  
  
## <a name="suppressing-audit-failures"></a>Potlačení selhání auditu  
 Další možností při auditování je, jestli se má potlačit jakákoli chyba auditu. Ve výchozím nastavení neovlivňuje chybu auditu aplikace. V případě potřeby však můžete nastavit možnost `false`, což způsobí, že vyvolání výjimky.  
  
## <a name="programming-auditing"></a>Auditování programování  
 Můžete určit chování auditování, buď programově, nebo prostřednictvím konfigurace.  
  
### <a name="auditing-classes"></a>Auditování třídy  
 Následující tabulka popisuje třídy a vlastnosti používané k programu auditování chování.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Umožňuje nastavení možností pro auditování jako chování služby.|  
|<xref:System.ServiceModel.AuditLogLocation>|Výčet k určení, které k zápisu do protokolu. Možné hodnoty jsou výchozí, aplikace a zabezpečení. Když vyberete výchozí, operačního systému určuje umístění skutečné protokolu. Najdete v části "Aplikace nebo zabezpečení protokolu událostí volba" dál v tomto tématu.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|Určuje, jaké typy událostí ověření zprávy se auditují na úrovni zpráv. Možnosti jsou `None`, `Failure`, `Success`, a `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Určuje, jaké typy událostí autorizace služby se auditují na úrovni služby. Možnosti jsou `None`, `Failure`, `Success`, a `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Určuje, co se stane žádost klienta při auditování selže. Například když služba pokusí se zapsat do protokolu zabezpečení, ale nemá `SeAuditPrivilege`. Výchozí hodnota `true` označuje, že chyby jsou ignorovány a požadavek klienta se zpracují normálně.|  
  
 Příklad nastavení aplikace do protokolu událostí auditu, naleznete v části [postup: auditování událostí zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Konfigurace  
 Konfigurace můžete použít také k určení chování auditování přidáním [ \<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) pod [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md). Je nutné přidat prvek v rámci [ \<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) jak je znázorněno v následujícím kódu.  
  
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
  
 Pokud je povoleno auditování a `auditLogLocation` není zadána, je výchozí název protokolu "Zabezpečení" protokolu pro platformu podporující zápis do protokolu zabezpečení, jinak hodnota je "Aplikace" protokolu. Pouze [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a [!INCLUDE[wv](../../../../includes/wv-md.md)] operační systémy podporují zápis do protokolu zabezpečení. Další informace najdete v části "Operační systém" dál v tomto tématu.  
  
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Pokud uživatel se zlými úmysly ví, že je povoleno auditování, útočník odeslat neplatná zprávy, které způsobí položky auditu k zapsání. Pokud protokol auditu tímto způsobem, systém auditování selže. Toto riziko lze nastavit <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnost `true` a použití vlastností prohlížeče událostí můžete řídit chování auditování. Další informace najdete v tématu Článek Microsoft Support na zobrazování a správu protokolů událostí pomocí prohlížeče událostí v systému Windows XP k dispozici na [postup zobrazení a správě protokolů událostí v prohlížeči událostí v systému Windows XP](http://go.microsoft.com/fwlink/?LinkId=89150).  
  
 Události auditu, které se zapisují do aplikačního protokolu na [!INCLUDE[wxp](../../../../includes/wxp-md.md)] jsou viditelné pro všechny ověřené uživatele.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Výběr mezi aplikací a protokolů událostí zabezpečení  
 Následující tabulky obsahují informace, které vám pomohou zvolit, jestli se k přihlášení do aplikace nebo v protokolu událostí zabezpečení.  
  
#### <a name="operating-system"></a>Operační systém  
  
|Systém|Protokolu aplikace|Protokolu zabezpečení|  
|------------|---------------------|------------------|  
|[!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] nebo novější|Podporováno|Nepodporováno|  
|[!INCLUDE[ws2003sp1](../../../../includes/ws2003sp1-md.md)] A [!INCLUDE[wv](../../../../includes/wv-md.md)]|Podporováno|Musíte mít přístup z více vláken kontextu `SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Další faktory  
 Kromě operační systém následující tabulka popisuje další nastavení, které řídí povolování protokolování.  
  
|Koeficient|Protokolu aplikace|Protokolu zabezpečení|  
|------------|---------------------|------------------|  
|Správa zásad auditu|Nelze použít.|Společně s konfiguraci protokolu zabezpečení také řídí místní autorita (LSA) zásady zabezpečení. Kategorie "Auditovat přístup k objektům" musí být rovněž povolena.|  
|Výchozí uživatelské prostředí|Všem ověřeným uživatelům můžete zapisovat do aplikačního protokolu, takže žádná další oprávnění krok je nutný pro procesy aplikace.|Proces aplikace (kontextu) musí mít `SeAuditPrivilege`.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>  
 <xref:System.ServiceModel.AuditLogLocation>  
 [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)  
 [Postupy: Auditování událostí zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)  
 [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)  
 [\<chování >](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)  
 [Model zabezpečení pro Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)

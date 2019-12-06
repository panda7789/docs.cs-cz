---
title: Auditování událostí zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: fec23439236fccb23964c0feb22691a973c787b1
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74838088"
---
# <a name="auditing-security-events"></a>Auditování událostí zabezpečení
Aplikace vytvořené pomocí Windows Communication Foundation (WCF) můžou protokolovat události zabezpečení (buď úspěšné, neúspěšné nebo oboje) pomocí funkce auditování. Události se zapisují do protokolu událostí systému Windows a dají se prozkoumat pomocí Prohlížeč událostí.  
  
 Auditování poskytuje způsob, jak může správce detekovat útok, který již nastal nebo právě probíhá. Kromě toho může auditování pomáhat vývojářům ladit problémy související se zabezpečením. Pokud například Chyba v konfiguraci autorizace nebo zásady kontroly omylem odepře přístup k autorizovanému uživateli, může vývojář rychle zjistit a izolovat příčinu této chyby zkoumáním protokolu událostí.  
  
 Další informace o zabezpečení služby WCF najdete v tématu [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md). Další informace o programování WCF naleznete v tématu [Základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Úroveň a chování auditu  
 Existují dvě úrovně auditů zabezpečení:  
  
- Úroveň autorizace služby, při které je volající autorizován.  
  
- Úroveň zprávy, ve které WCF kontroluje platnost zprávy a ověřuje volajícího.  
  
 Můžete kontrolovat úroveň auditu pro úspěch nebo neúspěch, což se označuje jako *chování auditu*.  
  
## <a name="audit-log-location"></a>Umístění protokolu auditu  
 Jakmile určíte úroveň auditu a chování, můžete vy (nebo správce) určit umístění protokolu auditu. K dispozici jsou tři možnosti: výchozí, aplikace a zabezpečení. Když zadáte výchozí hodnotu, skutečný protokol závisí na použitém systému a na tom, jestli systém podporuje zápis do protokolu zabezpečení. Další informace najdete v části operační systém dále v tomto tématu.  
  
 Pro zápis do protokolu zabezpečení vyžaduje `SeAuditPrivilege`. Ve výchozím nastavení mají toto oprávnění pouze účty místní systém a síťová služba. Chcete-li spravovat funkce protokolu zabezpečení `read` a `delete` vyžaduje `SeSecurityPrivilege`. Ve výchozím nastavení mají toto oprávnění pouze správci.  
  
 Naopak ověření uživatelé mohou číst a zapisovat do protokolu aplikace. ve výchozím nastavení [!INCLUDE[wxp](../../../../includes/wxp-md.md)] zapisuje události auditu do protokolu aplikace. Protokol může obsahovat také osobní údaje, které jsou viditelné všem ověřeným uživatelům.  
  
## <a name="suppressing-audit-failures"></a>Potlačení selhání auditu  
 Další možností při auditování je to, jestli se má potlačit chyba auditu. Ve výchozím nastavení nemá chyba auditu vliv na aplikaci. V případě potřeby však můžete nastavit možnost `false`, což způsobí, že bude vyvolána výjimka.  
  
## <a name="programming-auditing"></a>Auditování programování  
 Chování auditování můžete určit buď prostřednictvím kódu programu, nebo prostřednictvím konfigurace.  
  
### <a name="auditing-classes"></a>Třídy auditování  
 Následující tabulka popisuje třídy a vlastnosti, které se používají k chování auditování programu.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Povolí možnosti nastavení pro auditování jako chování služby.|  
|<xref:System.ServiceModel.AuditLogLocation>|Výčet, který určuje, do kterého protokolu zapisovat. Možné hodnoty jsou výchozí, aplikace a zabezpečení. Když vyberete výchozí, operační systém určí skutečné umístění protokolu. Další informace najdete v části Výběr protokolu událostí aplikace nebo zabezpečení níže v tomto tématu.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|Určuje, které typy událostí ověřování zpráv jsou auditovány na úrovni zprávy. Volby jsou `None`, `Failure`, `Success`a `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Určuje, které typy událostí autorizace služby jsou auditovány na úrovni služby. Volby jsou `None`, `Failure`, `Success`a `SuccessOrFailure`.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Určuje, co se stane s požadavkem klienta, když se auditování nezdařilo. Například když se služba pokusí zapisovat do protokolu zabezpečení, ale nemá `SeAuditPrivilege`. Výchozí hodnota `true` označuje, že selhání se ignorují a požadavek klienta se zpracovává normálně.|  
  
 Příklad nastavení aplikace pro protokolování událostí auditu najdete v tématu [Postupy: audit událostí zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Konfigurace  
 Konfiguraci můžete také použít k určení chování auditování přidáním [\<serviceSecurityAudit >](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md) v [> chování\<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md). Je nutné přidat prvek pod [chování\<](../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) , jak je znázorněno v následujícím kódu.  
  
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
  
 Pokud je povolené auditování a `auditLogLocation` nezadáte, použije se výchozí název protokolu "Security" (zabezpečení) pro platformu, která podporuje zápis do protokolu zabezpečení. v opačném případě se jedná o protokol "aplikace". Pouze operační systémy [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] a Windows Vista podporují zápis do protokolu zabezpečení. Další informace najdete v části operační systém dále v tomto tématu.  
  
## <a name="security-considerations"></a>Důležité informace o zabezpečení  
 Pokud uživatel se zlými úmysly ví, že je povolené auditování, může útočník odeslat neplatné zprávy, které způsobí zápis položek auditu. Pokud se tento způsob vyplní protokolem auditu, systém auditování se nezdařil. Pokud to chcete zmírnit, nastavte vlastnost <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> na `true` a použijte vlastnosti Prohlížeč událostí k řízení chování auditování. Další informace najdete v článku podpora Microsoftu o zobrazení a správě protokolů událostí pomocí Prohlížeč událostí v systému Windows XP, který je k dispozici na stránce [jak zobrazit a spravovat protokoly událostí v Prohlížeč událostí systému Windows XP](https://go.microsoft.com/fwlink/?LinkId=89150).  
  
 Události auditu, které jsou zapsány do aplikačního protokolu [!INCLUDE[wxp](../../../../includes/wxp-md.md)], jsou viditelné pro všechny ověřené uživatele.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Volba mezi protokoly událostí aplikace a zabezpečení  
 Následující tabulky obsahují informace, které vám pomůžou vybrat, jestli se chcete přihlásit k aplikaci nebo protokolu událostí zabezpečení.  
  
#### <a name="operating-system"></a>Operační systém  
  
|Systém|Protokol aplikace|Protokol zabezpečení|  
|------------|---------------------|------------------|  
|[!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] nebo novější|Podporované|Není podporováno|  
|[!INCLUDE[ws2003sp1](../../../../includes/ws2003sp1-md.md)] a Windows Vista|Podporované|Kontext vlákna musí mít `SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Jiné faktory  
 Kromě operačního systému jsou v následující tabulce popsána další nastavení, která řídí povolení protokolování.  
  
|faktor|Protokol aplikace|Protokol zabezpečení|  
|------------|---------------------|------------------|  
|Správa zásad auditu|Nelze použít.|Spolu s konfigurací je protokol zabezpečení také řízen zásadami místního úřadu zabezpečení (LSA). Je také nutné povolit kategorii přístup k objektům auditu.|  
|Výchozí uživatelské prostředí|Všichni ověření uživatelé můžou zapisovat do aplikačního protokolu, takže žádný další krok oprávnění není potřeba pro procesy aplikace.|Proces aplikace (kontext) musí mít `SeAuditPrivilege`.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Přehled zabezpečení](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Základní programování WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
- [Postupy: Auditování událostí zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)
- [\<serviceSecurityAudit>](../../../../docs/framework/configure-apps/file-schema/wcf/servicesecurityaudit.md)
- [chování \<](../../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [Model zabezpečení pro Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)

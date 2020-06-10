---
title: Auditování událostí zabezpečení
ms.date: 03/30/2017
helpviewer_keywords:
- auditing security events [WCF]
ms.assetid: 5633f61c-a3c9-40dd-8070-1c373b66a716
ms.openlocfilehash: b130ed57ba086535122c8c8795c42863348870d0
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84597654"
---
# <a name="auditing-security-events"></a>Auditování událostí zabezpečení
Aplikace vytvořené pomocí Windows Communication Foundation (WCF) můžou protokolovat události zabezpečení (buď úspěšné, neúspěšné nebo oboje) pomocí funkce auditování. Události se zapisují do protokolu událostí systému Windows a dají se prozkoumat pomocí Prohlížeč událostí.  
  
 Auditování poskytuje způsob, jak může správce detekovat útok, který již nastal nebo právě probíhá. Kromě toho může auditování pomáhat vývojářům ladit problémy související se zabezpečením. Pokud například Chyba v konfiguraci autorizace nebo zásady kontroly omylem odepře přístup k autorizovanému uživateli, může vývojář rychle zjistit a izolovat příčinu této chyby zkoumáním protokolu událostí.  
  
 Další informace o zabezpečení služby WCF najdete v tématu [Přehled zabezpečení](security-overview.md). Další informace o programování WCF naleznete v tématu [Základní programování WCF](../basic-wcf-programming.md).  
  
## <a name="audit-level-and-behavior"></a>Úroveň a chování auditu  
 Existují dvě úrovně auditů zabezpečení:  
  
- Úroveň autorizace služby, při které je volající autorizován.  
  
- Úroveň zprávy, ve které WCF kontroluje platnost zprávy a ověřuje volajícího.  
  
 Můžete kontrolovat úroveň auditu pro úspěch nebo neúspěch, což se označuje jako *chování auditu*.  
  
## <a name="audit-log-location"></a>Umístění protokolu auditu  
 Jakmile určíte úroveň auditu a chování, můžete vy (nebo správce) určit umístění protokolu auditu. K dispozici jsou tři možnosti: výchozí, aplikace a zabezpečení. Když zadáte výchozí hodnotu, skutečný protokol závisí na použitém systému a na tom, jestli systém podporuje zápis do protokolu zabezpečení. Další informace najdete v části operační systém dále v tomto tématu.  
  
 Pro zápis do protokolu zabezpečení vyžaduje `SeAuditPrivilege` . Ve výchozím nastavení mají toto oprávnění pouze účty místní systém a síťová služba. Pro správu funkcí protokolu zabezpečení `read` a `delete` vyžaduje `SeSecurityPrivilege` . Ve výchozím nastavení mají toto oprávnění pouze správci.  
  
 Naopak ověření uživatelé mohou číst a zapisovat do protokolu aplikace. Systém Windows XP ve výchozím nastavení zapisuje události auditu do protokolu aplikace. Protokol může obsahovat také osobní údaje, které jsou viditelné všem ověřeným uživatelům.  
  
## <a name="suppressing-audit-failures"></a>Potlačení selhání auditu  
 Další možností při auditování je to, jestli se má potlačit chyba auditu. Ve výchozím nastavení nemá chyba auditu vliv na aplikaci. V případě potřeby však můžete nastavit možnost na `false` , což způsobí vyvolání výjimky.  
  
## <a name="programming-auditing"></a>Auditování programování  
 Chování auditování můžete určit buď prostřednictvím kódu programu, nebo prostřednictvím konfigurace.  
  
### <a name="auditing-classes"></a>Třídy auditování  
 Následující tabulka popisuje třídy a vlastnosti, které se používají k chování auditování programu.  
  
|Třída|Popis|  
|-----------|-----------------|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>|Povolí možnosti nastavení pro auditování jako chování služby.|  
|<xref:System.ServiceModel.AuditLogLocation>|Výčet, který určuje, do kterého protokolu zapisovat. Možné hodnoty jsou výchozí, aplikace a zabezpečení. Když vyberete výchozí, operační systém určí skutečné umístění protokolu. Další informace najdete v části Výběr protokolu událostí aplikace nebo zabezpečení níže v tomto tématu.|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.MessageAuthenticationAuditLevel%2A>|Určuje, které typy událostí ověřování zpráv jsou auditovány na úrovni zprávy. Volby jsou `None` ,, `Failure` `Success` a `SuccessOrFailure` .|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.ServiceAuthorizationAuditLevel%2A>|Určuje, které typy událostí autorizace služby jsou auditovány na úrovni služby. Volby jsou `None` ,, `Failure` `Success` a `SuccessOrFailure` .|  
|<xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A>|Určuje, co se stane s požadavkem klienta, když se auditování nezdařilo. Například když se služba pokusí zapisovat do protokolu zabezpečení, ale nemá `SeAuditPrivilege` . Výchozí hodnota `true` znamená, že se chyby ignorují a požadavek klienta se zpracuje normálně.|  
  
 Příklad nastavení aplikace pro protokolování událostí auditu najdete v tématu [Postupy: audit událostí zabezpečení](how-to-audit-wcf-security-events.md).  
  
### <a name="configuration"></a>Konfigurace  
 Konfiguraci můžete také použít k určení chování auditování přidáním [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md) pod [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md) . Je nutné přidat prvek pod a [\<behavior>](../../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) , jak je znázorněno v následujícím kódu.  
  
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
  
 Pokud je auditování zapnuté a není `auditLogLocation` zadané, použije se výchozí název protokolu zabezpečení pro platformu, která podporuje zápis do protokolu zabezpečení. v opačném případě se jedná o protokol "Application". Pouze operační systémy Windows Server 2003 a Windows Vista podporují zápis do protokolu zabezpečení. Další informace najdete v části operační systém dále v tomto tématu.  
  
## <a name="security-considerations"></a>Aspekty zabezpečení  
 Pokud uživatel se zlými úmysly ví, že je povolené auditování, může útočník odeslat neplatné zprávy, které způsobí zápis položek auditu. Pokud se tento způsob vyplní protokolem auditu, systém auditování se nezdařil. Pokud to chcete zmírnit, nastavte <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior.SuppressAuditFailure%2A> vlastnost na `true` a použijte vlastnosti Prohlížeč událostí k řízení chování auditování.  
  
 Události auditu, které jsou zapsány do protokolu aplikace v systému Windows XP, jsou viditelné pro všechny ověřené uživatele.  
  
## <a name="choosing-between-application-and-security-event-logs"></a>Volba mezi protokoly událostí aplikace a zabezpečení  
 Následující tabulky obsahují informace, které vám pomůžou vybrat, jestli se chcete přihlásit k aplikaci nebo protokolu událostí zabezpečení.  
  
#### <a name="operating-system"></a>Operační systém  
  
|Systémový|Protokol aplikace|Protokol zabezpečení|  
|------------|---------------------|------------------|  
|Windows XP SP2 nebo novější|Podporuje se|Nepodporuje se|  
|Windows Server 2003 SP1 a Windows Vista|Podporuje se|Kontext vlákna musí mít`SeAuditPrivilege`|  
  
#### <a name="other-factors"></a>Jiné faktory  
 Kromě operačního systému jsou v následující tabulce popsána další nastavení, která řídí povolení protokolování.  
  
|Jednotek|Protokol aplikace|Protokol zabezpečení|  
|------------|---------------------|------------------|  
|Správa zásad auditu|Neužívá se.|Spolu s konfigurací je protokol zabezpečení také řízen zásadami místního úřadu zabezpečení (LSA). Je také nutné povolit kategorii přístup k objektům auditu.|  
|Výchozí uživatelské prostředí|Všichni ověření uživatelé můžou zapisovat do aplikačního protokolu, takže žádný další krok oprávnění není potřeba pro procesy aplikace.|Proces aplikace (kontext) musí mít `SeAuditPrivilege` .|  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- <xref:System.ServiceModel.AuditLogLocation>
- [Přehled zabezpečení](security-overview.md)
- [Základní programování WCF](../basic-wcf-programming.md)
- [Postupy: Auditování událostí zabezpečení](how-to-audit-wcf-security-events.md)
- [\<serviceSecurityAudit>](../../configure-apps/file-schema/wcf/servicesecurityaudit.md)
- [\<behaviors>](../../configure-apps/file-schema/wcf/behaviors.md)
- [Model zabezpečení pro Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677202(v=azure.10))

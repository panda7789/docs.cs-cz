---
title: <serviceSecurityAudit>
ms.date: 03/30/2017
ms.assetid: ba517369-a034-4f8e-a2c4-66517716062b
ms.openlocfilehash: 10888f26053014ffb1fec49d1dfe87c7fd09ab54
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399580"
---
# <a name="servicesecurityaudit"></a>\<serviceSecurityAudit>
Určuje nastavení, které povoluje auditování událostí zabezpečení během operací služby.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceSecurityAudit >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<serviceSecurityAudit auditLogLocation="Default/Application/Security"
                      messageAuthenticationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      serviceAuthorizationAuditLevel="None/Success/Failure/SuccessOrFailure"
                      suppressAuditFailure="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|auditLogLocation|Určuje umístění protokolu auditu. Platné hodnoty jsou následující:<br /><br /> Výchozí Události zabezpečení se zapisují do aplikačního protokolu v systému Windows XP a do protokolu událostí v systému Windows Server 2003 a Windows Vista.<br />Použití Události auditu se zapisují do protokolu událostí aplikace.<br />Bezpečnost Události auditu se zapisují do protokolu událostí zabezpečení.<br /><br /> Výchozí hodnota je výchozí hodnota. Další informace naleznete v tématu <xref:System.ServiceModel.AuditLogLocation>.|  
|suppressAuditFailure|Logická hodnota, která určuje chování pro potlačení selhání zápisu do protokolu auditu.<br /><br /> Aplikace by se měly informovat o selhání zápisu do protokolu auditu. Pokud vaše aplikace není navržena pro zpracování selhání auditu, měli byste použít tento atribut k potlačení selhání při zápisu do protokolu auditu.<br /><br /> Pokud tento atribut je `true`, jsou výjimky jiné než OutOfMemoryException, StackOverflowException, ThreadAbortException a ArgumentException v důsledku pokusů o zápis událostí auditu zpracovávány systémem a nejsou šířeny do použití. Pokud je `false`tento atribut, všechny výjimky, které jsou výsledkem pokusů o zápis událostí auditu, jsou předány do aplikace.<br /><br /> Výchozí hodnota je `true`.|  
|serviceAuthorizationAuditLevel|Určuje typy událostí autorizace, které jsou zaznamenány v protokolu auditu. Platné hodnoty jsou následující:<br /><br /> NTato Neprovádí se žádné auditování událostí autorizace služby.<br />Nástup Auditovány se jenom úspěšné události autorizace služby.<br />Poruše Auditovány se pouze události autorizace neúspěšné služby.<br />- SuccessOrFailure: Auditované události úspěšné i neúspěšné autorizace služby jsou auditovány.<br /><br /> Výchozí hodnota je žádné. Další informace naleznete v tématu <xref:System.ServiceModel.AuditLevel>.|  
|messageAuthenticationAuditLevel|Určuje typ protokolovaných událostí auditu ověřování zpráv. Platné hodnoty jsou následující:<br /><br /> NTato Negenerují se žádné události auditu.<br />Nástup Protokolovat se budou jenom úspěšná zabezpečení (úplné ověření včetně ověření podpisu zprávy, šifry a ověření tokenu).<br />Poruše Protokolují se pouze události selhání.<br />- SuccessOrFailure: Události úspěšného i neúspěchu jsou protokolovány.<br /><br /> Výchozí hodnota je žádné. Další informace naleznete v tématu <xref:System.ServiceModel.AuditLevel>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> chování](behavior-of-endpointbehaviors.md)|Určuje chování element.|  
  
## <a name="remarks"></a>Poznámky  
 Tento prvek konfigurace slouží k auditování událostí ověřování Windows Communication Foundation (WCF). Je-li povoleno auditování, lze auditovat buď úspěšné nebo neúspěšné pokusy o ověření (nebo obojí). Události se zapisují do jednoho ze tří protokolů událostí: aplikace, zabezpečení nebo výchozí protokol pro verzi operačního systému. Protokoly událostí je možné zobrazit v prohlížeči událostí systému Windows.  
  
 Podrobný příklad použití tohoto prvku konfigurace najdete v tématu [chování auditování služby](../../../wcf/samples/service-auditing-behavior.md).  
  
 Ve výchozím nastavení v systému Windows XP lze události auditu zobrazit v protokolu aplikace. v systémech Windows Server 2003 a Windows Vista lze události auditu zobrazit v protokolu zabezpečení. Umístění událostí auditu lze zadat nastavením `auditLogLocation` atributu na možnost aplikace nebo zabezpečení. Další informace najdete v tématu [jak: Auditovat události](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)zabezpečení. Pokud jsou události napsány v protokolu zabezpečení, LocalSecurityPolicy-> Povolit přístup k objektům by měl být nastaven na hodnotu "úspěch" a "selhání".  
  
 Při prohlížení protokolu událostí je zdrojem událostí auditu "ServiceModel audit 3.0.0.0". Záznamy auditu ověřování zprávy mají kategorii "MessageAuthentication", zatímco záznamy auditu autorizací služeb mají kategorii "ServiceAuthorization".  
  
 Události auditu ověřování zpráv se týkají ohledu na to, zda byla zpráva zfalšována, zda vypršela platnost zprávy a zda se může klient ověřit ve službě. Poskytují informace o tom, zda bylo ověření úspěšné nebo neúspěšné, spolu s identitou klienta a koncovým bodem, na který byla zpráva odeslána, spolu s akcí přidruženou ke zprávě.  
  
 Události auditu autorizace služby se týkají autorizačního rozhodnutí, které udělal Správce autorizací služby. Poskytují informace o tom, zda autorizace byla úspěšná nebo neúspěšná spolu s identitou klienta, koncového bodu, na který byla zpráva odeslána, k akci přidružené ke zprávě, identifikátoru autorizačního kontextu, který byl vygenerován z příchozí zpráva a typ Správce autorizací, který učinil rozhodnutí o přístupu.  
  
## <a name="example"></a>Příklad  
  
```xml  
<system.serviceModel>
  <behaviors>
    <serviceBehaviors>
      <behavior name="NewBehavior">
        <serviceSecurityAudit auditLogLocation="Application"
                              suppressAuditFailure="true"
                              serviceAuthorizationAuditLevel="Success"
                              messageAuthenticationAuditLevel="Success" />
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ServiceSecurityAuditElement>
- <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior>
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Auditování](../../../wcf/feature-details/auditing-security-events.md)
- [Postupy: Auditovat události zabezpečení](../../../wcf/feature-details/how-to-audit-wcf-security-events.md)
- [Chování při auditování služby](../../../wcf/samples/service-auditing-behavior.md)

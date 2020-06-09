---
title: Chování auditování služby
ms.date: 03/30/2017
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
ms.openlocfilehash: bfe13146a7f7cdec648a82a34c34077ec5466809
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84599929"
---
# <a name="service-auditing-behavior"></a>Chování auditování služby
Tato ukázka předvádí, jak použít <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> k povolení auditování událostí zabezpečení během operací služby. Tato ukázka je založena na [Začínáme](getting-started-sample.md). Služba a klient byly nakonfigurovány pomocí nástroje [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) . `mode`Atribut [\<security>](../../configure-apps/file-schema/wcf/security-of-custombinding.md) byl nastaven na hodnotu `Message` a `clientCredentialType` byl nastaven na hodnotu `Windows` . V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
 Konfigurační soubor služby používá `serviceSecurityAudit` prvek ke konfiguraci auditování.  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      ...  
<!-- serviceSecurityAudit allows specification of audit location   
     and whether to audit success, failure or both. This service   
     logs success and failure of messageAuthentication   
     to the default location -->  
     <serviceSecurityAudit auditLogLocation ="Default" messageAuthenticationAuditLevel = "SuccessOrFailure" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 Při spuštění ukázky se v okně konzoly klienta zobrazí požadavky na operace a odpovědi. Ukončete klienta stisknutím klávesy ENTER v okně konzoly.  
  
 Výsledné protokoly auditu můžete zobrazit spuštěním Prohlížeč událostí. Ve výchozím nastavení v systému Windows XP lze události auditu zobrazit v aplikačním protokolu, zatímco v systému Windows Server 2003 a Windows Vista, události auditu lze zobrazit v protokolu zabezpečení. V systémech Windows Server 2008 a Windows 7 se události auditu zobrazují v protokolech aplikací a služeb. Umístění událostí auditu lze zadat nastavením `auditLogLocation` atributu "Application" nebo "Security". Další informace najdete v tématu [Postupy: auditování událostí zabezpečení](../feature-details/how-to-audit-wcf-security-events.md). Pokud jsou události zapisovány do protokolu zabezpečení, LocalSecurityPolicy-> povolit přístup k objektům by měl být nastaven na hodnotu "úspěch" a "selhání".  
  
 Při prohlížení protokolu událostí je zdrojem událostí auditu "ServiceModel audit 3.0.0.0". Záznamy auditu ověřování zprávy mají kategorii "MessageAuthentication", zatímco záznamy auditu autorizací služeb mají kategorii "ServiceAuthorization".  
  
 Události auditu ověřování zpráv se týkají ohledu na to, zda byla zpráva zfalšována, zda vypršela platnost zprávy a zda se může klient ověřit ve službě. Poskytují informace o tom, zda bylo ověření úspěšné nebo neúspěšné, spolu s identitou klienta, a koncovým bodem, na který byla zpráva odeslána, spolu s akcí přidruženou ke zprávě.  
  
 Události auditu autorizace služby se týkají autorizačního rozhodnutí, které udělal Správce autorizací služby. Poskytují informace o tom, zda autorizace byla úspěšná nebo neúspěšná, spolu s identitou klienta, koncový bod, na který byla zpráva odeslána, akce přidružená ke zprávě, identifikátor autorizačního kontextu, který byl vygenerován z příchozí zprávy, a typ Správce autorizací, který učinil rozhodnutí o přístupu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li sestavit edici C# nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
## <a name="see-also"></a>Viz také

- [Auditování](../feature-details/auditing-security-events.md)
- [Postupy: Auditování událostí zabezpečení](../feature-details/how-to-audit-wcf-security-events.md)

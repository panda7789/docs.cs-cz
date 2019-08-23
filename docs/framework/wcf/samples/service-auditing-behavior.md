---
title: Chování auditování služby
ms.date: 03/30/2017
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
ms.openlocfilehash: 6d5f254f4f94adfaeaf5632ddd696891af177e93
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69964548"
---
# <a name="service-auditing-behavior"></a>Chování auditování služby
Tato ukázka předvádí, <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> jak použít k povolení auditování událostí zabezpečení během operací služby. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Služba a klient se nakonfigurovali pomocí [ \<> WSHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). `Message` `clientCredentialType`Atribut> zabezpečení byl nastaven na hodnotu a byl nastaven na `Windows`hodnotu. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) `mode` V této ukázce je klient Konzolová aplikace (. exe) a služba je hostována službou Internetová informační služba (IIS).  
  
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
  
 Výsledné protokoly auditu můžete zobrazit spuštěním Prohlížeč událostí. Ve výchozím nastavení v systému Windows XP lze události auditu zobrazit v aplikačním protokolu, zatímco v systému Windows Server 2003 a Windows Vista, události auditu lze zobrazit v protokolu zabezpečení. V systémech Windows Server 2008 a Windows 7 se události auditu zobrazují v protokolech aplikací a služeb. Umístění událostí auditu lze zadat nastavením `auditLogLocation` atributu "Application" nebo "Security". Další informace najdete v tématu [jak: Auditovat události](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)zabezpečení. Pokud jsou události zapisovány do protokolu zabezpečení, LocalSecurityPolicy-> Povolit přístup k objektům by měl být nastaven na hodnotu "úspěch" a "selhání".  
  
 Při prohlížení protokolu událostí je zdrojem událostí auditu "ServiceModel audit 3.0.0.0". Záznamy auditu ověřování zprávy mají kategorii "MessageAuthentication", zatímco záznamy auditu autorizací služeb mají kategorii "ServiceAuthorization".  
  
 Události auditu ověřování zpráv se týkají ohledu na to, zda byla zpráva zfalšována, zda vypršela platnost zprávy a zda se může klient ověřit ve službě. Poskytují informace o tom, zda bylo ověření úspěšné nebo neúspěšné, spolu s identitou klienta, a koncovým bodem, na který byla zpráva odeslána, spolu s akcí přidruženou ke zprávě.  
  
 Události auditu autorizace služby se týkají autorizačního rozhodnutí, které udělal Správce autorizací služby. Poskytují informace o tom, zda autorizace byla úspěšná nebo neúspěšná spolu s identitou klienta, koncového bodu, na který byla zpráva odeslána, k akci přidružené ke zprávě, identifikátoru autorizačního kontextu, který byl vygenerován z příchozí zpráva a typ Správce autorizací, který učinil rozhodnutí o přístupu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Pokud chcete vytvořit C# edici nebo Visual Basic .NET, postupujte podle pokynů v tématu sestavování [ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také:

- [Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Postupy: Auditovat události zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)

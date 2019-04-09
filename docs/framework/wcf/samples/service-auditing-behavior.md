---
title: Chování auditování služby
ms.date: 03/30/2017
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
ms.openlocfilehash: 5fdc213551b5a7b3474321551d7c2cb149ca978d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151421"
---
# <a name="service-auditing-behavior"></a>Chování auditování služby
Tato ukázka předvádí, jak používat <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> povolení auditování událostí zabezpečení během operací služby. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Klienta a služby byly nakonfigurovány pomocí [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). `mode` Atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) byla nastavena na `Message` a `clientCredentialType` byla nastavena na `Windows`. V této ukázce je konzolová aplikace (.exe) klient a služba je hostována v Internetové informační služby (IIS).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
 Konfigurační soubor služby používá `serviceSecurityAudit` element konfigurace auditování.  
  
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
  
 Při spuštění ukázky operace žádosti a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně konzoly vypnutí klient.  
  
 Výsledný protokoly auditu lze zobrazit pomocí prohlížeče událostí. Ve výchozím nastavení Windows XP událostí auditu, které lze zobrazit v protokolu aplikací při na Windows Server 2003 a Windows Vista událostí auditu, které vidíte v protokolu zabezpečení. Na Windows Server 2008 a Windows 7 událostí auditu, které najdete v protokolech aplikací a služeb. Umístění události auditu se dá nastavit tak, že nastavíte `auditLogLocation` atribut "Aplikace" nebo "Zabezpečení". Další informace najdete v tématu [jak: Auditování událostí zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md). Pokud události se zapisují do protokolu zabezpečení LocalSecurityPolicy -> Povolit přístup k objektům by měl být nastavena pro "Success" a "Selhání".  
  
 Při hledání v protokolu událostí, je zdrojem událostí auditu "ServiceModel auditu 3.0.0.0". Záznamy auditu ověřování zprávy mají kategorii "MessageAuthentication" záznamy auditu autorizace služby mají kategorii "ServiceAuthorization".  
  
 Zprávy ověřovacích událostí auditu pokrytí, zda zpráva je porušené, zda vypršela platnost zprávy a určuje, zda se klient může ověřit ve službě. Poskytují informace o tom, jestli ověření úspěšné nebo neúspěšné spolu s identitou klienta a koncového bodu zpráva byla odeslána spolu s akce spojený se zprávou.  
  
 Události auditu autorizace služby zahrnují rozhodnutí o autorizaci, které správce autorizace služby. Poskytují informace o tom, jestli byla úspěšná autorizace nebo se nepodařilo spolu s identitou klienta, koncový bod zprávy odeslané do akce spojený se zprávou, identifikátor autorizační kontext, který byl vytvořen příchozí zprávy a typ správce autorizace, který vytvořil rozhodnutí přístupu.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také:

- [Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)
- [Postupy: Auditování událostí zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)

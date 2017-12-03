---
title: "Chování auditování služby"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 59bf0cda-e496-4418-a3a1-2f0f6e85f8ce
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f84bff892a35288a75738d9cfa326ffc4119b433
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="service-auditing-behavior"></a>Chování auditování služby
Tento příklad znázorňuje způsob použití <xref:System.ServiceModel.Description.ServiceSecurityAuditBehavior> povolení auditování událostí zabezpečení během operací služby. Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md). Klienta a služby jsou nakonfigurované pomocí [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md). `mode` Atribut [ \<zabezpečení >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) byla nastavena na `Message` a `clientCredentialType` byla nastavena na `Windows`. V této ukázce klienta je konzolová aplikace (.exe) a služba je hostovaná Internetové informační služby (IIS).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
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
  
 Když spustíte ukázku, operace požadavky a odpovědi se zobrazí v okně konzoly klienta. Stisknutím klávesy ENTER v okně konzoly vypnout klienta.  
  
 Výsledný protokoly auditu je možné zobrazit pomocí prohlížeče událostí. Ve výchozím nastavení se zobrazí události auditu v protokolu aplikace při na Windows Server 2003 a Windows Vista, Windows XP se zobrazí události auditu v protokolu zabezpečení. Na Windows Server 2008 a Windows 7 se zobrazí události auditu v protokoly aplikací a služeb. Umístění události auditu lze zadat nastavením `auditLogLocation` atribut "Aplikace" nebo "Zabezpečení". Další informace najdete v tématu [postup: události auditu zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md). Pokud události se zapisují do protokolu zabezpečení LocalSecurityPolicy -> Povolit přístup k objektu by měla být nastavena pro "ÚSPĚCH" a "Selhání".  
  
 Při vyhledávání v protokolu událostí, zdroj událostí auditu je "ServiceModel auditu 3.0.0.0". Záznamů zprávy o auditu ověřování vlastní kategorie "MessageAuthentication", zatímco záznamy auditu autorizace služby, vlastní kategorie "ServiceAuthorization".  
  
 Události auditu ověřování zpráv tématech, zda zpráva bylo manipulováno, jestli vypršela platnost zprávu, a zda může klient ověřit ve službě. Poskytují informace o tom, jestli je ověřování byla úspěšná nebo neúspěšná spolu s identitou klienta a koncový bod zpráva byla odeslána spolu s akce přidružené ke zprávě.  
  
 Události auditu autorizace služby zahrnují rozhodnutí o autorizaci provedené správcem autorizace služby. Poskytují informace o tom, jestli ověření bylo úspěšné, nebo se nezdařilo spolu s identitou klienta, koncový bod zpráva byla odeslána k akci spojený se zprávou, identifikátor autorizační kontext, který se vygeneroval ze příchozí zprávy a typ Správce autorizací, který se rozhodnete přístup.  
  
### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Auditování](../../../../docs/framework/wcf/feature-details/auditing-security-events.md)  
 [Postupy: auditování událostí zabezpečení](../../../../docs/framework/wcf/feature-details/how-to-audit-wcf-security-events.md)

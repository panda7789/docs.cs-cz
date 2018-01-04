---
title: "Federace a důvěryhodnost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: federation [WCF], and trust
ms.assetid: 4bdec4f2-f8a2-4512-bdcf-14ef54b5877a
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 98b1274866dec2a4ca923d390f33df68449cf286
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="federation-and-trust"></a>Federace a důvěryhodnost
Toto téma popisuje různé aspekty související s federovaným aplikacím, hranice vztahů důvěryhodnosti a konfiguraci a použití vystavené tokeny v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].  
  
## <a name="services-security-token-services-and-trust"></a>Služby, služby tokenů zabezpečení a vztah důvěryhodnosti  
 Služby, které obvykle zveřejňují federované koncové body očekávají, že klienti k ověření pomocí tokenu poskytované konkrétní vystavitele. Je důležité, aby služba je nakonfigurována se správnými přihlašovacími údaji pro vystavitele; jinak nebude možné k ověřování podpisů přes vystavené tokeny a klient nebude moci komunikovat se službou. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Konfigurace přihlašovacích údajů vystavitele pro službu, najdete v části [postupy: Konfigurace pověření ve službě Federation](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
 Podobně při použití symetrické klíče, klíče jsou šifrována pro cílovou službu, takže musíte nakonfigurovat služby tokenů zabezpečení se správnými přihlašovacími údaji pro cílovou službu; jinak nebude možné k zašifrování klíče pro cílovou službu a znovu, bude klient nemůže komunikovat se službou.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]služby používají hodnotu <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> vlastnost na [elementu SecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/securitybindingelement.md) umožňující hodiny zkosení mezi klientem a službou. Federaci `MaxClockSkew` nastavení se vztahuje na hodiny zkosí mezi klientem a ze kterých klient získal vydaný token služby tokenů zabezpečení. Služby tokenů zabezpečení nemusí proto zkontrolujte hodiny zkosení přídavky při nastavování vystavený token platné a časy vypršení platnosti.  
  
> [!NOTE]
>  Význam hodiny zkosení zvyšuje jako zkracuje dobu životnosti vydaný token. Ve většině případů není hodiny zkosení významný problém, pokud dobu životnosti tokenu je 30 minut nebo déle. Scénáře s kratší životnosti nebo kde je důležité dobu přesný platnosti tokenu by se měly navrhovat vzít v úvahu zkosení hodiny.  
  
## <a name="federated-endpoints-and-time-outs"></a>Federované koncových bodů a vypršení časových limitů  
 Pokud klient komunikuje s federované koncový bod, musíte nejprve získat token odpovídající od služby tokenů zabezpečení. Pokud služby tokenů zabezpečení zpřístupní koncový bod federované, musí klient nejdřív získat od vystavitele pro tento koncový bod token. Každý token pořízení trvá určitou dobu a tento čas podléhá celkový časový limit pro odesílání skutečné zprávy koncovým bodem.  
  
 Časový limit na straně klienta kanálu je třeba nastavit na 30 sekund. Dva tokenu vystavitelů muset volat načíst tokeny před odesláním zprávy na poslední koncový bod a každou trvá 15 sekund vydání tokenu. V takovém případě se nezdaří pokus a <xref:System.TimeoutException> je vyvolána výjimka. Proto je nutné nastavit <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> hodnotu na kanálu klienta na hodnotu dostatečně velký pro zahrnout čas potřebný k načtení všech vystavené tokeny. V případě, kde není zadána hodnota pro <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> vlastnost, <xref:System.ServiceModel.Channels.Binding.OpenTimeout%2A> vlastnost nebo <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A> vlastnost (nebo obě) je nutné nastavit na hodnotu dostatečně velký pro zahrnout čas potřebný k načtení všech vystavené tokeny.  
  
## <a name="token-lifetime-and-renewal"></a>Životnost tokenu a obnovení  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Klienti Neprovádět kontrolu vydaný token při vytváření počátečního požadavku na službu.  Místo toho [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vztahy důvěryhodnosti služby tokenů zabezpečení vydání tokenu s odpovídající platné a časy vypršení platnosti. Pokud token je uložené v mezipaměti klienta a znovu použít, je na následné žádosti zaškrtnuta možnost dobu životnosti tokenu a klient automaticky obnovuje token v případě potřeby. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Token ukládání do mezipaměti najdete v tématu [postupy: vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).  
  
 Zadání krátkou životnost, v pořadí, 30 sekund nebo méně pro vydané tokeny nebo tokenů kontextu zabezpečení, může mít za následek vypršení časových limitů vyjednávání nebo ostatní výjimky se vyvolané [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienti při žádosti vystavené tokeny nebo při vyjednávání nebo obnovení tokenů kontextu zabezpečení.  
  
## <a name="issued-tokens-and-inclusionmode"></a>Vystavené tokeny a InclusionMode  
 Jestli vystavený token je serializována v zprávy odeslané z klienta do federované koncového bodu nebo není řízeny nastavením <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InclusionMode%2A> vlastnost <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> třídy. Tuto vlastnost lze nastavit na jednu z <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> hodnot výčtu, ale není užitečný ve scénářích, většina federované. `SecurityTokenInclusionMode.Never` a `SecurityTokenInclusionMode.AlwaysToInitiator` hodnoty způsobit, že klient k odeslání odkaz na tokenem vydaným službou tokenů zabezpečení k předávající straně. Pokud předávající strana má kopii vydaných tokenů, ověřování selže, protože odkaz tokenu není možné přeložit. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zpracovává `SecurityTokenInclusionMode.Once` jako ekvivalentní `SecurityTokenInclusionMode.AlwaysToRecipient`.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>  
 [Postupy: Vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Postupy: Konfigurace přihlašovacích údajů ve službě Federation Service](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Postupy: Vytvoření WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)

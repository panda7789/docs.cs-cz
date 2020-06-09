---
title: Federace a důvěryhodnost
ms.date: 03/30/2017
helpviewer_keywords:
- federation [WCF], and trust
ms.assetid: 4bdec4f2-f8a2-4512-bdcf-14ef54b5877a
ms.openlocfilehash: 8b924a4aeb9c667592e99d65666cd8f048d34c22
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595476"
---
# <a name="federation-and-trust"></a>Federace a důvěryhodnost
Toto téma popisuje různé aspekty týkající se federovaných aplikací, hranic vztahů důvěryhodnosti a konfigurace a používání vydaných tokenů ve službě Windows Communication Foundation (WCF).  
  
## <a name="services-security-token-services-and-trust"></a>Služby, služby tokenů zabezpečení a důvěryhodnost  
 Služby, které zveřejňují federované koncové body, obvykle očekávají, že se klienti ověřují pomocí tokenu poskytnutého konkrétním vystavitelem. Je důležité, aby byla služba nakonfigurovaná se správnými přihlašovacími údaji pro vystavitele. v opačném případě nebude schopen ověřit podpisy přes vydané tokeny a klient nebude moci komunikovat se službou. Další informace o konfiguraci přihlašovacích údajů vystavitele ve službě najdete v tématu [Postup: konfigurace přihlašovacích údajů na služba FS (Federation Service)](how-to-configure-credentials-on-a-federation-service.md).  
  
 Podobně při použití symetrických klíčů jsou klíče pro cílovou službu šifrované, takže musíte nakonfigurovat službu tokenu zabezpečení se správnými přihlašovacími údaji pro cílovou službu; v opačném případě nebude možné zašifrovat klíč pro cílovou službu a klient nebude moci komunikovat se službou.  
  
 Služby WCF používají hodnotu <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> vlastnosti v [SecurityBindingElement](../diagnostics/wmi/securitybindingelement.md) , aby bylo možné vyhodnotit časové zkosení mezi klientem a službou. Ve federaci se `MaxClockSkew` nastavení vztahuje na hodinové zkosení mezi klientem a službou tokenu zabezpečení, ze kterého klient získal vydaný token. Proto služba tokenů zabezpečení nemusí při nastavování účinnosti a doby vypršení platnosti vydaných tokenů dělat odchylky s časovým posunem.  
  
> [!NOTE]
> Důležitost hodinového zkosení se zvyšuje jako doba životnosti vydaného tokenu. Ve většině případů se hodinový posun nejedná o významný problém, pokud je životnost tokenu 30 minut nebo více. Scénáře s kratšími dobami života nebo tam, kde je důležité přesný čas platnosti tokenu, by měly být navržené tak, aby se přihlédlo k časově rozchodu.  
  
## <a name="federated-endpoints-and-time-outs"></a>Federované koncové body a časové limity  
 Když klient komunikuje s federovaným koncovým bodem, musí nejdřív získat příslušný token ze služby tokenu zabezpečení. Pokud služba tokenů zabezpečení zveřejňuje federovaný koncový bod, klient musí nejdřív získat token od vystavitele tohoto koncového bodu. Každé pořízení tokenu trvá čas a tento čas se vztahuje na celkový časový limit pro odeslání skutečné zprávy do konečného koncového bodu.  
  
 Například časový limit kanálu na straně klienta je nastavený na 30 sekund. Aby bylo možné načíst tokeny před odesláním zprávy do konečného koncového bodu, musí být volány dva vydavatelé tokenů, přičemž každý z nich trvá 15 sekund, než se token vystaví. V tomto případě se pokus nezdaří a <xref:System.TimeoutException> dojde k vyvolání. Proto je potřeba nastavit <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> hodnotu v kanálu klienta na dostatečně velkou hodnotu, aby se zahrnula doba potřebná k načtení všech vystavených tokenů. V případě, že pro vlastnost není zadána hodnota <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> , je <xref:System.ServiceModel.Channels.Binding.OpenTimeout%2A> třeba vlastnost nebo <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A> vlastnost (nebo obojí) nastavit na dostatečně velký, aby zahrnovaly čas potřebný k načtení všech vydaných tokenů.  
  
## <a name="token-lifetime-and-renewal"></a>Životnost a obnovení tokenu  
 Klienti WCF nekontrolují vydaný token při vytváření počátečních požadavků na službu.  Místo toho WCF důvěřuje službě tokenů zabezpečení, aby vydávala token s odpovídající efektivitou a časem vypršení platnosti. Pokud klient a znovu použije token do mezipaměti, vyhradí se u následujících požadavků platnost tokenu a klient v případě potřeby automaticky obnoví token. Další informace o ukládání tokenů do mezipaměti najdete v tématu [Postupy: vytvoření federovaného klienta](how-to-create-a-federated-client.md).  
  
 Určení krátkých životností, v pořadí 30 sekund nebo méně pro vydané tokeny nebo tokeny kontextu zabezpečení, může vést k vypršení časového limitu vyjednávání nebo k vygenerování jiných výjimek klienty WCF při vyžádání vydaných tokenů nebo při vyjednávání nebo obnovování tokenů kontextu zabezpečení.  
  
## <a name="issued-tokens-and-inclusionmode"></a>Vydané tokeny a InclusionMode  
 Zda je vystavený token serializován ve zprávě odeslané z klienta do federovaného koncového bodu nebo není kontrolován nastavením <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InclusionMode%2A> vlastnosti <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> třídy. Tato vlastnost může být nastavena na jednu z <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> hodnot výčtu, ale není užitečná ve většině federovaných scénářů. `SecurityTokenInclusionMode.Never`Hodnoty a `SecurityTokenInclusionMode.AlwaysToInitiator` způsobí, že klient pošle odkaz na token vydaný službou tokenu zabezpečení pro předávající stranu. Pokud předávající strana nemá kopii vydaného tokenu, ověření se nezdaří, protože odkaz na token není možné přeložit. WCF považuje `SecurityTokenInclusionMode.Once` za ekvivalentní `SecurityTokenInclusionMode.AlwaysToRecipient` .  
  
## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>
- [Postupy: Vytvoření federovaného klienta](how-to-create-a-federated-client.md)
- [Postupy: Konfigurace pověření ve službě Federation Service](how-to-configure-credentials-on-a-federation-service.md)
- [Postupy: Vytvoření WSFederationHttpBinding](how-to-create-a-wsfederationhttpbinding.md)

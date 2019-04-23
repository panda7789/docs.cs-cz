---
title: Federace a důvěryhodnost
ms.date: 03/30/2017
helpviewer_keywords:
- federation [WCF], and trust
ms.assetid: 4bdec4f2-f8a2-4512-bdcf-14ef54b5877a
ms.openlocfilehash: 4e1529db6cc52b6b8cc8881d2b2a35a754b4b311
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59225336"
---
# <a name="federation-and-trust"></a>Federace a důvěryhodnost
Toto téma popisuje různé aspekty související s federovaným aplikacím, hranicemi vztahů důvěryhodnosti a konfigurace a použití vydané tokeny ve Windows Communication Foundation (WCF).  
  
## <a name="services-security-token-services-and-trust"></a>Služby, služby tokenu zabezpečení a důvěryhodnost  
 Služby, které obvykle vystavují federované koncové body očekávat, že klienti k ověření pomocí tokenu poskytované konkrétní vystavitele. Je důležité, že služba je nakonfigurována se správnými přihlašovacími údaji pro vystavitele; v opačném případě nebude moct k ověřování podpisů nad vydané tokeny, a klient nebude moci komunikovat se službou. Další informace o konfiguraci přihlašovacích údajů vystavitele pro službu, naleznete v tématu [jak: Konfigurace pověření ve službě Federation Service](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).  
  
 Podobně při použití symetrické klíče, že klíče se zašifrují pro cílovou službu, tak se správnými přihlašovacími údaji pro cílovou službu, musíte nakonfigurovat službu tokenů zabezpečení v opačném případě nebude možné k šifrování klíče pro cílovou službu a znovu, klient nebude moci komunikovat se službou.  
  
 Služby WCF, použijte hodnotu <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings.MaxClockSkew%2A> vlastnost [SecurityBindingElement](../../../../docs/framework/wcf/diagnostics/wmi/securitybindingelement.md) umožňující hodiny nerovnoměrné rozdělení mezi klientem a službou. Na federaci `MaxClockSkew` nastavení se vztahuje na hodiny zkosí mezi klientem a služba tokenů zabezpečení z kde klient získal vydaný token. Služby tokenu zabezpečení nemusí proto zkontrolujte limity časový posun při nastavování vydaný token platí a časy vypršení platnosti.  
  
> [!NOTE]
>  Důležitost posun hodin se zvyšuje podle zkracuje dobu života vydaný token. Ve většině případů není časový posun významný problém, pokud token doba platnosti je 30 minut nebo déle. Scénáře s kratší doby platnosti nebo kde je důležité čas přesný platnosti tokenu by se měly navrhovat vzít v úvahu posun hodin.  
  
## <a name="federated-endpoints-and-time-outs"></a>Federované koncové body a časové limity  
 Pokud klient komunikuje s federovaný koncový bod, musíte nejprve získat příslušné token od služby tokenů zabezpečení. Pokud služba tokenů zabezpečení zpřístupní federovaný koncový bod, musí klient nejdřív získat token od vydavatele pro tento koncový bod. Získání tokenu každé služby trvá určitou dobu a tato doba je v souladu s celkový časový limit pro odesílání skutečné zpráva koncovým bodem.  
  
 Časový limit na straně klienta kanálu je třeba nastavit na 30 sekund. Dva vystavitele tokenu musí být volána k získání tokenů před odesláním zpráva koncovým bodem a každý trvá 15 sekund vydání tokenu. V takovém případě se pokus nezdaří a <xref:System.TimeoutException> je vyvolána výjimka. Proto je nutné nastavit <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> hodnotu na kanálu klienta na hodnotu dostatečně velký, aby patří čas potřebný k načtení všech vydané tokeny. V případě, pokud není zadána hodnota pro <xref:System.ServiceModel.IContextChannel.OperationTimeout%2A> vlastnost, <xref:System.ServiceModel.Channels.Binding.OpenTimeout%2A> vlastnost nebo <xref:System.ServiceModel.Channels.Binding.SendTimeout%2A> vlastnost (nebo obojí) musí být nastavena na hodnotu dostatečně velký, aby patří čas potřebný k načtení všech vydaných tokenů.  
  
## <a name="token-lifetime-and-renewal"></a>Životnost tokenu a obnovení  
 Klienti WCF nezaškrtávejte políčko vydaný token při provádění prvotní žádosti o službu.  Místo toho WCF vztahy důvěryhodnosti služby tokenů zabezpečení k vydání tokenu s vhodnou dobu platnosti a vypršení platnosti. Pokud je token v mezipaměti klienta a znovu použít, dobu životnosti tokenu je zaškrtnuté políčko na následné žádosti a klient automaticky token obnovuje, v případě potřeby. Další informace o ukládání tokenu do mezipaměti najdete v tématu [jak: Vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md).  
  
 Určení krátkou životnost, menší nebo v řádu 30 sekund pro vydané tokeny nebo tokeny kontextu zabezpečení, může mít za následek vypršení časových limitů vyjednávání nebo další výjimky vyvolané klienti WCF při žádosti o tokeny vydané nebo při vyjednávání nebo obnovení zabezpečení tokeny kontextu.  
  
## <a name="issued-tokens-and-inclusionmode"></a>Vystavené tokeny a InclusionMode  
 Určuje, zda je serializován ve zpráv odesílaných z klienta do federovaný koncový bod vydaný token, nebo není řízen pomocí nastavení <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters.InclusionMode%2A> vlastnost <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters> třídy. Tuto vlastnost lze nastavit na jednu z <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode> hodnot výčtu, ale není užitečné v situacích, většina federované. `SecurityTokenInclusionMode.Never` a `SecurityTokenInclusionMode.AlwaysToInitiator` hodnoty způsobit klientovi umožní odeslat odkaz na tokenem vydaným službou tokenů zabezpečení k předávající straně. Pokud předávající strana má kopii vystavený ověřovací token, se nezdaří, protože není možné přeložit odkaz na token. Zpracovává WCF `SecurityTokenInclusionMode.Once` jako ekvivalentní `SecurityTokenInclusionMode.AlwaysToRecipient`.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Security.Tokens.SecurityTokenInclusionMode>
- [Postupy: Vytvoření federovaného klienta](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Postupy: Konfigurace pověření ve službě Federation Service](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Postupy: Vytvoření instance WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)

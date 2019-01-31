---
title: <localClientSettings> – element
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: e43a03258f4a76c1d19c7bdcff99fcb1d1db19ac
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278925"
---
# <a name="localclientsettings-element"></a>\<localClientSettings > – element
Určuje nastavení zabezpečení místního klienta pro tuto vazbu.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vytvoření vazby >  
\<security>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security>
   <localClientSettings cacheCookies="Boolean"
                        cookieRenewalThresholdPercentage="Integer"
                        detectReplays="Boolean"
                        maxClockSkew="TimeSpan"
                        maxCookieCachingTime="TimeSpan"
                        reconnectTransportOnFailure="Boolean"
                        replayCacheSize="Integer"
                        replayWindow="TimeSpan"
                        sessionKeyRenewalInterval="TimeSpan"
                        sessionKeyRolloverInterval="TimeSpan"
                        timestampValidityDuration="TimeSpan" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`cacheCookies`|Logická hodnota určující, zda je povoleno ukládání do mezipaměti souborů cookie. Výchozí hodnota je `false`.|  
|`cookieRenewalThresholdPercentage`|Celé číslo určující maximální procento souborů cookie, které jde ji obnovit. Tato hodnota by měla být mezi 0 a 100 (včetně). Výchozí hodnota je 90.|  
|`detectReplays`|Logická hodnota určující, zda jsou zjištěny a řešeny automaticky opakované útoky proti kanálu. Výchozí hodnota je `false`.|  
|`maxClockSkew`|A <xref:System.TimeSpan> , která určuje maximální časový rozdíl mezi systémovými hodinami dvou komunikujících stran. Výchozí hodnota je "00: 05:00".<br /><br /> Pokud tato hodnota nastavena na výchozí hodnotu, příjemce přijímá zprávy s čas odeslání časová razítka na 5 minut později nebo dříve než čas přijetí zprávy. Nepředávejte test čas odeslání zprávy jsou odmítnuta. Toto nastavení se používá ve spojení s `replayWindow` atribut.|  
|`maxCookieCachingTime`|A <xref:System.TimeSpan> , která určuje maximální dobu života souboru cookie. Výchozí hodnota je "10675199.02:48:05.4775807".|  
|`reconnectTransportOnFailure`|Logická hodnota určující, zda připojení používající posílání WS-Reliable se pokusí znovu připojit po selhání přenosu. Výchozí hodnota je `true`, což znamená, že nedochází k pokusům o nekonečné pokusí znovu připojit. Cyklus je porušena časový limit nečinnosti, což způsobí, že kanálů pokusí vyvolat výjimku, pokud nelze je připojit.|  
|`replayCacheSize`|Celé kladné číslo určující počet náhodně generované identifikátory použitých pro zjištění opakování ukládat do mezipaměti. Pokud je tento limit překročen, nejstarší hodnota nonce je odebrán a nová hodnota nonce je vytvořen pro nové zprávy. Výchozí hodnota je 500000.|  
|`replayWindow`|A <xref:System.TimeSpan> , který určuje dobu, po kterou jsou platné náhodně generované identifikátory jednotlivých zpráv.<br /><br /> Po této hodnotě duration zprávy se stejnou hodnotu nonce jako odeslaným před nepřijme. Tento atribut se používá ve spojení s `maxClockSkew` atribut, aby se zabránilo opakované útoky. Útočník by mohl znovu přehrát zprávu po vypršení její okno opětovného přehrání. Tato zpráva, ale selže `maxClockSkew` testu, který odmítne zprávy s časovými razítky čas odeslání až po určitou dobu později nebo starší, než čas přijetí zprávy.|  
|`sessionKeyRenewalInterval`|A <xref:System.TimeSpan> , který určuje dobu, po které iniciátor obnoví klíč relace zabezpečení. Výchozí hodnota je "10: 00:00".|  
|`sessionKeyRolloverInterval`|A <xref:System.TimeSpan> , který určuje časový interval klíč předchozí relace je platný na příchozích zprávách během obnovení klíče. Výchozí hodnota je "00: 05:00".<br /><br /> Během obnovení klíče musí klient a server vždy odesílat zprávy pomocí nejnovější dostupné klíče. Obě strany bude přijímat příchozí zprávy, které jsou zabezpečené pomocí klíč předchozí relace, dokud nevyprší čas přechodu.|  
|`timestampValidityDuration`|Pozitivní <xref:System.TimeSpan> , který určuje dobu, ve kterém je platné časové razítko. Výchozí hodnota je "00: 15:00".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádná  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Určuje možnosti zabezpečení pro vlastní vazbu.|  
|[\<secureConversationBootstrap>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Určuje výchozí hodnoty pro inicializaci služby zabezpečené konverzace.|  
  
## <a name="remarks"></a>Poznámky  
 Nastavení, musí být místní v tom smyslu, že se nejedná o nastavení odvozený od zásady zabezpečení služby.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpečení vlastních vazeb](../../../../../docs/framework/wcf/samples/custom-binding-security.md)

---
title: <localClientSettings> – element
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: 3ec0394943c030a8866087c98a912682a2a2112e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400323"
---
# <a name="localclientsettings-element"></a>\<localClientSettings – element >
Určuje nastavení zabezpečení místního klienta pro tuto vazbu.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> zabezpečení**](security-of-custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<localClientSettings >**  
  
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
|`cacheCookies`|Logická hodnota, která určuje, zda je povoleno ukládání souborů cookie do mezipaměti. Výchozí hodnota je `false`.|  
|`cookieRenewalThresholdPercentage`|Celé číslo, které určuje maximální procento souborů cookie, které mohou být obnoveny. Tato hodnota by měla být mezi 0 a 100 (včetně). Výchozí hodnota je 90.|  
|`detectReplays`|Logická hodnota určující, zda jsou zjištěny opakované útoky proti kanálu a zda jsou řešeny automaticky. Výchozí hodnota je `false`.|  
|`maxClockSkew`|A <xref:System.TimeSpan> určuje maximální časový rozdíl mezi systémovými hodinami dvou komunikujících stran. Výchozí hodnota je "00:05:00".<br /><br /> Pokud je tato hodnota nastavená na výchozí hodnotu, příjemce přijímá zprávy s časovými razítky pro odeslání až 5 minut později nebo dříve, než čas, kdy byla zpráva přijata. Zprávy, které nevyhověly testu při odeslání, jsou odmítnuty. Toto nastavení se používá ve spojení s `replayWindow` atributem.|  
|`maxCookieCachingTime`|A <xref:System.TimeSpan> určuje maximální dobu života souborů cookie. Výchozí hodnota je "10675199.02:48:05.4775807".|  
|`reconnectTransportOnFailure`|Logická hodnota, která určuje, zda se připojení využívající zprávy WS-Reliable pokusí znovu připojit po selhání přenosu. Výchozí hodnota je `true`, což znamená, že došlo k pokusu o nekonečné pokusy o opětovné připojení. Cyklus je přerušen časovým limitem nečinnosti, což způsobí, že kanál vyvolá výjimku, když se nedá znovu připojit.|  
|`replayCacheSize`|Kladné celé číslo, které určuje počet hodnot náhodně generovaných identifikátorů v mezipaměti používaných pro detekci opakovaného přehrání. Pokud je tento limit překročen, je odebrána nejstarší hodnota nonce a pro novou zprávu je vytvořena nová hodnota nonce. Výchozí hodnota je 500000.|  
|`replayWindow`|A <xref:System.TimeSpan> určuje dobu, po kterou jsou jednotlivé náhodně generované identifikátory zprávy platné.<br /><br /> Po uplynutí této doby nebude přijata zpráva odeslaná se stejnou hodnota nonce jako ta, která byla odeslána před. Tento atribut se používá společně s `maxClockSkew` atributem, aby se zabránilo útokům přes opakované přehrání. Útočník může znovu přehrát zprávu po vypršení platnosti jejího okna opětovného přehrání. Tato zpráva však selže při selhání `maxClockSkew` testu, který odmítne zprávy s časovými razítky času odeslání až do určeného času později nebo dříve, než čas, kdy byla zpráva přijata.|  
|`sessionKeyRenewalInterval`|A <xref:System.TimeSpan> určuje dobu, po které iniciátor obnoví klíč pro relaci zabezpečení. Výchozí hodnota je "10:00:00".|  
|`sessionKeyRolloverInterval`|A <xref:System.TimeSpan> určuje časový interval, po který je klíč předchozí relace platný pro příchozí zprávy během obnovování klíče. Výchozí hodnota je "00:05:00".<br /><br /> Během obnovování klíče musí klient a server vždy odesílat zprávy pomocí nejaktuálnějšího dostupného klíče. Obě strany budou přijímat příchozí zprávy zabezpečené s předchozí klíčovou relací, dokud nevyprší doba přeběhu.|  
|`timestampValidityDuration`|Kladná <xref:System.TimeSpan> hodnota, která určuje dobu, po kterou je časové razítko platné. Výchozí hodnota je "00:15:00".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> zabezpečení](security-of-custombinding.md)|Určuje možnosti zabezpečení pro vlastní vazbu.|  
|[\<secureConversationBootstrap>](secureconversationbootstrap.md)|Určuje výchozí hodnoty, které se použijí při inicializaci služby zabezpečené konverzace.|  
  
## <a name="remarks"></a>Poznámky  
 Nastavení jsou místní v tom smyslu, že nejsou nastavení odvozená ze zásad zabezpečení služby.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpečení vlastních vazeb](../../../wcf/samples/custom-binding-security.md)

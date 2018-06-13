---
title: Element &lt;localClientSettings&gt;
ms.date: 03/30/2017
ms.assetid: 4680ace5-f4e1-4fcb-b9d8-a4a4af5cd7ae
ms.openlocfilehash: a960a18c472bed64609947220dffedf9ec90945c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32750944"
---
# <a name="ltlocalclientsettingsgt-element"></a>Element &lt;localClientSettings&gt;
Určuje nastavení zabezpečení místního klienta pro tuto vazbu.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<zabezpečení >  
  
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
|`cacheCookies`|Logická hodnota, která určuje, zda je povoleno ukládání do mezipaměti souborů cookie. Výchozí hodnota je `false`.|  
|`cookieRenewalThresholdPercentage`|Celé číslo, které určuje maximální procento soubory cookie, které může být obnovena. Tato hodnota by měla být mezi 0 a 100 (včetně). Výchozí hodnota je 90.|  
|`detectReplays`|Logická hodnota, která určuje, jestli jsou před zneužitím útoky na kanál zjistil a řešeny automaticky. Výchozí hodnota je `false`.|  
|`maxClockSkew`|A <xref:System.TimeSpan> , který určuje maximální časový rozdíl mezi systémovými hodinami dvou komunikujících stran. Výchozí hodnota je "00: 05:00".<br /><br /> Pokud je tato hodnota nastavená na výchozí hodnoty, příjemce přijímá zprávy s okamžiku odeslání časová razítka na 5 minut později nebo starší než čas zpráva byla přijata. Zprávy, které nepředávejte testovací odeslání čas odmítají. Toto nastavení se používá ve spojení s `replayWindow` atribut.|  
|`maxCookieCachingTime`|A <xref:System.TimeSpan> určující maximální doba života souborů cookie. Výchozí hodnota je "10675199.02:48:05.4775807".|  
|`reconnectTransportOnFailure`|Logická hodnota, která určuje, zda připojení pomocí protokolu WS-spolehlivé zasílání zpráv se pokusí znovu připojit po selhání přenosu. Výchozí hodnota je `true`, což znamená, že se pokusil nekonečné pokusí znovu připojit. Cyklus je rozděleno podle časový limit nečinnosti, což způsobí, že kanál, ke způsobí výjimku, pokud ji nelze znovu připojit.|  
|`replayCacheSize`|Kladné celé číslo určující počet do mezipaměti náhodně generované identifikátory používá pro rozpoznání opětovného přehrání. Pokud je tento limit překročen, nejstarší hodnotu nonce se odebere a novou hodnotu nonce se vytvoří pro novou zprávu. Výchozí hodnota je 500000.|  
|`replayWindow`|A <xref:System.TimeSpan> který určuje dobu, ve kterém jsou platné náhodně generované identifikátory jednotlivé zprávy.<br /><br /> Po této hodnotě duration nebudou přijaté zprávy odeslané s stejnou hodnotu nonce jako odesílat před. Tento atribut se používá ve spojení s `maxClockSkew` atribut, aby se zabránilo provedení útoku formou opakovaného. Útočník by mohl přehráním zprávu po vypršení platnosti jeho opětovného přehrání okno. Tato zpráva, ale dojde k selhání `maxClockSkew` test, který odmítne zprávy Časová razítka okamžiku odeslání až určitou dobu novější nebo starší, než čas zpráva byla přijata.|  
|`sessionKeyRenewalInterval`|A <xref:System.TimeSpan> který určuje dobu, po které bude iniciátoru obnovíte klíč relace zabezpečení. Výchozí hodnota je "10: 00:00".|  
|`sessionKeyRolloverInterval`|A <xref:System.TimeSpan> který určuje časový interval klíče předchozí relace je platná pro příchozí zprávy během obnovení klíče. Výchozí hodnota je "00: 05:00".<br /><br /> Během obnovení klíče musí klient a server vždy odesílat zprávy pomocí nejnovější dostupné klíče. Obě strany bude přijímat příchozí zprávy zabezpečené klíčem předchozí relace, dokud nevyprší časový výměny.|  
|`timestampValidityDuration`|U kladné <xref:System.TimeSpan> který určuje dobu, ve kterém je platný časové razítko. Výchozí hodnota je "00: 15:00".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Určuje možnosti zabezpečení u vlastních vazeb.|  
|[\<secureConversationBootstrap >](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Určuje výchozí hodnoty používané pro inicializaci služby Zabezpečené konverzaci.|  
  
## <a name="remarks"></a>Poznámky  
 Nastavení jsou místní v tom smyslu, že se nejedná o nastavení odvozené ze zásad zabezpečení služby.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.LocalClientSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalClientSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalClientSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Zabezpečení vlastních vazeb](../../../../../docs/framework/wcf/samples/custom-binding-security.md)

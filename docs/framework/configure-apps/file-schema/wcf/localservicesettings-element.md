---
title: Element &lt;localServiceSettings&gt;
ms.date: 03/30/2017
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
ms.openlocfilehash: 1257b151f75d05b610fe3463f8bef5f78d2b2fcd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32751152"
---
# <a name="ltlocalservicesettingsgt-element"></a>Element &lt;localServiceSettings&gt;
Určuje nastavení zabezpečení na místní služby pro tuto vazbu.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding >  
\<Vazba >  
\<zabezpečení >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security>  
   <localServiceSettings detectReplays="Boolean"  
      inactivityTimeout="TimeSpan"  
      issuedCookieLifeTime="TimeSpan"  
      maxCachedCookies="Integer"   
      maxClockSkew="TimeSpan"   
      maxPendingSessions="Integer"  
      maxStatefulNegotiations="Integer"  
      negotiationTimeout="TimeSpan"  
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
|`detectReplays`|Logická hodnota, která určuje, jestli jsou před zneužitím útoky na kanál zjistil a řešeny automaticky. Výchozí hodnota je `false`.|  
|`inactivityTimeout`|U kladné <xref:System.TimeSpan> který určuje dobu nečinnosti kanál čeká, než vyprší časový limit. Výchozí hodnota je "01: 00:00".|  
|`issuedCookieLifeTime`|A <xref:System.TimeSpan> , určuje životnost vystaveno pro všechny nové soubory cookie zabezpečení. Soubory cookie, které překračují své životnosti jsou recyklovány a muset znovu vyjednávat. Výchozí hodnota je "10: 00:00".|  
|`maxCachedCookies`|Kladné celé číslo, které určuje maximální počet souborů cookie, které mohou být uloženy v mezipaměti. Výchozí hodnota je 1 000.|  
|`maxClockSkew`|A <xref:System.TimeSpan> , který určuje maximální časový rozdíl mezi systémovými hodinami dvou komunikujících stran. Výchozí hodnota je "00: 05:00".<br /><br /> Pokud je tato hodnota nastavená na výchozí hodnoty, příjemce přijímá zprávy s okamžiku odeslání časová razítka na 5 minut později nebo starší než čas zpráva byla přijata. Zprávy, které nepředávejte testovací odeslání čas odmítají. Toto nastavení se používá ve spojení s `replayWindow` atribut.|  
|`maxPendingSessions`|Kladné celé číslo, které určuje maximální počet čekajících zabezpečení relací, které služba podporuje. Když je dosaženo tento limit, všichni noví klienti přijímat chyb SOAP. Výchozí hodnota je 1 000.|  
|`maxStatefulNegotiations`|Kladné celé číslo, které určuje počet vyjednávání zabezpečení, které mohou být souběžně aktivní. Vyjednávání relace nad tento limit jsou zařazeny do fronty a je možné dokončit, jakmile bude k dispozici místo pod limit. Výchozí hodnota je 1024.|  
|`negotiationTimeout`|A <xref:System.TimeSpan> určující dobu životnosti zásady zabezpečení používané podle kanálu. Při vypršení časového limitu, obnoví vyjednávání kanál s klientem pro novou zásadu zabezpečení. Výchozí hodnota je "00: 02:00".|  
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
 Nastavení jsou místní, protože nejsou vydané jako součást zásady zabezpečení služby a nemají vliv klientské vazby.  
  
 Následující atributy `localServiceSecuritySettings` element může pomoci zmírnit útok na útok na dostupnost služby (DOS) zabezpečení:  
  
-   `maxCachedCookies`: Určuje maximální počet SecurityContextTokens ohraničenou čas, která jsou uložena do mezipaměti serveru po provedení vyjednávání SPNEGO nebo SSL.  
  
-   `issuedCookieLifetime`: řídí životnost SecurityContextTokens, které jsou vystaveny serverem následující vyjednávání SPNEGO nebo SSL. Server ukládá do mezipaměti SecurityContextTokens pro toto časové období.  
  
-   `maxPendingSessions`: Určuje maximální počet zabezpečené konverzace, které se vytvoří na serveru, ale které byly zpracovány žádné zprávy aplikace. Tato kvóta brání klientům v navázání zabezpečené konverzace na službu, a způsobuje službu pro uchování stavu pro jednotlivé klienty, ale nikdy jejich používání.  
  
-   `inactivityTimeout`: Určuje maximální dobu, službu zachová zabezpečenou konverzaci aktivní někdy neobdrží zprávu aplikace na něm. Tato kvóta brání klientům v navázání zabezpečené konverzace na službu, a způsobuje službu pro uchování stavu pro jednotlivé klienty, ale nikdy jejich používání.  
  
 V relaci zabezpečené konverzace, Všimněte si, že oba `inactivityTimeout` a `receiveTimeout` atributů na vazby vliv časový limit relace. Kratší dvou Určuje, kdy dojde k vypršení časových limitů.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>  
 <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>  
 <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [Vazby](../../../../../docs/framework/wcf/bindings.md)  
 [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Zabezpečení vlastních vazeb](../../../../../docs/framework/wcf/samples/custom-binding-security.md)

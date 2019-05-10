---
title: <localServiceSettings> – element
ms.date: 03/30/2017
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
ms.openlocfilehash: 91e9944de30a78b904d1679512f622bcc2955af4
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64610198"
---
# <a name="localservicesettings-element"></a>\<localServiceSettings > – element
Určuje nastavení zabezpečení místní služby pro tuto vazbu.  
  
 \<system.serviceModel>  
\<vazby >  
\<customBinding>  
\<Vytvoření vazby >  
\<security>  
  
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
|`detectReplays`|Logická hodnota určující, zda jsou zjištěny a řešeny automaticky opakované útoky proti kanálu. Výchozí hodnota je `false`.|  
|`inactivityTimeout`|Pozitivní <xref:System.TimeSpan> , který určuje dobu nečinnosti kanálu čeká předtím, než vyprší časový limit. Výchozí hodnota je "01: 00:00".|  
|`issuedCookieLifeTime`|A <xref:System.TimeSpan> , který určuje životnost vydanou pro všechny nové bezpečnostní soubory cookie. Soubory cookie, které překračují jejich životního cyklu jsou recyklovány a potřebují pro znovu. Výchozí hodnota je "10: 00:00".|  
|`maxCachedCookies`|Kladné celé číslo, které určuje maximální počet souborů cookie, které lze uložit do mezipaměti. Výchozí hodnota je 1000.|  
|`maxClockSkew`|A <xref:System.TimeSpan> , která určuje maximální časový rozdíl mezi systémovými hodinami dvou komunikujících stran. Výchozí hodnota je "00: 05:00".<br /><br /> Pokud tato hodnota nastavena na výchozí hodnotu, příjemce přijímá zprávy s čas odeslání časová razítka na 5 minut později nebo dříve než čas přijetí zprávy. Nepředávejte test čas odeslání zprávy jsou odmítnuta. Toto nastavení se používá ve spojení s `replayWindow` atribut.|  
|`maxPendingSessions`|Kladné celé číslo, určující maximální počet nevyřešených bezpečnostních relací, které služba podporuje. Při dosažení tohoto limitu, všichni noví klienti zobrazí chyb SOAP. Výchozí hodnota je 1000.|  
|`maxStatefulNegotiations`|Kladné celé číslo, určující počet bezpečnostních vyjednávání, které mohou být souběžně aktivní. Vyjednávání relace nad tento limit se zařadí do fronty a je možné dokončit, jakmile je k dispozici prostor pod limit. Výchozí hodnota je 1024.|  
|`negotiationTimeout`|A <xref:System.TimeSpan> určující dobu života zásad zabezpečení, používaných kanálem. Když čas vyprší, kanál vyjednávání s klientem pro nové zásady zabezpečení. Výchozí hodnota je "00: 02:00".|  
|`reconnectTransportOnFailure`|Logická hodnota určující, zda připojení používající posílání WS-Reliable se pokusí znovu připojit po selhání přenosu. Výchozí hodnota je `true`, což znamená, že nedochází k pokusům o nekonečné pokusí znovu připojit. Cyklus je porušena časový limit nečinnosti, což způsobí, že kanálů pokusí vyvolat výjimku, pokud nelze je připojit.|  
|`replayCacheSize`|Celé kladné číslo určující počet náhodně generované identifikátory použitých pro zjištění opakování ukládat do mezipaměti. Pokud je tento limit překročen, nejstarší hodnota nonce je odebrán a nová hodnota nonce je vytvořen pro nové zprávy. Výchozí hodnota je 500000.|  
|`replayWindow`|A <xref:System.TimeSpan> , který určuje dobu, po kterou jsou platné náhodně generované identifikátory jednotlivých zpráv.<br /><br /> Po této hodnotě duration zprávy se stejnou hodnotu nonce jako odeslaným před nepřijme. Tento atribut se používá ve spojení s `maxClockSkew` atribut, aby se zabránilo opakované útoky. Útočník by mohl znovu přehrát zprávu po vypršení její okno opětovného přehrání. Tato zpráva, ale selže `maxClockSkew` testu, který odmítne zprávy s časovými razítky čas odeslání až po určitou dobu později nebo starší, než čas přijetí zprávy.|  
|`sessionKeyRenewalInterval`|A <xref:System.TimeSpan> , který určuje dobu, po které iniciátor obnoví klíč relace zabezpečení. Výchozí hodnota je "10: 00:00".|  
|`sessionKeyRolloverInterval`|A <xref:System.TimeSpan> , který určuje časový interval klíč předchozí relace je platný na příchozích zprávách během obnovení klíče. Výchozí hodnota je "00: 05:00".<br /><br /> Během obnovení klíče musí klient a server vždy odesílat zprávy pomocí nejnovější dostupné klíče. Obě strany bude přijímat příchozí zprávy, které jsou zabezpečené pomocí klíč předchozí relace, dokud nevyprší čas přechodu.|  
|`timestampValidityDuration`|Pozitivní <xref:System.TimeSpan> , který určuje dobu, ve kterém je platné časové razítko. Výchozí hodnota je "00: 15:00".|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)|Určuje možnosti zabezpečení pro vlastní vazbu.|  
|[\<secureConversationBootstrap>](../../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)|Určuje výchozí hodnoty pro inicializaci služby zabezpečené konverzace.|  
  
## <a name="remarks"></a>Poznámky  
 Nastavení jsou místní, protože nejsou publikované jako součást zásady zabezpečení služby a nemají vliv na vazby.  
  
 Následující atributy `localServiceSecuritySettings` element může pomoci zmírnit útok s cílem odepření služby (DOS) zabezpečení:  
  
- `maxCachedCookies`: Určuje maximální počet SecurityContextTokens časově, které jsou uložené v mezipaměti na serveru poté, co provede vyjednávání SPNEGO nebo SSL.  
  
- `issuedCookieLifetime`: Určuje životnost SecurityContextTokens, které jsou vystavované vyjednávání SPNEGO nebo SSL serveru. Server ukládá do mezipaměti SecurityContextTokens pro tuto dobu.  
  
- `maxPendingSessions`: Určuje maximální počet zabezpečených konverzací, které jsou vytvořeny na serveru, ale pro které byly zpracovány žádné zprávy aplikace. Tato kvóta brání klientům v navázání zabezpečené konverzace na službu, a způsobuje služby pro uchování stavu pro každého klienta, ale nikdy je používají.  
  
- `inactivityTimeout`: Určuje maximální dobu, že služba zachová zabezpečené konverzace aktivní bez někdy příjem zprávy aplikace. v něm. Tato kvóta brání klientům v navázání zabezpečené konverzace na službu, a způsobuje služby pro uchování stavu pro každého klienta, ale nikdy je používají.  
  
 V relaci zabezpečené konverzace, Všimněte si, že oba `inactivityTimeout` a `receiveTimeout` ovlivňují atributy ve vazbě časový limit relace. Čím kratší je časový z nich určuje, když dojde k vypršení časového limitu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Rozšíření vazeb](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Postupy: Vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpečení vlastních vazeb](../../../../../docs/framework/wcf/samples/custom-binding-security.md)

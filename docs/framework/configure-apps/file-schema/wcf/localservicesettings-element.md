---
title: <localServiceSettings> – element
ms.date: 03/30/2017
ms.assetid: 0658549c-3f65-46dd-8c5c-9895441ed734
ms.openlocfilehash: 36fcc9454a5762a4a375cc7f6eaee1c4cf0580e2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931718"
---
# <a name="localservicesettings-element"></a>\<localServiceSettings – element >
Určuje nastavení zabezpečení místní služby pro tuto vazbu.  
  
 \<system.serviceModel>  
\<> vazeb  
\<customBinding >  
\<> vazby  
\<> zabezpečení  
  
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
|`detectReplays`|Logická hodnota určující, zda jsou zjištěny opakované útoky proti kanálu a zda jsou řešeny automaticky. Výchozí hodnota je `false`.|  
|`inactivityTimeout`|Kladná <xref:System.TimeSpan> hodnota, která určuje dobu, po kterou kanál čeká, než vyprší časový limit. Výchozí hodnota je "01:00:00".|  
|`issuedCookieLifeTime`|A <xref:System.TimeSpan> určuje dobu života vydanou pro všechny nové soubory cookie zabezpečení. Soubory cookie, které překračují jejich životnost, se recyklují a je nutné je znovu vyjednávat. Výchozí hodnota je "10:00:00".|  
|`maxCachedCookies`|Celé kladné číslo určující maximální počet souborů cookie, které lze uložit do mezipaměti. Výchozí hodnota je 1000.|  
|`maxClockSkew`|A <xref:System.TimeSpan> určuje maximální časový rozdíl mezi systémovými hodinami dvou komunikujících stran. Výchozí hodnota je "00:05:00".<br /><br /> Pokud je tato hodnota nastavená na výchozí hodnotu, příjemce přijímá zprávy s časovými razítky pro odeslání až 5 minut později nebo dříve, než čas, kdy byla zpráva přijata. Zprávy, které nevyhověly testu při odeslání, jsou odmítnuty. Toto nastavení se používá ve spojení s `replayWindow` atributem.|  
|`maxPendingSessions`|Celé kladné číslo určující maximální počet nevyřešených bezpečnostních relací, které služba podporuje. Po dosažení tohoto limitu získají všichni noví klienti chyby protokolu SOAP. Výchozí hodnota je 1000.|  
|`maxStatefulNegotiations`|Celé kladné číslo určující počet vyjednávání zabezpečení, která mohou být souběžně aktivní. Relace vyjednávání přesahující limit jsou zařazené do fronty a můžou se dokončit jenom v případě, že bude k dispozici mezera pod limitem. Výchozí hodnota je 1024.|  
|`negotiationTimeout`|A <xref:System.TimeSpan> určuje dobu života zásad zabezpečení, kterou používá kanál. Po vypršení časového limitu bude kanál znovu vyjednávat s klientem pro nové zásady zabezpečení. Výchozí hodnota je "00:02:00".|  
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
 Nastavení jsou místní, protože nejsou publikována jako součást zásad zabezpečení služby a neovlivňují vazbu klienta.  
  
 Následující atributy `localServiceSecuritySettings` prvku mohou přispět k zmírnění útoku zabezpečení DOS (Denial of Service):  
  
- `maxCachedCookies`: řídí maximální počet SecurityContextTokens s časovými rozsahy, které server ukládá po provedení SPNEGO nebo vyjednávání SSL do mezipaměti.  
  
- `issuedCookieLifetime`: řídí životnost SecurityContextTokens vydaných serverem po vyjednávání SPNEGO nebo SSL. Server ukládá SecurityContextTokens do mezipaměti pro toto časové období.  
  
- `maxPendingSessions`: Určuje maximální počet zabezpečených konverzací, které jsou vytvořeny na serveru, ale pro které nebyly zpracovány žádné zprávy aplikace. Tato kvóta zabraňuje klientům v vytváření zabezpečených konverzací v rámci služby, což způsobuje, že služba udržuje stav pro každého klienta, ale nikdy je nepoužívá.  
  
- `inactivityTimeout`: Určuje maximální dobu, po kterou služba udržuje zabezpečenou konverzaci, aniž by na ní nikdy přijímala zprávu aplikace. Tato kvóta zabraňuje klientům v vytváření zabezpečených konverzací v rámci služby, což způsobuje, že služba udržuje stav pro každého klienta, ale nikdy je nepoužívá.  
  
 V relaci zabezpečené konverzace mějte na paměti, že `inactivityTimeout` i `receiveTimeout` atributy u vazby mají vliv na časový limit relace. Kratší z obou určuje, kdy dojde k vypršení časového limitu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.LocalServiceSecuritySettingsElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.SecurityBindingElement.LocalServiceSettings%2A>
- <xref:System.ServiceModel.Channels.LocalServiceSecuritySettings>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Vazby](../../../wcf/bindings.md)
- [Rozšíření vazeb](../../../wcf/extending/extending-bindings.md)
- [Vlastní vazby](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Zabezpečení vlastních vazeb](../../../wcf/samples/custom-binding-security.md)

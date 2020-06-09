---
title: Spolehlivé relace – přehled
ms.date: 03/30/2017
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
ms.openlocfilehash: a85a34c5e2ec7928c01586e4b01cdf5e90e896a7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601085"
---
# <a name="reliable-sessions-overview"></a>Spolehlivé relace – přehled

Spolehlivé zasílání zpráv protokolu SOAP Windows Communication Foundation (WCF) poskytuje koncovou spolehlivost přenosu zpráv mezi koncovými body SOAP. Je to v sítích, které jsou nespolehlivé při překonání selhání přenosu a selhání na úrovni zpráv SOAP. Konkrétně poskytuje objednané a (volitelně) seřazené doručování zpráv odesílaných napříč zprostředkovateli SOAP nebo přenosu. Doručování na základě relací poskytuje seskupování zpráv v relaci s volitelným řazením zpráv.

V tomto tématu jsou popsány spolehlivé relace, jak a kdy je budete používat, a jak je zabezpečit.

## <a name="wcf-reliable-sessions"></a>Spolehlivé relace WCF

Spolehlivé relace WCF je implementace spolehlivého zasílání zpráv SOAP podle definice protokolu WS-ReliableMessaging.

Spolehlivé zasílání zpráv SOAP WCF poskytuje ucelenou spolehlivou relaci mezi dvěma koncovými body bez ohledu na počet nebo typ zprostředkovatelů, které oddělují koncové body zasílání zpráv. Patří sem všichni zprostředkovatelé přenosu, kteří nepoužívají protokol SOAP (například proxy servery HTTP) nebo zprostředkovatelé, kteří používají protokol SOAP (například směrovače nebo mosty založené na protokolu SOAP), které jsou požadovány pro zprávy, které mají tok mezi koncovými body. Kanál spolehlivé relace podporuje *interaktivní* komunikaci, aby se služby propojené tímto kanálem spouštěly souběžně, a vyměňují a zpracovávají zprávy za podmínek nízké latence, což je v poměrně krátké době. Toto spojení znamená, že tyto komponenty probíhají společně nebo selžou společně, takže mezi nimi není žádná izolace.

Spolehlivé relace maskují dva druhy selhání:

- Selhání na úrovni zpráv SOAP, které zahrnuje ztráty nebo duplicitní zprávy a zprávy, které dorazí v jiném pořadí, než je v pořadí, ve kterém byly odeslány.

- Selhání přenosu.

Spolehlivá relace implementuje protokol WS-ReliableMessaging a okno přenosu v paměti, které umožňuje maskovat selhání na úrovni zpráv SOAP a znovu vytvoří připojení v případě selhání přenosu.

Spolehlivá relace poskytuje zprávy protokolu SOAP, které protokol TCP poskytuje pro pakety IP. Připojení soketu TCP poskytuje jednotné převádění paketů protokolu IP mezi uzly v daném pořadí. Spolehlivý kanál poskytuje stejný typ spolehlivého přenosu, ale liší se od spolehlivosti soketu TCP následujícími způsoby:

- Spolehlivost je na úrovni zprávy protokolu SOAP, nikoli v případě svévolné velikosti paketu bajtů.

- Spolehlivost je přenosově neutrální, nikoli jenom pro přenos přes protokol TCP.

- Spolehlivost není vázaná na konkrétní přenosovou relaci (například relace, kterou poskytuje připojení TCP), a může současně používat víc přenosů přenosu, nebo postupně po dobu životnosti spolehlivé relace.

- Spolehlivá relace je mezi koncovými body protokolu SOAP odesílatele a příjemce, a to bez ohledu na počet přenosů, které jsou potřeba k připojení mezi nimi. V krátké době spolehlivost protokolu TCP končí tím, že přenosová připojení skončí, zatímco stabilní relace zajišťuje komplexní spolehlivost.

## <a name="reliable-sessions-and-bindings"></a>Spolehlivé relace a vazby

Jak bylo zmíněno dříve, Spolehlivá relace je nezávislá na přenosu. Můžete také vytvořit spolehlivou relaci přes mnoho vzorů výměny zpráv, jako je například požadavek-odpověď nebo duplexní přenos. Spolehlivá relace WCF je vystavena jako vlastnost sady vazeb.

Používejte spolehlivé relace na koncových bodech, které používají:

- Transportní standardní vazby založené na protokolu HTTP:

  - `WsHttpBinding`a zveřejňujte požadavek-odpověď nebo jednosměrné smlouvy.

  - Při použití spolehlivé relace přes odpověď na požadavek nebo jednoduchou jednosměrnou kontrakt služby.

  - `WsDualHttpBinding`a zveřejňujte duplexní, požadavek-odpověď nebo jednosměrné kontrakty.

  - `WsFederationHttpBinding`a zveřejňujte požadavek-odpověď nebo jednosměrné smlouvy.

- Transportní standardní vazby založené na protokolu TCP:

  - `NetTcpBinding`a zveřejňujte duplexní, požadavek na odpověď nebo jednosměrné kontrakty.

Použití spolehlivé relace na všech dalších vazbách vytvořením vlastní vazby, jako je například HTTPS (Další informace o problémech najdete v tématu <a href="#reliable-sessions-and-security">spolehlivé relace a zabezpečení</a>) nebo vazby pojmenovaného kanálu.

Můžete vytvořit zásobník spolehlivé relace pro různé základní typy kanálů a výsledný tvar kanálu spolehlivé relace se liší. U klienta i serveru je typ podporovaného kanálu spolehlivé relace závislý na typu použitého kanálu. Následující tabulka uvádí typy kanálů relací podporovaných v klientovi jako funkce základního typu kanálu.

| Podporované typy kanálů spolehlivé relace&#8224; | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | Ano               | Ano                      | Ano              | Ano                     |
| `IRequestSessionChannel`                        | Ano               | Ano                      | Ne               | Ne                      |
| `IDuplexSessionChannel`                         | Ne                | No                       | Ano              | Ano                     |

&#8224;podporovaných typů kanálů jsou dostupné hodnoty pro `TChannel` hodnotu obecného parametru, která je předána <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> metodě.

V následující tabulce jsou uvedeny typy kanálů relací, které jsou na serveru podporovány jako funkce základního typu kanálu.

| Podporované typy kanálů spolehlivé relace&#8225; | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | Ano             | Ano                    | Ano              | Ano                     |
| `IReplySessionChannel`                          | Ano             | Ano                    | Ne               | Ne                      |
| `IDuplexSessionChannel`                         | Ne              | No                     | Ano              | Ano                     |

&#8225;podporovaných typů kanálů jsou dostupné hodnoty pro `TChannel` hodnotu obecného parametru, která je předána <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> metodě.

## <a name="reliable-sessions-and-security"></a>Spolehlivé relace a zabezpečení

Zabezpečení spolehlivé relace je důležité, aby bylo zajištěno, že jsou ověřeny komunikující strany (služby a klienti) a že zprávy vyměňované v relaci nejsou úmyslně poškozeny. Kromě toho je důležité zajistit integritu jednotlivých spolehlivých relací. Spolehlivá relace je zabezpečená vazbou na kontext zabezpečení reprezentovaný a spravovaný kanálem relace zabezpečení. Kanál zabezpečení poskytuje bezpečnostní relaci. Tokeny zabezpečení vyměňované během navazování relace se pak používají k zabezpečení zpráv ve stabilní relaci.

Když je spolehlivá relace přes TCP-S, relace protokolu TCP je svázána s stabilní relací. Proto zabezpečení přenosu zajišťuje, že zabezpečení je také svázáno s spolehlivou relací. V tomto případě je opětovné vytvoření připojení vypnuté.

Jedinou výjimkou je použití protokolu HTTPS. Relace SSL (Secure Sockets Layer) (SSL) není vázaná na stabilní relaci. To představuje hrozbu, protože relace, které sdílí kontext zabezpečení (relace SSL), nejsou navzájem chráněné. To může nebo nemusí být skutečná hrozba v závislosti na aplikaci.

## <a name="using-reliable-sessions"></a>Používání spolehlivých relací

Chcete-li použít spolehlivé relace WCF, vytvořte koncový bod s vazbou, která podporuje spolehlivou relaci. Použijte jednu z uživatelsky dodaných vazeb, které poskytuje WCF se zapnutou spolehlivou relací, nebo vytvořte vlastní vazbu, která to dělá.

Mezi systémem definované vazby, které podporují a povolují spolehlivou relaci, patří:

- <xref:System.ServiceModel.WSDualHttpBinding>

Uživatelsky zadané vazby, které podporují spolehlivé relace jako možnost, ale nepovolují jednu ve výchozím nastavení, zahrnují:

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

Příklad, jak vytvořit vlastní vazbu, naleznete v tématu [How to: Create a Custom Reliable Session Binding with https](how-to-create-a-custom-reliable-session-binding-with-https.md).

Diskuzi o vazbách WCF, které podporují spolehlivé relace, najdete v tématu [vazby poskytované systémem](../system-provided-bindings.md).

## <a name="when-to-use-reliable-sessions"></a>Kdy použít spolehlivé relace

Je důležité pochopit, kdy používat spolehlivé relace ve vaší aplikaci. Služba WCF podporuje spolehlivé relace mezi koncovými body, které jsou aktivní a aktivní ve stejnou dobu. Pokud vaše aplikace vyžaduje, aby jeden z koncových bodů nebyl po dobu určitou dobu dostupný, použijte fronty k zajištění spolehlivosti.

Pokud scénář vyžaduje dva koncové body, které jsou připojeny přes protokol TCP, může být protokol TCP dostačující pro zajištění spolehlivých výměn zpráv. I když není nutné používat spolehlivou relaci, protože TCP zajišťuje doručení paketů v pořadí a pouze jednou.

Pokud má váš scénář některé z následujících charakteristik, je nutné vážně zvážit použití spolehlivé relace.

- Zprostředkovatelé SOAP, jako jsou směrovače protokolu SOAP

- Zprostředkující servery proxy nebo přenosové mosty

- Přerušované připojení

- Relace přes protokol HTTP

## <a name="see-also"></a>Viz také

- [Používání vazeb ke konfiguraci služeb a klientů](../using-bindings-to-configure-services-and-clients.md)
- [Spolehlivá relace WS](../samples/ws-reliable-session.md)

---
title: Spolehlivé relace – přehled
ms.date: 03/30/2017
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
ms.openlocfilehash: 6dd90ef800daf236d77c419d48c0857ac2d78aa2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61962653"
---
# <a name="reliable-sessions-overview"></a>Spolehlivé relace – přehled

Windows Communication Foundation (WCF) protokolu SOAP spolehlivé zasílání zpráv poskytuje začátku do konce zpráv přenosu spolehlivosti mezi koncových bodů protokolu SOAP. Dělá to v sítích, které nespolehlivé překonat selhání přenosu a výpadky na úrovni zprávy protokolu SOAP. Zejména poskytuje založeného na relacích, jeden a (volitelně) objednané dodání pro zprávy odeslané přes zprostředkovatelů SOAP nebo přenos. Doručování na základě relace obsahuje seskupení zprávy v relaci s volitelné řazení zpráv.

Toto téma popisuje spolehlivé relace, jak a kdy je můžete použít a jak je zabezpečit.

## <a name="wcf-reliable-sessions"></a>Spolehlivé relace WCF

Spolehlivé relace WCF je implementace spolehlivé zasílání zpráv v souladu s definicemi WS-ReliableMessaging protokolu SOAP.

Spolehlivé zasílání zpráv WCF SOAP poskytuje začátku do konce stabilní relace mezi dva koncové body, bez ohledu na počet a typ zprostředkovatelů, které oddělují zasílání zpráv koncových bodů. To zahrnuje všechny přenosu zprostředkovatelů, které nepoužívají SOAP (například proxy protokolu HTTP) nebo zprostředkovatelů, které používají protokol SOAP (například založený na protokolu SOAP směrovače nebo mosty), které jsou požadovány pro zprávy, které jsou předávány mezi koncovými body. Kanál stabilní relace podporuje *interaktivní* komunikace tak, aby služby připojené taková kanálu běžet souběžně a exchange a zpracování zpráv v podmínkách s nízkou latencí, to znamená, v rámci poměrně krátké časové intervaly. Toto párování znamená, že tyto součásti pokroku společně selhání společně, tak, že neexistuje žádná izolace, kterou poskytuje mezi nimi.

Spolehlivá relace zakrývá dva druhy chyb:

- Selhání úroveň zprávy protokolu SOAP, včetně ztráty nebo duplicitní zprávy a zprávy přicházející v jiném pořadí od pořadí, ve kterém byly odeslány.

- Přenos chyb.

Spolehlivé relace implementuje protokol WS-ReliableMessaging a oknem přenosu v paměti na selhání maska úrovně zprávy protokolu SOAP a znovu naváže připojení v případě selhání přenosu.

Stabilní relace obsahuje zprávy protokolu SOAP TCP poskytuje pro pakety protokolu IP. Připojení soketu TCP poskytuje jednotném čísle, v daném pořadí přenosu paketů IP mezi uzly. Stabilního kanálu poskytuje stejný typ přenosu spolehlivé, ale liší se od spolehlivost soket TCP následujícími způsoby:

- Spolehlivost je na zprávu protokolu SOAP úroveň, není pro libovolně velikosti paket bajtů.

- Spolehlivost je přenos doménově neutrální, nejen pro přenos přes protokol TCP.

- Spolehlivost není vázaný na konkrétní přenos relace (například relace, které poskytuje připojení protokolu TCP) a využívat více relací přenos současně nebo postupně během životního cyklu ve stabilní relaci.

- Stabilní relace se nachází mezi odesílatelem a příjemcem koncových bodů protokolu SOAP, bez ohledu na počet připojení přenosu potřebných pro připojení mezi nimi. Stručně řečeno TCP spolehlivost skončí, kde přenosového připojení končí, když stabilní relace obsahuje spolehlivost začátku do konce.

## <a name="reliable-sessions-and-bindings"></a>Spolehlivé relace a vazby

Jak už bylo zmíněno dříve, je spolehlivé relace přenosu neutrální. Navíc můžete vytvořit stabilní relace přes mnoho zpráv exchange vzory, třeba požadavek odpověď nebo duplexní. Spolehlivé relace WCF je vystavena jako vlastnost sady vazby.

Použijte stabilní relace na koncové body, které používají:

- Standardní vazby přenosu založené na protokolu HTTP:

  - `WsHttpBinding` a vystavit požadavek odpověď nebo jednosměrné kontrakty.

  - Při použití stabilní relace přes požadavek odpověď nebo jednoduchý jednosměrné servisní smlouvy.

  - `WsDualHttpBinding` a vystavit duplexní, požadavek odpověď nebo jednosměrné kontrakty.

  - `WsFederationHttpBinding` a vystavit požadavek odpověď nebo jednosměrné kontrakty.

- Standardní vazby přenosu založené na TCP:

  - `NetTcpBinding` a vystavit oboustranný tisk, odpověď na žádost o nebo jednosměrné kontrakty.

Použijte stabilní relace na žádné vazby tak, že vytvoříte vlastní vazby, jako je například HTTPS (Další informace o problémech najdete v tématu <a href="#reliable-sessions-and-security">spolehlivé relace a zabezpečení</a>) nebo vazbu pojmenovaného kanálu.

Může seskupit na různé základní typy kanál stabilní relace a výsledné tvar kanálu stabilní relace se liší. Na klientovi i serveru na typ kanálu stabilní relace nepodporuje závisí na typu základní kanál, který slouží. Následující tabulka uvádí typy kanálům relace, které jsou podporované na straně klienta jako funkce základní typ kanálu.

| Podporované typy kanál stabilní relace&#8224; | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | Ano               | Ano                      | Ano              | Ano                     |
| `IRequestSessionChannel`                        | Ano               | Ano                      | Ne               | Ne                      |
| `IDuplexSessionChannel`                         | Ne                | Ne                       | Ano              | Ano                     |

&#8224;Kanál podporované typy jsou k dispozici pro obecné hodnoty `TChannel` hodnotu parametru, která je předána do <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> metody.

Následující tabulka uvádí typy kanálům relace podporován na serveru, jako funkce základní typ kanálu.

| Podporované typy kanál stabilní relace&#8225; | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | Ano             | Ano                    | Ano              | Ano                     |
| `IReplySessionChannel`                          | Ano             | Ano                    | Ne               | Ne                      |
| `IDuplexSessionChannel`                         | Ne              | Ne                     | Ano              | Ano                     |

&#8225;Kanál podporované typy jsou k dispozici pro obecné hodnoty `TChannel` hodnotu parametru, která je předána do <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> metody.

## <a name="reliable-sessions-and-security"></a>Spolehlivé relace a zabezpečení

Spolehlivé relace zabezpečení je důležité zajistit, že proběhne ověření komunikujících stran (klienta a služby) a že zprávy vyměňují v relaci nebylo manipulováno. Kromě toho je důležité k zajištění integrity každé jednotlivé stabilní relace. Spolehlivá relace je zabezpečená pomocí jeho vazbu na kontext zabezpečení, který je reprezentován a spravuje zabezpečený kanál relace. Poskytuje zabezpečený kanál relace zabezpečení. Tokeny zabezpečení při navazování relace, které si vyměňují se pak používají k zabezpečené zprávy ve stabilní relaci.

Po stabilní relace přes TCP S TCP relace se váže na ve stabilní relaci. Zabezpečení přenosu tedy jistotu, že zabezpečení je vázány i ve stabilní relaci. V takovém případě je navázání opakovaného připojení vypnutý.

Jedinou výjimkou je při použití protokolu HTTPS. Relace vrstvy SSL (Secure Sockets) není vázán na ve stabilní relaci. To ukládá hrozbu, protože nejsou chráněné relace, které sdílejí kontext zabezpečení (relace protokolu SSL) od sebe navzájem; To může nebo nemusí být skutečnou hrozbou, v závislosti na aplikaci.

## <a name="using-reliable-sessions"></a>Pomocí spolehlivé relace

Použití relací spolehlivého WCF, vytvořte koncový bod s vazbou, která podporuje stabilní relace. Použijte některou z vazeb poskytovaných systémem, které WCF poskytuje spolehlivé relace povolen nebo vytvořte vlastní vlastní vazby, který to.

Systémem definované vazby, které podporují a povolit stabilní relace ve výchozím nastavení zahrnují:

- <xref:System.ServiceModel.WSDualHttpBinding>

Vazby poskytované systémem, které podporují stabilní relace jako možnost, ale nepovolí jeden ve výchozím nastavení zahrnují:

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

Příklad toho, jak vytvořit vlastní vazby, naleznete v tématu [jak: Vytvoření vazby vlastního stabilní relaci s HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

Diskuzi o vazby WCF, které podporují spolehlivé relace, naleznete v tématu [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).

## <a name="when-to-use-reliable-sessions"></a>Kdy použít spolehlivé relace

Je důležité pochopit, kdy použít spolehlivé relace ve vaší aplikaci. WCF podporuje spolehlivé relace mezi koncovými body, které jsou aktivní a aktivní ve stejnou dobu. Pokud vaše aplikace vyžaduje jednu z koncových bodů nebudou k dispozici pro dobu a pak k zajištění spolehlivosti, slouží fronty.

Pokud tento scénář vyžaduje dva koncové body připojení přes protokol TCP, může být dostatečná pro poskytování výměny spolehlivých zpráv TCP. I když není nutné použít stabilní relace, od TCP zajišťuje, že pakety doručeny v pořadí a pouze jednou.

Pokud váš scénář obsahuje některý z těchto vlastností, pak musíte vážně zvážit použití stabilní relace.

- Zprostředkovatelů SOAP, jako jsou například routery SOAP

- Zprostředkovatelé proxy nebo mosty přenosu

- Přerušovaným připojením

- Relace přes protokol HTTP

## <a name="see-also"></a>Viz také:

- [Používání vazeb ke konfiguraci služeb a klientů](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Spolehlivá relace WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md)

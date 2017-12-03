---
title: "Spolehlivé relace – přehled"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b6ca4b3e254055c7142259ea6022a53f003ea25f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="reliable-sessions-overview"></a>Spolehlivé relace – přehled

[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]Spolehlivé zasílání zpráv protokolu SOAP poskytuje spolehlivost přenosu zpráv začátku do konce mezi koncových bodů protokolu SOAP. Dělá to v sítích, které nespolehlivé překonat přenosu chyb a selhání úroveň zprávy protokolu SOAP. Poskytuje konkrétně na bázi relací, jeden a (volitelně) seřazené doručení pro zprávy odeslané přes prostředníci SOAP nebo přenos. Na základě relace doručení poskytuje pro seskupování zpráv v relaci s volitelné řazení zpráv.

Toto téma popisuje spolehlivé relace, jak a kdy je použít a jak zabezpečit jejich.

## <a name="wcf-reliable-sessions"></a>Spolehlivé relace WCF

[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]spolehlivé relace je implementací protokolu SOAP spolehlivého zasílání zpráv podle definice protokolu WS-ReliableMessaging.

[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Spolehlivé zasílání zpráv protokolu SOAP poskytuje spolehlivé relace mezi dva koncové body, bez ohledu na počet a typ prostředníci, které oddělují zasílání zpráv koncové body začátku do konce. To zahrnuje všechny prostředníci přenosu, která nepoužívají protokolu SOAP (například HTTP proxy) nebo prostředníci používající SOAP (například založený na protokolu SOAP směrovače nebo mosty), které jsou požadovány pro zprávy tok mezi koncových bodů. Spolehlivá relace kanál podporuje *interaktivní* komunikaci, aby služby s připojením takový kanál spouštět souběžně a exchange a proces zprávy v podmínkách s nízkou latencí, který je v poměrně krátké časové intervaly. Tato párování znamená, že tyto součásti poskytnutí přehledu o pokroku společně nebo selhávají najednou, takže není bez izolace mezi je k dispozici.

Spolehlivá relace zakrývá dva druhy chyb:

- Selhání úroveň zprávy protokolu SOAP, včetně ztracené nebo duplicitní zprávy a zprávy, které přicházejí v jiném pořadí z pořadí, ve které byly odeslány.

- Přenosu chyb.

Spolehlivá relace implementuje protokol WS-ReliableMessaging a přenosu v paměti okna selhání maska úrovni zprávu protokolu SOAP a znovu naváže připojení v případě selhání přenosu.

Poskytuje spolehlivé relace protokolu SOAP zprávy TCP poskytuje pro pakety IP. Připojení soketu TCP poskytuje jednotném čísle, v pořadí přenosu paketů IP mezi uzly. Spolehlivé kanál poskytuje stejný typ přenosu spolehlivé, ale liší se od TCP soketu spolehlivost následujícími způsoby:

- Spolehlivost je na zprávu protokolu SOAP úrovni, ne pro paket nahodile velikostí bajtů.

- Spolehlivost je přenos jazykově neutrální, nejen pro přenos přes protokol TCP.

- Spolehlivost není vázaný na konkrétní přenosu relace (například relace, které poskytuje připojení protokolu TCP) a za dobu existence spolehlivé relace můžete použít více relací přenosu souběžně nebo postupně.

- Spolehlivá relace je mezi odesílatele a příjemce koncových bodů protokolu SOAP, bez ohledu na počet připojení přenosu požadované pro připojení mezi nimi. Stručně řečeno TCP spolehlivost ukončí, kde připojení přenosu skončí, zatímco poskytuje spolehlivé relace spolehlivost začátku do konce.

## <a name="reliable-sessions-and-bindings"></a>Spolehlivé relace a vazeb

Jak už bylo zmíněno dříve, spolehlivé relace je přenos neutrální. Můžete také vytvořit spolehlivé relace přes mnoho vzory exchange zprávu, třeba požadavek odpověď nebo duplexní režim. A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spolehlivé relace je k dispozici jako vlastnost sadu vazby.

Spolehlivá relace použijte u koncových bodů, které používají:

- Standardní vazby přenosu založené na protokolu HTTP:

  - `WsHttpBinding`a vystavit požadavku a odpovědi nebo jednosměrné kontrakty.

  - Při použití spolehlivé relace prostřednictvím požadavku a odpovědi nebo kontrakt jednoduché jednosměrné služby.

  - `WsDualHttpBinding`a vystavit duplexní režim, požadavku a odpovědi nebo jednosměrné kontrakty.

  - `WsFederationHttpBinding`a vystavit požadavku a odpovědi nebo jednosměrné kontrakty.

- Standardní vazby protokolu TCP přenosu:

  - `NetTcpBinding`a vystavit duplexní režim, požadavek odpověď nebo jednosměrné kontrakty.

Použít spolehlivé relace na žádné jiné vazby tak, že vytvoříte vlastní vazby, jako je například HTTPS (Další informace o problémech najdete v tématu <a href="#reliable-sessions-and-security">spolehlivé relace a zabezpečení</a>) nebo vazbu pojmenovaný kanál.

Můžete zásobníku spolehlivé relace na různé typy základní kanál a výsledný tvar kanálu spolehlivé relace se liší. Na klientovi a serveru na typ kanálu spolehlivé relace podporován závisí na typu základní kanál, který slouží. Následující tabulka uvádí typy kanálů relace podporován v klientovi jako funkce základní typ kanálu.

| Podporované typy kanál spolehlivé relace &#8224; | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | Ano               | Ano                      | Ano              | Ano                     |
| `IRequestSessionChannel`                        | Ano               | Ano                      | Ne               | Ne                      |
| `IDuplexSessionChannel`                         | Ne                | Ne                       | Ano              | Ano                     |

&#8224; Kanál podporované typy jsou k dispozici pro obecné hodnoty `TChannel` hodnota parametru, která je předána do <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> metoda.

Následující tabulka uvádí typy kanálů relace podporován na serveru jako funkce základní typ kanálu.

| Podporované typy kanál spolehlivé relace &#8225; | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | Ano             | Ano                    | Ano              | Ano                     |
| `IReplySessionChannel`                          | Ano             | Ano                    | Ne               | Ne                      |
| `IDuplexSessionChannel`                         | Ne              | Ne                     | Ano              | Ano                     |

&#8225; Kanál podporované typy jsou k dispozici pro obecné hodnoty `TChannel` hodnota parametru, která je předána do <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> metoda.

## <a name="reliable-sessions-and-security"></a>Spolehlivé relace a zabezpečení

Spolehlivá relace zabezpečení je důležité zajistit, že se ověřují komunikující strany (služba a klient) a že nejsou manipulováno zprávy vyměňují v relaci. Kromě toho je důležité k zajištění integrity každé jednotlivé spolehlivé relace. Spolehlivá relace je zabezpečená službou vazba na kontext zabezpečení, která je reprezentována a spravuje zabezpečený kanál relace. Zabezpečený kanál poskytuje zabezpečení relací. Tokeny zabezpečení vyměňují během vytvoření relace se pak používají k zabezpečení zprávy ve spolehlivých relací.

Po přes TCP S spolehlivé relace relace TCP je vázaný na spolehlivé relace. Zabezpečení přenosu proto zajistí, že zabezpečení je taky vázaný na spolehlivé relace. V takovém případě je obnovení spojení vypnutý.

Jedinou výjimkou je při použití protokolu HTTPS. Relace Secure Sockets Layer (SSL) není vázán na spolehlivé relace. To ukládá hrozbu, protože relace, které sdílejí kontextu zabezpečení (relace SSL) nejsou chráněné od sebe navzájem; Tato operace může nebo nemusí být skutečné hrozby v závislosti na aplikaci.

## <a name="using-reliable-sessions"></a>Pomocí spolehlivé relace

Chcete-li použít [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spolehlivé relace, vytvořit koncový bod s vazbou, který podporuje spolehlivé relace. Použijte jednu z vazby poskytované systémem, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje spolehlivé relace povolen nebo vytvořit vlastní vlastní vazby, který to.

Vazby definovaná systémem, které podporují a povolit spolehlivé relace ve výchozím nastavení patří:

- <xref:System.ServiceModel.WSDualHttpBinding>

Vazby poskytované systémem, které podporují spolehlivé relace jako možnost, ale nepovolíte jeden ve výchozím nastavení patří:

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

Příklad vytvoření vlastní vazby, naleznete v části [postupy: vytvoření vlastní vazby spolehlivé relace s protokolem HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).

Informace o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vazby, které podporují spolehlivé relace, najdete v části [System-Provided vazby](../../../../docs/framework/wcf/system-provided-bindings.md).

## <a name="when-to-use-reliable-sessions"></a>Kdy použít spolehlivé relace

Je důležité pochopit, kdy použít spolehlivé relace v aplikaci. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje spolehlivé relace mezi koncovými body, které jsou aktivní a zachování připojení ve stejnou dobu. Pokud vaše aplikace vyžaduje jeden z koncových bodů být k dispozici po dobu čas a potom používat fronty zajistit spolehlivost.

Pokud tento scénář vyžaduje dva koncové body, které jsou připojené přes protokol TCP, může být dostatečná k poskytování výměny zpráv spolehlivého TCP. I když není potřeba použít spolehlivé relace, protože TCP zajišťuje, že pakety dorazí v pořadí a pouze jednou.

Pokud váš scénář má některý z těchto vlastností, pak musíte vážně zvážit použití spolehlivé relace.

- Prostředníci SOAP, jako jsou směrovače protokolu SOAP

- Proxy prostředníci nebo mostů přenosu

- Přerušované připojení

- Relace prostřednictvím protokolu HTTP

## <a name="see-also"></a>Viz také

[Používání vazeb ke konfiguraci služeb a klientů](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)   
[Spolehlivá relace WS](../../../../docs/framework/wcf/samples/ws-reliable-session.md)

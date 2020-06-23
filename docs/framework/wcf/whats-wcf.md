---
title: Co je to Windows Communication Foundation
description: Přečtěte si o Windows Communication Foundation, což je rozhraní pro vytváření aplikací orientovaných na služby.
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
ms.openlocfilehash: 84cb45d62409769a79fa6a401fdb1aa6934c4099
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245606"
---
# <a name="what-is-windows-communication-foundation"></a>Co je to Windows Communication Foundation
Windows Communication Foundation (WCF) je rozhraní pro vytváření aplikací orientovaných na služby. Pomocí WCF můžete odesílat data jako asynchronní zprávy z jednoho koncového bodu služby do jiného. Koncový bod služby může být součástí nepřetržitě dostupné služby hostované službou IIS nebo může být služba hostovaná v aplikaci. Koncovým bodem může být klient služby, která žádá o data z koncového bodu služby. Zprávy mohou být jednoduché jako jeden znak nebo Word odeslaný jako XML nebo jako datový proud binárních dat. Mezi několik ukázkových scénářů patří:

- Zabezpečená služba pro zpracování obchodních transakcí.

- Služba, která poskytuje aktuální data jiným uživatelům, jako je například zpráva o provozu nebo jiná služba monitorování.

- Chatovací služba, která umožňuje dvěma lidem komunikovat data nebo je vyměňovat v reálném čase.

- Aplikace řídicího panelu, která se dotazuje na jednu nebo více služeb pro data a prezentuje ji v logické prezentaci.

- Odhalení pracovního postupu implementovaného pomocí programovací model Windows Workflow Foundation jako služby WCF.

- Aplikace Silverlight, která se bude dotazovat služby na nejnovější datové kanály.

Při vytváření takových aplikací bylo možné ještě před existencí služby WCF vytvářet vývoj koncových bodů snadněji než kdy dřív. Služba WCF je v souhrnu navržena tak, aby nabízela spravovatelný přístup k vytváření webových služeb a klientů webových služeb.

## <a name="features-of-wcf"></a>Funkce služby WCF

WCF zahrnuje následující sadu funkcí. Další informace najdete v tématu [Podrobnosti o funkcích WCF](./feature-details/index.md).

- **Orientace služby**

     Jedním z důsledků použití standardů WS je to, že technologie WCF umožňuje vytváření aplikací *orientovaných na služby* . Architektura typu SOA (Service-orientované) je závislá na webových službách pro posílání a přijímání dat. Služby mají obecně výhodně oddělené místo pevně zakódovaných z jedné aplikace do jiné. Volně spojený vztah předpokládá, že se každý klient vytvořený na libovolné platformě může připojit k jakékoli službě, pokud jsou splněné základní smlouvy.

- **Interoperabilita**

     WCF implementuje moderní oborové standardy pro interoperabilitu webové služby. Další informace o podporovaných standardech najdete v tématu [interoperabilita and Integration](./feature-details/interoperability-and-integration.md).

- **Více vzorů zpráv**

     Zprávy se vyměňují v jednom z několika vzorů. Nejběžnějším vzorem je vzor požadavků a odpovědí, kdy jeden koncový bod požaduje data z druhého koncového bodu. Druhý koncový bod odpoví. Existují i jiné způsoby, například jednosměrná zpráva, kdy jeden koncový bod odesílá zprávu bez nutnosti očekávat odpověď. Složitější vzor je duplexní vzorek, ve kterém dva koncové body navážou připojení a odesílají data zpátky a zpátky, podobně jako program pro zasílání rychlých zpráv. Další informace o tom, jak implementovat různé vzory výměny zpráv pomocí WCF, najdete v tématu [kontrakty](./feature-details/contracts.md).

- **Metadata služby**

     WCF podporuje publikování metadat služby pomocí formátů určených v oborových standardech, jako je WSDL, schéma XML a WS-Polica. Tato metadata lze použít k automatickému generování a konfiguraci klientů pro přístup ke službám WCF. Metadata se dají publikovat přes HTTP a HTTPS nebo pomocí standardu Exchange pro metadata webové služby. Další informace najdete v tématu [metadata](./feature-details/metadata.md).

- **Kontrakty dat**

     Protože je WCF sestaveno pomocí .NET Framework, zahrnuje také metody pro kód, které poskytují smlouvy, které chcete vykonat. Jedním z univerzálních typů smluv je kontrakt dat. V podstatě je při psaní služby pomocí jazyka Visual C# nebo Visual Basic nejjednodušší způsob, jak zpracovávat data, vytvářet třídy, které reprezentují datovou entitu s vlastnostmi, které patří k datové entitě. WCF zahrnuje komplexní systém pro práci s daty tímto snadným způsobem. Jakmile vytvoříte třídy, které reprezentují data, služba automaticky vygeneruje metadata, která klientům umožňují dodržovat typy dat, které jste navrhli. Další informace najdete v tématu [Použití kontraktů dat](feature-details/using-data-contracts.md).

- **Zabezpečení**

     Zprávy mohou být zašifrovány pro ochranu osobních údajů a před povolením přijímání zpráv můžete vyžadovat, aby si uživatelé ověřili sami. Zabezpečení je možné implementovat pomocí dobře známých standardů, jako je SSL nebo WS-SecureConversation. Další informace najdete v tématu [zabezpečení](./feature-details/security.md).

- **Více přenosů a kódování**

     Zprávy lze odesílat z několika integrovaných přenosových protokolů a kódování. Nejběžnější protokol a kódování je odesílat kódované zprávy protokolu SOAP pomocí protokolu HTTP (HyperText Transfer Protocol) pro použití na webu. Služba WCF také umožňuje odesílat zprávy přes protokol TCP, pojmenované kanály nebo službu MSMQ. Tyto zprávy lze kódovat jako text nebo pomocí optimalizovaného binárního formátu.  Binární data se dají efektivně odesílat pomocí standardu MTOM. Pokud žádný z poskytovaných přenosů nebo kódování nevyhovuje vašim potřebám, můžete vytvořit vlastní přenos nebo kódování. Další informace o přenosech a kódováních, které podporuje WCF, najdete v tématu [přenosy](./feature-details/transports.md).

- **Spolehlivé zprávy a zprávy zařazené do fronty**

     Služba WCF podporuje spolehlivé výměny zpráv pomocí spolehlivých relací implementovaných prostřednictvím zasílání zpráv WS-Reliable a pomocí služby MSMQ. Další informace o spolehlivé podpoře zasílání zpráv ve frontě v WCF najdete v tématu [fronty a spolehlivé relace](./feature-details/queues-and-reliable-sessions.md).

- **Trvalé zprávy**

     Trvalá zpráva je ta, která se nikdy neztratila z důvodu přerušení komunikace. Zprávy ve vzoru odolné zprávy jsou vždy uloženy do databáze. Pokud dojde k přerušení, databáze vám umožní pokračovat v výměně zpráv při obnovení připojení. Můžete také vytvořit trvalé zprávy pomocí programovací model Windows Workflow Foundation (WF). Další informace najdete v tématu [služby pracovních postupů](./feature-details/workflow-services.md).

- **Transakce**

     WCF podporuje také transakce pomocí jednoho ze tří modelů transakce: WS-AtomicTransactions, rozhraní API v <xref:System.Transactions> oboru názvů a Microsoft DTC (Distributed Transaction Coordinator). Další informace o podpoře transakcí v WCF najdete v tématu [transakce](./feature-details/transactions-in-wcf.md).

- **Podpora AJAX a REST**

     REST je příkladem vyvíjející se technologie Web 2,0. WCF se dá nakonfigurovat tak, aby zpracovával "jednoduchá" data XML, která nejsou zabalená v obálce SOAP. WCF lze také rozšířit tak, aby podporovalo konkrétní formáty XML, jako je například ATOM (oblíbený Standard RSS), a dokonce i jiné formáty než XML, jako je například JavaScript Object Notation (JSON).

- **Rozšiřitelnost**

     Architektura WCF má několik bodů rozšiřitelnosti. Pokud se vyžaduje další funkce, je k dispozici několik vstupních bodů, které vám umožní přizpůsobit chování služby. Další informace o dostupných bodech rozšiřitelnosti najdete v tématu [rozšíření WCF](./extending/index.md).

## <a name="wcf-integration-with-other-microsoft-technologies"></a>Integrace WCF s dalšími technologiemi Microsoftu

WCF je flexibilní platforma. Z důvodu této extrémní flexibility se WCF používá i v několika dalších produktech Microsoftu. Díky porozumění základům WCF máte okamžitou výhodu, pokud použijete také některý z těchto produktů.

První technologie pro párování s WCF byla programovací model Windows Workflow Foundation (WF). Pracovní postupy zjednodušují vývoj aplikací zapouzdřením kroků v pracovním postupu jako "aktivity". V první verzi programovací model Windows Workflow Foundation musel vývojář vytvořit hostitele pro pracovní postup. Další verze programovací model Windows Workflow Foundation byla integrována se službou WCF. To, že je povolený libovolný pracovní postup, který je možné snadno hostovat ve službě WCF. To můžete provést tak, že automaticky zvolíte typ projektu WF/WCF v aplikaci Visual Studio 2012 nebo novější.

Microsoft BizTalk Server R2 také využívá WCF jako komunikační technologii. BizTalk je navržený tak, aby přijímal a transformoval data z jednoho standardizovaného formátu do jiného. Zprávy musí být doručeny do centrálního okna zpráv, kde lze zprávu transformovat pomocí striktního mapování nebo pomocí jedné z funkcí BizTalk, jako je například modul pracovního postupu. BizTalk teď může k doručování zpráv do okna se zprávou použít obchodní adaptér WCF (LOB).

Microsoft Silverlight je platforma pro vytváření interoperabilních a bohatých webových aplikací, které vývojářům umožňují vytvářet weby náročné na média (například streamování videa). Od verze 2 Silverlight zavedlo WCF jako komunikační technologii pro připojení aplikací Silverlight k koncovým bodům WCF.

Funkce hostování aplikačního serveru Windows serveru AppFabric jsou určené konkrétně pro nasazení a správu aplikací, které používají WCF pro komunikaci. Mezi funkce hostování patří rozšířené možnosti nástrojů a konfigurace, které jsou určené konkrétně pro aplikace podporující WCF.

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel>
- [Základní koncepty Windows Communication Foundation](fundamental-concepts.md)
- [Architektura Windows Communication Foundation](architecture.md)
- [Pokyny a osvědčené postupy](guidelines-and-best-practices.md)
- [Kurz Začínáme](getting-started-tutorial.md)
- [Průvodce dokumentací](guide-to-the-documentation.md)
- [Základní programování WCF](basic-wcf-programming.md)
- [Ukázky služby Windows Communication Foundation](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751514%28v=vs.90%29)

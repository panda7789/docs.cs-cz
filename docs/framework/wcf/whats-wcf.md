---
title: Co je to Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
ms.openlocfilehash: 0aaa72741a1bb75862a1e3a4c5569ea53919a7f3
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/06/2018
ms.locfileid: "48845577"
---
# <a name="what-is-windows-communication-foundation"></a>Co je to Windows Communication Foundation
Windows Communication Foundation (WCF) je architektura určená k vytváření aplikací orientovaných na služby. Pomocí technologie WCF, můžete odeslat data jako asynchronní zprávy z jeden koncový bod služby do jiného. Koncový bod služby můžou být součástí nepřetržitě dostupnými službami hostované službou IIS nebo může být služba hostovaná v aplikaci. Koncový bod může být klient služby, který vyžaduje data z koncového bodu služby. Zprávy může být stejně jednoduché jako jeden znak nebo slova jako XML, nebo komplexního, jako binární datový proud. Několik ukázkových scénářů patří:

-   Zabezpečenou službu ke zpracování obchodních transakcí.

-   Služba poskytující aktuální data ostatním uživatelům, jako je například sestavy provoz nebo jiná monitorovací služba.

-   Chatovací služba, která umožňuje dvou osob, které umožňují komunikovat nebo vyměňovat data v reálném čase.

-   Řídicí panel aplikace, který se dotazuje jednu nebo víc služeb pro data a prezentuje logické prezentace.

-   Vystavení pracovního postupu implementovaná jako služba WCF pomocí programovacího modelu Windows Workflow Foundation.

-   Aplikace Silverlight k dotazování služby pro nejnovější datové kanály.

Během vytváření těchto aplikací je možné před existenci WCF, WCF usnadňuje vývoj koncových bodů než kdy dřív. Stručně řečeno WCF je určená k poskytování spravovaného přístupu k vytváření webových služeb a klienty webové služby.

## <a name="features-of-wcf"></a>Funkce služby WCF

WCF zahrnuje následující sady funkcí. Další informace najdete v tématu [podrobnosti o funkcích WCF](../../../docs/framework/wcf/feature-details/index.md).

-   **Orientaci na služby**

     Jednu pomocí standardů WS důsledkem je, že WCF umožňuje vytvořit *služby* aplikací. Architektura orientovaná na služby (SOA) je nekladou na webových službách odesílat a přijímat data. Služby mají hlavní výhodou volně spárované namísto pevně zakódovaný z jedné aplikace do jiného. Vztah volně spárované znamená, že jakýkoli klient vytvoří na libovolné platformě můžete připojit k libovolné službě tak dlouho, dokud jsou splněny základní kontrakty.

-   **Interoperabilita**

     WCF implementuje moderní oborové standardy pro interoperabilitu webové služby. Další informace o podporované standardy, naleznete v tématu [interoperabilita a integrace](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md).

-   **Více vzorům zprávy**

     Zprávy se vyměňují v jednom z několika způsoby. Nejběžnější vzor je vzor žádost odpověď, kde jeden koncový bod vyžaduje data z druhé koncový bod. Druhý odpovědi koncového bodu. Existují další způsoby, jako je například jednosměrná zpráva, ve kterém jeden koncový bod odešle zprávu bez jakékoli očekává odpověď. Složitější vzor je vzor duplexní exchange, kde dva koncové body připojení a odešlete data vpřed a zpět, podobný program pro zasílání rychlých zpráv. Další informace o tom, jak implementovat jiná zpráva exchange vzory pomocí technologie WCF najdete v části [kontrakty](../../../docs/framework/wcf/feature-details/contracts.md).

-   **Metadata služby**

     WCF podporuje použití formátů podle oborových standardů, jako je například WSDL, schéma XML a WS-Policy publikování metadat služby. Tato metadata slouží k automatickému generování a konfigurace klientů pro přístup ke službám WCF. Metadata je možné publikovat prostřednictvím protokolu HTTP a HTTPS nebo pomocí standardní webové služby Metadata Exchange. Další informace najdete v tématu [metadat](../../../docs/framework/wcf/feature-details/metadata.md).

-   **Kontrakty dat**

     Protože WCF se vytvořil pomocí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)], zahrnuje také přívětivá kód metody poskytnutí smluv, které chcete vynutit. Univerzální typů kontraktů kontraktu dat. je. V podstatě při kódování svojí služby pomocí jazyka Visual C# nebo Visual Basic, nejjednodušší způsob, jak zpracovávat data tím je vytvoření třídy, které představují data entity s vlastnostmi, které patří do datové entity. WCF obsahuje komplexní systém pro práci s daty tímto způsobem snadno. Po vytvoření třídy, které představují data, vaše služba automaticky generuje metadata, která umožňuje klientům v souladu s typy dat, které jste vytvořili. Další informace najdete v tématu [použití kontraktů dat](../../../docs/framework/wcf/feature-details/using-data-contracts.md)

-   **Zabezpečení**

     Zprávy se můžou šifrovat zájmu ochrany osobních údajů a může vyžadovat, aby uživatelé sami ověření před nebudou moct přijímat zprávy. Zabezpečení je možné implementovat pomocí dobře známých standardy, jako je protokol SSL nebo WS-SecureConversation. Další informace najdete v tématu [zabezpečení](../../../docs/framework/wcf/feature-details/security.md).

-   **Více přenosů a kódování**

     Na žádném z několika předdefinovaných přenosové protokoly a kódováním odesílat zprávy. Nejvíce běžné protokoly a kódováním je odesílání, kódování textu zprávy protokolu SOAP pomocí protokol HTTP (HyperText Transfer) pro použití na webu. WCF umožňuje odesílání zpráv přes protokol TCP, případně název kanálu nebo služby MSMQ. Tyto zprávy mohou být kódovány jako text nebo optimalizovaného binárního formátu.  Binární data mohou být odesílány efektivně pomocí standardní funkce MTOM. Pokud žádný zadaný přenosy ani kódování vyhovovala vašim potřebám, můžete si vytvořit vlastní kódování nebo přenos. Další informace o přenosy a kódování nepodporuje WCF najdete v části [přenosy](../../../docs/framework/wcf/feature-details/transports.md).

-   **Spolehlivé a zařazených do fronty zpráv**

     WCF podporuje spolehlivé zprávy exchange pomocí spolehlivé relace implementuje přes zasílání zpráv WS-Reliable a pomocí služby MSMQ. Další informace o podpoře zařazených do fronty a spolehlivé zasílání zpráv ve službě WCF najdete v části [fronty a spolehlivé relace](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).

-   **Trvalý zprávy**

     Zpráv trvalý je ten, který se nikdy ztraceno v důsledku přerušení komunikace. Zprávy ve vzorku zpráv trvalý se vždycky uloží do databáze. Pokud dojde k přerušení, databázi můžete obnovit výměně zpráv při obnovení připojení. Můžete také vytvořit zpráv trvalý pomocí Windows Workflow Foundation (WF). Další informace najdete v tématu [služeb pracovních postupů](../../../docs/framework/wcf/feature-details/workflow-services.md).

-   **Transakce**

     Také podporuje transakce použitím jednoho ze tří modelů transakce WCF: WS-AtomicTtransactions, rozhraní API v <xref:System.Transactions> obor názvů a Microsoft Distributed Transaction Coordinator. Další informace o transakci, najdete v článku podpory ve službě WCF [transakce](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md).

-   **AJAX a podpora REST**

     REST je příkladem vyvíjející technologie Web 2.0. WCF je možné nakonfigurovat ke zpracování "prostý" XML dat, která není zabalena v obálce SOAP. WCF je možné rozšířit také na podporu konkrétních formáty XML, jako je například ATOM (Oblíbené RSS standard) a dokonce i bez XML formáty, jako je například zápis JSON (JavaScript Object).

-   **Rozšíření**

     Architektura WCF se počet bodů rozšiřitelnosti. Pokud se vyžaduje dodatečné funkce, existuje několik vstupních bodů, které umožňují přizpůsobit chování služby. Další informace o dostupných rozšíření body naleznete v tématu [rozšíření WCF](../../../docs/framework/wcf/extending/index.md).

## <a name="wcf-integration-with-other-microsoft-technologies"></a>WCF integrace s dalšími technologiemi Microsoftu

WCF je flexibilní platforma. Z důvodu této flexibility extreme WCF se používá také v několika dalších produktů společnosti Microsoft. Pochopením základy WCF máte okamžitě využívat, pokud také použít některý z těchto produktů.

První technologie spárovat se s použitím technologie WCF byla Windows Workflow Foundation (WF). Pracovní postupy zjednodušit vývoj aplikací tím, že zapouzdřující krocích pracovního postupu jako "aktivity". V první verzi systému Windows Workflow Foundation vývojář se musel vytvořit hostitele pracovního postupu. Příští verzi Windows Workflow Foundation byla integrována s použitím technologie WCF. Která může jakýkoli pracovní postup snadno hostované ve službě WCF. Můžete to provést automaticky výběrem typu projektu WF/WCF v sadě Visual Studio 2012 nebo novější.

Microsoft BizTalk Server R2 také využívá jako komunikační technologie WCF. BizTalk je navržená pro příjem a transformovat data z jednoho standardizovaném formátu do druhého. Zprávy musí doručit do jeho okno se zprávou centrální zprávy se dají transformovat pomocí mapování strict nebo pomocí jedné z funkce BizTalk, jako je jeho modul pracovních postupů. BizTalk teď můžete použít adaptér WCF řádku obchodní (LOB) pro doručení zprávy do okna se zprávou.

Microsoft Silverlight je platforma pro vytváření interoperabilních, bohatých webových aplikací, které umožňují vývojářům vytvářet weby náročné na média (například streamování videa). Od verze 2, doplnil Silverlight WCF technologií komunikace, jak připojit aplikace Silverlight do koncových bodů WCF.

[!INCLUDE[dublin](../../../includes/dublin-md.md)] Aplikační server je vytvořená speciálně pro nasazení a správu aplikací, které používají WCF pro komunikaci. [!INCLUDE[dublin2](../../../includes/dublin2-md.md)] Zahrnuje bohaté možnosti nástrojů a konfigurace vytvořené speciálně pro aplikace pro práci s WCF.

## <a name="see-also"></a>Viz také

- <xref:System.ServiceModel>
- [Základní koncepty Windows Communication Foundation](../../../docs/framework/wcf/fundamental-concepts.md)
- [Architektura Windows Communication Foundation](../../../docs/framework/wcf/architecture.md)
- [Pokyny a osvědčené postupy](../../../docs/framework/wcf/guidelines-and-best-practices.md)
- [Kurz Začínáme](../../../docs/framework/wcf/getting-started-tutorial.md)
- [Průvodce dokumentací](../../../docs/framework/wcf/guide-to-the-documentation.md)
- [Základní programování WCF](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Ukázky Windows Communication Foundation](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)

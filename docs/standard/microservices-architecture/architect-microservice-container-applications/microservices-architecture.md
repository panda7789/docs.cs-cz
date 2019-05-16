---
title: Architektura mikroslužeb
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | 30.000 nohou zobrazení architektury Mikroslužeb.
ms.date: 09/20/2018
ms.openlocfilehash: 3cf2a94140042d3cf76b5b63fe4e98638c56dbfe
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644849"
---
# <a name="microservices-architecture"></a>Architektura mikroslužeb

Jak již název napovídá, architekturu mikroslužeb je takový přístup k sestavení aplikace serveru jako sada malých služeb. To znamená, že architektura mikroslužeb je především orientované do back endu, přestože tento přístup se také používá pro front-endu. Každá služba běží ve vlastním procesu a komunikuje s dalšími procesy pomocí protokolů, jako je například HTTP/HTTPS, protokoly Websocket, nebo [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Každá mikroslužba implementuje konkrétní začátku do konce domény nebo obchodní funkci v rámci určité hranici kontextu a každý musí vyvinout samostatně a možno nasadit nezávisle na sobě. Nakonec každá mikroslužba by měl vlastní jeho související domény datový model a logiku domény (suverenitu a správu decentralizované dat) a můžou vycházet různé technologie úložišť dat (SQL, NoSQL) a různé programovací jazyky.

Jaké velikosti má být mikroslužby? Při vývoji mikroslužby, velikost nesmí být důležité. Místo toho by měl být důležité, k vytvoření volně s velkou provázaností, služby, máte autonomie vývoje, nasazení a škálování pro každou službu. Samozřejmě při identifikaci a návrh mikroslužeb, snažte tak, aby byly co nejmenší, dokud není nutné příliš mnoho přímých závislostí s další mikroslužeb. Důležitější než velikost mikroslužby je interní soudržnosti, musí mít a jeho nezávislost od ostatních služeb.

Proč architektury mikroslužeb? Stručně řečeno umožňuje dlouhodobé flexibilitu. Mikroslužby povolit lepší udržovatelnosti komplexní, velký a vysoce škálovatelné systémy umožňují vytvářet aplikace založené na mnoho samostatně nasaditelných služeb, že obsahují svazky detailní a autonomní životního cyklu.

Další výhodou je mikroslužby můžete škálovat nezávisle. Namísto toho, aby jedna monolitické aplikace musí horizontální navýšení kapacity jako celek, můžete místo toho horizontální navýšení kapacity konkrétní mikroslužeb. Tímto způsobem je možné škálovat jenom funkční oblast, která potřebuje další zpracování napájení nebo sítě šířky pásma pro podporu poptávky, nikoli horizontální navýšení kapacity dalších oblastí aplikace, které není potřeba škálovat. To znamená, že úspory nákladů, které vzhledem k tomu, že budete potřebovat méně hardwaru.

![V tradičních monolitického přístupu škáluje aplikaci naklonováním celé aplikace v několika servery pro/virtuální počítač. V přístup založený mikroslužbách funkce je rozdělen do menších služeb, tak každé služby můžete škálovat nezávisle.](./media/image6.png)

**Obrázek 4 až 6**. Monolitické nasazení oproti přístup založený mikroslužbách

Jak ukazuje obrázek 4 až 6, umožňuje přístup založený mikroslužbách agilní změny a rychlé iterace jednotlivých mikroslužeb, vzhledem k tomu, že změníte konkrétní, malé oblasti komplexní, velký a škálovatelné aplikace.

Aplikační architektura založená na jemně aplikací založených na mikroslužbách umožňuje průběžnou integraci a průběžné doručování postupy. Také zrychluje doplňování nových funkcí do aplikace. Detailní složení aplikace také umožňuje spustit a otestovat mikroslužeb v izolaci a autonomně rozvíjet při zachování vymazat kontraktů mezi nimi. Dokud nezměníte rozhraní nebo smlouvy, můžete změnit vnitřní implementace všechny mikroslužby nebo přidat nové funkce bez narušení další mikroslužeb.

Tady jsou důležité aspekty umožňující úspěch v nasadíte do produkčního prostředí se systémem založených na mikroslužbách:

- Monitorování a kontroly stavu služeb a infrastruktury.

- Škálovatelná infrastruktura služby (to znamená cloud a orchestrátorů).

- Zabezpečení návrhu a implementace na různých úrovních: ověřování, autorizace, správu tajných kódů, zabezpečenou komunikaci, atd.

- Doručování aplikací rychle, obvykle s různými týmy, zaměřuje se na různé mikroslužeb.

- Postupy DevOps a CI/CD a infrastruktury.

Z nich jsou pouze první tři zahrnutých nebo zavedené v této příručce. Poslední dva body, které se vztahují k životního cyklu aplikací, jsou popsané v další [Kontejnerizovaných životní cyklus aplikace Dockeru s platformou a nástroji Microsoft](https://aka.ms/dockerlifecycleebook) e kniha.

## <a name="additional-resources"></a>Další zdroje

- **Mark Russinovich. Mikroslužby: Revoluci aplikací založené na cloudu** \
  <https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/>

- **Martina Fowlera. Mikroslužby** \
  <https://www.martinfowler.com/articles/microservices.html>

- **Martina Fowlera. Požadavky na Mikroslužbách** \
  <https://martinfowler.com/bliki/MicroservicePrerequisites.html>

- **Jimmy Nilsson. Spojí Cloud computingu** \
  <https://www.infoq.com/articles/CCC-Jimmy-Nilsson>

- **De la Torre Cesarovi. Životní cyklus aplikace Dockeru s platformou a nástroji Microsoft kontejnerizovaných** (ke stažení e kniha) \
  <https://aka.ms/dockerlifecycleebook>

>[!div class="step-by-step"]
>[Předchozí](service-oriented-architecture.md)
>[další](data-sovereignty-per-microservice.md)

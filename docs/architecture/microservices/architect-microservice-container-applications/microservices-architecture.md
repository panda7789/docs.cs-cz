---
title: Architektura mikroslužeb
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | 30.000 stop pohled na architekturu Mikroslužeb.
ms.date: 09/20/2018
ms.openlocfilehash: d1c58d218be9e5f8c0ae8ae732f9bdd06674a2c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "71834388"
---
# <a name="microservices-architecture"></a>Architektura mikroslužeb

Jak název napovídá, architektura mikroslužeb je přístup k vytváření serverové aplikace jako sadu malých služeb. To znamená, že architektura mikroslužeb je hlavně orientována na back-end, i když přístup se používá také pro front-end. Každá služba běží ve vlastním procesu a komunikuje s jinými procesy pomocí protokolů, jako je HTTP/HTTPS, WebSockets nebo [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Každá mikroslužba implementuje konkrétní doménu end nebo obchodní schopnosti v rámci určité hranice kontextu a každý musí být vyvinut samostatně a být nasaditelný nezávisle. Nakonec by každá mikroslužba měla vlastnit svůj související datový model domény a logiku domény (suverenita a decentralizovaná správa dat) a mohla by být založena na různých technologiích pro ukládání dat (SQL, NoSQL) a různých programovacích jazycích.

Jakou velikost by měla být mikroslužba? Při vývoji mikroslužby velikost by neměla být důležitým bodem. Místo toho by mělo být důležité vytvořit volně vázané služby, abyste měli autonomii vývoje, nasazení a škálování pro každou službu. Samozřejmě při identifikaci a navrhování mikroslužeb, měli byste se pokusit, aby byly co nejmenší, pokud nemáte příliš mnoho přímých závislostí s jinými mikroslužbami. Důležitější než velikost mikroslužby je vnitřní soudržnost, kterou musí mít, a její nezávislost na jiných službách.

Proč architektura mikroslužeb? Stručně řečeno, poskytuje dlouhodobou agilitu. Mikroslužby umožňují lepší udržovatelnost ve složitých, velkých a vysoce škálovatelných systémech tím, že umožňují vytvářet aplikace založené na mnoha nezávisle nasaditelných službách, které mají podrobné a autonomní životní cykly.

Jako další výhodu mikroslužeb můžete škálovat nezávisle. Místo toho, aby s jednu monolitickou aplikaci, kterou je nutné horizontální navýšení kapacity jako celek, můžete místo toho horizontální navýšení kapacity konkrétní mikroslužeb. Tímto způsobem můžete škálovat pouze funkční oblast, která potřebuje větší výpočetní výkon nebo šířku pásma sítě pro podporu poptávky, spíše než horizontální navýšení kapacity jiných oblastí aplikace, které není nutné škálovat. To znamená úsporu nákladů, protože potřebujete méně hardwaru.

![Diagram rozdílů mezi dvěma metodami nasazení.](./media/microservices-architecture/monolith-deployment-vs-microservice-approach.png)

**Obrázek 4-6**. Monolitické nasazení versus přístup mikroslužeb

Jak ukazuje obrázek 4-6, v tradičním monolitickém přístupu se aplikace škáluje klonováním celé aplikace v několika serverech/virtuálních mích. V přístupu mikroslužeb funkce je oddělena v menších službách, takže každá služba můžete škálovat nezávisle. Přístup mikroslužeb umožňuje agilní změny a rychlou iteraci každé mikroslužby, protože můžete změnit konkrétní, malé oblasti složitých, velkých a škálovatelných aplikací.

Navrhování jemně odstupňovaných aplikací založených na mikroslužbách umožňuje průběžnou integraci a průběžné postupy doručování. Také urychluje dodávku nových funkcí do aplikace. Jemně odstupňované složení aplikací také umožňuje spustit a otestovat mikroslužeb v izolaci a vyvíjet je autonomně při zachování jasné smlouvy mezi nimi. Pokud nezměníte rozhraní nebo smlouvy, můžete změnit interní implementaci jakékoli mikroslužby nebo přidat nové funkce bez přerušení jiných mikroslužeb.

Následující jsou důležité aspekty, které umožňují úspěch při vstupu do výroby pomocí systému založeného na mikroslužbách:

- Monitorování a zdravotní kontroly služeb a infrastruktury.

- Škálovatelná infrastruktura pro služby (to znamená cloud a orchestrátory).

- Návrh zabezpečení a implementace na více úrovních: ověřování, autorizace, správa tajných kódů, zabezpečená komunikace atd.

- Rychlé dodání aplikace, obvykle s různými týmy se zaměřením na různé mikroslužby.

- DevOps a CI/CD postupy a infrastruktury.

Z nich jsou v této příručce zahrnuty nebo zavedeny pouze první tři. Poslední dva body, které souvisejí s životním cyklem aplikací, jsou zahrnuty v dalším [kontejnerizovaném životním cyklu aplikací Dockeru s](https://aka.ms/dockerlifecycleebook) e-knihou Microsoft Platform and Tools.

## <a name="additional-resources"></a>Další zdroje

- **Mark Russinovich. Mikroslužby: Revoluce aplikací poháněná cloudem** \
  <https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/>

- **Martin Fowler. Mikroslužeb** \
  <https://www.martinfowler.com/articles/microservices.html>

- **Martin Fowler. Předpoklady mikroslužeb** \
  <https://martinfowler.com/bliki/MicroservicePrerequisites.html>

- **Jimmy Nilsson. Chunk Cloud Computing** \
  <https://www.infoq.com/articles/CCC-Jimmy-Nilsson>

- **Cesar de la Torre. Kontejnerizovaný životní cyklus aplikací Dockeru s platformou Microsoft Platform and Tools** (e-kniha ke stažení) \
  <https://aka.ms/dockerlifecycleebook>

>[!div class="step-by-step"]
>[Předchozí](service-oriented-architecture.md)
>[další](data-sovereignty-per-microservice.md)

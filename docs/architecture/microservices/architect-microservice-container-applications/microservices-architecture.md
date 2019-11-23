---
title: Architektura mikroslužeb
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | zobrazení architektury mikroslužeb 30,000 metrů.
ms.date: 09/20/2018
ms.openlocfilehash: d1c58d218be9e5f8c0ae8ae732f9bdd06674a2c2
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834388"
---
# <a name="microservices-architecture"></a>Architektura mikroslužeb

Jak název naznačuje, architektura mikroslužeb je přístup k vytvoření serverové aplikace jako sady malých služeb. To znamená, že architektura mikroslužeb se hlavně orientuje na back-end, i když je tento přístup také používán pro front-end. Každá služba se spouští ve vlastním procesu a komunikuje s ostatními procesy pomocí protokolů, jako jsou HTTP/HTTPS, WebSockets nebo [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Každá mikroslužba implementuje určitou ucelenou nebo podnikovou možnost v rámci určité hranice kontextu a každá z nich musí být vyvinutá samostatně a dá se nasadit nezávisle. Nakonec by každá mikroslužba měla vlastnit svůj související doménový datový model a doménovou logiku (na základě suverenity a decentralizované správy dat) a může být založená na různých technologiích úložiště dat (SQL, NoSQL) a různých programovacích jazycích.

Jakou velikost by měla mikroslužba? Při vývoji mikroslužeb by velikost neměla být důležitým bodem. Místo toho by měl být důležitým bodem vytvoření volně propojených služeb, takže máte samostatnou autonomii vývoje, nasazení a škálování pro každou službu. Samozřejmě při identifikaci a návrhu mikroslužeb byste se měli pokusit, aby byly co nejmenší, dokud nebudete mít příliš mnoho přímých závislostí s ostatními mikroslužbami. Důležitější než velikost mikroslužeb je interní soudržnosti, kterou musí mít, a její nezávislost z jiných služeb.

Proč architektura mikroslužeb? V krátké době poskytuje dlouhodobou flexibilitu. Mikroslužby umožňují lepší udržovatelnost v komplexních, rozsáhlých a vysoce škálovatelných systémech tím, že vám umožní vytvářet aplikace založené na řadě nezávisle nasazených služeb, které mají každý z nich podrobně a autonomní životní cyklus.

S další výhodou je možné mikroslužby škálovat nezávisle. Místo toho, abyste měli jednu monolitické aplikaci, kterou musíte škálovat jako jednotku, můžete místo toho škálovat konkrétní mikroslužby. Tímto způsobem můžete škálovat pouze funkční oblast, která vyžaduje vyšší výpočetní výkon nebo šířku pásma sítě pro podporu požadavků, nikoli škálovat jiné oblasti aplikace, které nemusejí být škálované. To znamená úspory nákladů, protože potřebujete méně hardwaru.

![Diagram rozdílů mezi dvěma metodami nasazení.](./media/microservices-architecture/monolith-deployment-vs-microservice-approach.png)

**Obrázek 4-6**. Monolitické nasazení versus přístup k mikroslužbám

Jak ukazuje obrázek 4-6, v tradičním přístupu monolitické se aplikace škáluje pomocí klonování celé aplikace na několika serverech/virtuálních počítačích. V přístupu k mikroslužbám jsou funkce oddělené v menších službách, takže každá služba se může škálovat nezávisle. Přístup k mikroslužbám umožňuje agilní změny a rychlé opakování každé mikroslužby, protože můžete změnit konkrétní, malé oblasti komplexních, rozsáhlých a škálovatelných aplikací.

Architektově odstupňované aplikace založené na mikroslužbách umožňují průběžnou integraci a průběžné doručování. Zrychluje také doručování nových funkcí do aplikace. Jemně odstupňované sestavování aplikací umožňuje také spouštět a testovat mikroslužby v izolaci a vyvíjet je samostatně a přitom zachovat jasné smlouvy mezi nimi. Pokud neměníte rozhraní nebo kontrakty, můžete změnit interní implementaci jakékoli mikroslužby nebo přidat nové funkce, aniž by došlo k narušení dalších mikroslužeb.

V následujícím seznamu jsou důležité aspekty, jak umožnit v přechodu do provozu pomocí systému založeného na mikroslužbách:

- Monitorování a kontrola stavu služeb a infrastruktury.

- Škálovatelná infrastruktura pro služby (tj. Cloud a orchestration).

- Návrh a implementace zabezpečení na více úrovních: ověřování, autorizace, Správa tajných kódů, zabezpečená komunikace atd.

- Rychlé doručování aplikací, obvykle s různými týmy zaměřenými na různé mikroslužby.

- Postupy a infrastruktura pro DevOps a CI/CD

Z těchto kroků se v této příručce vztahují nebo zavádějí jenom první tři. Poslední dva body, které se vztahují k životnímu cyklu aplikace, jsou pokryty dodatečným [životním cyklem aplikace Docker s využitím Microsoft Platform a nástrojů](https://aka.ms/dockerlifecycleebook) .

## <a name="additional-resources"></a>Další materiály a zdroje informací

- **Označte Russinovich. Mikroslužby: aplikace s revoluce, kterou Cloud \ využívá**
  <https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/>

- **Martin Fowlera. \ mikroslužeb**
  <https://www.martinfowler.com/articles/microservices.html>

- **Martin Fowlera. Předpoklady pro mikroslužby** \
  <https://martinfowler.com/bliki/MicroservicePrerequisites.html>

- **Jimmy Nilsson. \ cloud computingu bloků dat**
  <https://www.infoq.com/articles/CCC-Jimmy-Nilsson>

- **Cesar de la Torre. Kontejnerový životní cyklus aplikace Docker s platformou a nástroji Microsoftu** (elektronická kniha ke stažení) \
  <https://aka.ms/dockerlifecycleebook>

>[!div class="step-by-step"]
>[Předchozí](service-oriented-architecture.md)
>[Další](data-sovereignty-per-microservice.md)

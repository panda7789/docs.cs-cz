---
title: "Architektura Mikroslužeb"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Architektura Mikroslužeb"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 453f8a22157eee9601f2586d49d872d90634bb61
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="microservices-architecture"></a>Architektura Mikroslužeb

Jak již název napovídá, architektura mikroslužeb je přístup k vytvoření aplikace serveru jako sada malé služeb. Každá služba běží ve svém vlastním procesu a komunikuje s dalšími procesy pomocí protokolů, jako je například HTTP nebo HTTPS, Websocket, nebo [AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol). Každý mikroslužbu implementuje určitou začátku do konce doménu nebo obchodní schopností v určité hranici kontextu a každý musí být vyvinutá samostatně a možno nasadit nezávisle. Nakonec musí každý mikroslužbu vlastní jeho související domény datový model a logiku domény (suverenity a správa decentralizované dat) na základě různých datových technologií úložiště (SQL, NoSQL) a různé programovací jazyky.

Jaké velikost by měla být mikroslužbu? Při vývoji mikroslužbu, velikost by neměl být důležité. Důležité místo toho by měla být k vytvoření volně doplněná služby, abyste získali samostatnost vývoj, nasazení a škálování pro každou službu. Samozřejmě pokud určíte a navrhování mikroslužeb, můžete opakovat tak, aby byly co nejmenší, dokud jste příliš mnoho přímé závislosti s další mikroslužeb. Důležitější než je velikost mikroslužbu vnitřní soudržnost, které musí mít a jeho nezávislost z jiných služeb.

Proč architektura mikroslužeb? Stručně řečeno poskytuje dlouhodobé flexibility. Mikroslužeb povolit lepší udržovatelnosti v systémech komplexní, velký a vysoce škálovatelné umožňují vytvářet aplikace založené na mnoho nezávisle nasadit služby nichž každá má granulární a autonomní životní cykly.

Další výhodou je mikroslužeb můžete škálovat nezávisle. Místo nutnosti jednu monolitický aplikaci, která musí horizontální navýšení kapacity jako jednotku, můžete místo toho škálovat konkrétní mikroslužeb. Tímto způsobem je možné škálovat právě funkční oblast, která potřebuje další zpracování napájení nebo síťové šířky pásma pro podporu poptávky, nikoli škálování jiných oblastí aplikace, které nemusí být změněna. To znamená úsporu nákladů, protože potřebujete méně hardwaru.

![](./media/image6.png)

**Obrázek 4 až 6**. Monolitický nasazení a mikroslužeb přístup

Jak ukazuje obrázek 4 až 6, mikroslužeb přístup umožňuje agilní změny a rychlé iteraci každý mikroslužbu, protože můžete změnit konkrétní, malé oblasti komplexní, velký a škálovatelné aplikace.

Architektury podrobných aplikace založené na mikroslužeb umožňuje průběžnou integraci a postupy nastavené průběžné doručování. Také urychlí vytváření nových funkcí do aplikace. Podrobné složení aplikace také můžete spustit a otestovat mikroslužeb v izolaci a vyvíjí samostatně při zachování zrušte kontrakty mezi nimi. Tak dlouho, dokud nezměníte rozhraní nebo kontrakty, můžete změnit interní implementace žádné mikroslužbu nebo přidat další nové funkce, aniž by vás jiných mikroslužeb.

Důležité aspekty povolit úspěch v přejdete do ostrého provozu je-li systém mikroslužeb jsou následující:

-   Kontroluje stav a monitorování služeb a infrastruktury.

-   Škálovatelné infrastruktury pro služby (to znamená, cloudu a orchestrators).

-   Zabezpečení návrhu a implementace na více úrovních: ověřování, autorizace, správu tajné klíče, zabezpečenou komunikaci, atd.

-   Doručení rychlé aplikace, obvykle s různými týmy zaměřené na různých mikroslužeb.

-   Postupy DevOps a CI/CD a infrastruktury.

Z těchto jsou pouze první tři zahrnutých nebo byla zavedená v této příručce. Poslední dva body, které se vztahují k životního cyklu aplikací, jsou popsané v další [Kontejnerizované Docker cyklu aplikací s Microsoft platforma a nástroje](https://aka.ms/dockerlifecycleebook) elektronických knih.

## <a name="additional-resources"></a>Další zdroje

-   **Označit Russinovichem. Mikroslužeb: Aplikaci revolution používá technologii cloudu**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)

-   **Martin Fowler. Mikroslužeb**
    [*http://www.martinfowler.com/articles/microservices.html*](http://www.martinfowler.com/articles/microservices.html)

-   **Martin Fowler. Mikroslužbu požadavky**
    [*http://martinfowler.com/bliki/MicroservicePrerequisites.html*](http://martinfowler.com/bliki/MicroservicePrerequisites.html)

-   **Jimmy Nilsson. Bloku dat Cloud Computing**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)

-   **Cesaru členka Torre. Kontejnerizované Docker životního cyklu aplikací s Microsoft platforma a nástroje** (ke stažení elektronická kniha) [ *https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)




>[!div class="step-by-step"]
[Předchozí] (service-oriented-architecture.md) [Další] (data-sovereignty-per-microservice.md)

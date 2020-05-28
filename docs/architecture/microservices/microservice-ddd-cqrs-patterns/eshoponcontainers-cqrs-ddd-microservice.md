---
title: Použití přístupů CQRS a CQS v mikroslužbě DDD v aplikaci eShopOnContainers
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Pochopení způsobu implementace CQRS při řazení mikroslužeb v eShopOnContainers.
ms.date: 03/03/2020
ms.openlocfilehash: 0fd38a93a1056cda4abd2f9f89ee9efc626985c8
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144276"
---
# <a name="apply-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>Použití CQRS a CQS přístupů v mikroslužbě DDD v eShopOnContainers

Návrh mikroslužby pro řazení v referenční aplikaci eShopOnContainers je založen na zásadách CQRS. Používá ale nejjednodušší přístup, který právě odděluje dotazy z příkazů a používá stejnou databázi pro obě akce.

Podstatou těchto vzorů a důležitého bodu je, že dotazy jsou idempotentní: bez ohledu na to, kolikrát se systém dotazuje, se stav tohoto systému nezmění. Jinými slovy, dotazy mají volné vedlejší účinky.

Proto můžete použít jiný datový model "čtení", než je transakční logika "zápisy" do doménového modelu, přestože řazení mikroslužeb používá stejnou databázi. Proto jde o zjednodušený přístup k CQRS.

Na druhé straně příkazy, které aktivují transakce a aktualizace dat, mění stav v systému. V případě příkazů musíte být opatrní při práci se složitou složitostí a neustále se měnícími obchodními pravidly. Tady je místo, kde se mají lépe modelovat systém s použitím DDD.

Vzory DDD uvedené v této příručce by se neměly použít univerzálním způsobem. Zavádějí na návrh omezení. Tato omezení poskytují výhody, jako je vyšší kvalita v čase, zejména příkazy a jiný kód, který mění stav systému. Tato omezení však přidávají složitost s méně výhodami pro čtení a dotazování dat.

Jedním z těchto vzorů je agregovaný vzor, který prověříme v dalších částech. V rámci agregovaného vzoru se v důsledku relace v doméně považovat mnoho doménových objektů za jednu jednotku. V dotazech nesmíte vždycky získat výhody z tohoto vzoru. může zvýšit složitost logiky dotazů. Pro dotazy jen pro čtení nezískáte výhody zpracování více objektů jako jedné agregace. Získáte pouze složitost.

Jak je znázorněno na obrázku 7-2 v předchozí části, tato příručka navrhuje používání vzorů DDD pouze v oblasti transakčního a aktualizovaného prostředí mikroslužeb (to znamená, jak jsou spouštěny pomocí příkazů). Dotazy mohou sledovat jednodušší přístup a měly by být odděleny od příkazů po CQRS přístupu.

Pro implementaci "na straně" dotazů si můžete vybrat z mnoha přístupů, od celého plnohodnotnou ORM, jako je EF Core, projekce s automapper, uložené procedury, zobrazení, materializovaná zobrazení nebo mikroorm.

V této příručce a v eShopOnContainers (konkrétně pro objednávání mikroslužeb) jsme zvolili implementaci přímých dotazů pomocí mikroorm, jako je [dapperem](https://github.com/StackExchange/dapper-dot-net). To vám umožní implementovat jakýkoli dotaz založený na příkazech SQL a získat tak nejlepší výkon díky světlému rozhraní s velmi nízkou režií.

Všimněte si, že když použijete tento přístup, všechny aktualizace modelu, které mají vliv na způsob, jakým jsou entity trvale uložené v databázi SQL Database, potřebují také samostatné aktualizace pro dotazy SQL, které používá Dapperem nebo jakékoli jiné samostatné metody (jiné než EF) k dotazování.

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>Vzory CQRS a DDD nejsou architektury nejvyšší úrovně.

Je důležité pochopit, že CQRS a většinu vzorů DDD (například DDD vrstvy nebo doménový model s agregacemi) nejsou strukturální styly, ale jenom vzory architektury. Příklady stylů architektury jsou mikroslužby, SOA a architektura řízená událostmi (EDA). Popisují systém mnoha součástí, například mnoho mikroslužeb. Vzory CQRS a DDD popisují něco v jednom systému nebo komponentě; v tomto případě je to něco uvnitř mikroslužby.

Různé ohraničené kontexty (BCs) budou používat různé vzory. Mají různé zodpovědnosti a to vede k různým řešením. Je nutné zdůraznit, že vynucení stejného vzoru všude vede k selhání. Nepoužívejte vzory CQRS a DDD všude. Mnohé subsystémy, BCs nebo mikroslužby jsou jednodušší a je možné je snadno implementovat pomocí jednoduchých služeb CRUD nebo pomocí jiného přístupu.

Existuje pouze jedna architektura aplikace: architektura systému nebo komplexní aplikace, kterou navrhujete (například architektura mikroslužeb). Návrh každého vázaného kontextu nebo mikroslužby v této aplikaci ale odráží vlastní kompromisy a interní rozhodnutí o návrhu na úrovni schémat architektury. Nepokoušejte se použít stejné vzory architektury jako CQRS nebo DDD všude.

### <a name="additional-resources"></a>Další zdroje

- **Martin Fowlera. CQRS** \
  <https://martinfowler.com/bliki/CQRS.html>

- **Greg Young. Dokumenty CQRS** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf>

- **UDI Dahan. Vyjasněné CQRS** \
  <https://udidahan.com/2009/12/09/clarified-cqrs/>

>[!div class="step-by-step"]
>[Předchozí](apply-simplified-microservice-cqrs-ddd-patterns.md) 
> [Další](cqrs-microservice-reads.md)

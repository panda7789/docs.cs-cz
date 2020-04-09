---
title: Použití přístupů CQRS a CQS v mikroslužbě DDD v aplikaci eShopOnContainers
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Pochopit způsob CQRS je implementována v objednávání mikroslužby v eShopOnContainers.
ms.date: 03/03/2020
ms.openlocfilehash: eda0ee374b41a81811e92e2829b10dc8515e0ccd
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988489"
---
# <a name="apply-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>Použití přístupů CQRS a CQS v mikroslužbě DDD v eShopOnContainers

Návrh objednávání mikroslužby v referenční aplikaci eShopOnContainers je založen na principech CQRS. Používá však nejjednodušší přístup, který je pouze oddělení dotazů z příkazů a použití stejné databáze pro obě akce.

Podstatou těchto vzorů, a důležitý bod zde, je, že dotazy jsou idempotentní: bez ohledu na to, kolikrát dotaz systému, stav tohoto systému se nezmění. Jinými slovy, dotazy jsou bez vedlejších účinků.

Proto můžete použít jiný datový model "čtení" než transakční logika "zapíše" model domény, i když řazení mikroslužeb používají stejnou databázi. Jedná se tedy o zjednodušený přístup CQRS.

Na druhou stranu příkazy, které aktivují transakce a aktualizace dat, mění stav v systému. S příkazy, musíte být opatrní při řešení složitosti a neustále se měnící obchodní pravidla. To je místo, kde chcete použít DDD techniky mít lepší modelovaný systém.

Vzory DDD uvedené v této příručce by neměly být aplikovány univerzálně. Zavádějí omezení vašeho návrhu. Tato omezení poskytují výhody, jako je vyšší kvalita v průběhu času, zejména v příkazech a další kód, který upravuje stav systému. Tato omezení však přidat složitost s menšími výhodami pro čtení a dotazování dat.

Jedním z takových vzorů je agregační vzor, který zkoumáme více v pozdějších částech. Stručně řečeno, v agregační vzor považovat mnoho objektů domény jako jedna jednotka v důsledku jejich vztahu v doméně. Nemusí vždy získat výhody z tohoto vzoru v dotazech; může zvýšit složitost logiky dotazu. Pro dotazy jen pro čtení nezískáte výhody považovat za více objektů za jeden Agregace. Dostanete jen složitost.

Jak je znázorněno na obrázku 7-2 v předchozí části, tato příručka navrhuje použití vzorů DDD pouze v oblasti transakční/aktualizace mikroslužeb (to znamená, jak je spuštěno příkazy). Dotazy mohou postupovat podle jednodušší přístup a by měly být odděleny od příkazů, podle přístupu CQRS.

Pro implementaci "dotazů strana", můžete si vybrat mezi mnoha přístupy, z vašeho full-foukané ORM jako EF Core, AutoMapper projekce, uložené procedury, zobrazení, materialized zobrazení nebo mikro ORM.

V této příručce a v eShopOnContainers (konkrétně objednávání mikroslužby) jsme se rozhodli implementovat přímé dotazy pomocí micro ORM jako [Dapper](https://github.com/StackExchange/dapper-dot-net). To umožňuje implementovat libovolný dotaz založený na příkazech SQL, abyste získali nejlepší výkon díky světelnému rámci s velmi malou režií.

Všimněte si, že při použití tohoto přístupu všechny aktualizace modelu, které mají vliv na způsob, jakým jsou entity trvalé do databáze SQL také potřebovat samostatné aktualizace sql dotazů používaných Dapper nebo jiné samostatné (non-EF) přístupy k dotazování.

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>Vzory CQRS a DDD nejsou architektury nejvyšší úrovně

Je důležité si uvědomit, že CQRS a většina vzorů DDD (jako vrstvy DDD nebo model domény s agregacemi) nejsou architektonické styly, ale pouze vzory architektury. Mikroslužeb, SOA a architektura řízená událostmi (EDA) jsou příklady architektonických stylů. Popisují systém mnoha součástí, jako je například mnoho mikroslužeb. Vzory CQRS a DDD popisují něco uvnitř jednoho systému nebo součásti; v tomto případě něco uvnitř mikroslužby.

Různé ohraničené kontexty (BCs) bude využívat různé vzory. Mají různé povinnosti, a to vede k různým řešením. Stojí za to zdůraznit, že vynucení stejného vzoru všude vede k neúspěchu. Nepoužívejte vzory CQRS a DDD všude. Mnoho subsystémů, bc nebo mikroslužeb jsou jednodušší a lze implementovat snadněji pomocí jednoduchých služeb CRUD nebo pomocí jiného přístupu.

Existuje pouze jedna architektura aplikace: architektura systému nebo end-to-end aplikace, kterou navrhujete (například architektura mikroslužeb). Návrh každého ohraničeného kontextu nebo mikroslužby v rámci této aplikace však odráží jeho vlastní kompromisy a interní rozhodnutí o návrhu na úrovni vzorů architektury. Nepokoušejte se použít stejné architektonické vzory jako CQRS nebo DDD všude.

### <a name="additional-resources"></a>Další zdroje

- **Martin Fowler. CQRS** \
  <https://martinfowler.com/bliki/CQRS.html>

- **Greg Young. Dokumenty CQRS** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf>

- **Udi Dahan. Vyjasněné CQRS** \
  <http://udidahan.com/2009/12/09/clarified-cqrs/>

>[!div class="step-by-step"]
>[Předchozí](apply-simplified-microservice-cqrs-ddd-patterns.md)
>[další](cqrs-microservice-reads.md)

---
title: Použití přístupů CQRS a CQS v mikroslužbě DDD v aplikaci eShopOnContainers
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Pochopte způsob, jakým CQRS je implementována v pořadí mikroslužeb v aplikaci eShopOnContainers.
ms.date: 10/08/2018
ms.openlocfilehash: 0380e759595e8a159e89f858a5ced4dacfa4e9b4
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65875913"
---
# <a name="apply-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>Použít přístupy CQRS a CQS v mikroslužbě DDD v aplikaci eShopOnContainers

Návrh pořadí mikroslužeb v aplikaci eShopOnContainers referenční aplikace je založen na modelu CQRS zásady. Ale používá nejjednodušším přístupem, která je právě oddělení dotazů z příkazů a používat stejnou databázi pro obě akce.

Podstatu tyto vzory a tady důležitý bod je, že dotazy jsou idempotentní: bez ohledu na to, kolikrát dotaz systém, nedojde ke změně stavu systému. Jinými slovy dotazy jsou vedlejší efekt zdarma.

Proto můžete použít různé "čtení" datový model než transakční logiky "zapíše" model domény, přestože pořadí mikroslužeb používají tutéž databázi. Proto je zjednodušený přístup modelu CQRS.

Příkazy, které aktivují transakce a aktualizace dat, na druhé straně změnit stav systému. Pomocí příkazů, potřebujete mít na paměti při zabývají složitost a neustále se měnící obchodní pravidla. Toto je místo použití techniky DDD lépe modelové systém.

Univerzálně neměla používat vzorů DDD v této příručce. Ale zavádí omezení návrhu. Ta omezení poskytují výhody, jako je například vyšší kvality časem, zejména v příkazech a jiný kód, který upravuje stav systému. Ta omezení však přidat složitost s menším počtem výhody pro čtení a dotazování na data.

Jeden takový vzor je agregační vzor, který více prozkoumáme v dalších částech. Stručně řečeno agregační vzoru je považovat za mnoho objektů domény jednu jednotku v důsledku jejich vztahu v doméně. Nemusí vždy získat výhody tohoto modelu v dotazech; můžete zvýšit složitost logiku dotazu. Za dotazy na jen pro čtení nelze získat výhody zpracuje více objektů jako jedné agregace. Můžete získat pouze složitost.

Jak je znázorněno v obrázku 7-2, tento průvodce navrhuje pomocí vzorů DDD pouze v oblasti transakční/aktualizace vašeho mikroslužeb (jak aktivované příkazy). Dotazy můžete postupovat podle jednodušší přístup a by měla být oddělena od příkazy přístupu CQRS.

Pro implementaci "strana dotazy", můžete zvolit řada přístupů, z vaší kompletního ORM, jako je EF Core, AutoMapper projekce, uložených procedur, zobrazení, materializovaná zobrazení nebo micro ORM.

V tomto průvodci a v aplikaci eShopOnContainers (konkrétně pořadí mikroslužeb) jsme zvolili k implementaci přímé dotazy, které používají micro ORM jako [Dapperem](https://github.com/StackExchange/dapper-dot-net). To umožňuje implementovat jakýkoli dotaz na základě příkazů SQL pro co nejlepšího výkonu díky světla framework s velmi nízkou režií.

Všimněte si, že při použití tohoto přístupu všechny aktualizace modelu, které ovlivňují, jak jsou trvalé entity do služby SQL database také potřebovat samostatné aktualizace dotazy SQL, které jsou používány Dapperem nebo jakékoli další samostatné přístupy (bez EF) k dotazování.

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>Vzorů CQRS a DDD nejsou nejvyšší úrovně architektury

Je důležité pochopit, že CQRS a většina vzorů DDD (např. vrstvy DDD nebo doménový model se agregace) nejsou styly architektury, ale pouze vzory architektury. Mikroslužby, SOA a architektury řízené událostmi (EDA) jsou příkladem styly architektury. Popisují systém řadu součástí, jako je například mnoha mikroslužeb. Popište něco vzorů CQRS a DDD uvnitř jediného systému nebo component; v tomto případě něco v mikroslužbě.

Různých ohraničených kontextech (BCs) bude využívat různé vzorce. Mají rozdílné povinnosti a, který vede k různá řešení. Je vhodné, kdy se klade důraz, který vynucuje se stejným vzorem, který everywhere dojde k selhání. Všude, kde nepoužívejte vzorů CQRS a DDD. Mnoho subsystémy, BCs nebo mikroslužeb jsou jednodušší a je možné implementovat snadněji pomocí jednoduchého CRUD služby nebo jiný přístup.

Existuje pouze jedna aplikace architektury: architektura systému nebo začátku do konce aplikaci při návrhu (například architektuře mikroslužeb). Ale návrhu každé ohraničená kontextu nebo mikroslužbách v rámci této aplikace odráží vlastní kompromisy a rozhodnutí o návrhu interní úrovni vzory architektury. Nepokoušejte se použít stejné architektury vzorce jako CQRS a DDD všude.

### <a name="additional-resources"></a>Další zdroje

- **Martina Fowlera. CQRS** \
  <https://martinfowler.com/bliki/CQRS.html>

- **Grega Younga:. CQRS dokumentů** \
  <https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf>

- **Udi Dahan. Vyčištěné modelu CQRS** \
  <http://udidahan.com/2009/12/09/clarified-cqrs/>

>[!div class="step-by-step"]
>[Předchozí](apply-simplified-microservice-cqrs-ddd-patterns.md)
>[další](cqrs-microservice-reads.md)

---
title: Použití CQRS a CQS přístupů DDD mikroslužbu v eShopOnContainers
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Použití CQRS a CQS přístupů DDD mikroslužbu v eShopOnContainers
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: fa26aa86e09f7a5d390336e460fa0272f76e17a4
ms.sourcegitcommit: fc70fcb9c789b6a4aefcdace46f3643fd076450f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2018
ms.locfileid: "34805471"
---
# <a name="applying-cqrs-and-cqs-approaches-in-a-ddd-microservice-in-eshoponcontainers"></a>Použití CQRS a CQS přístupů DDD mikroslužbu v eShopOnContainers

Návrh řazení mikroslužbu v eShopOnContainers referenční aplikace je založena na CQRS zásady. Ale používá nejjednodušší přístup, který je právě oddělení dotazy z příkazů a pomocí stejné databáze pro obě akce.

Podstatu tyto vzorce a zde bodem důležité je, že dotazy jsou idempotent: bez ohledu na to, kolikrát dotaz systém, nedojde ke změně stavu tohoto systému. Můžete i použít datový model různých "čtení" než logice transakcí "zapíše" modelu domény, i když řazení mikroslužeb používá stejnou databázi. Toto je proto jednodušší přístup CQRS.

Na druhé straně příkazy, které aktivují transakce a aktualizace dat, změňte stav v systému. Pomocí příkazů, budete muset pečlivě, kdy se zabývají složitost a proměnlivých obchodní pravidla. To je případě, kdy chcete použít techniky DDD tak, aby měl lépe Modelovaný systému.

Vzory DDD uvádíme v této příručce by neměl být všeobecně aplikuje. Ale vést k omezení návrhu. Tato omezení zadejte výhod, třeba vyšší kvality v čase, zejména v příkazy a jiný kód, který upravuje stav systému. Ale tyto omezení přidání složitosti s méně výhody pro čtení a dotazování na data.

Jeden takový vzor je agregační vzor, který nám prozkoumat více v pozdějších částech. Stručně řečeno v agregační vzoru je považovat za mnoho objektů domény na jednu jednotku v důsledku jejich vztahu v doméně. Nemusí vždy získat výhody z tohoto vzoru v dotazech; ho může zvýšit složitosti logiku dotazu. Pro dotazy na jen pro čtení není získat výhody práce více objektů jako jeden agregace. Zobrazí pouze na složitost.

Jak je znázorněno na obrázku 9-2, tento průvodce navrhuje pomocí vzorce DDD pouze v oblasti transakční/aktualizace vašeho mikroslužbu (jak aktivovány příkazy). Dotazy můžete postupovat podle jednodušší a musí být oddělené příkazy pro následující CQRS přístup.

Pro implementaci "dotazy straně", můžete zvolit řada přístupů, z vaší plnohodnotném ORM jako základní EF, AutoMapper projekce, uložené procedury, zobrazení, Vyhodnocená zobrazení nebo malých ORM.

V této příručce a eShopOnContainers (konkrétně řazení mikroslužbu) jsme zvolili k implementaci přímých dotazů pomocí micro ORM jako [Dapper](https://github.com/StackExchange/dapper-dot-net). Díky tomu můžete implementovat jakýkoli dotaz na příkazy SQL pro získání nejlepší výkon, díky světla rozhraní s minimální režií na základě.

Všimněte si, že pokud použijete tuto metodu, aktualizace modelu, s dopadem na tom, jak jsou trvalé entity k databázi SQL také vyžadují samostatné aktualizace dotazy SQL, které jsou používány Dapper nebo jakékoli jiné samostatné (bez EF) přístupy k dotazování.

## <a name="cqrs-and-ddd-patterns-are-not-top-level-architectures"></a>CQRS a DDD vzory nejsou nejvyšší úrovně architektury

Je důležité si uvědomit, že CQRS a většina DDD vzory (například vrstvy DDD nebo modelu domény s agregace) nejsou architektury styly, ale pouze architektura vzory. Mikroslužeb, SOA a architektura založeného na událostech (Automatizace elektronického designu) jsou příklady architektury stylů. Popisují systému celá řada komponent, jako je například mnoho mikroslužeb. Vzory CQRS a DDD popisují něco v jednom systému nebo komponenty; v tomto případě něco uvnitř mikroslužby.

Různých kontextů ohraničenou (BCs) se využívají různé vzorce. Mají různé odpovědnosti a který vede k jiné řešení. Je vhodné zdůraznění, vynucení stejný vzor, který everywhere dojde k selhání. Všude, kde nepoužívejte CQRS a DDD vzory. Mnoho subsystémy, BCs nebo mikroslužeb jsou jednodušší a může být implementováno snadněji pomocí jednoduché CRUD služby nebo pomocí další přístup.

Existuje jenom jedna aplikace architektura: architektura systému nebo začátku do konce aplikace navrhujete (například architektuře mikroslužeb). V návrhu každé ohraničenou kontext nebo mikroslužbu v rámci této aplikace však odráží vlastní kompromisy a rozhodnutí o návrhu interní úrovni vzory architektura. Nepokoušejte se použít stejné architektury vzory jako CQRS nebo DDD everywhere.

####  <a name="additional-resources"></a>Další zdroje

-   **Martin Fowler. CQRS**
    [*https://martinfowler.com/bliki/CQRS.html*](https://martinfowler.com/bliki/CQRS.html)

-   **Gregu Young. CQS vs. CQRS**
    [*http://codebetter.com/gregyoung/2009/08/13/command-query-separation/*](http://codebetter.com/gregyoung/2009/08/13/command-query-separation/)

-   **Gregu Young. CQRS dokumenty**
    [*https://cqrs.files.wordpress.com/2010/11/cqrs\_documents.pdf*](https://cqrs.files.wordpress.com/2010/11/cqrs_documents.pdf)

-   **Gregu Young. CQRS, úkolů na základě uživatelská rozhraní a zdroje událostí**
    [*http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/*](http://codebetter.com/gregyoung/2010/02/16/cqrs-task-based-uis-event-sourcing-agh/)

-   **Udi Dahan. Vyčištěné CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **CQRS**
    [*http://udidahan.com/2009/12/09/clarified-cqrs/*](http://udidahan.com/2009/12/09/clarified-cqrs/)

-   **Událost Sourcing (ES)**
    [*http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/*](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/)


>[!div class="step-by-step"]
[Předchozí] (apply-simplified-microservice-cqrs-ddd-patterns.md) [Další] (cqrs reads.md mikroslužbu)

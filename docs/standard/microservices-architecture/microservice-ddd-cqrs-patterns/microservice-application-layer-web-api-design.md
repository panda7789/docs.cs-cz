---
title: Návrh aplikační vrstvy mikroslužby a webové rozhraní API
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Návrh aplikační vrstvy mikroslužby a webové rozhraní API
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: a8c03f99accf75f60fe6c21a0f09f304214b4a6c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50194097"
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a>Návrh aplikační vrstvy mikroslužby a webové rozhraní API

## <a name="using-solid-principles-and-dependency-injection"></a>Pomocí zásady PEVNÉ a injektáž závislostí

PLNÉ zásady jsou kritické technik, který se má použít v jakékoli moderní i klíčové podnikové aplikace, třeba vývoj mikroslužbě pomocí vzorů DDD. PLNÉ je zkratka této skupiny pěti základními zásadami:

-   Jednotné zásady odpovědnosti

-   Princip otevřený/uzavřený

-   Zásady Liskov nahrazení

-   Princip oddělení rozhraní

-   Princip inverzi závislostí

Více o způsob návrhu aplikace nebo interní vrstvy mikroslužby a oddělení závislosti mezi nimi je PLNÝ. To není v relaci k doméně, ale technického návrhu vaší aplikace. Principu poslední principu inverzi závislost umožňuje oddělit vrstvě infrastruktury od zbytku vrstvy, která umožňuje lépe samostatné implementace DDD vrstev.

Dependency Injection (DI) je jedním ze způsobů implementace principu závislost inverzi. Jde o techniku pro dosažení volné párování mezi objekty a jejich závislosti. Místo přímo vytvoření instance spolupracovníci, nebo pomocí statické odkazy, jsou objekty, které třída potřebuje, aby jeho činnostem poskytnuté (nebo "vloženy do") třídy. Nejčastěji se třídy deklarují svoje závislosti přes jejich konstruktoru, což jim umožní postupovat podle principu explicitní závislosti. DI je obvykle založena na konkrétní kontejnery řízení IOC (Inversion). ASP.NET Core nabízí jednoduchý kontejner IoC integrované, ale můžete použít také oblíbené kontejner IoC, třeba Autofac nebo Ninject.

Pomocí následujících SOLID zásady, tříd bodech přirozeně malé, skvěle a snadno otestované. Ale jak můžete víte, pokud příliš velký počet závislostí se vloží do vašich tříd? Pokud používáte DI pomocí konstruktoru, bude snadno zjistit, který jen pohlédnutím na počet parametrů pro váš konstruktor. Pokud je příliš velký počet závislostí, je obvykle znak ( [kódu pach](https://deviq.com/code-smells/)), že se snaží docílit příliš mnoho vaší třídy a pravděpodobně porušuje Princip jednotnou zodpovědnost.

By to obnášelo jiného průvodce k podrobně zahrnovat PLNÝ. Proto tato příručka vyžaduje, abyste nemají pouze minimální informace o těchto tématech.

#### <a name="additional-resources"></a>Další zdroje

-   **UCELENÝ: Principy základní OOP**
    [*https://deviq.com/solid/*](https://deviq.com/solid/%20)

-   **Inverze – kontejnery ovládacích prvků a vzor injektáž závislostí**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)

-   **Steve Smith. Je nový spojovací**
    [*https://ardalis.com/new-is-glue*](https://ardalis.com/new-is-glue)


>[!div class="step-by-step"]
[Předchozí](nosql-database-persistence-infrastructure.md)
[další](microservice-application-layer-implementation-web-api.md)

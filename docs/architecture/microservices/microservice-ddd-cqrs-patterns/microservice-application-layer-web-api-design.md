---
title: Návrh aplikační vrstvy a webového rozhraní API mikroslužby
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Stručně zmíněné základní zásady pro návrh vrstvy aplikace.
ms.date: 10/08/2018
ms.openlocfilehash: 3c3b9f74e76e01deafa1f97de5d3250d57716014
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70296738"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a>Návrh aplikační vrstvy a webového rozhraní API mikroslužeb

## <a name="use-solid-principles-and-dependency-injection"></a>Použití pevných principů a injektáže závislostí

ZÁKLADNÍ zásady představují klíčové techniky pro použití v jakékoli moderní a klíčové aplikaci, jako je například vývoj mikroslužeb se vzory DDD. SOLID je akronym, který seskupuje pět základních principů:

- Princip jedné zodpovědnosti

- Princip otevření/uzavření

- Liskov – princip nahrazení

- Princip oddělení rozhraní

- Princip inverze závislosti

SOLID je více informací o návrhu aplikace nebo vnitřních vrstev mikroslužeb a o vzájemných závislostech mezi nimi. Nesouvisí s doménou, ale s technickým návrhem aplikace. Konečný princip – princip inverze závislostí, umožňuje oddělit vrstvu infrastruktury od zbytku vrstev, což umožňuje lepší oddělit implementaci rozmístěných vrstev.

Vkládání závislostí (DI) je jeden způsob, jak implementovat princip inverze závislostí. Je to způsob, jak dosáhnout volného spojení mezi objekty a jejich závislostmi. Namísto přímého vytváření instancí spolupracovníků nebo použití statických odkazů (to znamená použití New...) objekty, které třída potřebuje k provedení svých akcí, jsou poskytovány třídě (nebo "vložené do") třídy. Nejčastěji třídy budou deklarovat své závislosti prostřednictvím jejich konstruktoru, což jim umožní dodržovat princip explicitní závislosti. Vkládání závislostí je obvykle založeno na konkrétních kontejnerech inverze ovládacích prvků (IoC). ASP.NET Core poskytuje jednoduchý integrovaný kontejner IoC, ale můžete použít i oblíbený IoC kontejner, jako je Autofac nebo Ninject.

Podle plných principů budou vaše třídy pravděpodobně přirozeně malé, dobře náročné a snadno testované. Ale jak zjistíte, jestli se do tříd vkládají příliš mnoho závislostí? Použijete-li parametr DI prostřednictvím konstruktoru, bude snadné ho detekovat pouze v případě, že se díváte na počet parametrů vašeho konstruktoru. Pokud existuje příliš mnoho závislostí, obvykle se jedná o znaménko ( [zápach kódu](https://deviq.com/code-smells/)), že se vaše třída pokouší provést příliš mnoho a je pravděpodobně porušena jedna zásada zodpovědnosti.

Mělo by to mít další průvodce, aby se podrobně kryl. Proto tato příručka vyžaduje, abyste měli jenom minimální znalosti těchto témat.

#### <a name="additional-resources"></a>Další materiály a zdroje informací

- **Solid: základní principy OOP** \
  <https://deviq.com/solid/>

- **Inverze řídicích kontejnerů a vzor pro vkládání závislostí** \
  <https://martinfowler.com/articles/injection.html>

- **Steve Smith. Nové je připevňování** \
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> [Předchozí](nosql-database-persistence-infrastructure.md)
> [Další](microservice-application-layer-implementation-web-api.md)

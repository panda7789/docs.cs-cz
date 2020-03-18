---
title: Návrh aplikační vrstvy a webového rozhraní API mikroslužby
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Stručná zmínka o principech SOLID pro návrh aplikační vrstvy.
ms.date: 10/08/2018
ms.openlocfilehash: 3c3b9f74e76e01deafa1f97de5d3250d57716014
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70296738"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a>Návrh aplikační vrstvy mikroslužeb a webového rozhraní API

## <a name="use-solid-principles-and-dependency-injection"></a>Použití principů SOLID a vkládání závislostí

Principy SOLID jsou kritické techniky, které mají být použity v jakékoli moderní a kritické aplikace, jako je například vývoj mikroslužeb se vzory DDD. SOLID je zkratka, která seskupuje pět základních principů:

- Zásada jednotné odpovědnosti

- Otevřený/uzavřený princip

- Liskovův substituční princip

- Princip segregace rozhraní

- Princip inverze závislostí

SOLID je více o tom, jak navrhnout vnitřní vrstvy aplikace nebo mikroslužeb a o oddělení závislostí mezi nimi. Nesouvisí s doménou, ale s technickým návrhem aplikace. Konečný princip, princip inverze závislostí, umožňuje oddělit vrstvu infrastruktury od ostatních vrstev, což umožňuje lepší oddělenou implementaci vrstev DDD.

Vkládání závislostí (DI) je jedním ze způsobů, jak implementovat princip inverze závislostí. Jedná se o techniku pro dosažení volné párování mezi objekty a jejich závislosti. Spíše než přímo vytváření konkretizovat spolupracovníky nebo pomocí statických odkazů (to znamená pomocí new...), objekty, které třída potřebuje k provedení své akce jsou k dispozici (nebo "vstřikuje do" třídy. Nejčastěji třídy deklarují své závislosti prostřednictvím svého konstruktoru, což jim umožňuje dodržovat zásadu explicitní závislosti. Vkládání závislostí je obvykle založena na konkrétní inverze řídicí (IoC) kontejnery. ASP.NET Core poskytuje jednoduchý vestavěný kontejner IoC, ale můžete také použít svůj oblíbený kontejner IoC, jako je Autofac nebo Ninject.

Dodržováním zásad SOLID budou vaše třídy přirozeně malé, dobře zapracované a snadno testovatelné. Ale jak můžete vědět, zda příliš mnoho závislostí jsou vstřikovány do vašich tříd? Pokud používáte DI prostřednictvím konstruktoru, bude snadné zjistit, že pouhým pohledem na počet parametrů pro konstruktoru. Pokud existuje příliš mnoho závislostí, je to obecně znaménko [(zápach kódu),](https://deviq.com/code-smells/)že vaše třída se snaží udělat příliš mnoho a pravděpodobně porušuje zásadu jedné odpovědnosti.

To by trvalo další průvodce na pokrytí SOLID v detailu. Proto tato příručka vyžaduje, abyste měli pouze minimální znalosti o těchto tématech.

#### <a name="additional-resources"></a>Další zdroje

- **SOLID: Základní principy OOP** \
  <https://deviq.com/solid/>

- **Inverze řídicích kontejnerů a vzor vkládání závislostí** \
  <https://martinfowler.com/articles/injection.html>

- **Steva Smithe. Novinou je lepidlo** \
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> [Předchozí](nosql-database-persistence-infrastructure.md)
> [další](microservice-application-layer-implementation-web-api.md)

---
title: Navrhování mikroslužbu aplikační vrstvu a webového rozhraní API
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Navrhování mikroslužbu aplikační vrstvu a webového rozhraní API
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 77e0556e4b6d9a22cf76a79ec86d744d9009a39f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a>Navrhování mikroslužbu aplikační vrstvu a webového rozhraní API

## <a name="using-solid-principles-and-dependency-injection"></a>Pomocí plnou principy a vkládání závislostí

PLNOU zásady jsou kritické techniky, který se má použít v jakékoli moderní a kritické aplikace, třeba vývoj mikroslužbu DDD vzory. PLNOU je zkratka z této skupiny pět základních zásad:

-   Jeden zásady odpovědnosti

-   Princip otevřený nebo zavřený

-   Zásady Liskov nahrazení

-   Princip oddělení rozhraní

-   Princip inverzi závislostí

UCELENÝ se více o při navrhování vaší aplikace nebo interní vrstvami mikroslužbu a oddělení závislosti mezi nimi. Nesouvisí se k doméně, ale technického návrhu aplikace. Poslední Princip Princip závislostí inverzi (DI) umožňuje oddělit vrstvě infrastruktury od zbytku vrstvy, která umožňuje lépe odpojeného implementace DDD vrstev.

DI je jedním ze způsobů k provedení zásady inverzi závislostí. Jde o techniku k dosažení volné párování mezi objekty a jejich závislosti. Ne přímo vytváření instancí spolupracovníci, nebo pomocí statické odkazy, jsou objekty, které potřebuje třídy za účelem provádění akcí poskytované (nebo "vloženy do") třída. Třídy bude nejčastěji deklarovat závislé prostřednictvím jejich konstruktoru, což jim umožní sledovat zásadu explicitní závislosti. DI většinou podle konkrétní kontejnery v inverzi z ovládacích prvků (IoC). ASP.NET Core poskytuje jednoduché předdefinované kontejner IoC, ale můžete použít také vaše oblíbené kontejner IoC jako Autofac nebo Ninject.

Pomocí následujících plnou zásady, vaše třídy bude jsou obvykle přirozeně malé, dobře započítané a snadno otestované. Ale jak můžete vy víte, pokud jsou probíhá příliš velký počet závislostí vloženy do vaší třídy? Pokud používáte DI pomocí konstruktoru, bude možné snadno zjistit, prohlížením právě počet parametrů pro vaše konstruktor. Pokud jsou moc velký počet závislostí, je obvykle znaménkem ( [code pach](http://deviq.com/code-smells/)), se pokouší o provedení příliš mnoho třídě a pravděpodobně porušuje zásady jeden odpovědnosti.

To bude trvat jiný průvodce tak, aby pokrývalo UCELENÝ podrobně. Tato příručka proto vyžaduje, abyste mají pouze minimální znalosti o těchto tématech.

#### <a name="additional-resources"></a>Další zdroje

-   **UCELENÝ: Principy základní mimoprocesová aplikace VOLÁNA**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)

-   **Inverze – kontejnery ovládacích prvků a vzoru vkládání závislostí**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)

-   **Steve Smith. Nové je pojidlem**
    [*https://ardalis.com/new-is-glue*](https://ardalis.com/new-is-glue)


>[!div class="step-by-step"]
[Předchozí] (nosql-database trvalost infrastructure.md) [Další] (microservice-application-layer-implementation-web-api.md)

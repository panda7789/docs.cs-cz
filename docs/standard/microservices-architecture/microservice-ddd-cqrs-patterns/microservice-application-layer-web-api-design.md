---
title: "Navrhování mikroslužbu aplikační vrstvu a webového rozhraní API"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Navrhování mikroslužbu aplikační vrstvu a webového rozhraní API"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: c166e0286d0769e24a6361037eb6c4694fb821ae
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a>Navrhování mikroslužbu aplikační vrstvu a webového rozhraní API

## <a name="using-solid-principles-and-dependency-injection"></a>Pomocí plnou principy a vkládání závislostí

PLNOU zásady jsou kritické techniky, který se má použít v jakékoli moderní a kritické aplikace, třeba vývoj mikroslužbu DDD vzory. PLNOU je zkratka z této skupiny pět základních zásad:

-   Jeden zásady odpovědnosti

-   Princip otevřený nebo zavřený

-   Zásady Liskov nahrazení

-   Princip inverzi oddělení

-   Princip inverzi závislostí

UCELENÝ se více o při navrhování vaší aplikace nebo interní vrstvami mikroslužbu a oddělení závislosti mezi nimi. Nesouvisí se k doméně, ale technického návrhu aplikace. Poslední Princip Princip závislostí inverzi (DI) umožňuje oddělit vrstvě infrastruktury od zbytku vrstvy, která umožňuje lépe odpojeného implementace DDD vrstev.

DI je jedním ze způsobů k provedení zásady inverzi závislostí. Jde o techniku k dosažení volné párování mezi objekty a jejich závislosti. Ne přímo vytváření instancí spolupracovníci, nebo pomocí statické odkazy, jsou objekty, které potřebuje třídy za účelem provádění akcí poskytované (nebo "vloženy do") třída. Třídy bude nejčastěji deklarovat závislé prostřednictvím jejich konstruktoru, což jim umožní sledovat zásadu explicitní závislosti. DI většinou podle konkrétní kontejnery v inverzi z ovládacích prvků (IoC). ASP.NET Core poskytuje jednoduché předdefinované kontejner IoC, ale můžete použít také vaše oblíbené kontejner IoC jako Autofac nebo Ninject.

Pomocí následujících plnou zásady, vaše třídy bude jsou obvykle přirozeně malé, dobře započítané a snadno otestované. Ale jak můžete vy víte, pokud jsou probíhá příliš velký počet závislostí vloženy do vaší třídy? Pokud používáte DI pomocí konstruktoru, bude možné snadno zjistit, prohlížením právě počet parametrů pro vaše konstruktor. Pokud jsou moc velký počet závislostí, je obvykle znaménkem ( [code pach](http://deviq.com/code-smells/)), se pokouší o provedení příliš mnoho třídě a pravděpodobně porušuje zásady jeden odpovědnosti.

To bude trvat jiný průvodce tak, aby pokrývalo UCELENÝ podrobně. Tato příručka proto vyžaduje, abyste mají pouze minimální znalosti o těchto tématech.

#### <a name="additional-resources"></a>Další zdroje

-   **UCELENÝ: Principy základní mimoprocesová aplikace VOLÁNA**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)

-   **Inverze – kontejnery ovládacích prvků a vkládání závislostí vzor**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)

-   **Steve Smith. Nové je pojidlem**
    [*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)


>[!div class="step-by-step"]
[Předchozí] (nosql-database trvalost infrastructure.md) [Další] (microservice-application-layer-implementation-web-api.md)

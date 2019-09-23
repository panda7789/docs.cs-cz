---
title: ASP.NET Core gRPC pro vývojáře WCF – gRPC pro vývojáře WCF
description: BUDE URČENO K ZÁPISU
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 7d02d7914aed39613b4a41da55515df80abddfe8
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184447"
---
# <a name="aspnet-core-grpc-for-wcf-developers"></a>ASP.NET Core gRPC pro vývojáře WCF

![titulní obrázek](./media/cover.png)

PUBLIKOVAL (A)

Týmy produktů Microsoft Developer divize, .NET a Visual Studio

Divize společnosti Microsoft Corporation

Jeden způsob Microsoftu

Redmond, Washington 98052-6399

Copyright © 2019 by Microsoft Corporation

Všechna práva vyhrazena. Žádná část obsahu této knihy se nedá reprodukovat ani přenést v jakékoli formě nebo jakýmkoli způsobem bez písemného svolení vydavatele.

Tato kniha je k dispozici "tak jak jsou" a vyjadřuje zobrazení a stanoviska autora. Zobrazení, názory a informace vyjádřené v této knize, včetně adres URL a dalších odkazů na internetové weby, se mohou změnit bez předchozího upozornění.

Některé příklady, které jsou zde uvedeny, jsou k dispozici pouze pro ilustraci a jsou smyšlené. Neexistuje žádné skutečné přidružení nebo připojení, které by mělo být odvozeno.

Microsoft a ochranné známky uvedené https://www.microsoft.com na webové stránce ochranné známky jsou ochranné známky skupiny společností Microsoft.

Logo Docker Whale je registrovaná ochranná známka společnosti Docker, Inc. Používá se oprávněním.

Všechny ostatní značky a loga jsou majetkem příslušných vlastníků.

Autorizova

> **Označení Rendle** -ředitel technického důstojníka – [Visual Recode](https://visualrecode.com)
>
> **Miranda Steiner** – technický autor

Editory

> **Maira Wenzel** – vývojář obsahu SR – Microsoft

## <a name="introduction"></a>Úvod

TODO

## <a name="purpose"></a>Účel

TODO

## <a name="who-should-use-this-guide"></a>Kdo by měl používat tuto příručku

**AKTUALIZOVAT**

Cílovou skupinou pro tento průvodce jsou vývojáři WCF, vedoucí vývoje a architekti, kteří mají zájem o migraci řešení WCF v rozhraní .NET 4 a starších ASP.NET Core 3,0 pomocí služeb gRPC.

## <a name="how-you-can-use-this-guide"></a>Jak můžete použít tuto příručku

**AKTUALIZOVAT**

Toto je krátký úvod k sestavování služeb gRPC v ASP.NET Core 3,0 s konkrétní referencí na WCF jako podobnou platformou. Vysvětluje principy gRPC, vztahující se k jednotlivým konceptům ekvivalentních funkcí WCF a poskytuje pokyny pro migraci existující aplikace WCF na gRPC. Je to také užitečné pro vývojáře, kteří mají zkušenosti s WCF a chtějí se naučit gRPC vytvářet nové služby. Ukázkovou aplikaci lze použít jako šablonu nebo odkaz pro vlastní projekty a vy můžete kopírovat a znovu použít kód z knihy nebo jejích ukázek.

Nebojte se této příručky s vaším týmem, abyste se ujistili, že se tyto otázky a příležitosti budou porozumět běžným způsobem. Díky tomu, že všichni pracují se společnou sadou terminologie a základními principy, pomáhají zajistit konzistentní používání vzorů a postupů architektury.

## <a name="references"></a>Odkazy

- **Web gRPC**  
  <https://grpc.io>
- **Volba mezi .NET Core a .NET Framework pro serverové aplikace**  
  <https://docs.microsoft.com/dotnet/standard/choosing-core-framework-server>

>[!div class="step-by-step"]
>[Next](introduction.md)

---
title: Podpora platformy .NET Core
description: "Další informace o podporuje train jinou verzi (LTS a aktuální) pro .NET Core"
keywords: "Rozhraní .NET, .NET core, lts, aktuální, ft, podpora, podpora vlaky podpora vlaky cyklu stopy verze"
author: kendrahavens
ms.author: mairaw
ms.date: 01/30/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: fedc7025-f320-4cba-957b-ef74885f66de
ms.workload: dotnetcore
ms.openlocfilehash: 2fcb33c7c5a4a3c31960a683865b0e5e29269a8b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="net-core-support"></a>Podpora platformy .NET Core

Toto je obecný popis podpory .NET Core.

## <a name="lts-and-current-release-trains"></a>LTS a vlaků aktuální verze

Dvě verze vlaky podporu je běžným pojmem používán po celém světě softwaru speciálně pro projekty open-source jako .NET Core. .NET core má verzi vlaky následující podporu: [dlouho podporují termín (LTS)](https://en.wikipedia.org/wiki/Long-term_support) a aktuální. Verze LTS jsou uchovávány stabilitu prostřednictvím jejich životního cyklu přijetí opravy pro důležité problémy a opravy zabezpečení. Nový pracovní funkce a opravy chyb pro další provést v aktuální verze. Z hlediska podpory tyto verzi vlaky mají následující atributy životní cyklus podpory.

Jsou LTS verze
* Podporované tři roky po datu obecné dostupnosti verze LTS
* Nebo jeden rok po obecné dostupnosti následné verze LTS

Aktuální verze jsou
* Podporované v rámci okna tři roky jako nadřazenou verzi LTS
* Podporované na tři měsíce po obecné dostupnosti následné aktuální verze
* A jeden rok po obecné dostupnosti následné verze LTS

## <a name="versioning"></a>Správa verzí
Nové verze LTS jsou označené nástrojem zvýšit hlavní číslo verze. Aktuální verze mít stejný počet hlavních jako odpovídající train LTS a jsou označené nástrojem zvýšit číslo podverze. Například 1.0.3 by být LTS a 1.1.0 by být aktuální. Oprava chyby aktualizace buď train přírůstek verzi opravy. Další informace o schématu Správa verzí, naleznete v části [verze rozhraní .NET Core](index.md).

## <a name="what-causes-updates-in-lts-and-current-trains"></a>Co způsobí, že aktualizace v LTS a aktuální vlaků?
Zjistit, jaké konkrétní změny, jako je například opravy chyb nebo přidání rozhraní API, způsobit, že aktualizace na verzi čísla, projděte si část rozhodovací strom v [Správa verzí dokumentace](index.md). Není k dispozici zlaté sadu pravidel, která rozhodnout, jaké změny jsou vyžádány do LTS větev z aktuální. Důvodů, proč aktualizovat větev LTS jsou obvykle nutné bezpečnostní aktualizace a opravy, které opravte očekávané chování. Také plánujeme zajistit podporu poslední plochy vývojáře operační systémy na větev LTS, i když to nemusí být vždy možné. Dobrým způsobem, jak zachytit na jaké rozhraní API, opravy a operační systémy jsou podporované v určité verze je procházet jeho [poznámky k verzi](https://github.com/dotnet/core/tree/master/release-notes) na Githubu.

### <a name="further-reading"></a>Další čtení
* [List fakt životního cyklu podpory základní rozhraní .NET](https://www.microsoft.com/net/core/support)
* [Aktuálně podporované operační systémy a verze](https://github.com/dotnet/core/blob/master/roadmap.md)

---
title: Správa instalace .NET Core
description: Spravujte více verzí rozhraní .NET Core SDK a modul Runtime na svém počítači, práce s strategie instalace vedle sebe.
author: leecow
ms.author: wiwagn
ms.date: 08/22/2018
ms.openlocfilehash: 06c3f43e7917efb8fd31898044d8f5d920c2cada
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523668"
---
# <a name="manage-net-core-installations"></a>Správa instalace .NET Core

.NET core umožňuje více verzí sady SDK a modulu Runtime existovat vedle sebe, povolení verze závislosti flexibilitu pro vytváření a spouštění aplikací .NET Core. Tyto instalace a chování vpřed automatické verze nabízejí využívat výhody, ale čteno jednou z nevýhod. Podle nainstalovaných aktualizací rozhraní .NET Core SDK nebo .NET Core Runtime, zůstanou předchozí verze na disku. Více nainstalovaných verzí postupem doby zvyšuje využití disku. Jsme vydali více než 50 aktualizace .NET Core SDK. Může existovat mnoho verzí sady SDK a modulu Runtime nainstalovaného v počítači, který nebylo možné odebrat.

## <a name="safe-to-remove"></a>Dá se bezpečně odebrat?

[Výběr verze .NET Core](selection.md) chování a kompatibilitu modulu runtime .NET Core napříč aktualizace umožňuje bezpečné odebrání předchozí verze. Aktualizace modulu runtime .NET core jsou kompatibilní v rámci hlavní verzi "vzdálené", jako je například 1.x a 2.x. Kromě toho novější verze sady .NET Core SDK obecně zachována možnost vytvářet aplikace, které jsou cílové předchozí verze modulu runtime kompatibilní způsobem.

Obecně stačí pouze nejnovější sadu SDK a nejnovější opravy verzi modulů runtime, požadované pro vaší aplikaci. Instance, kde zachování starší verze sady SDK nebo modul Runtime patří Údržba aplikací založených na project.json.  Pokud aplikace nemá konkrétní důvod pro starší verzi sady SDK nebo modulů runtime, můžete bezpečně odstranit starší verze.

Metody pro odebrání .NET Core se liší od platformách a trochu změnili ve verzích .NET Core. Podrobnosti o odebrání verzích .NET Core, které už nejsou potřeba, najdete v části ["Jak odebrat modul .NET Core Runtime a sadu SDK"](remove-runtime-sdk-versions.md) v [dokumentace k .NET Core](../index.md).

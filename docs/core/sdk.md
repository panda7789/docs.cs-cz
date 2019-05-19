---
title: Přehled sady SDK .NET core
description: Přečtěte si o .NET Core SDK, což je sada knihoven a nástrojů pro vytváření projektů .NET Core.
ms.date: 05/13/2019
ms.technology: dotnet-cli
ms.openlocfilehash: ed9d51b337af8edc251a4f3b02c31b72b76ba33d
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877978"
---
# <a name="net-core-sdk-overview"></a>Přehled sady SDK .NET core

.NET core Software Development Kit (SDK) je sada knihoven a nástrojů, které umožňují vývojářům vytvářet aplikace .NET Core a knihovny. Obsahuje následující součásti, které se používají k vytváření a spouštění aplikací:

- Nástroje .NET Core CLI.
- Knihovny .NET core a modulu runtime.
- `dotnet` [Ovladač](/tools/index.md#driver).

## <a name="acquiring-the-net-core-sdk"></a>Získání sady .NET Core SDK

Stejně jako u jakékoli nástroje první věc, kterou je získat potřebné nástroje k vašemu počítači. V závislosti na vašem scénáři můžete nainstalovat sadu SDK, pomocí jedné z následujících metod:

- Použití nativních instalačních programů.
- Použijte skript prostředí instalace.

Nativních instalačních programů jsou primárně určeny pro počítače pro vývojáře. Sada SDK se distribuuje pomocí mechanismu nativní instalace jednotlivých podporovaných platformách, jako jsou například DEB balíčky na Ubuntu nebo MSI svazků na Windows. Tyto instalační programy instalace a nastavení prostředí podle potřeby pro uživatele k použití sady SDK ihned po instalaci. Však také vyžadují oprávnění správce na počítači. Můžete najít sadu SDK k instalaci na [.NET stáhne](https://dotnet.microsoft.com/download) stránky.

Skriptů instalace, na druhé straně nevyžaduje oprávnění správce. Však jejich také nechcete nainstalovat všechny požadované součásti na počítač. je potřeba všechny požadované součásti nainstalovat ručně. Tyto skripty jsou určené hlavně pro nastavení serverů sestavení nebo když chcete nainstalovat nástroje bez oprávnění správce (Poznámka: výše uvedené požadavky výstrahou). Můžete najít další informace najdete v [nainstalovat odkaz na skript](tools/dotnet-install-script.md) článku. Pokud máte zájem o tom, jak nastavení sady SDK na svém serveru sestavení CI, přejděte [pomocí .NET Core SDK a nástroje v kontinuální integrace (CI)](tools/using-ci-with-cli.md) článku.

Ve výchozím nastavení nainstaluje sadu SDK způsobem (SxS) "side-by-side", což znamená, že více verzí nástroje rozhraní příkazového řádku mohou existovat vedle sebe v daném okamžiku v jednom počítači. Jak získá výběru verze, pokud spouštíte příkazy rozhraní příkazového řádku je vysvětleno podrobněji [vyberte verzi .NET Core používat](/versions/selection.md) článku.

## <a name="see-also"></a>Viz také:

- [Rozhraní příkazového řádku .NET Core](tools/index.md)
- [Přehled správy verzí .NET core](/versions/index.md)
- [Odebrání modulu runtime .NET Core a sady SDK](versions/remove-runtime-sdk-versions.md)
- [Vyberte verzi .NET Core používat](/versions/selection.md)
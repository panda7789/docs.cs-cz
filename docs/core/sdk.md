---
title: Přehled sady SDK .NET core
description: Přečtěte si o .NET Core SDK, což je sada knihoven a nástrojů pro vytváření projektů .NET Core.
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 0b63de92dbee318326f670175ff6824a8c056784
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631891"
---
# <a name="net-core-sdk-overview"></a>Přehled sady SDK .NET core

.NET core Software Development Kit (SDK) je sada knihoven a nástrojů, které umožňují vývojářům vytvářet aplikace .NET Core a knihovny. Toto je balíček, který pravděpodobně využijí vývojáři. 

Obsahuje následující součásti:

1. Nástroje příkazového řádku .NET Core, které se používají k vytváření aplikací
2. .NET core (knihoven a modulu runtime), které umožňují aplikacím i dají vytvořit a spustit
3. `dotnet` Ovladače pro spouštění [příkazy rozhraní příkazového řádku](tools/index.md) a spouštění aplikací

## <a name="acquiring-the-net-core-sdk"></a>Získání sady .NET Core SDK
Stejně jako u jakékoli nástroje první věc, kterou je získat potřebné nástroje k vašemu počítači. V závislosti na vašem scénáři můžete použít buď nativních instalačních programů do instalace sady SDK nebo pomocí skriptu prostředí instalace.

Nativních instalačních programů jsou primárně určeny pro počítače pro vývojáře. Sada SDK se distribuuje pomocí mechanismu nativní instalace jednotlivých podporovaných platformách, například DEB balíčků na Ubuntu nebo MSI svazků na Windows. Tyto instalační programy se instalace a nastavení prostředí podle potřeby pro uživatele k použití sady SDK ihned po instalaci. Však také vyžadují oprávnění správce na počítači. Můžete zobrazit v pokynech k instalaci na [Průvodce instalací rozhraní .NET Core](https://aka.ms/dotnetcoregs).

Skriptů instalace, na druhé straně nevyžaduje oprávnění správce. Nicméně, nebude také nainstalovat všechny požadované součásti na počítač. je potřeba všechny požadované součásti nainstalovat ručně. Tyto skripty jsou určené hlavně pro nastavení serverů sestavení nebo když chcete nainstalovat nástroje bez oprávnění správce (Poznámka: výše uvedené požadavky výstrahou). Další informace najdete v [instalaci skriptu referenční téma](tools/dotnet-install-script.md). Pokud máte zájem o nastavení sady SDK na svém serveru sestavení CI, může trvat podívat [SDK se servery pro CI](tools/using-ci-with-cli.md) dokumentu.

Ve výchozím nastavení sada SDK nainstaluje způsobem (SxS) "side-by-side". To znamená, že více verzí nástroje rozhraní příkazového řádku, mohou existovat vedle sebe v daném okamžiku v jednom počítači. Jak se používá správná verze je vysvětleno podrobněji [ovladač části](tools/index.md#driver) tématu nástroje příkazového řádku .NET Core.

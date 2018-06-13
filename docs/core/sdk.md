---
title: Přehled sady SDK rozhraní .NET core
description: Zjistěte informace o rozhraní .NET Core SDK, což je sada knihoven a nástroje pro vytváření projektů .NET Core.
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 5fc04c3ef5a1502251a9caf0b6a5f5809faad5b9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33210899"
---
# <a name="net-core-sdk-overview"></a>Přehled sady SDK rozhraní .NET core 

## <a name="introduction"></a>Úvod
.NET core Software Development Kit (SDK) je sada knihoven a nástroje, které umožňují vývojářům vytvářet aplikace .NET Core a knihovny. Toto je balíček, který bude s největší pravděpodobností získat vývojáři. 

Obsahuje následující součásti:

1. Nástroje příkazového řádku .NET Core, které se používají k vytváření aplikací
2. .NET core (knihovny a runtime), které umožňují aplikacím i vytvořené a spusťte
3. `dotnet` Ovladače pro spuštění [rozhraní příkazového řádku](tools/index.md) i spuštěné aplikace


## <a name="acquiring-the-net-core-sdk"></a>Získávání .NET Core SDK
První věc, stejně jako u všech nástrojů je získat nástroje k vašemu počítači. V závislosti na scénáři můžete použít buď nativní instalační programy nainstalovat sadu SDK nebo použít instalační skript prostředí.

Nativní instalační programy jsou primárně určené pro počítače, pro vývojáře. Sada SDK je distribuován pomocí mechanismu nativní instalace každou podporovanou platformu, pro instanci bázi DEB balíčků na Ubuntu nebo MSI sady v systému Windows. Tato instalační programy nainstaluje a nastavení prostředí podle potřeby pro uživatele se používat sadu SDK okamžitě po instalaci. Však také vyžadují oprávnění správce na počítači. Můžete zobrazit v pokynech k instalaci na [Průvodce instalací .NET Core](https://aka.ms/dotnetcoregs).

Skriptů instalace, na druhé straně nevyžaduje oprávnění správce. Však budou nebude také nainstalovat všechny požadované součásti na tento počítač; budete muset všechny požadované součásti nainstalovat ručně. Tyto skripty jsou určené hlavně pro nastavení servery sestavení nebo pokud chcete nainstalovat nástroje bez oprávnění správce (Poznámka: výše uvedené požadavky přímý přístup paměti). Další informace najdete na [instalaci skriptu referenční téma](tools/dotnet-install-script.md). Pokud vás zajímá postup nastavení SDK na vašem serveru sestavení položky konfigurace můžete provést podívejte se na [SDK se servery CI](tools/using-ci-with-cli.md) dokumentu. 

Ve výchozím nastavení sada SDK nainstaluje způsobem (SxS) "-souběžného". To znamená, že více verzí nástrojů příkazového řádku, mohou existovat vedle sebe současně na jednom počítači. Získá použití správnou verzi je vysvětlené podrobněji v [části ovladačů](tools/index.md#driver) tématu nástroje příkazového řádku .NET Core.

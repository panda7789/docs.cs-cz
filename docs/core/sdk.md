---
title: Přehled sady .NET Core SDK
description: Informace o sadě .NET Core SDK, což je sada knihoven a nástrojů používaných k vytváření projektů .NET Core.
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: c2723e0e28c889f91f79ea3c0b26aa38f69fb41c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "78157463"
---
# <a name="net-core-sdk-overview"></a>Přehled sady .NET Core SDK

Sada .NET Core SDK je sada knihoven a nástrojů, které vývojářům umožňují vytvářet aplikace a knihovny .NET Core. Obsahuje následující součásti, které se používají k vytváření a spouštění aplikací:

- Rozhraní CLI jádra .NET.
- Knihovny .NET Core a runtime.
- `dotnet` [Ovladač](tools/index.md#driver).

## <a name="acquiring-the-net-core-sdk"></a>Získání sady .NET Core SDK

Stejně jako u všech nástrojů, první věc je dostat nástroje do vašeho stroje. V závislosti na scénáři můžete nainstalovat sadu SDK pomocí jedné z následujících metod:

- Použijte nativní instalační programy.
- Použijte instalační skript prostředí.

Nativní instalační programy jsou primárně určeny pro vývojářské počítače. Sada SDK je distribuována pomocí nativního instalačního mechanismu každé podporované platformy, jako jsou balíčky DEB v balíčcích Ubuntu nebo MSI v systému Windows. Tyto instalační programy nainstalují a nastaví prostředí podle potřeby, aby uživatel mohl sadu SDK používat ihned po instalaci. Však také vyžadují oprávnění správce v počítači. Sada SDK, kterou chcete nainstalovat, naleznete na stránce [ke stažení rozhraní .NET.](https://dotnet.microsoft.com/download)

Instalace skriptů na druhé straně nevyžaduje oprávnění správce. Však také neinstalují žádné požadavky na počítači; je třeba nainstalovat všechny požadavky ručně. Skripty jsou určeny především pro nastavení sestavení serverů, nebo když chcete nainstalovat nástroje bez oprávnění správce (poznamenejte si požadavky upozornění výše). Další informace naleznete v [článku odkazu na instalační skript.](tools/dotnet-install-script.md) Pokud vás zajímá, jak nastavit sadu SDK na serveru sestavení CI, přečtěte si článek Použití sady [.NET Core SDK a nástrojů v článku Průběžná integrace (CI).](tools/using-ci-with-cli.md)

Ve výchozím nastavení se sada SDK instaluje způsobem "side-by-side" (SxS), což znamená, že více verzí může existovat současně v daném okamžiku na jednom počítači. Jak se verze vybere při spuštění příkazů rozhraní příkazového příkazu, je podrobněji vysvětleno v článku [Vyberte verzi .NET Core, která chcete použít.](versions/selection.md)

## <a name="see-also"></a>Viz také

- [Přehled rozhraní CLI jádra .NET](tools/index.md)
- [Přehled správy verzí jádra rozhraní .NET](versions/index.md)
- [Odebrání runtime jádra .NET a sady SDK](versions/remove-runtime-sdk-versions.md)
- [Vyberte verzi .NET Core, kterou chcete použít.](versions/selection.md)

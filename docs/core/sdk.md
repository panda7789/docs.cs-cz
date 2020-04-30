---
title: Přehled sady .NET Core SDK
description: Přečtěte si o .NET Core SDK, což je sada knihoven a nástrojů sloužících k vytváření projektů .NET Core.
ms.date: 07/31/2019
ms.technology: dotnet-cli
ms.openlocfilehash: 7eb06e4fd94ed2a73af2741e98e21e02728c27e4
ms.sourcegitcommit: d7666f6e49c57a769612602ea7857b927294ce47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/30/2020
ms.locfileid: "82595738"
---
# <a name="net-core-sdk-overview"></a>Přehled sady .NET Core SDK

.NET Core SDK je sada knihoven a nástrojů, které vývojářům umožňují vytvářet aplikace a knihovny .NET Core. Obsahuje následující komponenty, které se používají pro sestavování a spouštění aplikací:

- .NET Core CLI.
- Knihovny .NET Core a modul runtime.
- `dotnet` [Ovladač](tools/index.md#driver).

## <a name="acquiring-the-net-core-sdk"></a>Získání .NET Core SDK

Stejně jako u libovolných nástrojů je první věc získat nástroje do vašeho počítače. V závislosti na vašem scénáři můžete sadu SDK nainstalovat pomocí jedné z následujících metod:

- Použijte nativní instalační programy.
- Použijte skript instalačního prostředí.

Nativní instalační programy jsou primárně určeny pro počítače vývojářů. Sada SDK se distribuuje pomocí nativního instalačního mechanismu každé podporované platformy, jako jsou DEB balíčky na Ubuntu nebo sady MSI v systému Windows. Tyto instalační programy instalují a nastavují prostředí podle potřeby, aby mohl uživatel používat sadu SDK hned po instalaci. Ale také vyžadují oprávnění správce v počítači. Sadu SDK pro instalaci můžete najít na stránce [soubory ke stažení pro rozhraní .NET](https://dotnet.microsoft.com/download) .

Nainstalovat skripty na druhé straně nevyžadují oprávnění správce. Neinstalují ale ani žádné požadavky na tento počítač. všechny požadavky musíte nainstalovat ručně. Skripty jsou určeny hlavně pro nastavení serverů sestavení nebo když chcete nainstalovat nástroje bez oprávnění správce (Poznamenejte si omezení požadavků výše). Další informace najdete v článku s [odkazem na instalaci skriptu](tools/dotnet-install-script.md) . Pokud vás zajímá, jak nastavit sadu SDK na serveru sestavení CI, přečtěte si článek [použití .NET Core SDK a nástrojů v článku průběžná integrace (CI)](tools/using-ci-with-cli.md) .

Ve výchozím nastavení se sada SDK instaluje v rámci "souběžného" (SxS), což znamená, že více verzí může v jednom počítači koexistovat v daném čase současně. Způsob, jakým se verze vybrala při spuštění příkazů rozhraní příkazového řádku, je podrobněji vysvětlen v článku [Výběr verze .NET Core pro použití](versions/selection.md) .

## <a name="see-also"></a>Viz také

- [Přehled rozhraní .NET Core CLI](tools/index.md)
- [Přehled verzí .NET Core](versions/index.md)
- [Postup odebrání modulu runtime .NET Core a sady SDK](install/remove-runtime-sdk-versions.md)
- [Vyberte verzi .NET Core, kterou chcete použít.](versions/selection.md)

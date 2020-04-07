---
title: Zvýšený přístup pro příkazy dotnet
description: Seznamte se s doporučenými postupy pro příkazy dotnet, které vyžadují zvýšený přístup.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: f99e0b257772e0a73d4945f1129997d1d3308ed2
ms.sourcegitcommit: f87ad41b8e62622da126aa928f7640108c4eff98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/07/2020
ms.locfileid: "80805788"
---
# <a name="elevated-access-for-dotnet-commands"></a>Zvýšený přístup pro příkazy dotnet

Osvědčené postupy vývoje softwaru vedou vývojáře k psaní softwaru, který vyžaduje nejmenší oprávnění. Některé software, jako jsou nástroje pro sledování výkonu, však vyžaduje oprávnění správce z důvodu pravidel operačního systému. Následující pokyny popisují podporované scénáře pro psaní takového softwaru pomocí rozhraní .NET Core.

Následující příkazy lze spustit se zvýšenými oprávněními:

- `dotnet tool`příkazy, jako je [například instalace nástroje dotnet](dotnet-tool-install.md).
- `dotnet run --no-build`
- `dotnet-core-uninstall`

Nedoporučujeme spouštět další příkazy se zvýšenými oprávněními. Zejména nedoporučujeme zvýšení s příkazy, které používají MSBuild, například [dotnet obnovení](dotnet-restore.md), [dotnet sestavení](dotnet-build.md)a [dotnet spustit](dotnet-run.md). Primární problém je problémy se správou oprávnění, když uživatel přechází tam a zpět mezi kořenovým a omezeným účtem po vydání příkazů dotnet. Jako uživatele s omezeným přístupem můžete zjistit, že nemáte přístup k souboru vytvořenému kořenovým uživatelem. Existují způsoby, jak tuto situaci vyřešit, ale oni jsou zbytečné se dostat do na prvním místě.

Příkazy můžete spouštět jako root, pokud nepřecházíte tam a zpět mezi kořenovým a omezeným účtem. Například kontejnery Dockeru běží jako root ve výchozím nastavení, takže mají tuto charakteristiku.

## <a name="global-tool-installation"></a>Globální instalace nástrojů

Následující pokyny ukazují doporučený způsob instalace, spuštění a odinstalace nástrojů .NET Core, které ke spuštění vyžadují zvýšená oprávnění.

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

### <a name="install-the-tool"></a>Instalace nástroje

Pokud složka `%ProgramFiles%\dotnet-tools` již existuje, zkontrolujte, zda má skupina Uživatelé oprávnění k zápisu nebo úpravám tohoto adresáře:

- Klepněte pravým `%ProgramFiles%\dotnet-tools` tlačítkem myši na složku a vyberte **příkaz Vlastnosti**. Otevře se dialogové okno **Společné vlastnosti.**
- Vyberte kartu **Zabezpečení.** V části **Seskupení nebo uživatelská jména**zkontrolujte, zda skupina Uživatelé nemá oprávnění k zápisu nebo úpravám adresáře.
- Pokud skupina "Uživatelé" může psát nebo upravovat adresář, použijte při instalaci nástrojů jiný název adresáře, nikoli *dotnet-tools*.

Chcete-li nainstalovat nástroje, spusťte následující příkaz ve zvýšené mačkovém řádku. Během instalace vytvoří složku *dotnet-tools.*

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a>Spuštění globálního nástroje

**Možnost 1** Použijte úplnou cestu se zvýšenou výzvou:

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

**Možnost č. 2** Přidejte nově vytvořenou složku do aplikace `%Path%`. Tuto operaci musíte provést pouze jednou.

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

A běh s:

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Odinstalace globálního nástroje

Ve zvýšené mač zadejte následující příkaz:

```dotnetcli
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linux"></a>[Linux](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macos"></a>[Macos](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a>Místní nástroje

Místní nástroje jsou vymezeny podle stromu podadresářů a uživatele. Při spuštění se zvýšenými oprávněními sdílejí místní nástroje omezené uživatelské prostředí s prostředím se zvýšenými oprávněními. V Linuxu a macOS to má za následek nastavení souborů s přístupem pouze pro root uživatele. Pokud uživatel přepne zpět na omezený účet, uživatel již nemůže přistupovat k souborům ani do něj zapisovat. Instalace nástrojů, které vyžadují zvýšení oprávnění jako místní nástroje, se tedy nedoporučuje. Místo toho `--tool-path` použijte možnost a předchozí pokyny pro globální nástroje.

## <a name="elevation-during-development"></a>Nadmořská výška během vývoje

Během vývoje budete pravděpodobně potřebovat zvýšený přístup k testování aplikace. Tento scénář je běžné pro aplikace IoT, například. Doporučujeme sestavit aplikaci bez zvýšení oprávnění a potom ji spustit s nadmořskou výškou. Existuje několik vzorů, takto:

- Použití generovaného spustitelného souboru (poskytuje nejlepší výkon při spuštění):

   ```dotnetcli
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```

- Použití příkazu [dotnet](dotnet-run.md) `—no-build` run s příznakem, abyste se vyhnuli generování nových binárních souborů:

   ```dotnetcli
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a>Viz také

- [Přehled globálních nástrojů .NET Core](global-tools.md)

---
title: Zvýšený přístup pro příkazy dotnet
description: Seznamte se s osvědčenými postupy pro příkazy dotnet, které vyžadují vyšší přístup.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: cf7c93a0adcae7092a61a6fc6046cd45cf00bf58
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216305"
---
# <a name="elevated-access-for-dotnet-commands"></a>Zvýšený přístup pro příkazy dotnet

Osvědčené postupy pro vývoj softwaru pomáhají vývojářům psát software, který vyžaduje nejnižší množství oprávnění. Nicméně nějaký software, například nástroje pro monitorování výkonu, vyžaduje oprávnění správce z důvodu pravidel operačního systému. Následující pokyny popisují podporované scénáře pro zápis takového softwaru pomocí .NET Core. 

Následující příkazy lze spustit se zvýšenými oprávněními:

- `dotnet tool`příkazy, jako je například [Instalace nástroje dotnet](dotnet-tool-install.md).
- `dotnet run --no-build`

Nedoporučujeme spouštět další příkazy se zvýšenými oprávněními. Konkrétně nedoporučujeme zvyšovat zvýšení oprávnění pomocí příkazů, které používají MSBuild, například [dotnet Restore](dotnet-restore.md), [sestavení dotnet](dotnet-build.md)a [spuštění dotnet](dotnet-run.md). Primárním problémem jsou problémy se správou oprávnění, když uživatel prochází zpátky a zpátky mezi kořenovým a omezeným účtem po vystavení příkazů dotnet. Můžete se setkat s omezeným uživatelem, který nemáte přístup k souboru vytvořenému kořenovým uživatelem. Existují způsoby, jak tuto situaci vyřešit, ale nejsou potřebné k tomu, aby se na první místo dostaly.

Příkazy můžete spustit jako kořen, pokud nebudete mezi kořenem a omezeným účtem přecházet zpátky a zpátky. Například kontejnery Docker se ve výchozím nastavení spouštějí jako kořenové, takže mají tuto vlastnost.

## <a name="global-tool-installation"></a>Instalace globálních nástrojů

Následující pokyny ukazují doporučený způsob, jak nainstalovat, spustit a odinstalovat nástroje .NET Core, které vyžadují vyšší oprávnění ke spuštění.

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

### <a name="install-the-global-tool"></a>Instalace globálního nástroje

Pokud složka `%ProgramFiles%\dotnet-tools` již existuje, proveďte následující kroky a ověřte, zda má skupina uživatelé oprávnění k zápisu nebo úpravě tohoto adresáře:

- Klikněte pravým tlačítkem `%ProgramFiles%\dotnet-tools` na složku a vyberte **vlastnosti**. Otevře se dialogové okno **společné vlastnosti** . 
- Vyberte kartu **zabezpečení** . V části **uživatelské jméno nebo název skupiny**ověřte, zda má skupina uživatelé oprávnění k zápisu nebo úpravám adresáře. 
- Pokud skupina uživatelé může zapisovat nebo upravovat adresář, použijte při instalaci nástrojů místo příkazu *dotnet-Tools*jiný název adresáře.

Nástroje nainstalujete spuštěním následujícího příkazu v příkazovém řádku se zvýšenými oprávněními. Během instalace vytvoří složku *dotnet-Tools* .

```dotnetcli
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a>Spustit globální nástroj

**Možnost 1** Použít úplnou cestu s výzvou se zvýšenými oprávněními:

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

**Možnost 2** Přidejte nově vytvořenou složku do `%Path%`. Tuto operaci je nutné provést pouze jednou.

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

A spustit pomocí:

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Odinstalace globálního nástroje

Do příkazového řádku se zvýšenými oprávněními zadejte následující příkaz:

```dotnetcli
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macostabmacos"></a>[macOS](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a>Místní nástroje

Místní nástroje jsou vymezeny podle stromu podadresářů pro jednotlivé uživatele. Při spuštění se zvýšenými oprávněními místní nástroje sdílí omezené uživatelské prostředí do prostředí se zvýšenými oprávněními. V systému Linux a macOS to vede k nastavování souborů s přístupem uživatele root. Pokud uživatel přepne zpět na účet s omezeným přístupem, uživatel již nebude moci přistupovat k souborům nebo do něj zapisovat. Proto se nedoporučuje instalovat nástroje, které vyžadují zvýšení oprávnění, protože místní nástroje. Místo toho použijte `--tool-path` možnost a předchozí pokyny pro globální nástroje.

## <a name="elevation-during-development"></a>Zvýšení úrovně během vývoje

Během vývoje můžete potřebovat vyšší úroveň přístupu k otestování aplikace. Tento scénář je běžný například pro aplikace IoT. Doporučujeme sestavit aplikaci bez zvýšení oprávnění a pak ji spustit se zvýšením oprávnění. Existuje několik vzorů, jak je znázorněno níže:

- Pomocí vygenerovaného spustitelného souboru (poskytuje nejlepší výkon při spuštění):

   ```bash
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```
    
- Pomocí příkazu [dotnet Run](dotnet-run.md) s `—no-build` příznakem Vyhněte se generování nových binárních souborů:

   ```bash
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a>Viz také:

- [Přehled globálních nástrojů .NET Core](global-tools.md)

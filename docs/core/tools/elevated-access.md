---
title: Zvýšený přístup pro příkazy dotnet
description: Seznamte se s osvědčenými postupy pro příkazy dotnet, které vyžadují vyšší přístup.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 4aff9badfa8ad9b83adc4496d4ebd6df29252e36
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156761"
---
# <a name="elevated-access-for-dotnet-commands"></a>Zvýšený přístup pro příkazy dotnet

Osvědčené postupy pro vývoj softwaru pomáhají vývojářům psát software, který vyžaduje nejnižší množství oprávnění. Nicméně nějaký software, například nástroje pro monitorování výkonu, vyžaduje oprávnění správce z důvodu pravidel operačního systému. Následující pokyny popisují podporované scénáře pro zápis takového softwaru pomocí .NET Core.

Následující příkazy lze spustit se zvýšenými oprávněními:

- `dotnet tool` příkazy, jako je například [Instalace nástroje dotnet](dotnet-tool-install.md).
- `dotnet run --no-build`

Nedoporučujeme spouštět další příkazy se zvýšenými oprávněními. Konkrétně nedoporučujeme zvyšovat zvýšení oprávnění pomocí příkazů, které používají MSBuild, například [dotnet Restore](dotnet-restore.md), [sestavení dotnet](dotnet-build.md)a [spuštění dotnet](dotnet-run.md). Primárním problémem jsou problémy se správou oprávnění, když uživatel prochází zpátky a zpátky mezi kořenovým a omezeným účtem po vystavení příkazů dotnet. Můžete se setkat s omezeným uživatelem, který nemáte přístup k souboru vytvořenému kořenovým uživatelem. Existují způsoby, jak tuto situaci vyřešit, ale nejsou potřebné k tomu, aby se na první místo dostaly.

Příkazy můžete spustit jako kořen, pokud nebudete mezi kořenem a omezeným účtem přecházet zpátky a zpátky. Například kontejnery Docker se ve výchozím nastavení spouštějí jako kořenové, takže mají tuto vlastnost.

## <a name="global-tool-installation"></a>Instalace globálních nástrojů

Následující pokyny ukazují doporučený způsob, jak nainstalovat, spustit a odinstalovat nástroje .NET Core, které vyžadují vyšší oprávnění ke spuštění.

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

### <a name="install-the-tool"></a>Instalace nástroje

Pokud `%ProgramFiles%\dotnet-tools` složka již existuje, proveďte následující kroky a ověřte, zda má skupina uživatelé oprávnění k zápisu nebo úpravě tohoto adresáře:

- Klikněte pravým tlačítkem na složku `%ProgramFiles%\dotnet-tools` a vyberte možnost **vlastnosti**. Otevře se dialogové okno **společné vlastnosti** .
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

# <a name="linux"></a>[Linux](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macos"></a>[macOS](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a>Místní nástroje

Místní nástroje jsou vymezeny podle stromu podadresářů pro jednotlivé uživatele. Při spuštění se zvýšenými oprávněními místní nástroje sdílí omezené uživatelské prostředí do prostředí se zvýšenými oprávněními. V systému Linux a macOS to vede k nastavování souborů s přístupem uživatele root. Pokud uživatel přepne zpět na účet s omezeným přístupem, uživatel již nebude moci přistupovat k souborům nebo do něj zapisovat. Proto se nedoporučuje instalovat nástroje, které vyžadují zvýšení oprávnění, protože místní nástroje. Místo toho použijte možnost `--tool-path` a předchozí pokyny pro globální nástroje.

## <a name="elevation-during-development"></a>Zvýšení úrovně během vývoje

Během vývoje můžete potřebovat vyšší úroveň přístupu k otestování aplikace. Tento scénář je běžný například pro aplikace IoT. Doporučujeme sestavit aplikaci bez zvýšení oprávnění a pak ji spustit se zvýšením oprávnění. Existuje několik vzorů, jak je znázorněno níže:

- Pomocí vygenerovaného spustitelného souboru (poskytuje nejlepší výkon při spuštění):

   ```dotnetcli
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```

- Pomocí příkazu [dotnet Run](dotnet-run.md) s příznakem `—no-build` se vyhnete generování nových binárních souborů:

   ```dotnetcli
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a>Viz také

- [Přehled globálních nástrojů .NET Core](global-tools.md)

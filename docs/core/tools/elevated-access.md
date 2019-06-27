---
title: Přístup se zvýšeným oprávněním pro příkazy dotnet
description: Podívejte se na osvědčené postupy pro dotnet příkazy, které vyžadují přístup se zvýšeným oprávněním.
author: wli3
ms.date: 06/26/2019
ms.openlocfilehash: 3d874a76eadbf5330c4e5efe4e86bfeca0a9b504
ms.sourcegitcommit: 52e588dc2ee74d484cd07ac60076be25cbf777ab
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2019
ms.locfileid: "67410644"
---
# <a name="elevated-access-for-dotnet-commands"></a>Přístup se zvýšeným oprávněním pro příkazy dotnet

Osvědčené postupy při vývoji softwaru Příručka vývojáře k vytváření softwaru, který vyžaduje minimální množství oprávnění. Některý software, jako jsou nástroje pro monitorování výkonu však vyžaduje oprávnění správce z důvodu pravidla operačního systému. Následující pokyny popisuje podporované scénáře pro zápis takový software s .NET Core. 

Může být spuštěn se zvýšenými oprávněními následující příkazy:

- `dotnet tool` příkazy, jako například [instalace nástrojů dotnet](dotnet-tool-install.md).
- `dotnet run --no-build`

Nedoporučujeme spouštění dalších příkazů se zvýšenými oprávněními. Zejména nedoporučujeme zvýšení oprávnění pomocí příkazů, které používají MSBuild, jako například [dotnet restore](dotnet-restore.md), [dotnet sestavení](dotnet-build.md), a [dotnet spustit](dotnet-run.md). Primární problém je oprávnění správy problémů, když uživatel přejde vpřed a zpět mezi kořenové a účet s omezeným přístupem po vydání příkazy dotnet. Můžete zjistit jako uživatel s omezeným přístupem, že nemáte přístup k souboru vytvořená uživatelem root. Existují způsoby, jak tuto situaci vyřešit, ale jsou nutné získat na prvním místě.

Můžete spouštět příkazy jako uživatel root, tak dlouho, dokud není přejít vpřed a zpět mezi kořenové a účet s omezeným přístupem. Například kontejnery Dockeru jako uživatel root ve výchozím nastavení spouští, takže mají tato vlastnost.

## <a name="global-tool-installation"></a>Nástroj pro globální instalace

Následující pokyny ukazují doporučeným způsobem, jak nainstalovat, spustit a odinstalaci nástroje .NET Core, které vyžadují zvýšená oprávnění ke spuštění.

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

### <a name="install-the-global-tool"></a>Nainstalujte nástroj global

Pokud složka `%ProgramFiles%\dotnet-tools` již existuje, následujícím postupem zkontrolujte, zda má skupina "Users" oprávnění k zápisu nebo úpravám tohoto adresáře:

* Klikněte pravým tlačítkem myši `%ProgramFiles%\dotnet-tools` a pak zvolte položku **vlastnosti**. **Společné vlastnosti** zobrazí se dialogové okno. 
* Vyberte **zabezpečení** kartu. V části **skupiny nebo jméno uživatele**, zkontrolujte, zda má skupina "Users" oprávnění k zápisu nebo úpravám adresáři. 
* Pokud skupiny "Users" může zápisu nebo úpravám adresáři, použijte název jiného adresáře při instalaci nástrojů spíše než *nástrojů dotnet*.

Chcete-li nainstalovat nástroje, spusťte následující příkaz v řádku se zvýšenými oprávněními. Vytvoří *nástrojů dotnet* složky během instalace.

```cmd
dotnet tool install PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools".
```

### <a name="run-the-global-tool"></a>Spusťte nástroj global

**Možnost 1** použít úplnou cestu s řádku se zvýšenými oprávněními:

```cmd
"%ProgramFiles%\dotnet-tools\TOOLCOMMAND"
```

**Možnost 2** přidat nově vytvořená složka k `%Path%`. Stačí jednou tuto operaci provést.

```cmd
setx Path "%Path%;%ProgramFiles%\dotnet-tools\"
```

A spuštění:

```cmd
TOOLCOMMAND
```

### <a name="uninstall-the-global-tool"></a>Odinstalujte nástroj global

V řádku se zvýšenými oprávněními zadejte následující příkaz:

```cmd
dotnet tool uninstall PACKAGEID --tool-path "%ProgramFiles%\dotnet-tools"
```

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

# <a name="macostabmacos"></a>[macOS](#tab/macos)

[!INCLUDE [elevated-access-unix](../../../includes/elevated-access-unix.md)]

---

## <a name="local-tools"></a>Místní nástroje

Místní nástroje jsou omezená na podstrom na uživatele. Při spuštění se zvýšenými oprávněními, sdílet nástrojů pro místní prostředí s omezeným přístupem uživatele do prostředí se zvýšenými oprávněními. V Linuxu a macOS výsledkem souborů nastavena s přístupem jen pro uživatele root. Uživatel přepne zpět na účet s omezeným přístupem, uživatel může již přistupovat k nebo zápis do souborů. Proto instalace nástrojů, které vyžadují zvýšení jako místní nástroje se nedoporučuje. Místo toho použijte `--tool-path` možnost a předchozí pokyny pro globální nástroje.

## <a name="elevation-during-development"></a>Zvýšení oprávnění během vývoje.

Během vývoje potřebujete přístup se zvýšeným oprávněním k testování aplikace. Tento scénář je běžné, že aplikace IoT, např. Doporučujeme vám vytvořit aplikaci bez zvýšení oprávnění a pak ho spusťte se zvýšením oprávnění. Existuje několik vzorových postupů, následujícím způsobem:

- Pomocí generované spustitelné soubory (poskytuje nejlepší výkon při spuštění):

   ```bash
   dotnet build
   sudo ./bin/Debug/netcoreapp3.0/APPLICATIONNAME
   ```
    
- Použití [dotnet spustit](dotnet-run.md) příkazů `—no-build` příznak pro zabránění generování nových binárních souborů:

   ```bash
   dotnet build
   sudo dotnet run --no-build
   ```

## <a name="see-also"></a>Viz také:

* [Přehled globální nástroje .NET core](global-tools.md)

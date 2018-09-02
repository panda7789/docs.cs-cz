---
title: Odebrání modulu runtime .NET a sady SDK
description: Pokyny k odebrání součásti modulu Runtime .NET Core a sady SDK Windows, Mac a Linux
ms.date: 07/28/2018
author: billwagner
ms.author: wiwagn
ms.openlocfilehash: 1806d1af3b10e44ccc2eff788d8958ca976fe85b
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43409140"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>Odebrání modulu Runtime .NET Core a sady SDK

V průběhu času při instalaci aktualizované verze modulu runtime .NET Core a sady SDK, můžete chtít odebrat zastaralé verzích .NET Core z vašeho počítače. Odebírají se starší verze modulu runtime se může změnit modul runtime se rozhodli spustit sdílené architektuře aplikací podle popisu v článku na [výběr verze .NET Core](selection.md).

Počínaje .NET Core 2.1, rozhraní příkazového řádku .NET poskytuje možnosti, které slouží k výpisu verze sady SDK a modulu runtime, který je na vašem počítači nainstalovaný.  Použití [ `dotnet --list-sdks` ](../tools/dotnet.md#options) zobrazíte seznam sad SDK na vašem počítači nainstalovaný. Použití [ `dotnet --list-runtimes` ](../tools/dotnet.md#options) zobrazíte seznam modulů runtime na vašem počítači nainstalovaný. Následující text uvádí typické výstup pro Windows, macOS nebo Linux:

# <a name="windowstabwindows"></a>[Windows](#tab/Windows)

```console
C:\> dotnet --list-sdks
2.1.200-preview-007474 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007480 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007509 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007570 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007576 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007587 [C:\Program Files\dotnet\sdk]
2.1.200-preview-007589 [C:\Program Files\dotnet\sdk]
2.1.200 [C:\Program Files\dotnet\sdk]
2.1.201 [C:\Program Files\dotnet\sdk]
2.1.202 [C:\Program Files\dotnet\sdk]
2.1.300-preview2-008533 [C:\Program Files\dotnet\sdk]
2.1.300 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009063 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009088 [C:\Program Files\dotnet\sdk]
2.1.400-preview-009171 [C:\Program Files\dotnet\sdk]

C:\> dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.AspNetCore.App]
Microsoft.NETCore.App 2.0.6 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.7 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.9 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.2 [C:\Program Files\dotnet\shared\Microsoft.NETCore.App]
```

# <a name="linuxtablinux"></a>[Linux](#tab/Linux)

```console
$ dotnet --list-sdks
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]

$ dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/share/dotnet/shared/Microsoft.NETCore.App]
```

# <a name="macostabmacos"></a>[macOS](#tab/macOS)

```console
$ dotnet --list-sdks
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]

$ dotnet --list-runtimes
Microsoft.AspNetCore.All 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.All 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.All]
Microsoft.AspNetCore.App 2.1.0-preview2-final [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.AspNetCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.AspNetCore.App]
Microsoft.NETCore.App 1.0.4 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 1.1.2 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview1-002111-00 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0-preview2-25407-01 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.0.5 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0-preview2-26406-04 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.0 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
Microsoft.NETCore.App 2.1.1 [/usr/local/share/dotnet/shared/Microsoft.NETCore.App]
```

***

## <a name="uninstalling-net-core"></a>Odinstalování rozhraní .NET Core

# <a name="windowstabwindows"></a>[Windows](#tab/Windows)

.NET core používá Windows **přidat nebo odebrat programy** dialogové okno odebrat verze modulu runtime .NET Core a sady SDK. Následující obrázek ukazuje **přidat nebo odebrat programy** dialogové okno s několika verzí modulu runtime .NET a nainstalované sady SDK.

![Přidat nebo odebrat programy se odebrat .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

Vyberte všechny verze, kterou chcete odebrat z počítače a klikněte na tlačítko **odinstalovat**.

# <a name="linuxtablinux"></a>[Linux](#tab/Linux)

Existují další možnosti odinstalace .NET Core (SDK nebo modul runtime) v Linuxu. Nejlepší způsob pro vás k odinstalaci .NET Core je zrcadlení akci, kterou jste použili k instalaci .NET Core. Specifika závisí na zvoleném distribuce a metodu instalace.

> [!IMPORTANT]
> Pro Red Hat zařízení, najdete [Red Hat – Příručka Začínáme](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) informace o instalaci a odinstalaci .NET Core.

Počínaje .NET Core 2.1, není nutné odinstalovat sadu .NET Core SDK, při upgradu pomocí Správce balíčků. Správce balíčků `update` nebo `refresh` příkazy automaticky odebere starší verze po úspěšné instalaci novější verze.

Pokud jste nainstalovali .NET Core pomocí Správce balíčků, použijte tento stejný správce balíčků pro odinstalaci sady .NET SDK nebo modulu runtime. Instalace .NET core podporují nejoblíbenější správců balíčků. Správce balíčků vaší distribuce pro přesné syntaxi ve vašem prostředí najdete v dokumentaci:

- [apt-Get(8)](https://linux.die.net/man/8/apt-get) používá Debian systémů, včetně Ubuntu.
- [YUM(8)](https://linux.die.net/man/8/yum) se používá na Fedora a CentOS, Oracle Linux.
- [zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) se používá v openSUSE a operačním systémem SUSE Linux Enterprise systému (SLES).
- [dnf(8)](https://dnf.readthedocs.io/latest/command_ref.html) se používá na Fedora.

V téměř všech případech se příkaz k odebrání balíčku je `remove`.

Název balíčku pro instalaci .NET Core SDK pro většinu Správce balíčků je `dotnet-sdk`následovaný číslo verze. Počínaje verzí 2.1.300 .NET Core SDK a verze `2.1` modulu runtime jsou nezbytné pouze čísla hlavní verze a podverze: .NET Core SDK verze 2.1.300 například může být odkazováno jako balíček `dotnet-sdk-2.1`. Předchozí verze vyžadují celého řetězci verze: například `dotnet-sdk-2.1.200` by byla zapotřebí pro 2.1.200 verzi .NET Core SDK.

Pro počítače, které jste nainstalovali pouze modul runtime a ne sadu SDK, je název balíčku `dotnet-runtime-<version>` pro modul runtime .NET Core a `aspnetcore-runtime-<version>` pro zásobník celý modulu runtime.

Instalace .NET core před 2.0 neodinstalovali hostitelská aplikace, když sada SDK byla odinstalována pomocí Správce balíčků. Pomocí `apt-get`, má příkaz tuto podobu:

```bash
apt-get remove dotnet-host
```

Všimněte si, že neexistuje žádná verze připojené k `dotnet-host`.

Pokud jste si nainstalovali pomocí tarballu, musíte odebrat .NET Core pomocí ruční metodu.

Můžete odebrat sady SDK a moduly runtime samostatně, odebráním adresáře, který obsahuje tuto verzi. Například, chcete-li odebrat 1.0.1 SDK a modul runtime, použili byste následující příkazy bash:

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

Nadřazené adresáře sady SDK a modulu runtime jsou uvedené ve výstupu `dotnet --list-sdks` a `dotnet --list-runtimes` příkaz, jak je znázorněno v předchozí tabulce.

# <a name="macostabmacos"></a>[macOS](#tab/macOS)

Na počítači Mac je nutné odstranit sady SDK a moduly runtime samostatně, tak, že odeberete adresáře, který obsahuje tuto verzi. Například, chcete-li odebrat 1.0.1 SDK a modul runtime, použili byste následující příkazy bash:

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

Nadřazené adresáře sady SDK a modulu runtime jsou uvedené ve výstupu `dotnet --list-sdks` a `dotnet --list-runtimes` příkaz, jak je znázorněno v předchozí tabulce.

Počínaje .NET Core 2.1, není nutné odinstalovat sadu .NET Core SDK, při upgradu pomocí Správce balíčků. Správce balíčků `update` nebo `refresh` příkazy automaticky odebere starší verze po úspěšné instalaci novější verze.

---

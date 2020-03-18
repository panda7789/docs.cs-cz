---
title: Odebrání runtime jádra .NET a sady SDK
description: Tento článek popisuje, jak určit, které verze rozhraní .NET Core Runtime a sady SDK jsou aktuálně nainstalovány, a potom, jak je odebrat v systémech Windows, Mac a Linux.
ms.date: 12/17/2019
author: billwagner
ms.author: wiwagn
ms.custom: updateeachrelease
ms.openlocfilehash: 71c11825981c6259a779e1ac8f947a41618e922d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398837"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>Odebrání sady .NET Core Runtime a sady SDK

V průběhu času při instalaci aktualizovaných verzí rozhraní .NET Core runtime a sady SDK můžete chtít odebrat zastaralé verze rozhraní .NET Core z počítače. Odebrání starších verzí runtime může změnit za běhu zvoleného ke spuštění aplikací sdíleného frameworku, jak je podrobně popsáno v článku o [výběru verze .NET Core](selection.md).

## <a name="should-i-remove-a-version"></a>Mám odebrat verzi?

Chování [výběru verze .NET Core](selection.md) a kompatibilita rozhraní .NET Core za běhu mezi aktualizacemi umožňují bezpečné odebrání předchozích verzí. Aktualizace runtime .NET Core jsou kompatibilní v rámci hlavní verze 'pásmo', jako je 1.x a 2.x. Kromě toho novější verze sady .NET Core SDK obecně zachovat schopnost vytvářet aplikace, které se zaměřují na předchozí verze runtime kompatibilním způsobem.

Obecně platí, že potřebujete pouze nejnovější sdk a nejnovější verzi opravy runtimes požadované pro vaši aplikaci. Instance, kde zachování starší verze Sady SDK nebo Runtime patří udržování **project.json-založené**aplikace. Pokud vaše aplikace nemá konkrétní důvody pro starší sady SDK nebo runtimes, můžete bezpečně odebrat starší verze.

## <a name="determine-what-is-installed"></a>Určení nainstalovaného

Počínaje rozhraním .NET Core 2.1 obsahuje rozhraní .NET CLI možnosti, které můžete použít k zobrazení seznamu verzí sady SDK a runtime nainstalovaných v počítači.  Slouží [`dotnet --list-sdks`](../tools/dotnet.md#options) k zobrazení seznamu sad SDK nainstalovaných v počítači. Slouží [`dotnet --list-runtimes`](../tools/dotnet.md#options) k zobrazení seznamu runčasů nainstalovaných v počítači. Následující text ukazuje typický výstup pro Windows, macOS nebo Linux:

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[Windows](#tab/windows)

Spuštěním následujícího příkazu:

```dotnetcli
dotnet --list-sdks
```

Získáte výstup podobný následující:

```console
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
```

A spuštěním následujícího příkazu:

```dotnetcli
dotnet --list-runtimes
```

Získáte výstup podobný následující:

```console
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

# <a name="linux"></a>[Linux](#tab/linux)

Spuštěním následujícího příkazu:

```dotnetcli
dotnet --list-sdks
```

Získáte výstup podobný následující:

```console
1.0.1 [/usr/share/dotnet/sdk]
1.0.4 [/usr/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/share/dotnet/sdk]
2.0.0 [/usr/share/dotnet/sdk]
2.1.4 [/usr/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/share/dotnet/sdk]
2.1.300 [/usr/share/dotnet/sdk]
2.1.301 [/usr/share/dotnet/sdk]
```

A spuštěním následujícího příkazu:

```dotnetcli
dotnet --list-runtimes
```

Získáte výstup podobný následující:

```console
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

# <a name="macos"></a>[Macos](#tab/macos)

Spuštěním následujícího příkazu:

```dotnetcli
dotnet --list-sdks
```

Získáte výstup podobný následující:

```console
1.0.1 [/usr/local/share/dotnet/sdk]
1.0.4 [/usr/local/share/dotnet/sdk]
2.0.0-preview1-005977 [/usr/local/share/dotnet/sdk]
2.0.0-preview2-006497 [/usr/local/share/dotnet/sdk]
2.0.0 [/usr/local/share/dotnet/sdk]
2.1.4 [/usr/local/share/dotnet/sdk]
2.1.300-preview2-008530 [/usr/local/share/dotnet/sdk]
2.1.300 [/usr/local/share/dotnet/sdk]
2.1.301 [/usr/local/share/dotnet/sdk]
```

A spuštěním následujícího příkazu:

```dotnetcli
dotnet --list-runtimes
```

Získáte výstup podobný následující:

```console
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

---

## <a name="uninstall-net-core"></a>Odinstalace jádra .NET Core

# <a name="windows"></a>[Windows](#tab/windows)

Jádro .NET používá dialogové okno **Přidat nebo odebrat programy** systému Windows k odebrání verzí runtime .NET Core a sady SDK. Následující obrázek znázorňuje dialogové okno **Přidat nebo odebrat programy** s několika nainstalovanými verzemi běhu .NET a sady SDK.

![Přidat nebo odebrat programy pro odebrání rozhraní .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

Vyberte všechny verze, které chcete odebrat ze zařízení, a klepněte na tlačítko **Odinstalovat**.

# <a name="linux"></a>[Linux](#tab/linux)

Existuje více možností odinstalace .NET Core (buď SDK nebo runtime) na Linuxu. Nejlepší způsob, jak odinstalovat jádro .NET Core, je zrcadlit akci použitou k instalaci jádra .NET Core. Specifika závisí na zvolené distribuci a způsobu instalace.

> [!IMPORTANT]
> Informace o instalaci rozhraní .NET Core naleznete v [průvodci začínám](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) s red hatem.

Počínaje rozhraním .NET Core 2.1 není nutné odinstalovat sadu .NET Core SDK při upgradu pomocí správce balíčků. Správce `update` balíčků `refresh` nebo příkazy automaticky odeberou starší verzi po úspěšné instalaci novější verze.

Pokud jste nainstalovali .NET Core pomocí správce balíčků, použijte stejný správce balíčků k odinstalaci sady .NET SDK nebo runtime. Instalace .NET Core podporují nejoblíbenější správce balíčků. Přesné syntaxe ve vašem prostředí naleznete v dokumentaci správce balíčků vaší distribuce:

- [apt-get(8)](https://linux.die.net/man/8/apt-get) používají systémy založené na Debianu, včetně Ubuntu.
- [yum(8)](https://linux.die.net/man/8/yum) se používá na Fedora, CentOS a Oracle Linux.
- [zypper(8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) se používá na openSUSE a SUSE Linux Enterprise System (SLES).
- [dnf(8)](https://dnf.readthedocs.io/en/latest/command_ref.html) se používá na Fedoru.

Téměř ve všech případech je `remove`příkaz k odebrání balíčku .

Název balíčku pro instalaci sady .NET Core SDK pro většinu správců balíčků je `dotnet-sdk`následovaný číslem verze. Počínaje verzí 2.1.300 sady .NET Core SDK a verzí `2.1` runtime jsou potřebná pouze čísla hlavních a dílčích verzí: například sada .NET Core SDK verze 2.1.300 může být považována za balíček `dotnet-sdk-2.1`. Předchozí verze vyžadují celý řetězec verze: `dotnet-sdk-2.1.200` například by bylo vyžadováno pro verzi 2.1.200 sady .NET Core SDK.

Pro počítače, které nainstalovaly pouze runtime a nikoli SDK, je `dotnet-runtime-<version>` název balíčku `aspnetcore-runtime-<version>` pro soubor .NET Core runtime a pro celý zásobník runtime.

Instalace jádra .NET starší než 2.0 neodinstalovaly hostitelskou aplikaci při odinstalaci sady SDK pomocí správce balíčků. Pomocí `apt-get`příkazu je:

```bash
apt-get remove dotnet-host
```

Všimněte si, že neexistuje `dotnet-host`žádná verze připojena k .

Pokud jste nainstalovali pomocí tarballu, musíte odebrat .NET Core pomocí ruční metody.

Sady SDK a runtimes odeberete samostatně odebráním adresáře, který tuto verzi obsahuje. Chcete-li například odebrat 1.0.1 SDK a runtime, použijte následující příkazy bash:

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

Nadřazené adresáře pro sadu SDK a `dotnet --list-sdks` `dotnet --list-runtimes` runtime jsou uvedeny ve výstupu z příkazu a, jak je znázorněno v předchozí tabulce.

# <a name="macos"></a>[Macos](#tab/macos)

Na Macu je nutné odebrat sady SDK a runtimes samostatně odebráním adresáře, který tuto verzi obsahuje. Chcete-li například odebrat 1.0.1 SDK a runtime, použijte následující příkazy bash:

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

Nadřazené adresáře pro sadu SDK a `dotnet --list-sdks` `dotnet --list-runtimes` runtime jsou uvedeny ve výstupu z příkazu a, jak je znázorněno v předchozí tabulce.

---

## <a name="net-core-uninstall-tool"></a>Nástroj pro odinstalaci .NET Core

[Nástroj .NET Core Uninstall Tool](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) umožňuje odebrat sady .NET Core SDK a runtimes ze systému. K dispozici je kolekce možností, které určují, které verze by měly být odinstalovány.

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a>Závislost sady Visual Studio na verzích sady .NET Core SDK

Před Visual Studio 2019 verze 16.3, Visual Studio instalátory volal samostatný instalační program .NET Core SDK. V důsledku toho se verze sady SDK zobrazí v dialogovém okně **Přidat nebo odebrat programy systému** Windows. Odebrání sad SDK jádra .NET, které byly nainstalovány aplikací Visual Studio pomocí samostatného instalačního programu, může dojít k přerušení sady Visual Studio. Pokud visual studio má problémy po odinstalaci sad SDK, spusťte opravit v této konkrétní verzi sady Visual Studio. V následující tabulce jsou uvedeny některé závislosti sady Visual Studio na verzích sady .NET Core SDK:

| Verze sady Visual Studio | Verze sady .NET Core SDK |
| -- | -- |
|  Visual Studio 2019 verze 16.2  | .NET Jádro SDK 2.2.4xx, 2.1.8xx |
|  Visual Studio 2019 verze 16.1 | .NET Jádro SDK 2.2.3xx, 2.1.7xx |
| Visual Studio 2019 verze 16.0 | .NET Jádro SDK 2.2.2xx, 2.1.6xx |
| Visual Studio 2017 verze 15.9 | .NET Jádro SDK 2.2.1xx, 2.1.5xx |
| Visual Studio 2017 verze 15.8 | Sada .NET Core SDK 2.1.4xx |

Počínaje Visual Studio 2019 verze 16.3, Visual Studio má na starosti vlastní kopii .NET Core SDK. Z tohoto důvodu již tyto verze sady SDK nevidíte v dialogovém okně **Přidat nebo odebrat programy.**

## <a name="remove-the-nuget-fallback-folder"></a>Odebrání záložní složky NuGet

Před sadou .NET Core 3.0 SDK instalační programy .NET Core SDK používaly *nugetfallbackfolder* k uložení mezipaměti balíčků NuGet. Tato mezipaměť byla použita při operacích, jako `dotnet restore` je například nebo `dotnet build /t:Restore`. Je `NuGetFallbackFolder` umístěn na *adrese C:\Program Files\dotnet\sdk* v systému Windows a na adrese */usr/local/share/dotnet/sdk* v systému macOS.

Tuto složku můžete odebrat, pokud:

* Vyvíjíte pouze pomocí sady .NET Core 3.0 SDK nebo novějších verzí.
* Vyvíjíte pomocí .NET Core SDK verze starší než 3.0, ale můžete pracovat online a věci mohou být pomalejší jednou.

Pokud chcete odebrat záložní složku NuGet, můžete ji odstranit, ale budete potřebovat oprávnění správce, abyste tak učinili.

Není doporučeno odstranit složku *dotnet.* Tím byste odstranili všechny globální nástroje, které jste dříve nainstalovali. Také v systému Windows:

- Přerušíte verzi Visual Studia 2019 verze 16.3 a novější. Můžete spustit **opravit** obnovit.
- Pokud jsou v dialogovém okně **Přidat nebo odebrat programy** položky .NET Core SDK, budou osamocené.

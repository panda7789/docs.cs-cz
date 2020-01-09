---
title: Odebrání modulu runtime .NET Core a sady SDK
description: Tento článek popisuje, jak určit, které verze modulu runtime .NET Core a sady SDK jsou momentálně nainstalované, a jak je odstranit v systémech Windows, Mac a Linux.
ms.date: 12/17/2019
author: billwagner
ms.author: wiwagn
ms.custom: updateeachrelease
ms.openlocfilehash: 8f8dbf7a8730712dc546643a6ef86425a3e19794
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713988"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>Postup odebrání modulu runtime .NET Core a sady SDK

V průběhu času, při instalaci aktualizovaných verzí modulu runtime .NET Core a sady SDK, můžete chtít z počítače odebrat zastaralé verze rozhraní .NET Core. Odebrání starších verzí modulu runtime může změnit modul runtime zvolený tak, aby spouštěl aplikace sdíleného rozhraní, jak je popsáno v článku [Výběr verze .NET Core](selection.md).

## <a name="should-i-remove-a-version"></a>Mám odebrat verzi?

Chování při [výběru verze .NET Core](selection.md) a kompatibilita modulu runtime .NET Core napříč aktualizacemi umožňují bezpečné odebrání předchozích verzí. Aktualizace modulu runtime .NET Core jsou kompatibilní s hlavní verzí "pásma", jako je například 1. x a 2. x. Kromě toho novější verze .NET Core SDK obecně udržují možnost vytvářet aplikace, které cílí na předchozí verze modulu runtime kompatibilním způsobem.

Obecně platí, že potřebujete jenom nejnovější sadu SDK a nejnovější verzi patch runtime, která je pro vaši aplikaci nutná. Instance, které udržují starší verze sady SDK nebo modulu runtime, zahrnují údržbu aplikací založených na **Project. JSON**. Pokud vaše aplikace nemá konkrétní důvody pro předchozí sady SDK nebo moduly runtime, můžete starší verze odstranit bezpečně.

## <a name="determine-what-is-installed"></a>Určete, co je nainstalováno

Počínaje rozhraním .NET Core 2,1 mají rozhraní .NET CLI možnosti, které můžete použít k vypsání verzí sady SDK a modulu runtime, které jsou nainstalovány na vašem počítači.  Pomocí [`dotnet --list-sdks`](../tools/dotnet.md#options) můžete zobrazit seznam sad SDK nainstalovaných v počítači. Pomocí [`dotnet --list-runtimes`](../tools/dotnet.md#options) můžete zobrazit seznam modulů runtime instalovaných v počítači. Následující text zobrazuje typický výstup pro Windows, macOS nebo Linux:

<!-- markdownlint-disable MD025 -->

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

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

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

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

# <a name="macostabmacos"></a>[macOS](#tab/macos)

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

---

## <a name="uninstalling-net-core"></a>Odinstalace .NET Core

# <a name="windowstabwindows"></a>[Windows](#tab/windows)

.NET Core používá dialogové okno **Přidat nebo odebrat programy** v systému Windows k odebrání verzí modulu runtime .NET Core a sady SDK. Následující obrázek ukazuje dialog **Přidat nebo odebrat programy** s nainstalovaným několika verzemi modulu .NET runtime a sady SDK.

![Přidat nebo odebrat programy pro odebrání .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

Vyberte všechny verze, které chcete z počítače odebrat, a klikněte na **odinstalovat**.

# <a name="linuxtablinux"></a>[Linux](#tab/linux)

K dispozici je více možností pro odinstalaci rozhraní .NET Core (buď sady SDK nebo modulu runtime) v systému Linux. Nejlepším způsobem, jak odinstalovat .NET Core, je zrcadlit akci, kterou jste použili k instalaci .NET Core. Konkrétní závislosti závisí na zvolené distribuci a metodě instalace.

> [!IMPORTANT]
> V případě instalací Red Hat si přečtěte informace o instalaci a odinstalaci .NET Core v [příručce pro Red hat Začínáme](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) .

Počínaje rozhraním .NET Core 2,1 není nutné při upgradu pomocí Správce balíčků .NET Core SDK odinstalovat. Po úspěšné instalaci novější verze aplikace `update` správce balíčků nebo příkazy `refresh` tuto starší verzi odstraní automaticky.

Pokud jste nainstalovali .NET Core pomocí Správce balíčků, použijte stejného správce balíčků pro odinstalaci sady .NET SDK nebo modulu runtime. Instalace .NET Core podporují většinu oblíbených správců balíčků. V dokumentaci pro správce balíčků distribuce vyhledejte přesnou syntaxi vašeho prostředí.

- [apt-get (8)](https://linux.die.net/man/8/apt-get) se používá v systémech založených na Debian, včetně Ubuntu.
- [Yumu (8)](https://linux.die.net/man/8/yum) se používá na Fedora, CentOS a Oracle Linux.
- [zypperu (8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) se používá v systémech OPENSUSE a SUSE Linux Enterprise (SLES).
- [DNF (8)](https://dnf.readthedocs.io/en/latest/command_ref.html) se používá v Fedora.

V téměř všech případech je příkaz k odebrání balíčku `remove`.

Název balíčku pro instalaci .NET Core SDK pro většinu správců balíčků je `dotnet-sdk`následovaný číslem verze. Počínaje verzí 2.1.300 .NET Core SDK a verze `2.1` modulu runtime jsou nutná pouze čísla hlavní verze a podverze, například, .NET Core SDK verze 2.1.300 může být odkazována jako `dotnet-sdk-2.1`balíčku. Předchozí verze vyžadují řetězec celé verze, například `dotnet-sdk-2.1.200` nutné pro 2.1.200 verze .NET Core SDK.

Pro počítače, které mají nainstalované pouze modul runtime, a ne sadu SDK, je název balíčku `dotnet-runtime-<version>` pro modul runtime .NET Core a `aspnetcore-runtime-<version>` pro celý zásobník modulu runtime.

Instalace .NET Core starší než 2,0 odinstalovaly hostitelskou aplikaci, když se sada SDK odinstalovala pomocí Správce balíčků. Pomocí `apt-get`příkaz:

```bash
apt-get remove dotnet-host
```

Všimněte si, že k `dotnet-host`není připojena žádná verze.

Pokud jste nainstalovali tarballu pomocí nástroje, je nutné pomocí ruční metody odebrat rozhraní .NET Core.

Sady SDK a moduly runtime odeberete samostatně tak, že odeberete adresář, který obsahuje tuto verzi. Chcete-li například odebrat sadu 1.0.1 SDK a modul runtime, použijte následující příkazy bash:

```bash
sudo rm -rf /usr/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/share/dotnet/host/fxr/1.0.1
```

Nadřazené adresáře pro sadu SDK a modul runtime jsou uvedeny ve výstupu příkazu `dotnet --list-sdks` a `dotnet --list-runtimes`, jak je znázorněno v předchozí tabulce.

# <a name="macostabmacos"></a>[macOS](#tab/macos)

V systému Mac musíte sady SDK a moduly runtime odebrat samostatně odebráním adresáře, který tuto verzi obsahuje. Chcete-li například odebrat sadu 1.0.1 SDK a modul runtime, použijte následující příkazy bash:

```bash
sudo rm -rf /usr/local/share/dotnet/sdk/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/1.0.1
sudo rm -rf /usr/local/share/dotnet/host/fxr/1.0.1
```

Nadřazené adresáře pro sadu SDK a modul runtime jsou uvedeny ve výstupu příkazu `dotnet --list-sdks` a `dotnet --list-runtimes`, jak je znázorněno v předchozí tabulce.

---

## <a name="net-core-uninstall-tool"></a>Nástroj pro odinstalaci .NET Core

[Nástroj pro odinstalaci .NET Core](../additional-tools/uninstall-tool.md) (`dotnet-core-uninstall`) umožňuje odebrat sady .NET Core SDK a moduly runtime ze systému. K dispozici je kolekce možností, pomocí kterých určíte, které verze se mají odinstalovat.

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a>Závislost sady Visual Studio na .NET Core SDK verzích

Před Visual Studio 2019 verze 16,3 se instalátory sady Visual Studio nazývají samostatné instalační služby .NET Core SDK. V důsledku toho se verze sady SDK zobrazí v dialogovém okně **Přidat nebo odebrat programy** v systému Windows. Odebrání sady .NET Core SDK, které byly nainstalovány v aplikaci Visual Studio pomocí samostatného instalačního programu, může poškodit aplikaci Visual Studio. Pokud má aplikace Visual Studio problémy po odinstalaci sad SDK, spusťte v této konkrétní verzi sady Visual Studio opravu. V následující tabulce jsou uvedeny některé závislosti sady Visual Studio na .NET Core SDK verzích:

| Verze sady Visual Studio | Verze .NET Core SDK |
| -- | -- |
| Visual Studio 2019 verze 16,2 | .NET Core SDK 2.2.4 xx, 2.1.8 XX |
| Visual Studio 2019 verze 16,1 | .NET Core SDK 2.2.3 xx, 2.1.7 XX |
| Visual Studio 2019 verze 16,0 | .NET Core SDK 2.2.2 xx, 2.1.6 xx |
| Visual Studio 2017 verze 15,9 | .NET Core SDK 2.2.1 xx xx, 2.1.5 XX |
| Visual Studio 2017 verze 15.8 | .NET Core SDK 2.1.4 XX |

Počínaje sadou Visual Studio 2019 16,3 se Visual Studio účtuje na vlastní kopii .NET Core SDK. Z tohoto důvodu se tyto verze sady SDK už nezobrazuje v dialogovém okně **Přidat nebo odebrat programy** .

## <a name="remove-the-nuget-fallback-folder"></a>Odebrat záložní složku NuGet

Před sadou .NET Core 3,0 SDK .NET Core SDK Instalační programy používaly *NuGetFallbackFolder* k ukládání mezipaměti balíčků NuGet. Tato mezipaměť se použila během operací, jako je `dotnet restore` nebo `dotnet build /t:Restore`. `NuGetFallbackFolder` se nachází v adresáři *C:\Program Files\dotnet\sdk* ve Windows a v */usr/local/share/dotnet/SDK* na MacOS.

Tuto složku můžete chtít odebrat, pokud:

* Vyvíjíte pouze pomocí .NET Core 3,0 SDK nebo novějších verzí.
* Vyvíjíte pomocí .NET Core SDK verzí starších než 3,0, ale můžete pracovat online a věci můžou být pomalejší.

Pokud chcete odebrat záložní složku NuGet, můžete ji odstranit, ale budete k tomu potřebovat oprávnění správce.

Nedoporučuje se odstranit složku *dotnet* . Tím by se odebraly všechny globální nástroje, které jste předtím nainstalovali. Také ve Windows:

- Budete přerušit Visual Studio 2019 verze 16,3 a novější. Můžete spustit **opravu** pro obnovení.
- Pokud v dialogovém okně **Přidat nebo odebrat programy** existují .NET Core SDK položky, budou osamocené.

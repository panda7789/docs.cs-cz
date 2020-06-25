---
title: Odebrání modulu runtime .NET Core a sady SDK
description: Tento článek popisuje, jak určit, které verze modulu runtime .NET Core a sady SDK jsou momentálně nainstalované, a jak je odstranit v systémech Windows, Mac a Linux.
author: adegeo
ms.author: adegeo
ms.date: 04/28/2020
zone_pivot_groups: operating-systems-set-one
ms.openlocfilehash: 1e4a846cf5e3d0209f5ade873520ef64abc12e7c
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324645"
---
# <a name="how-to-remove-the-net-core-runtime-and-sdk"></a>Postup odebrání modulu runtime .NET Core a sady SDK

V průběhu času, při instalaci aktualizovaných verzí modulu runtime .NET Core a sady SDK, můžete chtít z počítače odebrat zastaralé verze rozhraní .NET Core. Odebrání starších verzí modulu runtime může změnit modul runtime zvolený tak, aby spouštěl aplikace sdíleného rozhraní, jak je popsáno v článku [Výběr verze .NET Core](../versions/selection.md).

## <a name="should-i-remove-a-version"></a>Mám odebrat verzi?

Chování při [výběru verze .NET Core](../versions/selection.md) a kompatibilita modulu runtime .NET Core napříč aktualizacemi umožňují bezpečné odebrání předchozích verzí. Aktualizace modulu runtime .NET Core jsou kompatibilní s hlavní verzí "pásma", jako je například 1. x a 2. x. Kromě toho novější verze .NET Core SDK obecně udržují možnost vytvářet aplikace, které cílí na předchozí verze modulu runtime kompatibilním způsobem.

Obecně platí, že potřebujete jenom nejnovější sadu SDK a nejnovější verzi patch runtime, která je pro vaši aplikaci nutná. Instance, kde byste mohli chtít zachovat starší verze sady SDK nebo běhové verze, zahrnují údržbu *project.jsch*aplikací. Pokud vaše aplikace nemá konkrétní důvody pro předchozí sady SDK nebo moduly runtime, můžete starší verze odstranit bezpečně.

## <a name="determine-what-is-installed"></a>Určete, co je nainstalováno

Počínaje rozhraním .NET Core 2,1 mají rozhraní .NET CLI možnosti, které můžete použít k vypsání verzí sady SDK a modulu runtime, které jsou nainstalovány na vašem počítači.  Pomocí [`dotnet --list-sdks`](../tools/dotnet.md#options) zobrazíte seznam sad SDK nainstalovaných v počítači. Použijte [`dotnet --list-runtimes`](../tools/dotnet.md#options) k zobrazení seznamu modulů runtime instalovaných v počítači. Další informace najdete v tématu [Jak ověřit, zda je rozhraní .NET Core již nainstalováno](how-to-detect-installed-versions.md).

## <a name="uninstall-net-core"></a>Odinstalace .NET Core

::: zone pivot="os-windows"

.NET Core používá pro odebrání verzí modulu runtime .NET Core a sady SDK dialogové okno **funkce & aplikace** systému Windows. Následující obrázek ukazuje dialogové okno **aplikace & funkce** . Můžete vyhledat **základní sadu SDK** pro filtrování a zobrazení nainstalovaných verzí rozhraní .NET Core.

![Přidat nebo odebrat programy pro odebrání .NET Core](./media/remove-runtime-sdk-versions/programs-and-features.png)

Vyberte všechny verze, které chcete z počítače odebrat, a klikněte na **odinstalovat**.

::: zone-end

::: zone pivot="os-linux"

K dispozici je více možností pro odinstalaci rozhraní .NET Core (buď sady SDK nebo modulu runtime) v systému Linux. Nejlepším způsobem, jak odinstalovat .NET Core, je zrcadlit akci, kterou jste použili k instalaci .NET Core. Konkrétní závislosti závisí na zvolené distribuci a metodě instalace.

> [!IMPORTANT]
> V případě instalací Red Hat si přečtěte informace o instalaci a odinstalaci .NET Core v [příručce pro Red hat Začínáme](https://access.redhat.com/documentation/en-us/net_core/2.0/html/getting_started_guide/gs_install_dotnet#install_register_rehel) .

Počínaje rozhraním .NET Core 2,1 není nutné při upgradu pomocí Správce balíčků .NET Core SDK odinstalovat. Správce balíčků `update` nebo `refresh` příkazy automaticky odebere starší verzi po úspěšné instalaci novější verze.

Pokud jste nainstalovali .NET Core pomocí Správce balíčků, použijte stejného správce balíčků pro odinstalaci sady .NET SDK nebo modulu runtime. Instalace .NET Core podporují většinu oblíbených správců balíčků. Přesnou syntaxi správce balíčků distribuce najdete v dokumentaci ke konkrétní syntaxi prostředí:

- [apt-get (8)](https://linux.die.net/man/8/apt-get) se používá v systémech založených na Debian, včetně Ubuntu.
- [Yumu (8)](https://linux.die.net/man/8/yum) se používá na Fedora, CentOS a Oracle Linux.
- [zypperu (8)](https://en.opensuse.org/SDB:Zypper_manual_(plain)) se používá v systémech OPENSUSE a SUSE Linux Enterprise (SLES).
- [DNF (8)](https://dnf.readthedocs.io/en/latest/command_ref.html) se používá v Fedora.

V téměř všech případech je příkaz k odebrání balíčku `remove` .

Název balíčku pro instalaci .NET Core SDK pro většinu správců balíčků je `dotnet-sdk` následovaný číslem verze. Počínaje verzí 2.1.300 .NET Core SDK a verzí `2.1` modulu runtime jsou nutná pouze čísla hlavní verze a podverze. například .NET Core SDK verze 2.1.300 může být odkazována jako balíček `dotnet-sdk-2.1` . Předchozí verze vyžadují řetězec celé verze: například `dotnet-sdk-2.1.200` by vyžadovala 2.1.200 verze .NET Core SDK.

Pro počítače, které mají nainstalované pouze modul runtime a nikoli sadu SDK, je název balíčku `dotnet-runtime-<version>` pro modul runtime .NET Core a `aspnetcore-runtime-<version>` pro celý zásobník modulu runtime.

Instalace .NET Core starší než 2,0 odinstalovaly hostitelskou aplikaci, když se sada SDK odinstalovala pomocí Správce balíčků. Pomocí `apt-get` příkazu je tento příkaz:

```bash
apt-get remove dotnet-host
```

Všimněte si, že není připojená žádná verze `dotnet-host` .

Pokud jste nainstalovali tarballu pomocí nástroje, je nutné pomocí ruční metody odebrat rozhraní .NET Core.

V systému Linux musíte sady SDK a moduly runtime odebrat samostatně odebráním adresářů se správou verzí. Jejich odebráním se odstraní sada SDK a modul runtime z disku. Chcete-li například odebrat sadu 1.0.1 SDK a modul runtime, použijte následující příkazy bash:

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

Nadřazené adresáře pro sadu SDK a modul runtime jsou uvedeny ve výstupu `dotnet --list-sdks` `dotnet --list-runtimes` příkazu a, jak je znázorněno v předchozí tabulce.

::: zone-end

::: zone pivot="os-macos"

V systému Mac musíte sady SDK a moduly runtime odebrat samostatně tak, že odeberete adresáře s verzemi. Jejich odebráním se odstraní sada SDK a modul runtime z disku. Chcete-li například odebrat sadu 1.0.1 SDK a modul runtime, použijte následující příkazy bash:

```bash
version="1.0.1"
sudo rm -rf /usr/local/share/dotnet/sdk/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.NETCore.App/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.All/$version
sudo rm -rf /usr/local/share/dotnet/shared/Microsoft.AspNetCore.App/$version
sudo rm -rf /usr/local/share/dotnet/host/fxr/$version
```

Nadřazené adresáře pro sadu SDK a modul runtime jsou uvedeny ve výstupu `dotnet --list-sdks` `dotnet --list-runtimes` příkazu a, jak je znázorněno v předchozí tabulce.

::: zone-end

## <a name="net-core-uninstall-tool"></a>Nástroj pro odinstalaci .NET Core

[Nástroj pro odinstalaci .NET Core](../additional-tools/uninstall-tool.md) ( `dotnet-core-uninstall` ) umožňuje odebrat sady SDK a moduly runtime .NET Core ze systému. K dispozici je kolekce možností, pomocí kterých určíte, které verze se mají odinstalovat.

## <a name="visual-studio-dependency-on-net-core-sdk-versions"></a>Závislost sady Visual Studio na .NET Core SDK verzích

Před Visual Studio 2019 verze 16,3 se instalátory sady Visual Studio nazývají samostatné instalační služby .NET Core SDK. V důsledku toho se verze sady SDK zobrazí v dialogovém okně **aplikace pro Windows & funkce** . Odebrání sady .NET Core SDK, které byly nainstalovány v aplikaci Visual Studio pomocí samostatného instalačního programu, může poškodit aplikaci Visual Studio. Pokud má aplikace Visual Studio problémy po odinstalaci sad SDK, spusťte v této konkrétní verzi sady Visual Studio opravu. V následující tabulce jsou uvedeny některé závislosti sady Visual Studio na .NET Core SDK verzích:

| Verze sady Visual Studio           | Verze .NET Core SDK          |
|---------------------------------|--------------------------------|
|  Visual Studio 2019 verze 16.2  | .NET Core SDK 2.2.4 xx, 2.1.8 XX |
|  Visual Studio 2019 verze 16.1 | .NET Core SDK 2.2.3 xx, 2.1.7 XX |
| Visual Studio 2019 verze 16,0 | .NET Core SDK 2.2.2 xx, 2.1.6 xx |
| Visual Studio 2017 verze 15,9 | .NET Core SDK 2.2.1 xx xx, 2.1.5 XX |
| Visual Studio 2017 verze 15,8 | .NET Core SDK 2.1.4 XX          |

Počínaje verzí Visual Studio 2019 verze 16,3 se Visual Studio účtuje na vlastní kopii .NET Core SDK. Z tohoto důvodu se tyto verze sady SDK už nezobrazuje v dialogovém okně **aplikace & funkce** .

## <a name="remove-the-nuget-fallback-folder"></a>Odebrat záložní složku NuGet

Před sadou .NET Core 3,0 SDK .NET Core SDK Instalační programy používaly složku s názvem *NuGetFallbackFolder* k uložení mezipaměti balíčků NuGet. Tato mezipaměť se použila během operací, jako je `dotnet restore` nebo `dotnet build /t:Restore` . *NuGetFallbackFolder* se nachází v adresáři *C:\Program Files\dotnet\sdk* v systému Windows a v */usr/local/share/dotnet/SDK* na MacOS.

Tuto složku můžete chtít odebrat, pokud:

- Vyvíjíte pouze pomocí .NET Core 3,0 SDK nebo novějších verzí.
- Vyvíjíte pomocí .NET Core SDK verzí starších než 3,0, ale můžete pracovat online.

Pokud chcete odebrat záložní složku NuGet, můžete ji odstranit, ale budete k tomu potřebovat oprávnění správce.

Nedoporučuje se odstranit složku *dotnet* . Tím by se odebraly všechny globální nástroje, které jste předtím nainstalovali. Také ve Windows:

- Budete přerušit Visual Studio 2019 verze 16,3 a novější. Můžete spustit **opravu** pro obnovení.
- Pokud v dialogovém okně **aplikace & funkce** existují .NET Core SDKé položky, budou osamocené.

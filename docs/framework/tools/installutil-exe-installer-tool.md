---
title: Installutil.exe (instalační nástroj)
ms.date: 03/30/2017
helpviewer_keywords:
- uninstalling server resources
- removing server resources
- status information for installation
- installation progress reports
- installing server resources
- Installer tool
- Installutil.exe
- files, Installer tool
- progress information for installation
- reporting installation progress
ms.assetid: 3f9d0533-f895-4897-b4ea-528284e0241d
ms.openlocfilehash: caca946617c681ce6516b7184a9ea506cc67158d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105065"
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (instalační nástroj)

Instalační program je nástrojem příkazového řádku, který umožňuje nainstalovat a odinstalovat serverové zdroje spuštěním komponent nástroje v zadaných sestaveních. Tento nástroj funguje ve spojení se třídami v oboru názvů <xref:System.Configuration.Install>.

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a>Parametry

|Argument|Popis|
|--------------|-----------------|
|`assembly`|Název souboru sestavení, ve kterém se mají spustit komponenty instalačního programu. Tento parametr vynechejte, pokud chcete zadat silný název sestavení pomocí možnosti `/AssemblyName`.|

<a name="options"></a>

## <a name="options"></a>Možnosti

|Možnost|Popis|
|------------|-----------------|
|`/h[elp]`<br /><br /> -nebo-<br /><br /> `/?`|Zobrazí syntaxi příkazu a možnosti nástroje.|
|*sestavení* `/help`<br /><br /> -nebo-<br /><br /> *sestavení* `/?`|Zobrazí další možnosti, které jsou rozpoznávány jednotlivými instalačními programy v rámci zadaného sestavení, spolu se syntaxí a možnostmi příkazů pro soubor InstallUtil.exe. Tato možnost přidá text vrácený vlastností <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> každé součásti instalačního programu do textu Help souboru InstallUtil. exe.|
|`/AssemblyName`*AssemblyName*<br /><br /> , Verze = hlavní_verze. podverze *. sestavení. revize*<br /><br /> , Culture =*locale*<br /><br /> , PublicKeyToken =*PublicKeyToken*|Udává silný název sestavení, které je třeba zaregistrovat v globální mezipaměti sestavení (GAC). Název sestavení musí být plně kvalifikovaný v souladu s verzí, jazykovou verzí a veřejným klíčem sestavení. Plně kvalifikovaný název musí být v uvozovkách.<br /><br /> Například „myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0“ je plně kvalifikovaný název sestavení.|
|`/InstallStateDir=[` *directory* `]`|Určuje adresář souboru .InstallState, který obsahuje data používaná při odinstalování sestavení. Ve výchozím nastavení je to adresář obsahující sestavení.|
|`/LogFile=`[*filename*]|Určuje název souboru protokolu, do kterého je zaznamenán průběh instalace. Ve výchozím nastavení, pokud je vynechána možnost `/LogFile`, soubor protokolu s názvem *AssemblyName*. InstallLog se vytvoří. Pokud je *název souboru* vynechán, nevygeneruje se žádný soubor protokolu.|
|`/LogToConsole`= {`true`&#124;`false`}|Pokud `true`, zobrazí výstup do konzoly. Pokud `false` (výchozí), potlačí výstup do konzoly.|
|`/ShowCallStack`|Vypíše zásobník volání do souboru protokolu, jestliže v kterémkoli bodu instalace dojde k výjimce.|
|`/u`[`ninstall`]|Odinstaluje zadaná sestavení. Na rozdíl od jiných možností `/u` platí pro všechna sestavení bez ohledu na to, kde se možnost zobrazí na příkazovém řádku.|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a>Další možnosti instalačního programu

Jednotlivé instalační programy používané v rámci sestavení mohou kromě těch, které jsou uvedeny v části [Možnosti](#options) , rozpoznat i možnosti. Chcete-li získat informace o těchto možnostech, spusťte příkaz InstallUtil. exe s cestami k sestavením na příkazovém řádku spolu s možností `/?` nebo `/help`. Chcete-li zadat tyto možnosti, přidejte je do příkazového řádku spolu s možnostmi rozeznávanými souborem InstallUtil.exe.

> [!NOTE]
> Text v nápovědě k možnostem podporovaným jednotlivými komponentami instalačního programu je vrácen vlastností <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType>. Jednotlivé možnosti, které byly zadány na příkazovém řádku, jsou přístupné programově z vlastnosti <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType>.

Všechny možnosti a parametry příkazového řádku jsou zapsány do souboru protokolu instalace. Pokud však použijete parametr `/Password`, který je rozpoznáván některými součástmi instalačního programu, informace o hesle budou nahrazeny osmi hvězdičkami (*) a nebudou se zobrazovat v souboru protokolu.

> [!IMPORTANT]
> V některých případech parametry předávané instalačním programem mohou obsahovat citlivé údaje nebo informace umožňující identifikaci konkrétní osoby, které jsou ve výchozím nastavení zapsány do souboru protokolu jako prostý text. Chcete-li zabránit tomuto chování, můžete soubor protokolu potlačit zadáním `/LogFile=` (bez argumentu *filename* ) po Installutil. exe v příkazovém řádku.

## <a name="remarks"></a>Poznámky

Aplikace rozhraní .NET Framework se skládají z tradičních programových souborů a souvisejících zdrojů, jako jsou například fronty zpráv, protokoly událostí a čítače výkonu, které musí být vytvořeny při zavedení aplikace. Pomocí komponent instalačního programu sestavení můžete vytvořit tyto zdroje při instalaci vaší aplikace a odstranit je při odinstalaci aplikace. InstallUtil.exe rozpozná a spustí tyto komponenty instalačního programu.

Do příkazového řádku můžete zadat několik sestavení najednou. Každá možnost, která předchází název sestavení, se vztahuje na instalaci tohoto sestavení. S výjimkou `/u` a `/AssemblyName`jsou možnosti kumulativní, ale lze je přepsat. To znamená, že možnosti zadané pro jedno sestavení se vztahují na všechna následující sestavení, pokud dané možnosti není přidělena jiná hodnota.

Pokud spustíte Installutil.exe proti sestavení bez zadání jakékoli možnosti, do adresáře sestavení se umístí následující tři soubory:

- InstallUtil.InstallLog – obsahuje obecný popis průběhu instalace.

- *AssemblyName*. InstallLog – obsahuje informace specifické pro potvrzovací fázi procesu instalace. Další informace o potvrzovací fázi najdete v tématu metoda <xref:System.Configuration.Install.Installer.Commit%2A>.

- *AssemblyName*. InstallState – obsahuje data, která se používají k odinstalování sestavení.

InstallUtil. exe používá reflexi ke kontrole zadaných sestavení a k nalezení všech typů <xref:System.Configuration.Install.Installer>, které mají atribut <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> nastaven na `true`. Nástroj pak provede buď <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType>, nebo metodu <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> v každé instanci typu <xref:System.Configuration.Install.Installer>. InstallUtil.exe provede instalaci transakčním způsobem; to znamená, že pokud instalace jednoho sestavení selže, zruší instalace všech ostatních sestavení. Odinstalování není transakční.

Installutil.exe nemůže nainstalovat nebo odinstalovat sestavení se zpožděným podpisem, ale může nainstalovat nebo odinstalovat sestavení se silným názvem.

Od rozhraní .NET Framework verze 2.0, je 32bitová verze Common Language Runtime (CLR) dodávána pouze s 32bitovou verzí instalačního programu, zatímco 64bitová verze CLR je dodávána s 32bitovou i 64bitovou verzí instalačního programu. Jestliže používáte 64bitový CLR, 32bitová sestavení instalujte pomocí 32bitového instalačního programu a 64bitovou verzi instalačního programu použijte k instalaci 64bitových sestavení Microsoft Intermediate Language (MSIL). Obě verze instalačního programu se chovají stejně.

Installutil.exe nelze použít k nasazení služby systému Windows, která byla vytvořena pomocí C++, protože Installutil.exe nedokáže rozpoznat vložený nativní kód, který je vytvořen pomocí kompilátoru jazyka C++. Pokud se pokusíte nasadit službu C++ systému Windows pomocí nástroje Installutil. exe, bude vyvolána výjimka jako <xref:System.BadImageFormatException>. V tomto případě přesuňte kód služby do modulu C++ a pak napište objekt instalačního programu v jazyce C# nebo Visual Basic.

## <a name="examples"></a>Příklady

Následující příkaz zobrazí popis syntaxe příkazů a možností InstallUtil.exe.

```console
installutil /?
```

Následující příkaz zobrazí popis syntaxe příkazů a možností InstallUtil.exe. Také se zobrazí popis a seznam možností podporovaných součástmi instalační služby v nástroji `myAssembly.exe`, pokud byl text zprávy přiřazen k vlastnosti <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> instalačního programu.

```console
installutil /? myAssembly.exe
```

Následující příkaz spustí komponenty instalačního programu v sestavení `myAssembly.exe`.

```console
installutil myAssembly.exe
```

Následující příkaz spustí součásti instalačního programu v sestavení pomocí přepínače `/AssemblyName` a plně kvalifikovaného názvu.

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Následující příkaz spustí součásti instalačního programu v sestavení určeném názvem souboru a v sestavení určeném silným názvem. Všimněte si, že všechna sestavení určená názvem souboru musí předcházet sestavením zadaným silným názvem na příkazovém řádku, protože možnost `/AssemblyName` nelze přepsat.

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Následující příkaz spustí součásti odinstalačního nástroje v sestavení `myAssembly.exe`.

```console
installutil /u myAssembly.exe
```

Následující příkaz spustí součásti odinstalačního nástroje v sestaveních `myAssembly1.exe` a `myAssembly2.exe`.

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

Protože pozice možnosti `/u` na příkazovém řádku není důležitá, jedná se o ekvivalent následujícího příkazu.

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

Následující příkaz spustí instalační programy v sestavení `myAssembly.exe` a určí, že informace o průběhu budou zapsány do `myLog.InstallLog`.

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

Následující příkaz spustí instalační programy v sestavení `myAssembly.exe`, určuje, že informace o průběhu mají být zapsány do `myLog.InstallLog`a pomocí možnosti vlastní `/reg` instalační program, které určují, zda mají být aktualizace provedeny v registru systému.

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

Následující příkaz spustí instalační programy v sestavení `myAssembly.exe`, použije možnost vlastního `/email` instalačního programu k zadání e-mailové adresy uživatele a potlačí výstup do souboru protokolu.

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

Následující příkaz zapíše průběh instalace `myAssembly.exe` pro `myLog.InstallLog` a zapíše průběh `myTestAssembly.exe` do `myTestLog.InstallLog`.

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a>Viz také:

- <xref:System.Configuration.Install>
- [Nástroje](index.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)

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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105065"
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (instalační nástroj)

Instalační program je nástrojem příkazového řádku, který umožňuje nainstalovat a odinstalovat serverové zdroje spuštěním komponent nástroje v zadaných sestaveních. Tento nástroj pracuje ve spojení <xref:System.Configuration.Install> s třídami v oboru názvů.

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a>Parametry

|Argument|Popis|
|--------------|-----------------|
|`assembly`|Název souboru sestavení, ve kterém se mají spustit komponenty instalačního programu. Vynechte tento parametr, pokud chcete zadat silný `/AssemblyName` název sestavení pomocí možnosti.|

<a name="options"></a>

## <a name="options"></a>Možnosti

|Možnost|Popis|
|------------|-----------------|
|`/h[elp]`<br /><br /> -nebo-<br /><br /> `/?`|Zobrazí syntaxi příkazu a možnosti nástroje.|
|`/help`*montáž*<br /><br /> -nebo-<br /><br /> `/?`*montáž*|Zobrazí další možnosti, které jsou rozpoznávány jednotlivými instalačními programy v rámci zadaného sestavení, spolu se syntaxí a možnostmi příkazů pro soubor InstallUtil.exe. Tato možnost přidá text vrácený vlastností <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> každé součásti instalačního programu do textu nápovědy souboru InstallUtil.exe.|
|`/AssemblyName`"*název_sestavení*<br /><br /> ,Version=*major.minor.build.revision*<br /><br /> ,Kultura =*národní prostředí*<br /><br /> ,PublicKeyToken=*publicKeyToken*"|Udává silný název sestavení, které je třeba zaregistrovat v globální mezipaměti sestavení (GAC). Název sestavení musí být plně kvalifikovaný v souladu s verzí, jazykovou verzí a veřejným klíčem sestavení. Plně kvalifikovaný název musí být v uvozovkách.<br /><br /> Například „myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0“ je plně kvalifikovaný název sestavení.|
|`/InstallStateDir=[`*název adresáře*`]`|Určuje adresář souboru .InstallState, který obsahuje data používaná při odinstalování sestavení. Ve výchozím nastavení je to adresář obsahující sestavení.|
|`/LogFile=`[*název souboru*]|Určuje název souboru protokolu, do kterého je zaznamenán průběh instalace. Ve výchozím nastavení, pokud je `/LogFile` tato možnost vynechána, soubor protokolu s názvem *název_assembly*. InstallLog je vytvořen. Pokud je *název souboru* vynechán, není generován žádný soubor protokolu.|
|`/LogToConsole`={`true` `false`&#124;}|Pokud `true`zobrazí výstup do konzoly. Pokud `false` (výchozí), potlačí výstup do konzoly.|
|`/ShowCallStack`|Vypíše zásobník volání do souboru protokolu, jestliže v kterémkoli bodu instalace dojde k výjimce.|
|`/u`[`ninstall`]|Odinstaluje zadaná sestavení. Na rozdíl od `/u` ostatních možností platí pro všechna sestavení bez ohledu na to, kde se tato možnost objeví na příkazovém řádku.|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a>Další možnosti instalačního programu

Jednotliví instalátoři, kteří se používají v rámci sestavy, mohou kromě možností uvedených v části [Možnosti](#options) rozpoznat i možnosti. Chcete-li se o těchto možnostech dozvědět, spusťte soubor InstallUtil.exe s cestami sestavení na příkazovém řádku spolu s možností `/?` nebo. `/help` Chcete-li zadat tyto možnosti, přidejte je do příkazového řádku spolu s možnostmi rozeznávanými souborem InstallUtil.exe.

> [!NOTE]
> Text nápovědy k možnostem podporovaným jednotlivými <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> součástmi instalačního programu je vrácen vlastností. Jednotlivé možnosti, které byly zadány na příkazovém <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> řádku, jsou přístupně programově z vlastnosti.

Všechny možnosti a parametry příkazového řádku jsou zapsány do souboru protokolu instalace. Pokud však použijete `/Password` parametr, který je rozpoznán některými součástmi instalačního programu, budou informace o hesle nahrazeny osmi hvězdičkami (*) a nezobrazí se v souboru protokolu.

> [!IMPORTANT]
> V některých případech parametry předávané instalačním programem mohou obsahovat citlivé údaje nebo informace umožňující identifikaci konkrétní osoby, které jsou ve výchozím nastavení zapsány do souboru protokolu jako prostý text. Chcete-li tomuto chování zabránit, můžete `/LogFile=` potlačit soubor protokolu zadáním (bez *argumentu názvu souboru)* po installutil.exe na příkazovém řádku.

## <a name="remarks"></a>Poznámky

Aplikace rozhraní .NET Framework se skládají z tradičních programových souborů a souvisejících zdrojů, jako jsou například fronty zpráv, protokoly událostí a čítače výkonu, které musí být vytvořeny při zavedení aplikace. Pomocí komponent instalačního programu sestavení můžete vytvořit tyto zdroje při instalaci vaší aplikace a odstranit je při odinstalaci aplikace. InstallUtil.exe rozpozná a spustí tyto komponenty instalačního programu.

Do příkazového řádku můžete zadat několik sestavení najednou. Každá možnost, která předchází název sestavení, se vztahuje na instalaci tohoto sestavení. S `/u` výjimkou `/AssemblyName`a , možnosti jsou kumulativní, ale overridable. To znamená, že možnosti zadané pro jedno sestavení se vztahují na všechna následující sestavení, pokud dané možnosti není přidělena jiná hodnota.

Pokud spustíte Installutil.exe proti sestavení bez zadání jakékoli možnosti, do adresáře sestavení se umístí následující tři soubory:

- InstallUtil.InstallLog – obsahuje obecný popis průběhu instalace.

- *název_sestavení*. InstallLog - Obsahuje informace specifické pro fázi potvrzení procesu instalace. Další informace o fázi potvrzení <xref:System.Configuration.Install.Installer.Commit%2A> naleznete v metodě.

- *název_sestavení*. InstallState - Obsahuje data použitá k odinstalaci sestavení.

Installutil.exe používá reflexe ke kontrole zadaných <xref:System.Configuration.Install.Installer> sestavení a <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> najít `true`všechny typy, které mají atribut nastaven na . Nástroj pak provede buď <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> nebo <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> metodu na <xref:System.Configuration.Install.Installer> každé instanci typu. InstallUtil.exe provede instalaci transakčním způsobem; to znamená, že pokud instalace jednoho sestavení selže, zruší instalace všech ostatních sestavení. Odinstalování není transakční.

Installutil.exe nemůže nainstalovat nebo odinstalovat sestavení se zpožděným podpisem, ale může nainstalovat nebo odinstalovat sestavení se silným názvem.

Od rozhraní .NET Framework verze 2.0, je 32bitová verze Common Language Runtime (CLR) dodávána pouze s 32bitovou verzí instalačního programu, zatímco 64bitová verze CLR je dodávána s 32bitovou i 64bitovou verzí instalačního programu. Jestliže používáte 64bitový CLR, 32bitová sestavení instalujte pomocí 32bitového instalačního programu a 64bitovou verzi instalačního programu použijte k instalaci 64bitových sestavení Microsoft Intermediate Language (MSIL). Obě verze instalačního programu se chovají stejně.

Installutil.exe nelze použít k nasazení služby systému Windows, která byla vytvořena pomocí C++, protože Installutil.exe nedokáže rozpoznat vložený nativní kód, který je vytvořen pomocí kompilátoru jazyka C++. Pokud se pokusíte nasadit službu Systému Windows c++ <xref:System.BadImageFormatException> s Installutil.exe, výjimka, jako je například vyvolána. V tomto případě přesuňte kód služby do modulu C++ a pak napište objekt instalačního programu v jazyce C# nebo Visual Basic.

## <a name="examples"></a>Příklady

Následující příkaz zobrazí popis syntaxe příkazů a možností InstallUtil.exe.

```console
installutil /?
```

Následující příkaz zobrazí popis syntaxe příkazů a možností InstallUtil.exe. Zobrazí také popis a seznam možností podporovaných součástmi `myAssembly.exe` instalačního programu v aplikaci, <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> pokud byl vlastnosti instalačního programu přiřazen text nápovědy.

```console
installutil /? myAssembly.exe
```

Následující příkaz provede součásti instalačního programu `myAssembly.exe`v sestavě .

```console
installutil myAssembly.exe
```

Následující příkaz provede součásti instalačního programu v `/AssemblyName` sestavě pomocí přepínače a plně kvalifikovaného názvu.

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Následující příkaz spustí součásti instalačního programu v sestavení určeném názvem souboru a v sestavení určeném silným názvem. Všimněte si, že všechna sestavení určená názvem souboru musí předcházet sestavením určeným silným názvem na příkazovém řádku, protože `/AssemblyName` tuto možnost nelze přepsat.

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Následující příkaz provede součásti odinstalačního programu `myAssembly.exe`v sestavě .

```console
installutil /u myAssembly.exe
```

Následující příkaz provede součásti odinstalačního programu `myAssembly1.exe` v `myAssembly2.exe`sestavách a .

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

Vzhledem k `/u` tomu, že pozice možnosti na příkazovém řádku není důležitá, je to ekvivalentní následujícímu příkazu.

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

Následující příkaz provede instalační programy v `myAssembly.exe` sestavení a určí, že `myLog.InstallLog`informace o průběhu budou zapsány do aplikace .

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

Následující příkaz provede instalační programy v `myAssembly.exe`sestavení , určí, že `myLog.InstallLog`informace o průběhu by `/reg` měly být zapsány do aplikace a pomocí vlastní možnosti instalačních programů určí, že aktualizace by měly být provedeny v systémovém registru.

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

Následující příkaz provede instalační programy v `myAssembly.exe`sestavení , použije vlastní `/email` možnost instalačního programu k zadání e-mailové adresy uživatele a potlačí výstup do souboru protokolu.

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

Následující příkaz zapíše průběh `myAssembly.exe` `myLog.InstallLog` instalace pro a `myTestAssembly.exe` `myTestLog.InstallLog`zapíše průběh pro do .

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a>Viz také

- <xref:System.Configuration.Install>
- [Nástroje](index.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)

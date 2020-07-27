---
title: Installutil.exe (instalační nástroj)
description: Použijte Installutil.exe nástroj Installer Tool. Tento nástroj umožňuje nainstalovat nebo odinstalovat prostředky serveru spuštěním součástí instalačního programu v zadaných sestaveních.
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
ms.openlocfilehash: 042e5f64a7a863173db9c4e601d3152b0df46d97
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164445"
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (instalační nástroj)

Instalační program je nástrojem příkazového řádku, který umožňuje nainstalovat a odinstalovat serverové zdroje spuštěním komponent nástroje v zadaných sestaveních. Tento nástroj funguje ve spojení se třídami v <xref:System.Configuration.Install> oboru názvů.

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```console
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...
```

## <a name="parameters"></a>Parametry

|Argument|Popis|
|--------------|-----------------|
|`assembly`|Název souboru sestavení, ve kterém se mají spustit komponenty instalačního programu. Tento parametr vynechejte, pokud chcete zadat silný název sestavení pomocí `/AssemblyName` Možnosti.|

<a name="options"></a>

## <a name="options"></a>Možnosti

|Možnost|Popis|
|------------|-----------------|
|`/h[elp]`<br /><br /> -nebo-<br /><br /> `/?`|Zobrazí syntaxi příkazu a možnosti nástroje.|
|`/help`*sestavení*<br /><br /> -nebo-<br /><br /> `/?`*sestavení*|Zobrazí další možnosti, které jsou rozpoznávány jednotlivými instalačními programy v rámci zadaného sestavení, spolu se syntaxí a možnostmi příkazů pro soubor InstallUtil.exe. Tato možnost přidá text vrácený každou vlastností komponenty instalačního programu <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> do textu help InstallUtil.exe.|
|`/AssemblyName`*AssemblyName*<br /><br /> , Verze = hlavní_verze. podverze *. sestavení. revize*<br /><br /> , Culture =*locale*<br /><br /> , PublicKeyToken =*PublicKeyToken*|Udává silný název sestavení, které je třeba zaregistrovat v globální mezipaměti sestavení (GAC). Název sestavení musí být plně kvalifikovaný v souladu s verzí, jazykovou verzí a veřejným klíčem sestavení. Plně kvalifikovaný název musí být v uvozovkách.<br /><br /> Například „myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0“ je plně kvalifikovaný název sestavení.|
|`/InstallStateDir=[`*adresář*`]`|Určuje adresář souboru .InstallState, který obsahuje data používaná při odinstalování sestavení. Ve výchozím nastavení je to adresář obsahující sestavení.|
|`/LogFile=`[*filename*]|Určuje název souboru protokolu, do kterého je zaznamenán průběh instalace. Ve výchozím nastavení, pokud `/LogFile` je tato možnost vynechána, soubor protokolu s názvem *AssemblyName*. InstallLog se vytvoří. Pokud je *název souboru* vynechán, nevygeneruje se žádný soubor protokolu.|
|`/LogToConsole`= { `true`&#124;`false` }|Pokud `true` se zobrazí výstup do konzoly nástroje. Pokud `false` (výchozí), potlačí výstup do konzoly.|
|`/ShowCallStack`|Vypíše zásobník volání do souboru protokolu, jestliže v kterémkoli bodu instalace dojde k výjimce.|
|`/u`[`ninstall`]|Odinstaluje zadaná sestavení. Na rozdíl od jiných možností `/u` platí pro všechna sestavení bez ohledu na to, kde se možnost zobrazí na příkazovém řádku.|

<a name="cmdline"></a>

## <a name="additional-installer-options"></a>Další možnosti instalačního programu

Jednotlivé instalační programy používané v rámci sestavení mohou kromě těch, které jsou uvedeny v části [Možnosti](#options) , rozpoznat i možnosti. Chcete-li získat informace o těchto možnostech, spusťte InstallUtil.exe s cestami sestavení na příkazovém řádku spolu s `/?` možností nebo `/help` . Chcete-li zadat tyto možnosti, přidejte je do příkazového řádku spolu s možnostmi rozeznávanými souborem InstallUtil.exe.

> [!NOTE]
> Tato vlastnost vrací text Help na možnostech podporovaných jednotlivými součástmi instalačního programu <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> . Jednotlivé možnosti, které byly zadány na příkazovém řádku, jsou přístupné z vlastnosti programově <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> .

Všechny možnosti a parametry příkazového řádku jsou zapsány do souboru protokolu instalace. Pokud však použijete `/Password` parametr, který je rozpoznáván některými komponentami instalačního programu, informace o hesle budou nahrazeny osmi hvězdičkami (*) a nezobrazí se v souboru protokolu.

> [!IMPORTANT]
> V některých případech parametry předávané instalačním programem mohou obsahovat citlivé údaje nebo informace umožňující identifikaci konkrétní osoby, které jsou ve výchozím nastavení zapsány do souboru protokolu jako prostý text. Chcete-li zabránit tomuto chování, můžete soubor protokolu potlačit zadáním `/LogFile=` (bez argumentu *filename* ) po Installutil.exe v příkazovém řádku.

## <a name="remarks"></a>Poznámky

Aplikace rozhraní .NET Framework se skládají z tradičních programových souborů a souvisejících zdrojů, jako jsou například fronty zpráv, protokoly událostí a čítače výkonu, které musí být vytvořeny při zavedení aplikace. Pomocí komponent instalačního programu sestavení můžete vytvořit tyto zdroje při instalaci vaší aplikace a odstranit je při odinstalaci aplikace. InstallUtil.exe rozpozná a spustí tyto komponenty instalačního programu.

Do příkazového řádku můžete zadat několik sestavení najednou. Každá možnost, která předchází název sestavení, se vztahuje na instalaci tohoto sestavení. S výjimkou `/u` a `/AssemblyName` jsou možnosti kumulativní, ale lze přepsat. To znamená, že možnosti zadané pro jedno sestavení se vztahují na všechna následující sestavení, pokud dané možnosti není přidělena jiná hodnota.

Pokud spustíte Installutil.exe proti sestavení bez zadání jakékoli možnosti, do adresáře sestavení se umístí následující tři soubory:

- InstallUtil.InstallLog – obsahuje obecný popis průběhu instalace.

- *AssemblyName*. InstallLog – obsahuje informace specifické pro potvrzovací fázi procesu instalace. Další informace o potvrzovací fázi naleznete v <xref:System.Configuration.Install.Installer.Commit%2A> metodě.

- *AssemblyName*. InstallState – obsahuje data, která se používají k odinstalování sestavení.

Installutil.exe používá reflexi ke kontrole zadaných sestavení a k nalezení všech <xref:System.Configuration.Install.Installer> typů, které mají <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> atribut nastaven na `true` . Nástroj pak provede buď metodu, <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> nebo <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> v každé instanci <xref:System.Configuration.Install.Installer> typu. InstallUtil.exe provede instalaci transakčním způsobem; to znamená, že pokud instalace jednoho sestavení selže, zruší instalace všech ostatních sestavení. Odinstalování není transakční.

Installutil.exe nemůže nainstalovat nebo odinstalovat sestavení se zpožděným podpisem, ale může nainstalovat nebo odinstalovat sestavení se silným názvem.

Od rozhraní .NET Framework verze 2.0, je 32bitová verze Common Language Runtime (CLR) dodávána pouze s 32bitovou verzí instalačního programu, zatímco 64bitová verze CLR je dodávána s 32bitovou i 64bitovou verzí instalačního programu. Jestliže používáte 64bitový CLR, 32bitová sestavení instalujte pomocí 32bitového instalačního programu a 64bitovou verzi instalačního programu použijte k instalaci 64bitových sestavení Microsoft Intermediate Language (MSIL). Obě verze instalačního programu se chovají stejně.

Installutil.exe nelze použít k nasazení služby systému Windows, která byla vytvořena pomocí C++, protože Installutil.exe nedokáže rozpoznat vložený nativní kód, který je vytvořen pomocí kompilátoru jazyka C++. Pokud se pokusíte nasadit službu Windows C++ pomocí Installutil.exe, bude vyvolána výjimka, jako například <xref:System.BadImageFormatException> . V tomto případě přesuňte kód služby do modulu C++ a pak napište objekt instalačního programu v jazyce C# nebo Visual Basic.

## <a name="examples"></a>Příklady

Následující příkaz zobrazí popis syntaxe příkazů a možností InstallUtil.exe.

```console
installutil /?
```

Následující příkaz zobrazí popis syntaxe příkazů a možností InstallUtil.exe. Také se zobrazí popis a seznam možností podporovaných součástmi instalační služby v nástroji, `myAssembly.exe` Pokud byl text zprávy přiřazen vlastnosti instalačního programu <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> .

```console
installutil /? myAssembly.exe
```

Následující příkaz spustí součásti instalačního programu v sestavení `myAssembly.exe` .

```console
installutil myAssembly.exe
```

Následující příkaz spustí komponenty instalačního programu v sestavení pomocí `/AssemblyName` přepínače a plně kvalifikovaného názvu.

```console
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Následující příkaz spustí součásti instalačního programu v sestavení určeném názvem souboru a v sestavení určeném silným názvem. Všimněte si, že všechna sestavení určená názvem souboru musí předcházet sestavení zadaným silným názvem na příkazovém řádku, protože `/AssemblyName` možnost nelze přepsat.

```console
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"
```

Následující příkaz spustí součásti odinstalačního nástroje v sestavení `myAssembly.exe` .

```console
installutil /u myAssembly.exe
```

Následující příkaz spustí součásti odinstalačního nástroje v sestaveních `myAssembly1.exe` a `myAssembly2.exe` .

```console
installutil myAssembly1.exe /u myAssembly2.exe
```

Protože pozice `/u` Možnosti na příkazovém řádku není důležitá, jedná se o ekvivalent následujícího příkazu.

```console
installutil /u myAssembly1.exe myAssembly2.exe
```

Následující příkaz spustí instalační programy v sestavení `myAssembly.exe` a určí, že informace o průběhu budou zapsány do `myLog.InstallLog` .

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe
```

Následující příkaz spustí instalační programy v sestavení `myAssembly.exe` , určí, zda mají být do nástroje zapisovány informace o průběhu `myLog.InstallLog` , a pomocí vlastní možnosti instalační program `/reg` určí, zda mají být aktualizace provedeny v registru systému.

```console
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe
```

Následující příkaz spustí instalační programy v sestavení `myAssembly.exe` , použije vlastní možnost instalačního programu `/email` k zadání e-mailové adresy uživatele a potlačí výstup do souboru protokolu.

```console
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe
```

Následující příkaz zapíše průběh instalace pro a `myAssembly.exe` `myLog.InstallLog` zapíše průběh pro `myTestAssembly.exe` do `myTestLog.InstallLog` .

```console
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe
```

## <a name="see-also"></a>Viz také

- <xref:System.Configuration.Install>
- [Nástroje](index.md)
- [Výzvy příkazového řádku](developer-command-prompt-for-vs.md)

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ec7e498e0f0634d4f0e104247b430fb591f702ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (instalační nástroj)
Instalační program je nástrojem příkazového řádku, který umožňuje nainstalovat a odinstalovat serverové zdroje spuštěním komponent nástroje v zadaných sestaveních. Tento nástroj funguje ve spojení s třídami v <xref:System.Configuration.Install> oboru názvů.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|`assembly`|Název souboru sestavení, ve kterém se mají spustit komponenty instalačního programu. Tento parametr vynecháte, pokud chcete zadat silné název sestavení pomocí `/AssemblyName` možnost.|  
  
<a name="options"></a>   
## <a name="options"></a>Možnosti  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/h[elp]`<br /><br /> -nebo-<br /><br /> `/?`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|`/help` *Sestavení*<br /><br /> -nebo-<br /><br /> `/?` *Sestavení*|Zobrazí další možnosti, které jsou rozpoznávány jednotlivými instalačními programy v rámci zadaného sestavení, spolu se syntaxí a možnostmi příkazů pro soubor InstallUtil.exe. Tato možnost rozšíří text vrácený jednotlivé komponenty Instalační program <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> vlastnost text nápovědy pro InstallUtil.exe.|  
|`/AssemblyName` "*assemblyName*<br /><br /> ,Version=*major.minor.build.revision*<br /><br /> , Culture =*národní prostředí*<br /><br /> ,PublicKeyToken=*publicKeyToken*"|Udává silný název sestavení, které je třeba zaregistrovat v globální mezipaměti sestavení (GAC). Název sestavení musí být plně kvalifikovaný v souladu s verzí, jazykovou verzí a veřejným klíčem sestavení. Plně kvalifikovaný název musí být v uvozovkách.<br /><br /> Například „myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0“ je plně kvalifikovaný název sestavení.|  
|`/InstallStateDir=[` *directoryName* `]`|Určuje adresář souboru .InstallState, který obsahuje data používaná při odinstalování sestavení. Ve výchozím nastavení je to adresář obsahující sestavení.|  
|`/LogFile=`[*filename*]|Určuje název souboru protokolu, do kterého je zaznamenán průběh instalace. Ve výchozím nastavení pokud `/LogFile` není zadán parametr, soubor protokolu s názvem *assemblyname*. InstallLog se vytvoří. Pokud *filename* je tento parametr vynechán, je generován žádný soubor protokolu.|  
|`/LogToConsole`={`true`&#124;`false`}|Pokud `true`, zobrazí výstup do konzoly. Pokud `false` (výchozí), potlačí výstup do konzoly.|  
|`/ShowCallStack`|Vypíše zásobník volání do souboru protokolu, jestliže v kterémkoli bodu instalace dojde k výjimce.|  
|`/u`[`ninstall`]|Odinstaluje zadaná sestavení. Na rozdíl od ostatních možností `/u` platí pro všechna sestavení bez ohledu na to, kde se zobrazí možnost na příkazovém řádku.|  
  
<a name="cmdline"></a>   
## <a name="additional-installer-options"></a>Další možnosti instalačního programu  
 Jednotlivé instalační programy použité v rámci sestavení může rozpoznat možnosti kromě oprávnění uvedených v [možnosti](#options) části. Další informace o těchto možnostech najdete spusťte InstallUtil.exe s cesty sestavení na příkazovém řádku spolu s `/?` nebo `/help` možnost. Chcete-li zadat tyto možnosti, přidejte je do příkazového řádku spolu s možnostmi rozeznávanými souborem InstallUtil.exe.  
  
> [!NOTE]
>  Vrátí text nápovědy na možnosti podporované instalačního programu jednotlivých součástí <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> vlastnost. Jsou přístupné prostřednictvím kódu programu z jednotlivých možností, které byly zadány na příkazovém řádku <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> vlastnost.  
  
 Všechny možnosti a parametry příkazového řádku jsou zapsány do souboru protokolu instalace. Ale pokud používáte `/Password` parametr, který je rozpoznáno některé součásti instalačního programu, informace o hesle budou nahrazeny osm hvězdičky (*) a nezobrazí se v souboru protokolu.  
  
> [!IMPORTANT]
>  V některých případech parametry předávané instalačním programem mohou obsahovat citlivé údaje nebo informace umožňující identifikaci konkrétní osoby, které jsou ve výchozím nastavení zapsány do souboru protokolu jako prostý text. Aby toto chování můžete potlačit zadáním soubor protokolu `/LogFile=` (bez *filename* argument) po Installutil.exe na příkazovém řádku.  
  
## <a name="remarks"></a>Poznámky  
 Aplikace rozhraní .NET Framework se skládají z tradičních programových souborů a souvisejících zdrojů, jako jsou například fronty zpráv, protokoly událostí a čítače výkonu, které musí být vytvořeny při zavedení aplikace. Pomocí komponent instalačního programu sestavení můžete vytvořit tyto zdroje při instalaci vaší aplikace a odstranit je při odinstalaci aplikace. InstallUtil.exe rozpozná a spustí tyto komponenty instalačního programu.  
  
 Do příkazového řádku můžete zadat několik sestavení najednou. Každá možnost, která předchází název sestavení, se vztahuje na instalaci tohoto sestavení. S výjimkou `/u` a `/AssemblyName`, jsou možnosti vyskytne. To znamená, že možnosti zadané pro jedno sestavení se vztahují na všechna následující sestavení, pokud dané možnosti není přidělena jiná hodnota.  
  
 Pokud spustíte Installutil.exe proti sestavení bez zadání jakékoli možnosti, do adresáře sestavení se umístí následující tři soubory:  
  
-   InstallUtil.InstallLog – obsahuje obecný popis průběhu instalace.  
  
-   *AssemblyName*. InstallLog - obsahuje informace specifické pro fázi potvrzení procesu instalace. Další informace týkající se fáze potvrzení najdete v tématu <xref:System.Configuration.Install.Installer.Commit%2A> metoda.  
  
-   *AssemblyName*. InstallState - obsahuje data použít k odinstalaci sestavení.  
  
 InstallUtil.exe používá reflexe, chcete-li prověřit zadaného sestavení a najít všechny <xref:System.Configuration.Install.Installer> typy, které mají <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> atribut nastaven na `true`. Nástroj potom provede buď <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> nebo <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> metoda na každou instanci <xref:System.Configuration.Install.Installer> typu. InstallUtil.exe provede instalaci transakčním způsobem; to znamená, že pokud instalace jednoho sestavení selže, zruší instalace všech ostatních sestavení. Odinstalování není transakční.  
  
 Installutil.exe nemůže nainstalovat nebo odinstalovat sestavení se zpožděným podpisem, ale může nainstalovat nebo odinstalovat sestavení se silným názvem.  
  
 Od rozhraní .NET Framework verze 2.0, je 32bitová verze Common Language Runtime (CLR) dodávána pouze s 32bitovou verzí instalačního programu, zatímco 64bitová verze CLR je dodávána s 32bitovou i 64bitovou verzí instalačního programu. Jestliže používáte 64bitový CLR, 32bitová sestavení instalujte pomocí 32bitového instalačního programu a 64bitovou verzi instalačního programu použijte k instalaci 64bitových sestavení Microsoft Intermediate Language (MSIL). Obě verze instalačního programu se chovají stejně.  
  
 Installutil.exe nelze použít k nasazení služby systému Windows, která byla vytvořena pomocí C++, protože Installutil.exe nedokáže rozpoznat vložený nativní kód, který je vytvořen pomocí kompilátoru jazyka C++. Pokud se pokusíte nasazení služby C++ Windows s Installutil.exe výjimku, jako <xref:System.BadImageFormatException> bude vyvolána. V tomto případě přesuňte kód služby do modulu C++ a pak napište objekt instalačního programu v jazyce C# nebo Visual Basic.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz zobrazí popis syntaxe příkazů a možností InstallUtil.exe.  
  
```  
installutil /?  
```  
  
 Následující příkaz zobrazí popis syntaxe příkazů a možností InstallUtil.exe. Zobrazuje také popis a seznam možností podporovanou instalační program komponenty `myAssembly.exe` Pokud byl přiřazen textu nápovědy instalačního programu <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> vlastnost.  
  
```  
installutil /? myAssembly.exe  
```  
  
 Následující příkaz spustí instalační program součásti v sestavení `myAssembly.exe`.  
  
```  
installutil myAssembly.exe  
```  
  
 Tento příkaz spustí instalační program součásti v sestavení pomocí `/AssemblyName` přepínač a plně kvalifikovaný název.  
  
```  
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 Následující příkaz spustí součásti instalačního programu v sestavení určeném názvem souboru a v sestavení určeném silným názvem. Všimněte si, že ve všech sestaveních určeného názvu souboru musí předchází sestavení určený silným názvem na příkazovém řádku, protože `/AssemblyName` možnost nelze přepsat.  
  
```  
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 Tento příkaz spustí komponenty odinstalační program, který v sestavení `myAssembly.exe`.  
  
```  
installutil /u myAssembly.exe   
```  
  
 Tento příkaz spustí v sestavení komponenty uninistaller `myAssembly1.exe` a `myAssembly2.exe`.  
  
```  
installutil myAssembly1.exe /u myAssembly2.exe  
```  
  
 Protože pozici `/u` možnost na příkazovém řádku není důležité, jde o ekvivalent následující příkaz.  
  
```  
installutil /u myAssembly1.exe myAssembly2.exe  
```  
  
 Tento příkaz spustí instalační služby v sestavení `myAssembly.exe` a určuje, že informace o průběhu budou zapisovat do `myLog.InstallLog`.  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe   
```  
  
 Tento příkaz spustí instalační služby v sestavení `myAssembly.exe`, určuje, zda mají být informace o průběhu zapisovány do `myLog.InstallLog`a používá vlastní instalační programy se `/reg` můžete určit, že aktualizace je třeba v systému registru.  
  
```  
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe  
```  
  
 Tento příkaz spustí instalační služby v sestavení `myAssembly.exe`, používá instalační program je vlastní `/email` možnost zadat e-mailovou adresu uživatele a potlačí výstup do souboru protokolu.  
  
```  
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe  
```  
  
 Následující příkaz zapíše průběh instalace pro `myAssembly.exe` k `myLog.InstallLog` a zapisuje průběh pro `myTestAssembly.exe` k `myTestLog.InstallLog`.  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe  
```  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Configuration.Install>  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

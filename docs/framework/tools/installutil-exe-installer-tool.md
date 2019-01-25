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
ms.openlocfilehash: e2cba7099b84cb8a11fb7c11fae960293eb60a18
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54658257"
---
# <a name="installutilexe-installer-tool"></a>Installutil.exe (instalační nástroj)
Instalační program je nástrojem příkazového řádku, který umožňuje nainstalovat a odinstalovat serverové zdroje spuštěním komponent nástroje v zadaných sestaveních. Tento nástroj funguje ve spojení s třídami v <xref:System.Configuration.Install> oboru názvů.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
installutil [/u[ninstall]] [options] assembly [[options] assembly] ...  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|`assembly`|Název souboru sestavení, ve kterém se mají spustit komponenty instalačního programu. Tento parametr vynechat, pokud chcete zadat silný název sestavení pomocí `/AssemblyName` možnost.|  
  
<a name="options"></a>   
## <a name="options"></a>Možnosti  
  
|Možnost|Popis|  
|------------|-----------------|  
|`/h[elp]`<br /><br /> -nebo-<br /><br /> `/?`|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|`/help` *Sestavení*<br /><br /> -nebo-<br /><br /> `/?` *Sestavení*|Zobrazí další možnosti, které jsou rozpoznávány jednotlivými instalačními programy v rámci zadaného sestavení, spolu se syntaxí a možnostmi příkazů pro soubor InstallUtil.exe. Tato možnost přidá text vrácený každé komponenty instalačního programu <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> vlastnost textu nápovědy souboru InstallUtil.exe.|  
|`/AssemblyName` "*assemblyName*<br /><br /> ,Version=*major.minor.build.revision*<br /><br /> , Jazyková verze =*národního prostředí*<br /><br /> ,PublicKeyToken=*publicKeyToken*"|Udává silný název sestavení, které je třeba zaregistrovat v globální mezipaměti sestavení (GAC). Název sestavení musí být plně kvalifikovaný v souladu s verzí, jazykovou verzí a veřejným klíčem sestavení. Plně kvalifikovaný název musí být v uvozovkách.<br /><br /> Například „myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0“ je plně kvalifikovaný název sestavení.|  
|`/InstallStateDir=[` *directoryName* `]`|Určuje adresář souboru .InstallState, který obsahuje data používaná při odinstalování sestavení. Ve výchozím nastavení je to adresář obsahující sestavení.|  
|`/LogFile=`[*filename*]|Určuje název souboru protokolu, do kterého je zaznamenán průběh instalace. Ve výchozím nastavení pokud `/LogFile` možnost vynecháte, soubor protokolu s názvem *assemblyname*. InstallLog se vytvoří. Pokud *filename* je tento parametr vynechán, je generována žádný soubor protokolu.|  
|`/LogToConsole`={`true`&#124;`false`}|Pokud `true`, výstup se vypíše do konzoly. Pokud `false` (výchozí), potlačí výstup na konzolu.|  
|`/ShowCallStack`|Vypíše zásobník volání do souboru protokolu, jestliže v kterémkoli bodu instalace dojde k výjimce.|  
|`/u`[`ninstall`]|Odinstaluje zadaná sestavení. Na rozdíl od ostatních možností `/u` vztahuje na všechna sestavení bez ohledu na to, kde se zobrazí možnost na příkazovém řádku.|  
  
<a name="cmdline"></a>   
## <a name="additional-installer-options"></a>Další možnosti instalačního programu  
 Jednotlivé instalační programy používané v rámci sestavení pravděpodobně rozpoznávají možnosti kromě oprávnění uvedených v seznamu [možnosti](#options) oddílu. Další informace o těchto možnostech, spusťte soubor InstallUtil.exe s cestami sestavení na příkazovém řádku spolu s `/?` nebo `/help` možnost. Chcete-li zadat tyto možnosti, přidejte je do příkazového řádku spolu s možnostmi rozeznávanými souborem InstallUtil.exe.  
  
> [!NOTE]
>  Text nápovědy týkající se možností podporovaných jednotlivými komponentami instalačního programu je vrácený <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> vlastnost. Jsou přístupné prostřednictvím kódu programu z jednotlivých možností, které byly zadány v příkazovém řádku <xref:System.Configuration.Install.Installer.Context%2A?displayProperty=nameWithType> vlastnost.  
  
 Všechny možnosti a parametry příkazového řádku jsou zapsány do souboru protokolu instalace. Nicméně pokud použijete `/Password` parametr, který je rozpoznáván některými komponentami instalačního programu, informace o hesle se nahradí osmi hvězdičkami (*) a nezobrazí se v souboru protokolu.  
  
> [!IMPORTANT]
>  V některých případech parametry předávané instalačním programem mohou obsahovat citlivé údaje nebo informace umožňující identifikaci konkrétní osoby, které jsou ve výchozím nastavení zapsány do souboru protokolu jako prostý text. K takovému chování můžete potlačit soubor protokolu zadáním `/LogFile=` (bez *filename* argument) za Installutil.exe v příkazovém řádku.  
  
## <a name="remarks"></a>Poznámky  
 Aplikace rozhraní .NET Framework se skládají z tradičních programových souborů a souvisejících zdrojů, jako jsou například fronty zpráv, protokoly událostí a čítače výkonu, které musí být vytvořeny při zavedení aplikace. Pomocí komponent instalačního programu sestavení můžete vytvořit tyto zdroje při instalaci vaší aplikace a odstranit je při odinstalaci aplikace. InstallUtil.exe rozpozná a spustí tyto komponenty instalačního programu.  
  
 Do příkazového řádku můžete zadat několik sestavení najednou. Každá možnost, která předchází název sestavení, se vztahuje na instalaci tohoto sestavení. S výjimkou `/u` a `/AssemblyName`, jsou možnosti kumulativní, ale overridable. To znamená, že možnosti zadané pro jedno sestavení se vztahují na všechna následující sestavení, pokud dané možnosti není přidělena jiná hodnota.  
  
 Pokud spustíte Installutil.exe proti sestavení bez zadání jakékoli možnosti, do adresáře sestavení se umístí následující tři soubory:  
  
-   InstallUtil.InstallLog – obsahuje obecný popis průběhu instalace.  
  
-   *AssemblyName*. InstallLog – obsahuje informace specifické pro potvrzovací fáze procesu instalace. Další informace o potvrzovací fázi naleznete v tématu <xref:System.Configuration.Install.Installer.Commit%2A> metody.  
  
-   *AssemblyName*. InstallState - obsahuje data používaná při odinstalování sestavení.  
  
 InstallUtil.exe používá reflexi ke kontrole zadaného sestavení a k nalezení všech <xref:System.Configuration.Install.Installer> typy, které mají <xref:System.ComponentModel.RunInstallerAttribute?displayProperty=nameWithType> atribut nastaven na `true`. Tento nástroj poté spustí buď <xref:System.Configuration.Install.Installer.Install%2A?displayProperty=nameWithType> nebo <xref:System.Configuration.Install.Installer.Uninstall%2A?displayProperty=nameWithType> metoda pro každou instanci <xref:System.Configuration.Install.Installer> typu. InstallUtil.exe provede instalaci transakčním způsobem; to znamená, že pokud instalace jednoho sestavení selže, zruší instalace všech ostatních sestavení. Odinstalování není transakční.  
  
 Installutil.exe nemůže nainstalovat nebo odinstalovat sestavení se zpožděným podpisem, ale může nainstalovat nebo odinstalovat sestavení se silným názvem.  
  
 Od rozhraní .NET Framework verze 2.0, je 32bitová verze Common Language Runtime (CLR) dodávána pouze s 32bitovou verzí instalačního programu, zatímco 64bitová verze CLR je dodávána s 32bitovou i 64bitovou verzí instalačního programu. Jestliže používáte 64bitový CLR, 32bitová sestavení instalujte pomocí 32bitového instalačního programu a 64bitovou verzi instalačního programu použijte k instalaci 64bitových sestavení Microsoft Intermediate Language (MSIL). Obě verze instalačního programu se chovají stejně.  
  
 Installutil.exe nelze použít k nasazení služby systému Windows, která byla vytvořena pomocí C++, protože Installutil.exe nedokáže rozpoznat vložený nativní kód, který je vytvořen pomocí kompilátoru jazyka C++. Pokud se pokusíte nasadit službu C++ Windows pomocí Installutil.exe Výjimka jako například <xref:System.BadImageFormatException> bude vyvolána výjimka. V tomto případě přesuňte kód služby do modulu C++ a pak napište objekt instalačního programu v jazyce C# nebo Visual Basic.  
  
## <a name="examples"></a>Příklady  
 Následující příkaz zobrazí popis syntaxe příkazů a možností InstallUtil.exe.  
  
```  
installutil /?  
```  
  
 Následující příkaz zobrazí popis syntaxe příkazů a možností InstallUtil.exe. Zobrazuje také popis a seznam možností podporovaných příkazem součástmi instalačního programu v `myAssembly.exe` Pokud byla přiřazena text nápovědy instalačního programu <xref:System.Configuration.Install.Installer.HelpText%2A?displayProperty=nameWithType> vlastnost.  
  
```  
installutil /? myAssembly.exe  
```  
  
 Následující příkaz spustí součásti instalačního programu v sestavení `myAssembly.exe`.  
  
```  
installutil myAssembly.exe  
```  
  
 Následující příkaz spustí součásti instalačního programu v sestavení s použitím `/AssemblyName` přepínače a plně kvalifikovaný název.  
  
```  
installutil /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 Následující příkaz spustí součásti instalačního programu v sestavení určeném názvem souboru a v sestavení určeném silným názvem. Všimněte si, že všechna sestavení určená názvem souboru musí být uvedena před sestaveními určenými silným názvem v příkazovém řádku vzhledem k tomu, `/AssemblyName` možnost se nedá přepsat.  
  
```  
installutil myAssembly.exe /AssemblyName "myAssembly, Culture=neutral, PublicKeyToken=0038abc9deabfle5, Version=4.0.0.0"  
```  
  
 Následující příkaz spustí součásti odinstalačního programu v sestavení `myAssembly.exe`.  
  
```  
installutil /u myAssembly.exe   
```  
  
 Následující příkaz spustí součásti odinstalačního programu v sestaveních `myAssembly1.exe` a `myAssembly2.exe`.  
  
```  
installutil myAssembly1.exe /u myAssembly2.exe  
```  
  
 Protože pozice `/u` možnost na příkazovém řádku není důležitá, jedná se o ekvivalent následujícího příkazu.  
  
```  
installutil /u myAssembly1.exe myAssembly2.exe  
```  
  
 Následující příkaz spustí instalační programy v sestavení `myAssembly.exe` a určuje, že informace o průběhu budou zapsány do `myLog.InstallLog`.  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe   
```  
  
 Následující příkaz spustí instalační programy v sestavení `myAssembly.exe`, určuje, že informace o průběhu mají být zapsána do `myLog.InstallLog`a používá vlastní `/reg` možnost určit, zda má být aktualizován v systému registru.  
  
```  
installutil /LogFile=myLog.InstallLog /reg=true myAssembly.exe  
```  
  
 Následující příkaz spustí instalační programy v sestavení `myAssembly.exe`, použití instalačního programu vlastní `/email` možnost zadat e-mailovou adresu uživatele a potlačuje výstup do souboru protokolu.  
  
```  
installutil /LogFile= /email=admin@mycompany.com myAssembly.exe  
```  
  
 Následující příkaz zapíše postup instalace pro `myAssembly.exe` k `myLog.InstallLog` a zapíše postup pro `myTestAssembly.exe` k `myTestLog.InstallLog`.  
  
```  
installutil /LogFile=myLog.InstallLog myAssembly.exe /LogFile=myTestLog.InstallLog myTestAssembly.exe  
```  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Configuration.Install>
- [Nástroje](../../../docs/framework/tools/index.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

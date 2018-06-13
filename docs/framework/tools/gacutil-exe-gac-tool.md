---
title: Gacutil.exe (nástroj globální mezipaměti sestavení)
ms.date: 03/30/2017
helpviewer_keywords:
- assemblies [.NET Framework], global assembly cache
- global assembly cache, viewing contents
- viewing assemblies in global assembly cache
- global assembly cache, manipulating contents
- GAC (global assembly cache), Gacutil.exe
- Gacutil.exe
- GAC (global assembly cache), viewing contents
- installing assemblies into global assembly cache
- removing assemblies from global assembly cache
- list of assemblies in global assembly cache
- cache [.NET Framework], global assembly cache
- GAC (global assembly cache), manipulating contents
- global assembly cache, Gacutil.exe
- Global Assembly Cache tool
ms.assetid: 4c7be9c8-72ae-481f-a01c-1a4716806e99
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98423e6c103f7eb93b4bfa35ef19b6551c0df0e0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33399591"
---
# <a name="gacutilexe-global-assembly-cache-tool"></a>Gacutil.exe (nástroj globální mezipaměti sestavení)
Nástroj Global Assembly Cache umožňuje zobrazit a měnit obsah globální mezipaměti sestavení (GAC) a mezipaměti pro stahování.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
gacutil [options] [assemblyName | assemblyPath | assemblyListFile]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*assemblyName*|Název sestavení. Můžete například zadat buď částečně zadaného sestavení název `myAssembly` nebo název plně zadané sestavení jako `myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5`.|  
|*AssemblyPath*|Název souboru obsahujícího manifest sestavení.|  
|*assemblyListFile*|Cesta k textovému souboru ANSI obsahujícímu sestavení, která mají být nainstalována nebo odinstalována. Chcete-li použít textový soubor pro instalaci sestavení, zadejte cestu ke každému sestavení na samostatný řádek souboru. Nástroj interpretuje relativní cesty relativní k umístění *assemblyListFile*. Chcete-li použít textový soubor k odinstalování sestavení, zadejte plně kvalifikovaný název každého sestavení na samostatném řádku v souboru. Najdete v článku *assemblyListFile* obsah příklady později v tomto tématu.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/cdl**|Odstraní obsah mezipaměti pro stahování.|  
|**/f**|Zadejte tato možnost se **/i** nebo **/il** vynuťte sestavení, které chcete znovu nainstalovat. Pokud sestavení se stejným názvem již v globální mezipaměti sestavení (GAC) existuje, nástroj je přepíše.|  
|**/h**[**elp**]|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/i** *assemblyPath*|Nainstaluje sestavení do globální mezipaměti sestavení (GAC).|  
|**/IF***assemblyPath* |Nainstaluje sestavení do globální mezipaměti sestavení (GAC). Pokud sestavení se stejným názvem již v globální mezipaměti sestavení (GAC) existuje, nástroj je přepíše.<br /><br /> Určení Tato možnost odpovídá zadání **/i** a **/f** možnosti společně.|  
|**/IL** *assemblyListFile*|Nainstaluje jeden nebo více sestavení zadaný v *assemblyListFile* do globální mezipaměti sestavení.|  
|**/IR***assemblyPath* <br /><br /> *Schéma*<br /><br /> *id*<br /><br /> *Popis*|Nainstaluje sestavení do globální mezipaměti sestavení a přidá odkaz pro jeho započítání. Je nutné zadat *assemblyPath*, *schéma*, *id*, a *popis* parametry s touto možností. Popis platné hodnoty pro tyto parametry můžete určit, najdete **/r** možnost.<br /><br /> Určení Tato možnost odpovídá zadání **/i** a **/r** možnosti společně.|  
|**/l** [*assemblyName*]|Zobrazí obsah globální mezipaměti sestavení (GAC). Pokud zadáte *assemblyName* parametr nástroj uvádí jenom sestavení odpovídající tímto názvem.|  
|**/Ldl**|Vypíše obsah mezipaměti stažených souborů.|  
|**/ld** [*assemblyName*]|Vypíše všechna sestavení a jim odpovídající počty odkazů. Pokud zadáte *assemblyName* parametr, nástroj uvádí jenom sestavení odpovídající tohoto názvu a jejich odpovídající odkaz počty.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/r** [*assemblyName &#124; assemblyPath*]<br /><br /> *Schéma*<br /><br /> *id*<br /><br /> *Popis*|Určuje trasovaný odkaz na sestavení, která mají být nainstalována nebo odinstalována. Zadejte tato možnost se **/i**, **/il**, **/u**, nebo **/ul** možnosti.<br /><br /> Chcete-li nainstalovat sestavení, zadejte *assemblyPath*, *schéma*, *id*, a *popis* parametry s touto možností. Chcete-li odinstalovat sestavení, zadejte *assemblyName*, *schéma*, *id*, a *popis* parametry.<br /><br /> Chcete-li odebrat odkaz na sestavení, musíte zadat stejný *schéma*, *id*, a *popis* parametry, které byly zadány s **/i** a **/r** (nebo **/ir**) možnosti při instalaci sestavení. Provádíte-li odinstalování sestavení, nástroj odstraní sestavení také z globální mezipaměti sestavení (GAC) za předpokladu, že jde o poslední odstraňovaný odkaz a že Instalační služba systému Windows nemá na sestavení žádné zbývající odkazy.<br /><br /> *Schéma* parametr určuje typ instalační schéma. Můžete určit jednu z následujících hodnot:<br /><br /> -UNINSTALL_KEY: Tuto hodnotu zadejte, pokud instalační program přidá aplikaci do přidat nebo odebrat programy v Microsoft Windows. Aplikace se přidávají do ovládacího panelu Přidat nebo odebrat programy přidáním klíče registru HKLM\Software\Microsoft\Windows\CurrentVersion.<br />-FILEPATH: Tuto hodnotu zadejte, pokud instalační program nepřidá aplikaci přidat nebo odebrat programy.<br />-NEPRŮHLEDNÉ: Tuto hodnotu zadat, pokud zadávání klíče registru nebo cesta k souboru nebude použitelná pro váš scénář instalace. Tuto hodnotu můžete zadat vlastní informace o *id* parametr.<br /><br /> Hodnota pro zadejte *id* parametr závisí na hodnotu zadanou pro *schéma* parametr:<br /><br /> – Pokud zadáte UNINSTALL_KEY pro *schéma* parametr, zadejte název aplikace, nastavte v klíči registru HKLM\Software\Microsoft\Windows\CurrentVersion. Například pokud je klíč registru HKLM\Software\Microsoft\Windows\CurrentVersion\MyApp, zadejte Moje aplikace pro *id* parametr.<br />– Pokud zadáte cestu k souboru pro *schéma* parametr, zadejte úplnou cestu ke spustitelnému souboru, který nainstaluje sestavení jako *id* parametr.<br />– Pokud zadáte NEPRŮHLEDNÉ pro *schéma* parametr, můžete zadat všechny část dat, jako *id* parametr. Zadaná data musí být uzavřena do uvozovek ("").<br /><br /> *Popis* parametru můžete zadat popisný text o aplikaci pro instalaci. Tyto informace se zobrazují při výčtu odkazů.|  
|**/ tichou**|Potlačí zobrazování všech výstupů.|  
|**/u***assemblyName* |Odinstaluje sestavení z globální mezipaměti sestavení (GAC).|  
|**/UF***assemblyName* |Vynutí odinstalování zadaného sestavení odstraněním všech odkazů na něj.<br /><br /> Určení Tato možnost odpovídá zadání **/u** a **/f** možnosti společně. **Poznámka:** tuto možnost nelze použít pro odebrání sestavení, která byla nainstalována pomocí Instalační služby systému Windows. Pokud se o tuto operaci pokusíte, nástroj zobrazí chybovou zprávu.|  
|**/UL** *assemblyListFile*|Odinstaluje jeden nebo více sestavení zadaný v *assemblyListFile* z globální mezipaměti sestavení.|  
|**/u**[**ngen**] *assemblyName*|Odinstaluje zadané sestavení z globální mezipaměti sestavení (GAC). Existují-li pro zadané sestavení počty odkazů, nástroj tyto počty zobrazí a neodstraní sestavení z globální mezipaměti sestavení (GAC). **Poznámka:** v rozhraní .NET Framework verze 2.0, `/ungen` není podporován. Místo toho použijte `uninstall` příkaz z [Ngen.exe (Generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md). <br /><br /> V rozhraní .NET Framework verze 1.0 a 1.1 zadání **/ ungen** způsobí, že Gacutil.exe odebrání sestavení z mezipaměť nativních bitových kopií. Tato mezipaměť ukládá nativní bitové kopie pro sestavení, které byly vytvořeny pomocí [Ngen.exe (Generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|  
|**/UR***assemblyName* <br /><br /> *Schéma*<br /><br /> *id*<br /><br /> *Popis*|Odinstaluje odkaz na zadané sestavení z globální mezipaměti sestavení (GAC). Chcete-li odebrat odkaz na sestavení, musíte zadat stejný *schéma*, *id*, a *popis* parametry, které byly zadány s **/i** a **/r** (nebo **/ir)** možností při instalaci sestavení. Popis platné hodnoty pro tyto parametry můžete určit, najdete **/r** možnost.<br /><br /> Určení Tato možnost odpovídá zadání **/u** a **/r** možnosti společně.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pro používání nástroje Gacutil.exe je zapotřebí mít oprávnění správce.  
  
 Nástroj Gacutil.exe konkrétně umožňuje nainstalovat sestavení do mezipaměti, odstranit je z mezipaměti a vypsat obsah mezipaměti.  
  
 Nástroj Gacutil.exe poskytuje možnosti, které podporují počítání odkazů podobné schématu počítání odkazů podporovanému Instalační službou systému Windows. Nástroj Gacutil.exe lze použít k instalaci dvou aplikací, které instalují stejné sestavení. Nástroj sleduje počet odkazů na sestavení. V důsledku toho zůstane sestavení v počítači, dokud nejsou obě aplikace odinstalovány. Používáte-li nástroj Gacutil.exe k instalacím skutečných produktů, použijte možnosti podporující počítání odkazů. Použití **/i** a **/r** možnosti instalace sestavení a přidejte odkaz na počet ho. Použití **/u** a **/r** možnosti společně můžete odebrat počet odkazů pro sestavení. Uvědomte si, že pomocí **/i** a **/u** možnosti samostatně nepodporuje počítání odkazů. Tyto možnosti je vhodné použít při vývoji produktu, ale nikoli pro jeho skutečnou instalaci.  
  
 Použití **/il** nebo **/ul** možnosti pro instalaci nebo odinstalaci seznam sestavení, které jsou uložené v textový soubor s ANSI. Obsah textového souboru musí být správně naformátován. Chcete-li použít textový soubor pro instalaci sestavení, zadejte cestu ke každému sestavení na samostatný řádek souboru. Následující příklad ukazuje obsah souboru obsahujícího sestavení, která mají být nainstalována.  
  
```  
myAssembly1.dll  
myAssembly2.dll  
myAssembly3.dll  
```  
  
 Chcete-li použít textový soubor k odinstalování sestavení, zadejte plně kvalifikovaný název každého sestavení na samostatném řádku v souboru. Následující příklad ukazuje obsah souboru obsahujícího sestavení, která mají být odinstalována.  
  
```  
myAssembly1,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab  
myAssembly2,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab  
myAssembly3,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab  
```  
  
## <a name="examples"></a>Příklady  
 Následující příklad nainstaluje sestavení `mydll.dll` do globální mezipaměti sestavení.  
  
```  
gacutil /i mydll.dll  
```  
  
 Tento příkaz odebere sestavení `hello` ze sestavení v globální mezipaměti, dokud počty žádný odkaz existovat pro sestavení.  
  
```  
gacutil /u hello  
```  
  
 Předchozí příkaz může z mezipaměti sestavení odebrat více než jedno sestavení, protože název sestavení není zadán úplně. Například, pokud obě verze 1.0.0.0 a 3.2.2.1 z `hello` jsou nainstalovány v mezipaměti, příkaz `gacutil /u hello` odebere obě sestavení.  
  
 Chcete-li zabránit odebrání více než jednoho sestavení, použijte následující příkaz. Tento příkaz odebere pouze `hello` sestavení, které odpovídá plně zadaná verze číslo, jazykovou verzi a veřejný klíč.  
  
```  
gacutil /u hello, Version=1.0.0.1, Culture="de",PublicKeyToken=45e343aae32233ca  
```  
  
 Následující příklad nainstaluje sestavení zadaný v souboru `assemblyList.txt` do globální mezipaměti sestavení.  
  
 `gacutil /il assemblyList.txt`  
  
 Tento příkaz odebere zadaný v souboru sestavení `assemblyList.txt` z globální mezipaměti sestavení.  
  
 `gacutil /ul assemblyList.txt`  
  
 Následující příkaz nainstaluje `myDll.dll` do globální mezipaměti sestavení a přidá odkaz na počet ho. Sestavení `myDll.dll` používá aplikace `MyApp`. `UNINSTALL_KEY MyApp` Parametr určuje klíč registru, který přidá `MyApp` přidat nebo odebrat programy v systému Windows. Parametr Popis je zadán jako `My Application Description`.  
  
```  
gacutil /i /r myDll.dll UNINSTALL_KEY MyApp "My Application Description"  
```  
  
 Následující příkaz nainstaluje `myDll.dll` do globální mezipaměti sestavení a přidá odkaz na počet ho. Parametr schéma `FILEPATH`a parametr id `c:\applications\myApp\myApp.exe`, zadejte cestu k aplikaci, která se instaluje `myDll.dll.` parametr Popis je zadán jako `MyApp`.  
  
 `gacutil /i /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp`  
  
 Následující příkaz nainstaluje `myDll.dll` do globální mezipaměti sestavení a přidá odkaz na počet ho. Parametr schéma `OPAQUE`, umožňuje přizpůsobit parametry id a popis.  
  
```  
gacutil /i /r mydll.dll OPAQUE "Insert custom application details here" "Insert Custom description information here"  
```  
  
 Tento příkaz odebere odkaz na `myDll.dll` aplikací `myApp`. Jde-li o poslední odkaz na sestavení, příkaz toto sestavení zároveň odebere z globální mezipaměti sestavení (GAC).  
  
 `gacutil /u /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp`  
  
 Následující příkaz vypíše obsah globální mezipaměti sestavení (GAC).  
  
```  
gacutil /l  
```  
  
## <a name="see-also"></a>Viz také  
 [Nástroje](../../../docs/framework/tools/index.md)  
 [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)  
 [Regasm.exe (nástroj registrace sestavení)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)  
 [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

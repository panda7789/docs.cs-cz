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
ms.openlocfilehash: 779cf36fb10cc3acbefabd6ef90a885cc221f3f6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54541219"
---
# <a name="gacutilexe-global-assembly-cache-tool"></a>Gacutil.exe (nástroj globální mezipaměti sestavení)
Nástroj Global Assembly Cache umožňuje zobrazit a měnit obsah globální mezipaměti sestavení (GAC) a mezipaměti pro stahování.  
  
 Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).  
  
 V příkazovém řádku zadejte následující:  
  
## <a name="syntax"></a>Syntaxe  
  
```  
gacutil [options] [assemblyName | assemblyPath | assemblyListFile]  
```  
  
#### <a name="parameters"></a>Parametry  
  
|Argument|Popis|  
|--------------|-----------------|  
|*assemblyName*|Název sestavení. Lze zadat buď částečný název sestavení, například `myAssembly` nebo úplný název sestavení jako `myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5`.|  
|*assemblyPath*|Název souboru obsahujícího manifest sestavení.|  
|*assemblyListFile*|Cesta k textovému souboru ANSI obsahujícímu sestavení, která mají být nainstalována nebo odinstalována. Chcete-li použít textový soubor pro instalaci sestavení, zadejte cestu ke každému sestavení na samostatný řádek souboru. Nástroj interpretuje relativní cesty vůči umístění *assemblyListFile*. Chcete-li použít textový soubor k odinstalování sestavení, zadejte plně kvalifikovaný název každého sestavení na samostatném řádku v souboru. Zobrazit *assemblyListFile* obsah příklady dále v tomto tématu.|  
  
|Možnost|Popis|  
|------------|-----------------|  
|**/cdl**|Odstraní obsah mezipaměti pro stahování.|  
|**/f**|Tato možnost se **/i** nebo **/il** možnosti, jak vynutit přeinstalování sestavení. Pokud sestavení se stejným názvem již v globální mezipaměti sestavení (GAC) existuje, nástroj je přepíše.|  
|**/h**[**elp**]|Zobrazí syntaxi příkazu a možnosti nástroje.|  
|**/i** *assemblyPath*|Nainstaluje sestavení do globální mezipaměti sestavení (GAC).|  
|**/IF** *assemblyPath*|Nainstaluje sestavení do globální mezipaměti sestavení (GAC). Pokud sestavení se stejným názvem již v globální mezipaměti sestavení (GAC) existuje, nástroj je přepíše.<br /><br /> Zadání této možnosti je ekvivalentní se zadáním **/i** a **/f** najednou.|  
|**/IL** *assemblyListFile*|Nainstaluje jednu nebo více sestavení zadaných v *assemblyListFile* do globální mezipaměti sestavení.|  
|**/IR** *assemblyPath*<br /><br /> *scheme*<br /><br /> *id*<br /><br /> *description*|Nainstaluje sestavení do globální mezipaměti sestavení a přidá odkaz pro jeho započítání. Je nutné zadat *assemblyPath*, *schéma*, *id*, a *popis* s touto možností parametry. Popis platných hodnot pro tyto parametry můžete zadat, najdete v článku **/r** možnost.<br /><br /> Zadání této možnosti je ekvivalentní se zadáním **/i** a **/r** najednou.|  
|**/l** [*assemblyName*]|Zobrazí obsah globální mezipaměti sestavení (GAC). Pokud zadáte *assemblyName* parametr, nástroj vypíše pouze sestavení daného názvu.|  
|**/ldl**|Vypíše obsah mezipaměti stažených souborů.|  
|**/lr** [*assemblyName*]|Vypíše všechna sestavení a jim odpovídající počty odkazů. Pokud zadáte *assemblyName* parametr, nástroj vypíše pouze sestavení daného názvu a jim odpovídající počty odkazů.|  
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|  
|**/r** [*assemblyName &#124; assemblyPath*]<br /><br /> *scheme*<br /><br /> *id*<br /><br /> *description*|Určuje trasovaný odkaz na sestavení, která mají být nainstalována nebo odinstalována. Tato možnost se **/i**, **/il**, **/u**, nebo **/ul** možnosti.<br /><br /> Chcete-li nainstalovat sestavení, zadejte *assemblyPath*, *schéma*, *id*, a *popis* s touto možností parametry. Chcete-li odinstalovat sestavení, zadejte *assemblyName*, *schéma*, *id*, a *popis* parametry.<br /><br /> Chcete-li odebrat odkaz na sestavení, je nutné zadat stejný *schéma*, *id*, a *popis* parametry, které byly zadány s **/i** a **/r** (nebo **/ir**) možnosti při instalaci sestavení. Provádíte-li odinstalování sestavení, nástroj odstraní sestavení také z globální mezipaměti sestavení (GAC) za předpokladu, že jde o poslední odstraňovaný odkaz a že Instalační služba systému Windows nemá na sestavení žádné zbývající odkazy.<br /><br /> *Schéma* parametr určuje typ instalačního schématu. Můžete určit jednu z následujících hodnot:<br /><br /> -UNINSTALL_KEY: Tuto hodnotu zadejte, pokud instalační program přidá aplikaci do panelu Přidat nebo odebrat programy v Microsoft Windows. Aplikace se přidávají do ovládacího panelu Přidat nebo odebrat programy přidáním klíče registru HKLM\Software\Microsoft\Windows\CurrentVersion.<br />– CESTA K SOUBORU: Tuto hodnotu zadejte, pokud instalační program nepřidá aplikaci do panelu Přidat nebo odebrat programy.<br />-NEPRŮHLEDNÉ: Zadejte tuto hodnotu, pokud dodání klíče registru nebo cesta k souboru se nedá použít u instalačního scénáře. Tato hodnota umožňuje určit vlastní informace pro *id* parametru.<br /><br /> Hodnotu pro *id* parametr závisí na hodnotě zadané pro *schéma* parametr:<br /><br /> – Pokud zadáte hodnotu UNINSTALL_KEY *schéma* parametr, zadejte název aplikace nastavený v klíči registru HKLM\Software\Microsoft\Windows\CurrentVersion. Například pokud je klíč registru HKLM\Software\Microsoft\Windows\CurrentVersion\MyApp, zadejte MyApp *id* parametru.<br />– Pokud zadáte cestu k souboru pro *schéma* parametr, zadejte úplnou cestu ke spustitelnému souboru, který sestavení nainstaluje *id* parametru.<br />– Pokud zadáte OPAQUE *schéma* parametr, můžete zadat nějakou část dat, jako *id* parametru. Zadaná data musí být uzavřena do uvozovek ("").<br /><br /> *Popis* parametrů můžete zadat popisný text o aplikaci pro instalaci. Tyto informace se zobrazují při výčtu odkazů.|  
|**/ silent**|Potlačí zobrazování všech výstupů.|  
|**/u** *assemblyName*|Odinstaluje sestavení z globální mezipaměti sestavení (GAC).|  
|**/UF** *assemblyName*|Vynutí odinstalování zadaného sestavení odstraněním všech odkazů na něj.<br /><br /> Zadání této možnosti je ekvivalentní se zadáním **/u** a **/f** najednou. **Poznámka:**  Tuto možnost nelze použít k odstranění sestavení nainstalovaného pomocí Instalační služby systému Windows společnosti Microsoft. Pokud se o tuto operaci pokusíte, nástroj zobrazí chybovou zprávu.|  
|**/UL** *assemblyListFile*|Odinstaluje jeden nebo více sestavení zadaných v *assemblyListFile* z globální mezipaměti sestavení.|  
|**/u**[**ngen**] *assemblyName*|Odinstaluje zadané sestavení z globální mezipaměti sestavení (GAC). Existují-li pro zadané sestavení počty odkazů, nástroj tyto počty zobrazí a neodstraní sestavení z globální mezipaměti sestavení (GAC). **Poznámka:**  V rozhraní .NET Framework verze 2.0 `/ungen` se nepodporuje. Místo toho použijte `uninstall` příkaz [Ngen.exe (Generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md). <br /><br /> V rozhraní .NET Framework verze 1.0 a 1.1 určení **/ ungen** způsobí, že Gacutil.exe k odebrání sestavení z mezipaměti nativních bitových kopií. Tato mezipaměť ukládá nativní bitové kopie pro sestavení, které byly vytvořeny pomocí [Ngen.exe (Generátor nativních obrázků)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|  
|**/UR** *assemblyName*<br /><br /> *scheme*<br /><br /> *id*<br /><br /> *description*|Odinstaluje odkaz na zadané sestavení z globální mezipaměti sestavení (GAC). Chcete-li odebrat odkaz na sestavení, je nutné zadat stejný *schéma*, *id*, a *popis* parametry, které byly zadány s **/i** a **/r** (nebo **/ir)** možnosti při instalaci sestavení. Popis platných hodnot pro tyto parametry můžete zadat, najdete v článku **/r** možnost.<br /><br /> Zadání této možnosti je ekvivalentní se zadáním **/u** a **/r** najednou.|  
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Pro používání nástroje Gacutil.exe je zapotřebí mít oprávnění správce.  
  
 Nástroj Gacutil.exe konkrétně umožňuje nainstalovat sestavení do mezipaměti, odstranit je z mezipaměti a vypsat obsah mezipaměti.  
  
 Nástroj Gacutil.exe poskytuje možnosti, které podporují počítání odkazů podobné schématu počítání odkazů podporovanému Instalační službou systému Windows. Nástroj Gacutil.exe lze použít k instalaci dvou aplikací, které instalují stejné sestavení. Nástroj sleduje počet odkazů na sestavení. V důsledku toho zůstane sestavení v počítači, dokud nejsou obě aplikace odinstalovány. Používáte-li nástroj Gacutil.exe k instalacím skutečných produktů, použijte možnosti podporující počítání odkazů. Použití **/i** a **/r** možnosti společně, chcete-li nainstalovat sestavení a přidejte odkaz na započítat jej. Použití **/u** a **/r** možnosti dohromady a odeberte počet odkazů pro sestavení. Mějte na paměti, že při použití **/i** a **/u** možnosti samostatně nepodporuje počítání odkazů. Tyto možnosti je vhodné použít při vývoji produktu, ale nikoli pro jeho skutečnou instalaci.  
  
 Použití **/il** nebo **/ul** možnosti, jak nainstalovat nebo odinstalovat seznam sestavení uložený v textovém souboru ANSI. Obsah textového souboru musí být správně naformátován. Chcete-li použít textový soubor pro instalaci sestavení, zadejte cestu ke každému sestavení na samostatný řádek souboru. Následující příklad ukazuje obsah souboru obsahujícího sestavení, která mají být nainstalována.  
  
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

> [!NOTE]
>  Pokus o instalaci sestavení s názvem souboru delší než 79 a 91 znaků (kromě přípony souboru) může způsobit následující chybu:
> ```
> Failure adding assembly to the cache:   The file name is too long.
> ```
> Toto je vzhledem k tomu, že interně Gacutil.exe vytvoří cestu maximálně MAX_PATH znaků, která se skládá z následujících elementů:
> - GAC Root - 34 znaků (tj. `C:\Windows\Microsoft.NET\assembly\`)
> - Architektura – 7 nebo 9 znaků (tj. `GAC_32\`, `GAC_64\`, `GAC_MSIL`)
> - AssemblyName – až 91 znaků, v závislosti na velikosti další prvky (např.) `System.Xml.Linq\`)
> - AssemblyInfo - 31 až 48 znaků nebo více skládající se z:
>   - Framework – 5 znaků (např.) `v4.0_`)
>   - AssemblyVersion – 8 až 24 znaků (např.) `9.0.1000.0_`)
>   - AssemblyLanguage - 1 do 8 znaků (např.) `de_`, `sr-Cyrl_`)
>   - PublicKey - 17 znaků (např.) `31bf3856ad364e35\`)
> - DllFileName – až 91 + 4 znaky (tj. `<AssemblyName>.dll`)

## <a name="examples"></a>Příklady  
 Následující příkaz nainstaluje sestavení `mydll.dll` do globální mezipaměti sestavení.  
  
```  
gacutil /i mydll.dll  
```  
  
 Následující příkaz odstraní sestavení `hello` ze sestavení globální mezipaměti tak dlouho, dokud se počítá žádný odkaz pro sestavení neexistují.  
  
```  
gacutil /u hello  
```  
  
 Předchozí příkaz může z mezipaměti sestavení odebrat více než jedno sestavení, protože název sestavení není zadán úplně. Například, pokud obě verze 1.0.0.0 a 3.2.2.1 `hello` jsou nainstalovány v mezipaměti, příkaz `gacutil /u hello` odebere obě sestavení.  
  
 Chcete-li zabránit odebrání více než jednoho sestavení, použijte následující příkaz. Tento příkaz odebere pouze `hello` sestavení, které odpovídá plně zadanému číslu verze, jazykovou verzi a veřejný klíč.  
  
```  
gacutil /u hello, Version=1.0.0.1, Culture="de",PublicKeyToken=45e343aae32233ca  
```  
  
 Následující příkaz nainstaluje sestavení zadaná v souboru `assemblyList.txt` do globální mezipaměti sestavení.  
  
 `gacutil /il assemblyList.txt`  
  
 Následující příkaz odstraní sestavení zadaná v souboru `assemblyList.txt` z globální mezipaměti sestavení.  
  
 `gacutil /ul assemblyList.txt`  
  
 Následující příkaz nainstaluje `myDll.dll` do globální mezipaměti sestavení a přidá odkaz na započítat jej. Sestavení `myDll.dll` používá aplikace `MyApp`. `UNINSTALL_KEY MyApp` Parametr určuje klíč registru, který přidá `MyApp` přidat nebo odebrat programy v Windows. Popis parametru je zadán jako `My Application Description`.  
  
```  
gacutil /i /r myDll.dll UNINSTALL_KEY MyApp "My Application Description"  
```  
  
 Následující příkaz nainstaluje `myDll.dll` do globální mezipaměti sestavení a přidá odkaz na započítat jej. Parametr scheme `FILEPATH`a parametr id `c:\applications\myApp\myApp.exe`, zadejte cestu k aplikaci, která se instaluje `myDll.dll.` popis parametru je zadán jako `MyApp`.  
  
 `gacutil /i /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp`  
  
 Následující příkaz nainstaluje `myDll.dll` do globální mezipaměti sestavení a přidá odkaz na započítat jej. Parametr scheme `OPAQUE`, vám umožní přizpůsobit parametry id a description.  
  
```  
gacutil /i /r mydll.dll OPAQUE "Insert custom application details here" "Insert Custom description information here"  
```  
  
 Následující příkaz odebere odkaz na `myDll.dll` aplikací `myApp`. Jde-li o poslední odkaz na sestavení, příkaz toto sestavení zároveň odebere z globální mezipaměti sestavení (GAC).  
  
 `gacutil /u /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp`  
  
 Následující příkaz vypíše obsah globální mezipaměti sestavení (GAC).  
  
```  
gacutil /l  
```  
  
## <a name="see-also"></a>Viz také:
- [Nástroje](../../../docs/framework/tools/index.md)
- [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)
- [Regasm.exe (nástroj registrace sestavení)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

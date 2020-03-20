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
ms.openlocfilehash: 87f3cb799ba4e406906759e1facd19d00c8bdace
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73107504"
---
# <a name="gacutilexe-global-assembly-cache-tool"></a>Gacutil.exe (nástroj globální mezipaměti sestavení)

Nástroj Global Assembly Cache umožňuje zobrazit a měnit obsah globální mezipaměti sestavení (GAC) a mezipaměti pro stahování.

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```console
gacutil [options] [assemblyName | assemblyPath | assemblyListFile]
```

## <a name="parameters"></a>Parametry

|Argument|Popis|
|--------------|-----------------|
|*Assemblyname*|Název sestavení. Můžete zadat buď částečně zadaný `myAssembly` název sestavení, například, `myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5`nebo plně zadaný název sestavení, například .|
|*assemblyPath*|Název souboru obsahujícího manifest sestavení.|
|*assemblyListFile*|Cesta k textovému souboru ANSI obsahujícímu sestavení, která mají být nainstalována nebo odinstalována. Chcete-li použít textový soubor pro instalaci sestavení, zadejte cestu ke každému sestavení na samostatný řádek souboru. Nástroj interpretuje relativní cesty vzhledem k umístění *assemblyListFile*. Chcete-li použít textový soubor k odinstalování sestavení, zadejte plně kvalifikovaný název každého sestavení na samostatném řádku v souboru. Viz příklady obsahu *assemblyListFile* dále v tomto tématu.|

|Možnost|Popis|
|------------|-----------------|
|**/cdl**|Odstraní obsah mezipaměti pro stahování.|
|**/f**|Tuto možnost zadejte pomocí možností **/i** nebo **/il,** které vynutí přeinstalaci sestavení. Pokud sestavení se stejným názvem již v globální mezipaměti sestavení (GAC) existuje, nástroj je přepíše.|
|**/h**[**elp**]|Zobrazí syntaxi příkazu a možnosti nástroje.|
|**/i** *assemblyPath*|Nainstaluje sestavení do globální mezipaměti sestavení (GAC).|
|**/if**  *assemblyPath*|Nainstaluje sestavení do globální mezipaměti sestavení (GAC). Pokud sestavení se stejným názvem již v globální mezipaměti sestavení (GAC) existuje, nástroj je přepíše.<br /><br /> Zadání této možnosti je ekvivalentní k zadání **/i** a **/f** možnosti společně.|
|**/il** *assemblyListFile*|Nainstaluje jedno nebo více sestavení určených v *assemblyListFile* do globální mezipaměti sestavení.|
|**/ir**  *assemblyPath*<br /><br /> *Schéma*<br /><br /> *Id*<br /><br /> *description*|Nainstaluje sestavení do globální mezipaměti sestavení a přidá odkaz pro jeho započítání. Je nutné zadat parametry *assemblyPath*, *scheme*, *id*a *description* s touto volbou. Popis platných hodnot, které můžete zadat pro tyto parametry, naleznete v tématu **/r** možnost.<br /><br /> Zadání této možnosti je ekvivalentní k zadání **/i** a **/r** možnosti společně.|
|**/l** [*název_sestavení*]|Zobrazí obsah globální mezipaměti sestavení (GAC). Pokud zadáte parametr *assemblyName,* nástroj zobrazí pouze sestavení odpovídající tomuto názvu.|
|**/ldl**|Vypíše obsah mezipaměti stažených souborů.|
|**/lr** [*název_sestavení*]|Vypíše všechna sestavení a jim odpovídající počty odkazů. Pokud zadáte parametr *assemblyName,* nástroj zobrazí pouze sestavení odpovídající tomuto názvu a jejich odpovídající počty odkazů.|
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|
|**/r** [*assemblyName &#124; assemblyPath*]<br /><br /> *Schéma*<br /><br /> *Id*<br /><br /> *description*|Určuje trasovaný odkaz na sestavení, která mají být nainstalována nebo odinstalována. Tuto možnost zadejte s možnostmi **/i**, **/il**, **/u**nebo **/ul.**<br /><br /> Chcete-li nainstalovat sestavení, zadejte s touto volbou parametry *assemblyPath*, *scheme*, *id*a *description.* Chcete-li odinstalovat sestavení, zadejte parametry *assemblyName*, *scheme*, *id*a *description.*<br /><br /> Chcete-li odebrat odkaz na sestavení, musíte zadat stejné *schéma*, *id*a parametry *popisu,* které byly zadány s možnostmi **/i** a **/r** (nebo **/ir)** při instalaci sestavení. Provádíte-li odinstalování sestavení, nástroj odstraní sestavení také z globální mezipaměti sestavení (GAC) za předpokladu, že jde o poslední odstraňovaný odkaz a že Instalační služba systému Windows nemá na sestavení žádné zbývající odkazy.<br /><br /> Parametr *schématu* určuje typ schématu instalace. Můžete určit jednu z následujících hodnot:<br /><br /> - UNINSTALL_KEY: Zadejte tuto hodnotu, pokud instalační program přidá aplikaci do přidat nebo odebrat programy v systému Microsoft Windows. Aplikace se přidávají do ovládacího panelu Přidat nebo odebrat programy přidáním klíče registru HKLM\Software\Microsoft\Windows\CurrentVersion.<br />- FILEPATH: Zadejte tuto hodnotu, pokud instalační program nepřidá aplikaci do přidat nebo odebrat programy.<br />- OPAQUE: Zadejte tuto hodnotu, pokud zadání klíče registru nebo cesty k souboru se nevztahuje na váš scénář instalace. Tato hodnota umožňuje zadat vlastní informace pro *id* parametr.<br /><br /> Hodnota, která má být zadána pro parametr *id,* závisí na hodnotě zadané pro parametr *schématu:*<br /><br /> - Pokud zadáte UNINSTALL_KEY *parametru schématu,* zadejte název aplikace nastavené v klíči registru HKLM\Software\Microsoft\Windows\CurrentVersion. Pokud je například klíč registru HKLM\Software\Microsoft\Windows\CurrentVersion\MyApp, zadejte pro parametr *id* aplikaci MyApp.<br />- Pokud zadáte FILEPATH pro parametr *schématu,* zadejte úplnou cestu ke spustitelnému souboru, který nainstaluje sestavení jako parametr *id.*<br />- Pokud zadáte OPAQUE pro parametr *schématu,* můžete zadat libovolnou část dat jako parametr *id.* Zadaná data musí být uzavřena do uvozovek ("").<br /><br /> Parametr *description* umožňuje zadat popisný text o aplikaci, kterou chcete nainstalovat. Tyto informace se zobrazují při výčtu odkazů.|
|**/silent**|Potlačí zobrazování všech výstupů.|
|**/u**  *název_sestavení*|Odinstaluje sestavení z globální mezipaměti sestavení (GAC).|
|**/uf**  *název sestavení*|Vynutí odinstalování zadaného sestavení odstraněním všech odkazů na něj.<br /><br /> Zadání této možnosti je ekvivalentní zadání možností **/u** a **/f** společně. **Poznámka:**  Tuto možnost nelze použít k odebrání sestavení, které bylo nainstalováno pomocí Instalační služby systému Microsoft Windows. Pokud se o tuto operaci pokusíte, nástroj zobrazí chybovou zprávu.|
|**/ul** *assemblyListFile*|Odinstaluje jedno nebo více sestavení zadaných v *assemblyListFile* z globální mezipaměti sestavení.|
|**/u**[**ngen**] *název_sestavení*|Odinstaluje zadané sestavení z globální mezipaměti sestavení (GAC). Existují-li pro zadané sestavení počty odkazů, nástroj tyto počty zobrazí a neodstraní sestavení z globální mezipaměti sestavení (GAC). **Poznámka:**  V rozhraní .NET Framework verze `/ungen` 2.0 není podporován. Místo toho `uninstall` použijte příkaz [Ngen.exe (Native Image Generator)](ngen-exe-native-image-generator.md). <br /><br /> V rozhraní .NET Framework verze 1.0 a 1.1, zadání **/ungen** způsobí Gacutil.exe odebrat sestavení z mezipaměti nativní image. Tato mezipaměť ukládá nativní bitové kopie pro sestavení, která byla vytvořena pomocí [souboru Ngen.exe (Native Image Generator).](ngen-exe-native-image-generator.md)|
|**/ur**  *název_sestavení*<br /><br /> *Schéma*<br /><br /> *Id*<br /><br /> *description*|Odinstaluje odkaz na zadané sestavení z globální mezipaměti sestavení (GAC). Chcete-li odebrat odkaz na sestavení, musíte zadat stejné *schéma*, *id*a parametry *popisu,* které byly zadány s možnostmi **/i** a **/r** (nebo **/ir)** při instalaci sestavení. Popis platných hodnot, které můžete zadat pro tyto parametry, naleznete v tématu **/r** možnost.<br /><br /> Zadání této možnosti je ekvivalentní zadání **/u** a **/r** možnosti společně.|
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Pro používání nástroje Gacutil.exe je zapotřebí mít oprávnění správce.

Nástroj Gacutil.exe konkrétně umožňuje nainstalovat sestavení do mezipaměti, odstranit je z mezipaměti a vypsat obsah mezipaměti.

Nástroj Gacutil.exe poskytuje možnosti, které podporují počítání odkazů podobné schématu počítání odkazů podporovanému Instalační službou systému Windows. Nástroj Gacutil.exe lze použít k instalaci dvou aplikací, které instalují stejné sestavení. Nástroj sleduje počet odkazů na sestavení. V důsledku toho zůstane sestavení v počítači, dokud nejsou obě aplikace odinstalovány. Používáte-li nástroj Gacutil.exe k instalacím skutečných produktů, použijte možnosti podporující počítání odkazů. Pomocí možností **/i** a **/r** společně nainstalujte sestavení a přidejte odkaz pro jeho počítání. Pomocí možností **/u** a **/r** společně odeberte počet odkazů pro sestavení. Uvědomte si, že použití **/i** a **/u** možnosti sám nepodporuje počítání odkazů. Tyto možnosti je vhodné použít při vývoji produktu, ale nikoli pro jeho skutečnou instalaci.

Pomocí možností **/il** nebo **/ul** nainstalujte nebo odinstalujte seznam sestavení uložených v textovém souboru ANSI. Obsah textového souboru musí být správně naformátován. Chcete-li použít textový soubor pro instalaci sestavení, zadejte cestu ke každému sestavení na samostatný řádek souboru. Následující příklad ukazuje obsah souboru obsahujícího sestavení, která mají být nainstalována.

```text
myAssembly1.dll
myAssembly2.dll
myAssembly3.dll
```

Chcete-li použít textový soubor k odinstalování sestavení, zadejte plně kvalifikovaný název každého sestavení na samostatném řádku v souboru. Následující příklad ukazuje obsah souboru obsahujícího sestavení, která mají být odinstalována.

```text
myAssembly1,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab
myAssembly2,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab
myAssembly3,Version=1.1.0.0,Culture=en,PublicKeyToken=874e23ab874e23ab
```

> [!NOTE]
> Pokus o instalaci sestavení s názvem souboru delším než 79 až 91 znaků (s výjimkou přípony souboru) může způsobit následující chybu:
>
> ```output
> Failure adding assembly to the cache:   The file name is too long.
> ```
>
> Důvodem je, že interně Gacutil.exe vytvoří cestu až MAX_PATH znaků, které se skládá z následujících prvků:
>
> - GAC Root - 34 znaků (tj. `C:\Windows\Microsoft.NET\assembly\`)
> - Architektura - 7 nebo 9 znaků (tj. `GAC_32\`, `GAC_64\`, `GAC_MSIL`)
> - AssemblyName - Až 91 znaků, v závislosti na velikosti ostatních prvků (např. `System.Xml.Linq\`)
> - AssemblyInfo - 31 až 48 znaků nebo více skládající se z:
>   - Framework - 5 znaků (např. `v4.0_`)
>   - AssemblyVersion - 8 až 24 znaků (např. `9.0.1000.0_`)
>   - AssemblyLanguage - 1 až 8 znaků (např. `de_`, `sr-Cyrl_`)
>   - PublicKey - 17 znaků (např. `31bf3856ad364e35\`)
> - DllFileName - Až 91 + 4 znaky (tj. `<AssemblyName>.dll`)

## <a name="examples"></a>Příklady

Následující příkaz nainstaluje `mydll.dll` sestavení do globální mezipaměti sestavení.

```console
gacutil /i mydll.dll
```

Následující příkaz odebere `hello` sestavení z globální mezipaměti sestavení, pokud pro sestavení neexistují žádné počty odkazů.

```console
gacutil /u hello
```

Předchozí příkaz může z mezipaměti sestavení odebrat více než jedno sestavení, protože název sestavení není zadán úplně. Například pokud obě verze 1.0.0.0 a 3.2.2.1 `hello` jsou nainstalovány v mezipaměti, příkaz `gacutil /u hello` odebere obě sestavení.

Chcete-li zabránit odebrání více než jednoho sestavení, použijte následující příkaz. Tento příkaz odebere `hello` pouze sestavení, které odpovídá plně zadanému číslu verze, jazykové verzi a veřejnému klíči.

```console
gacutil /u hello, Version=1.0.0.1, Culture="de",PublicKeyToken=45e343aae32233ca
```

Následující příkaz nainstaluje sestavení zadaná `assemblyList.txt` v souboru do globální mezipaměti sestavení.

```console
gacutil /il assemblyList.txt
```

Následující příkaz odebere sestavení zadaná `assemblyList.txt` v souboru z globální mezipaměti sestavení.

```console
gacutil /ul assemblyList.txt
```

Následující příkaz nainstaluje `myDll.dll` do globální mezipaměti sestavení a přidá odkaz na jeho počítání. Sestavení `myDll.dll` používá aplikace `MyApp`. Parametr `UNINSTALL_KEY MyApp` určuje klíč registru, `MyApp` který přidává do přidat nebo odebrat programy v systému Windows. Parametr popisu je `My Application Description`určen jako .

```console
gacutil /i /r myDll.dll UNINSTALL_KEY MyApp "My Application Description"
```

Následující příkaz nainstaluje `myDll.dll` do globální mezipaměti sestavení a přidá odkaz na jeho počítání. Parametr scheme `FILEPATH`, a id `c:\applications\myApp\myApp.exe`parametr , zadejte cestu k `myDll.dll.` aplikaci, která `MyApp`instaluje Parametr popisu je určen jako .

```console
gacutil /i /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp
```

Následující příkaz nainstaluje `myDll.dll` do globální mezipaměti sestavení a přidá odkaz na jeho počítání. Parametr schématu `OPAQUE`, umožňuje přizpůsobit id a parametry popisu.

```console
gacutil /i /r mydll.dll OPAQUE "Insert custom application details here" "Insert Custom description information here"
```

Následující příkaz odebere odkaz `myDll.dll` aplikace `myApp`. Jde-li o poslední odkaz na sestavení, příkaz toto sestavení zároveň odebere z globální mezipaměti sestavení (GAC).

```console
gacutil /u /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp
```

Následující příkaz vypíše obsah globální mezipaměti sestavení (GAC).

```console
gacutil /l
```

## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Globální mezipaměť sestavení](../app-domains/gac.md)
- [Regasm.exe (nástroj registrace sestavení)](regasm-exe-assembly-registration-tool.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)

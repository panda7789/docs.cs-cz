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
ms.openlocfilehash: 99ffbccca8cd8a719e5571638308e28d494d687a
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926879"
---
# <a name="gacutilexe-global-assembly-cache-tool"></a>Gacutil.exe (nástroj globální mezipaměti sestavení)

Nástroj Global Assembly Cache umožňuje zobrazit a měnit obsah globální mezipaměti sestavení (GAC) a mezipaměti pro stahování.

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```console
gacutil [options] [assemblyName | assemblyPath | assemblyListFile]
```

## <a name="parameters"></a>Parametry

|Argument|Popis|
|--------------|-----------------|
|*assemblyName*|Název sestavení. Můžete zadat buď částečně zadaný název sestavení, například `myAssembly` nebo plně zadaný název sestavení `myAssembly, Version=2.0.0.0, Culture=neutral, PublicKeyToken=0038abc9deabfle5`, například.|
|*assemblyPath*|Název souboru obsahujícího manifest sestavení.|
|*Souboru assemblyListFile*|Cesta k textovému souboru ANSI obsahujícímu sestavení, která mají být nainstalována nebo odinstalována. Chcete-li použít textový soubor pro instalaci sestavení, zadejte cestu ke každému sestavení na samostatný řádek souboru. Nástroj interpretuje relativní cesty relativně k umístění *souboru assemblyListFile*. Chcete-li použít textový soubor k odinstalování sestavení, zadejte plně kvalifikovaný název každého sestavení na samostatném řádku v souboru. Podívejte se na příklady obsahu *souboru assemblyListFile* dále v tomto tématu.|

|Možnost|Popis|
|------------|-----------------|
|**/cdl**|Odstraní obsah mezipaměti pro stahování.|
|**/f**|Tuto možnost zadejte s možnostmi **/i** nebo **/Il** pro vynucení opětovné instalace sestavení. Pokud sestavení se stejným názvem již v globální mezipaměti sestavení (GAC) existuje, nástroj je přepíše.|
|**/h**[**elp**]|Zobrazí syntaxi příkazu a možnosti nástroje.|
|**/i** *AssemblyPath*|Nainstaluje sestavení do globální mezipaměti sestavení (GAC).|
|**/IF** *assemblyPath*|Nainstaluje sestavení do globální mezipaměti sestavení (GAC). Pokud sestavení se stejným názvem již v globální mezipaměti sestavení (GAC) existuje, nástroj je přepíše.<br /><br /> Zadání této možnosti je ekvivalentní se zadáním možností **/i** a **/f** společně.|
|**/Il** *souboru assemblyListFile*|Nainstaluje jedno nebo více sestavení určených v *souboru assemblyListFile* do globální mezipaměti sestavení (GAC).|
|**/IR** *assemblyPath*<br /><br /> *programu*<br /><br /> *id*<br /><br /> *název*|Nainstaluje sestavení do globální mezipaměti sestavení a přidá odkaz pro jeho započítání. Pomocí této možnosti je nutné zadat parametry *AssemblyPath*, *schéma*, *ID*a *Description* . Popis platných hodnot, které lze pro tyto parametry zadat, naleznete v možnosti **/r** .<br /><br /> Zadání této možnosti je ekvivalentní se zadáním možností **/i** a **/r** společně.|
|**/l** [*AssemblyName*]|Zobrazí obsah globální mezipaměti sestavení (GAC). Zadáte-li parametr *AssemblyName* , nástroj vypíše pouze sestavení, která odpovídají tomuto názvu.|
|**/ldl**|Vypíše obsah mezipaměti stažených souborů.|
|**/LR** [*AssemblyName*]|Vypíše všechna sestavení a jim odpovídající počty odkazů. Zadáte-li parametr *AssemblyName* , nástroj vypíše pouze sestavení odpovídající tomuto názvu a odpovídající počty odkazů.|
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|
|**/r** [*AssemblyName &#124; AssemblyPath*]<br /><br /> *programu*<br /><br /> *id*<br /><br /> *název*|Určuje trasovaný odkaz na sestavení, která mají být nainstalována nebo odinstalována. Tuto možnost zadejte s možnostmi **/i**, **/Il**, **/u**nebo **/ul** .<br /><br /> Chcete-li nainstalovat sestavení, zadejte parametry *AssemblyPath*, *schématu*, *ID*a *Description* s touto možností. Chcete-li odinstalovat sestavení, zadejte parametry *AssemblyName*, *schématu*, *ID*a *Description* .<br /><br /> Chcete-li odebrat odkaz na sestavení, je nutné zadat stejné parametry *schématu*, *ID*a *popisu* , jaké byly zadány s možnostmi **/i** a **/r** (nebo **/IR**) při instalaci sestavení. Provádíte-li odinstalování sestavení, nástroj odstraní sestavení také z globální mezipaměti sestavení (GAC) za předpokladu, že jde o poslední odstraňovaný odkaz a že Instalační služba systému Windows nemá na sestavení žádné zbývající odkazy.<br /><br /> Parametr *schématu* určuje typ schématu instalace. Můžete určit jednu z následujících hodnot:<br /><br /> - UNINSTALL_KEY: Tuto hodnotu zadejte, pokud instalační program přidá aplikaci do ovládacího panelu Přidat nebo odebrat programy v systému Microsoft Windows. Aplikace se přidávají do ovládacího panelu Přidat nebo odebrat programy přidáním klíče registru HKLM\Software\Microsoft\Windows\CurrentVersion.<br />FILEPATH Tuto hodnotu zadejte, pokud instalační program nepřidá aplikaci do ovládacího panelu Přidat nebo odebrat programy.<br />KRYTÍM Tuto hodnotu zadejte, pokud pro váš scénář instalace neplatí klíč registru nebo cesta k souboru. Tato hodnota umožňuje zadat vlastní informace pro parametr *ID* .<br /><br /> Hodnota, která se má zadat pro parametr *ID* závisí na hodnotě zadané pro parametr *schématu* :<br /><br /> – Pokud pro parametr *schématu* zadáte UNINSTALL_KEY, zadejte název aplikace nastavené v klíči registru HKLM\Software\Microsoft\Windows\CurrentVersion. Pokud je klíč registru například HKLM\Software\Microsoft\Windows\CurrentVersion\MyApp, zadejte MyApp pro parametr *ID* .<br />– Pokud zadáte FILEPATH pro parametr *schématu* , zadejte úplnou cestu ke spustitelnému souboru, který nainstaluje sestavení jako parametr *ID* .<br />– Pokud zadáte neprůhledný parametr *schématu* , můžete zadat libovolný údaj jako parametr *ID* . Zadaná data musí být uzavřena do uvozovek ("").<br /><br /> Parametr *Description* umožňuje zadat popisný text o aplikaci, která se má nainstalovat. Tyto informace se zobrazují při výčtu odkazů.|
|**/ silent**|Potlačí zobrazování všech výstupů.|
|**/u** *assemblyName*|Odinstaluje sestavení z globální mezipaměti sestavení (GAC).|
|**/UF** *assemblyName*|Vynutí odinstalování zadaného sestavení odstraněním všech odkazů na něj.<br /><br /> Zadání této možnosti je ekvivalentní se zadáním možností **/u** a **/f** společně. **Poznámka:**  Tuto možnost nelze použít k odstranění sestavení nainstalovaného pomocí Instalační služby systému Windows společnosti Microsoft. Pokud se o tuto operaci pokusíte, nástroj zobrazí chybovou zprávu.|
|**/ul** *souboru assemblyListFile*|Odinstaluje jedno nebo více sestavení určených v *souboru assemblyListFile* z globální mezipaměti sestavení (GAC).|
|**/u**[**ngen**] *assemblyName*|Odinstaluje zadané sestavení z globální mezipaměti sestavení (GAC). Existují-li pro zadané sestavení počty odkazů, nástroj tyto počty zobrazí a neodstraní sestavení z globální mezipaměti sestavení (GAC). **Poznámka:**  V .NET Framework verze 2,0 `/ungen` se nepodporuje. Místo toho použijte `uninstall` příkaz [Ngen. exe (generátor nativních imagí)](../../../docs/framework/tools/ngen-exe-native-image-generator.md). <br /><br /> V .NET Framework verzích 1,0 a 1,1 způsobí zadání **/ungen** , že nástroj Gacutil. exe odebere sestavení z mezipaměti nativních imagí. Tato mezipaměť ukládá nativní bitové kopie pro sestavení, která byla vytvořena pomocí nástroje [Ngen. exe (generátor nativních imagí)](../../../docs/framework/tools/ngen-exe-native-image-generator.md).|
|**/UR** *assemblyName*<br /><br /> *programu*<br /><br /> *id*<br /><br /> *název*|Odinstaluje odkaz na zadané sestavení z globální mezipaměti sestavení (GAC). Chcete-li odebrat odkaz na sestavení, je nutné zadat stejné parametry *schématu*, *ID*a *popisu* , jaké byly zadány s možnostmi **/i** a **/r** (nebo **/IR)** při instalaci sestavení. Popis platných hodnot, které lze pro tyto parametry zadat, naleznete v možnosti **/r** .<br /><br /> Zadání této možnosti je ekvivalentní se zadáním možností **/u** a **/r** společně.|
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Pro používání nástroje Gacutil.exe je zapotřebí mít oprávnění správce.

Nástroj Gacutil.exe konkrétně umožňuje nainstalovat sestavení do mezipaměti, odstranit je z mezipaměti a vypsat obsah mezipaměti.

Nástroj Gacutil.exe poskytuje možnosti, které podporují počítání odkazů podobné schématu počítání odkazů podporovanému Instalační službou systému Windows. Nástroj Gacutil.exe lze použít k instalaci dvou aplikací, které instalují stejné sestavení. Nástroj sleduje počet odkazů na sestavení. V důsledku toho zůstane sestavení v počítači, dokud nejsou obě aplikace odinstalovány. Používáte-li nástroj Gacutil.exe k instalacím skutečných produktů, použijte možnosti podporující počítání odkazů. Použijte možnosti **/i** a **/r** společně pro instalaci sestavení a přidání odkazu pro jeho počítání. Použijte možnosti **/u** a **/r** společně pro odebrání počtu odkazů pro sestavení. Počítejte s tím, že použití možností **/i** a **/u** samostatně nepodporuje počítání odkazů. Tyto možnosti je vhodné použít při vývoji produktu, ale nikoli pro jeho skutečnou instalaci.

K instalaci nebo odinstalaci seznamu sestavení uložených v textovém souboru ANSI použijte možnosti **/Il** nebo **/ul** . Obsah textového souboru musí být správně naformátován. Chcete-li použít textový soubor pro instalaci sestavení, zadejte cestu ke každému sestavení na samostatný řádek souboru. Následující příklad ukazuje obsah souboru obsahujícího sestavení, která mají být nainstalována.

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
> Při pokusu o instalaci sestavení s názvem souboru delším než 79 až 91 znaků (s výjimkou přípony souboru) může dojít k následující chybě:
>
> ```output
> Failure adding assembly to the cache:   The file name is too long.
> ```
>
> Je to proto, že interně Gacutil. exe sestaví cestu až do znaků MAX_PATH, která se skládá z následujících prvků:
>
> - Kořenová (GAC) – 34 znaků (IE) `C:\Windows\Microsoft.NET\assembly\`)
> - Znaky architektury 7 nebo 9 (IE. `GAC_32\`, `GAC_64\`, `GAC_MSIL`)
> - AssemblyName – až 91 znaků v závislosti na velikosti ostatních elementů (např. `System.Xml.Linq\`)
> - AssemblyInfo-31 až 48 znaků nebo více skládající se z:
>   - Znaky Framework-5 (např. `v4.0_`)
>   - AssemblyVersion-8 až 24 znaků (např. `9.0.1000.0_`)
>   - AssemblyLanguage-1 až 8 znaků (např. `de_`, `sr-Cyrl_`)
>   - PublicKey – 17 znaků (např. `31bf3856ad364e35\`)
> - DllFileName – až 91 + 4 znaky (IE. `<AssemblyName>.dll`)

## <a name="examples"></a>Příklady

Následující příkaz nainstaluje sestavení `mydll.dll` do globální mezipaměti sestavení (GAC).

```console
gacutil /i mydll.dll
```

Následující příkaz odebere sestavení `hello` z globální mezipaměti sestavení (GAC), pokud pro sestavení neexistují žádné počty odkazů.

```console
gacutil /u hello
```

Předchozí příkaz může z mezipaměti sestavení odebrat více než jedno sestavení, protože název sestavení není zadán úplně. Například pokud `hello` jsou v mezipaměti nainstalovány obě verze 1.0.0.0 a 3.2.2.1, příkaz `gacutil /u hello` odebere obě sestavení.

Chcete-li zabránit odebrání více než jednoho sestavení, použijte následující příkaz. Tento příkaz odebere pouze `hello` sestavení, které odpovídá plně určenému číslu verze, jazykové verzi a veřejnému klíči.

```console
gacutil /u hello, Version=1.0.0.1, Culture="de",PublicKeyToken=45e343aae32233ca
```

Následující příkaz nainstaluje sestavení uvedená v souboru `assemblyList.txt` do globální mezipaměti sestavení (GAC).

```console
gacutil /il assemblyList.txt
```

Následující příkaz odebere sestavení uvedená v souboru `assemblyList.txt` z globální mezipaměti sestavení (GAC).

```console
gacutil /ul assemblyList.txt
```

Následující příkaz se nainstaluje `myDll.dll` do globální mezipaměti sestavení (GAC) a přidá odkaz pro jeho počítání. Sestavení `myDll.dll` používá aplikace `MyApp`. Parametr určuje klíč registru, který se přidá `MyApp` do ovládacího panelu Přidat nebo odebrat programy v systému Windows. `UNINSTALL_KEY MyApp` Parametr Description je zadán jako `My Application Description`.

```console
gacutil /i /r myDll.dll UNINSTALL_KEY MyApp "My Application Description"
```

Následující příkaz se nainstaluje `myDll.dll` do globální mezipaměti sestavení (GAC) a přidá odkaz pro jeho počítání. Parametr schématu, `FILEPATH`a `c:\applications\myApp\myApp.exe`parametr ID zadejte cestu k aplikaci, která instaluje `myDll.dll.` parametr Description, je zadána jako `MyApp`.

```console
gacutil /i /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp
```

Následující příkaz se nainstaluje `myDll.dll` do globální mezipaměti sestavení (GAC) a přidá odkaz pro jeho počítání. Parametr `OPAQUE`schématu umožňuje přizpůsobit parametry ID a popisu.

```console
gacutil /i /r mydll.dll OPAQUE "Insert custom application details here" "Insert Custom description information here"
```

Následující příkaz odebere odkaz na `myDll.dll` aplikaci. `myApp` Jde-li o poslední odkaz na sestavení, příkaz toto sestavení zároveň odebere z globální mezipaměti sestavení (GAC).

```console
gacutil /u /r myDll.dll FILEPATH c:\applications\myApp\myApp.exe MyApp
```

Následující příkaz vypíše obsah globální mezipaměti sestavení (GAC).

```console
gacutil /l
```

## <a name="see-also"></a>Viz také:

- [Nástroje](../../../docs/framework/tools/index.md)
- [Globální mezipaměť sestavení](../../../docs/framework/app-domains/gac.md)
- [Regasm.exe (nástroj registrace sestavení)](../../../docs/framework/tools/regasm-exe-assembly-registration-tool.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

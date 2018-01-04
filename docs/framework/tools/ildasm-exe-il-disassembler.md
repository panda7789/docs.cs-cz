---
title: Ildasm.exe (IL Disassembler)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- PE files, MSIL Disassembler
- portable executable files, MSIL Disassembler
- Ildasm.exe
- MSIL Disassembler
- text files produced by MSIL Disassembler
- disassembling file for MSIL Assembler input
ms.assetid: db27f6b2-f1ec-499e-be3a-7eecf95ca42b
caps.latest.revision: "33"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f42726b24abe78b151e4174da37b7c7bfff4c8d4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (IL Disassembler)

IL Disassembler je doprovodný nástroj, který assembleru IL (*Ilasm.exe*). *Ildasm.exe* trvá soubor přenosné spustitelný soubor (PE), který obsahuje kód intermediate language (IL) a vytvoří textový soubor vhodný jako vstup pro *Ilasm.exe*.

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```
ildasm [options] [PEfilename] [options]
```

#### <a name="parameters"></a>Parametry

Jsou k dispozici pro následující možnosti *.exe*, *.dll*, *.obj*, *.lib*, a *.winmd* soubory.

| Možnost | Popis |
| ------ | ----------- |
|**/ out =**`filename`|Vytvoří výstupní soubor se zadaným `filename`, místo zobrazení výsledky v grafickém uživatelském rozhraní.|
|**/RTF**|Vytvoří výstup ve formátu RTF (Rich Text Format). Neplatná s **/text** možnost.|
|**/ text**|Zobrazí výsledky v okně konzoly namísto grafického uživatelského rozhraní nebo výstupního souboru.|
|**/ HTML**|Vytvoří výstup ve formátu HTML. Platný s **/výstup** pouze možnost.|
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|

Následující další možnosti jsou dostupné pro *.exe*, *.dll*, a *.winmd* soubory.

| Možnost | Popis |
| ------ | ----------- |
|**/bytes**|Zobrazí skutečné bajty v šestnáctkovém formátu jako komentáře k instrukcím.|
|**/caverbal**|Vytvoří objekty blob vlastních atributů ve slovním vyjádření. Výchozím nastavením je binární vyjádření.|
|**/linenum**|Zahrne odkazy do původních zdrojových řádků.|
|**/nobar**|Potlačí místní okno indikátoru průběhu zpětného překladu.|
|**/noca**|Potlačí výstup vlastních atributů.|
|**/ Project**|Zobrazuje metadata způsob, jakým se zdá, že spravovaného kódu, místo způsob, jakým se zobrazí v nativního [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Pokud `PEfilename` není metadat Windows (*.winmd*) souborů, tato možnost nemá žádný vliv. V tématu [podpora v rozhraní .NET Framework pro aplikace pro Windows Store a prostředí Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).|
|**/pubonly**|Zpětně přeloží pouze veřejné typy a členy. Ekvivalentní **/visibility:PUB**.|
|**/quoteallnames**|Vloží všechny názvy do jednoduchých uvozovek.|
|**/raweh**|Zobrazí klauzule zpracování výjimek v nezpracovaném tvaru.|
|**/ Source**|Zobrazí původní zdrojové řádky jako komentáře.|
|**/ tokens**|Zobrazí tokeny metadat pro třídy a členy.|
|**/Visibility:** `vis`[+`vis`...]|Zpětně přeloží pouze typy nebo členy se zadanou viditelností. Platné hodnoty jsou následující `vis`:<br /><br /> **Protokol PUB** – veřejné<br /><br /> **PRI** – privátní<br /><br /> **Služba FAM** – rodiny<br /><br /> **ASM** – sestavení<br /><br /> **FÁ** – rodiny a sestavení<br /><br /> **FOA** – třídu nebo sestavení<br /><br /> **Kontejner nastavení HESEL** – privátní oboru<br /><br /> Definice těchto viditelnost modifikátory naleznete v tématu <xref:System.Reflection.MethodAttributes> a <xref:System.Reflection.TypeAttributes>.|

Tyto možnosti jsou platné pro *.exe*, *.dll*, a *.winmd* soubory pro soubor nebo pouze výstup konzoly.

| Možnost | Popis |
| ------ | ----------- |
|**/ all**|Určuje kombinaci **/header**, **/bytes**, **/stats**, **/classlist**, a **/tokeny** Možnosti.|
|**/classlist**|Zahrne seznam tříd definovaných v modulu.|
|**/ předat dál**|Použije dopřednou deklaraci tříd.|
|**/headers**|Zahrne do výstupu informace z hlavičky souboru.|
|**/ bodu:** `class`[**::** `member`[`(sig`]]|V závislosti na zadaných argumentech zpětně přeloží následující:<br /><br /> -Provede zpětný překlad zadaný `class`.<br />-Provede zpětný překlad zadaný `member` z `class`.<br />-Provede zpětný překlad `member` z `class` zadaný podpisem `sig`. Formát `sig` je:<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)<br />     **Poznámka:** v rozhraní .NET Framework verze 1.0 a 1.1, `sig` musí následovat kulaté závorky: `(sig)`. Musí být vynechána počínaje Net Framework 2.0 kulaté závorky: (`sig`.|
|**/noil**|Potlačí výstup kódu sestavení jazyka IL.|
|**/ stats**|Vloží statistiky o bitové kopii.|
|**/typelist**|Vytvoří úplný seznam typů pro zachování řazení typů při přenosu.|
|**/ Unicode**|Použije pro výstup kódování Unicode.|
|**/UTF8**|Použije pro výstup kódování UTF-8. Výchozím je ANSI.|

Tyto možnosti jsou platné pro *.exe*, *.dll*, *.obj*, *.lib*, a *.winmd* soubory pro soubor nebo pouze výstup konzoly.

| Možnost | Popis |
| ------ | ----------- |
|**/ metadata**[=`specifier`]|Zobrazuje metadata, kde `specifier` je:<br /><br /> **MDHEADER** – zobrazit záhlaví informace metadat a velikosti.<br /><br /> **ŠESTNÁCTKOVÝCH** – zobrazují informace ve šestnáctkově také slova.<br /><br /> **CSV** – zobrazit záznamů počet a velikost haldy.<br /><br /> **UNREX** – zobrazit chyby definicí.<br /><br /> **SCHÉMA** – zobrazit záhlaví a schéma informace metadat.<br /><br /> **NEZPRACOVANÁ** – zobrazit nezpracované metadat tabulky.<br /><br /> **HALDÁCH** – zobrazit nezpracované haldách.<br /><br /> **Ověřit** – ověření konzistence metadat.<br /><br /> Můžete zadat **/metadata** vícekrát, s různými hodnotami `specifier`.|

Tyto možnosti jsou platné pro *.lib* soubory pro soubor nebo pouze výstup konzoly.

| Možnost | Popis |
| ------ | ----------- |
|**/objectfile**=`filename`|Zobrazí metadata souboru jednoho objektu v zadané knihovně.|

> [!NOTE]
> Všechny možnosti pro *Ildasm.exe* jsou velká a malá písmena a rozpoznaný podle prvních tří písmen. Například **/quo** je ekvivalentní **/quoteallnames**. Možnosti s argumenty přijímají jako oddělovač mezi možností a argumentem dvojtečku (:) nebo symbol rovná se (=). Například **/výstup:** *filename* je ekvivalentní **/výstup =** *filename*.

## <a name="remarks"></a>Poznámky

*Ildasm.exe* funguje pouze na soubory PE na disku. Nepracuje se soubory nainstalovanými do globální mezipaměti sestavení.

Textový soubor vyprodukované *Ildasm.exe* lze použít jako vstup pro assembleru IL (*Ilasm.exe*). Toho lze využít například při kompilování kódu v programovacím jazyce, který nepodporuje všechny atributy modulu runtime. Po kompilaci kódu a spouštění jeho výstup *Ildasm.exe*, bude výsledný soubor IL text může být ručně upravovat přidat chybějící atributy. Poté lze tento textový soubor zpracovat nástrojem IL Assembler a vytvořit konečný spustitelný soubor.

> [!NOTE]
> Momentálně nelze tuto techniku použít se soubory PE obsahujícími vložený nativní kód (například PE soubory vytvořené jazykem Visual C++).  

Chcete-li zobrazit metadata a zpětně přeložený kód libovolného existujícího souboru PE v hierarchickém stromovém zobrazení, lze použít výchozí grafické uživatelské rozhraní nástroje IL Disassembler. Chcete-li použít grafické uživatelské rozhraní, zadejte **ildasm** na příkazovém řádku bez nutnosti zadávat *PEfilename* argument, nebo jakékoli možnosti. Z **soubor** nabídky, můžete přejít k souboru PE, který chcete načíst do *Ildasm.exe*. Pokud chcete uložit metadata a zpětně přeložený kód zobrazí pro vybrané PE, vyberte **Dump** příkaz **souboru** nabídky. Uložte hierarchické stromové zobrazení pouze, vyberte **Dump Treeview** příkaz **souboru** nabídky. Podrobný průvodce načítání souboru do *Ildasm.exe* a interpretace výstup, najdete v článku *Ildasm.exe* kurzu, umístěný ve složce ukázky, který se dodává s [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

Pokud zadáte *Ildasm.exe* s *PEfilename* argument, který obsahuje vložené prostředky, nástroj vytvoří několik výstupní soubory: textový soubor, který obsahuje kód IL a pro každou vložených spravované prostředek, souboru .resources vytvořeného pomocí názvu prostředku z metadat. Pokud nespravovaný prostředek je integrovaný v *PEfilename*, soubor .res je vytvořen pomocí název souboru zadaný pro IL výstupem **/výstup** možnost.

> [!NOTE]
> *Ildasm.exe* zobrazuje pouze metadata popisy pro *.obj* a *.lib* vstupní soubory. Kód IL není pro tyto typy souborů zpětně překládán.

Můžete spustit *Ildasm.exe* přes an.exe nebo *.dll* soubor k určení, jestli je soubor spravovaný. Není-li soubor spravovaný, nástroj zobrazí zprávu oznamující, že soubor neobsahuje žádnou platnou hlavičku modulu CLR a nelze jej zpětně přeložit. Pokud soubor spravovaný je, nástroj se úspěšně spustí.

## <a name="version-information"></a>Informace o verzi

Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], *Ildasm.exe* zobrazením Nezpracovaná binární obsah, který zpracovává nerozpoznané zařazování BLOB (binární rozsáhlý objekt). Následující kód například ukazuje, jak je zobrazen zařazovací objekt BLOB vygenerovaný programem jazyka C#:

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], *Ildasm.exe* zobrazí atributy, které se použijí pro implementace rozhraní, jak je znázorněno v následující výňatek ze *Ildasm.exe* výstup:

```
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

## <a name="examples"></a>Příklady

Následující příkaz způsobí, že metadata a převeden kód pro soubor PE `MyHello.exe` zobrazíte v *Ildasm.exe* výchozí grafickým uživatelským rozhraním.

```console
ildasm myHello.exe
```

Následující příkaz provede zpětný překlad soubor `MyFile.exe` a uloží výsledné IL assembleru text v souboru *MyFile.il*.

```console
ildasm MyFile.exe /output:MyFile.il
```

Následující příkaz provede zpětný překlad soubor `MyFile.exe` a zobrazí výsledná IL assembleru text do okna konzoly.

```console
ildasm MyFile.exe /text
```

Pokud soubor `MyApp.exe` obsahuje vložené spravovaných a nespravovaných prostředků, následující příkaz vytvoří čtyři soubory: *MyApp.il*, *MyApp.res*, *Icons.resources*, a *Message.resources*:

```console
ildasm MyApp.exe /output:MyApp.il
```

Následující příkaz provede zpětný překlad metodu `MyMethod` v rámci třídy `MyClass` v `MyFile.exe` a zobrazí se výstup do okna konzoly.

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

V předchozím příkladu, může být několik metod s názvem `MyMethod` s jinou podpisy. Následující příkaz provede zpětný překlad metodu instance `MyMethod` s návratovým typem **void** a typy parametrů **int32** a **řetězec**.

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> V rozhraní .NET Framework verze 1.0 a 1.1, levé závorky, který následuje metodu název musí být vyrovnané podle pravé závorky po podpis: `MyMethod(instance void(int32))`. Od verze rozhraní .NET Framework 2.0 uzavírací kulatá závorka, musí být vynechána: `MyMethod(instance void(int32)`.

K načtení `static` – metoda (`Shared` metody v jazyce Visual Basic), vynechejte klíčové slovo `instance`. Třídy typy, které nejsou primitivní typy, jako je `int32` a `string` musí obsahovat obor názvů a musí být zadáno klíčové slovo `class`. Před externími typy musí být uveden název knihovny v hranatých závorkách. Následující příkaz provede zpětný překlad statickou metodu s názvem `MyMethod` který má jeden parametr typu <xref:System.AppDomain> a má návratový typ <xref:System.AppDomain>.

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

Před vnořeným typem musí být uvedena třída, která jej obsahuje, oddělená lomítkem. Například pokud `MyNamespace.MyClass` třída obsahuje vnořené třídy s názvem `NestedClass`, vnořené třídy se identifikuje následujícím způsobem: `class MyNamespace.MyClass/NestedClass`.

## <a name="see-also"></a>Viz také

[Nástroje](../../../docs/framework/tools/index.md)  
[Ilasm.exe (IL Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md)  
[Proces spravovaného spuštění](../../../docs/standard/managed-execution-process.md)  
[Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

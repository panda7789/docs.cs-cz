---
title: Ildasm.exe (IL Disassembler)
ms.date: 03/30/2017
helpviewer_keywords:
- PE files, MSIL Disassembler
- portable executable files, MSIL Disassembler
- Ildasm.exe
- MSIL Disassembler
- text files produced by MSIL Disassembler
- disassembling file for MSIL Assembler input
ms.assetid: db27f6b2-f1ec-499e-be3a-7eecf95ca42b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9d08d6164c00d2b5b750c9edda46a7be18153152
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71044647"
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (IL Disassembler)

IL Disassembler je doprovodný nástroj k assembleru IL (*Ilasm. exe*). *Ildasm. exe* přebírá přenosný spustitelný soubor (PE), který obsahuje kód mezilehlého jazyka (IL) a vytváří textový soubor vhodný jako vstup do *Ilasm. exe*.

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```console
ildasm [options] [PEfilename] [options]
```

## <a name="parameters"></a>Parametry

Pro soubory *. exe*, *. dll*, *. obj*, *. lib*a *. winmd* jsou k dispozici následující možnosti.

| Možnost | Popis |
| ------ | ----------- |
|**/out =** `filename`|Vytvoří výstupní soubor se zadaným parametrem `filename`namísto zobrazení výsledků v grafickém uživatelském rozhraní.|
|**/rtf**|Vytvoří výstup ve formátu RTF (Rich Text Format). Neplatné s možností **/text**|
|**/text**|Zobrazí výsledky v okně konzoly namísto grafického uživatelského rozhraní nebo výstupního souboru.|
|**/html**|Vytvoří výstup ve formátu HTML. Platí pouze s možností **/Output** .|
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|

Pro soubory *. exe*, *. dll*a *. winmd* jsou k dispozici následující další možnosti.

| Možnost | Popis |
| ------ | ----------- |
|**/bytes**|Zobrazí skutečné bajty v šestnáctkovém formátu jako komentáře k instrukcím.|
|**/caverbal**|Vytvoří objekty blob vlastních atributů ve slovním vyjádření. Výchozím nastavením je binární vyjádření.|
|**/linenum**|Zahrne odkazy do původních zdrojových řádků.|
|**/nobar**|Potlačí místní okno indikátoru průběhu zpětného překladu.|
|**/noca**|Potlačí výstup vlastních atributů.|
|**/project**|Zobrazuje metadata tak, jak se zobrazí spravovanému kódu, namísto způsobu zobrazení v nativním prostředí Windows Runtime. Pokud `PEfilename` není soubor metadat Windows ( *. winmd*), tato možnost nemá žádný vliv. Viz [.NET Framework Podpora aplikací pro Windows Store a prostředí Windows Runtime](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).|
|**/pubonly**|Zpětně přeloží pouze veřejné typy a členy. Ekvivalent **/visibility: Pub**.|
|**/quoteallnames**|Vloží všechny názvy do jednoduchých uvozovek.|
|**/raweh**|Zobrazí klauzule zpracování výjimek v nezpracovaném tvaru.|
|**/Source**|Zobrazí původní zdrojové řádky jako komentáře.|
|**/Tokens**|Zobrazí tokeny metadat pro třídy a členy.|
|**/visibility:** `vis`[+`vis`...]|Zpětně přeloží pouze typy nebo členy se zadanou viditelností. Platné jsou následující hodnoty `vis`:<br /><br /> **Pub** – veřejné<br /><br /> **Pri** – privátní<br /><br /> **FAM** – rodina<br /><br /> **ASM** – sestavení<br /><br /> **FAA** – řada a sestavení<br /><br /> **FOA** – řada nebo sestavení<br /><br /> **PSC** – privátní obor<br /><br /> Definice těchto modifikátorů viditelnosti naleznete v tématech <xref:System.Reflection.MethodAttributes> a <xref:System.Reflection.TypeAttributes>.|

Následující možnosti jsou platné pro soubory *. exe*, *. dll*a *. winmd* pouze pro výstup do souboru nebo konzoly.

| Možnost | Popis |
| ------ | ----------- |
|**/All**|Určuje kombinaci možností **/header**, **/bytes**, **/stats**, **/classlist**a **/tokens** .|
|**/classlist**|Zahrne seznam tříd definovaných v modulu.|
|**/forward**|Použije dopřednou deklaraci tříd.|
|**/Headers**|Zahrne do výstupu informace z hlavičky souboru.|
|**/Item:** `class`[ **::** `member`[`(sig`]]|V závislosti na zadaných argumentech zpětně přeloží následující:<br /><br /> -Rozloží zadanou `class`.<br />-Rozloží zadanou `member` `class`z.<br />-Rozloží `member` `class` sadu se zadaným podpisem `sig`. Formát `sig` je:<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)<br />     **Poznámka:** V .NET Framework verzích 1,0 a 1,1 `sig` musí následovat pravá závorka:. `(sig)` Počínaje rozhraním .NET Framework 2,0 musí být uzavírací závorka vynechána: `(sig`.|
|**/noil**|Potlačí výstup kódu sestavení jazyka IL.|
|**/stats**|Vloží statistiky o bitové kopii.|
|**/typelist**|Vytvoří úplný seznam typů pro zachování řazení typů při přenosu.|
|**/unicode**|Použije pro výstup kódování Unicode.|
|**/utf8**|Použije pro výstup kódování UTF-8. Výchozím je ANSI.|

Následující možnosti jsou platné pro soubory *. exe*, *. dll*, *. obj*, *. lib*a *. winmd* pouze pro výstup do souboru nebo konzoly.

| Možnost | Popis |
| ------ | ----------- |
|**/metadata**[=`specifier`]|Zobrazuje metadata, kde `specifier` je:<br /><br /> **MDHEADER** – zobrazí informace a velikosti záhlaví metadat.<br /><br /> **Hex** – zobrazí informace v šestnáctkové soustavě i v slovech.<br /><br /> **CSV** – zobrazit počty záznamů a velikosti haldy.<br /><br /> **UNREX** – zobrazí nerozpoznané externí typy.<br /><br /> **Schéma** – zobrazí hlavičku metadat a informace o schématu.<br /><br /> **Raw** – zobrazí nezpracované tabulky metadat.<br /><br /> **Haldy** – zobrazí nezpracované haldy.<br /><br /> **Ověřit** – ověří konzistenci metadat.<br /><br /> **/Metadata** můžete zadat vícekrát s různými hodnotami pro `specifier`.|

Následující možnosti jsou platné pro soubory *. lib* pouze pro výstup do souboru nebo konzoly.

| Možnost | Popis |
| ------ | ----------- |
|**/objectfile**=`filename`|Zobrazí metadata souboru jednoho objektu v zadané knihovně.|

> [!NOTE]
> Všechny možnosti nástroje *Ildasm. exe* nerozlišují velká a malá písmena, která jsou rozpoznána prvními třemi písmeny. Například **/quo** je ekvivalentem **/quoteallnames**. Možnosti s argumenty přijímají jako oddělovač mezi možností a argumentem dvojtečku (:) nebo symbol rovná se (=). Například **/output:** *filename* je ekvivalentem **/Output =** *filename*.

## <a name="remarks"></a>Poznámky

Nástroj *Ildasm. exe* pracuje pouze na souborech PE na disku. Nepracuje se soubory nainstalovanými do globální mezipaměti sestavení.

Textový soubor vytvořený pomocí programu *Ildasm. exe* lze použít jako vstup pro rozhraní IL Assembler (*Ilasm. exe*). Toho lze využít například při kompilování kódu v programovacím jazyce, který nepodporuje všechny atributy modulu runtime. Po zkompilování kódu a spuštění jeho výstupu prostřednictvím programu *Ildasm. exe*lze výsledný textový soubor IL ručně upravit a přidat chybějící atributy. Poté lze tento textový soubor zpracovat nástrojem IL Assembler a vytvořit konečný spustitelný soubor.

> [!NOTE]
> Momentálně nelze tuto techniku použít se soubory PE obsahujícími vložený nativní kód (například PE soubory vytvořené jazykem Visual C++).  

Chcete-li zobrazit metadata a zpětně přeložený kód libovolného existujícího souboru PE v hierarchickém stromovém zobrazení, lze použít výchozí grafické uživatelské rozhraní nástroje IL Disassembler. Chcete-li použít grafické uživatelské rozhraní, zadejte text **Ildasm** na příkazovém řádku bez zadání argumentu *PEfilename* nebo jakékoli možnosti. V nabídce **soubor** můžete přejít na soubor PE, který chcete načíst do programu *Ildasm. exe*. Chcete-li uložit metadata a zpětně přeložený kód pro vybrané prostředí PE, vyberte příkaz pro **Výpis paměti** v nabídce **soubor** . Chcete-li uložit pouze hierarchické zobrazení stromové struktury, vyberte příkaz **dump TreeView** v nabídce **soubor** . Podrobný průvodce načítání souboru do programu *Ildasm. exe* a interpretace výstupu naleznete v kurzu *Ildasm. exe* , který je umístěn ve složce Samples, která je dodávána s Windows SDK.

Pokud zadáte *Ildasm. exe* s argumentem *PEfilename* , který obsahuje vložené prostředky, nástroj vytvoří více výstupních souborů: textový soubor, který obsahuje kód Il a pro každý vložený spravovaný prostředek, soubor. Resources vytvořený pomocí název prostředku z metadat Pokud je nespravovaný prostředek vložený do *PEfilename*, vytvoří se soubor. res pomocí parametru **/Output** zadaného pro výstup Il.

> [!NOTE]
> Nástroj *Ildasm. exe* zobrazuje pouze popisy metadat pro vstupní soubory *. obj* a *. lib* . Kód IL není pro tyto typy souborů zpětně překládán.

*Ildasm. exe* můžete spustit přes soubor. exe nebo *. dll* , abyste zjistili, jestli je soubor spravovaný. Není-li soubor spravovaný, nástroj zobrazí zprávu oznamující, že soubor neobsahuje žádnou platnou hlavičku modulu CLR a nelze jej zpětně přeložit. Pokud soubor spravovaný je, nástroj se úspěšně spustí.

## <a name="version-information"></a>Informace o verzi

Od .NET Framework 4,5 nástroj *Ildasm. exe* zpracovává NEROZPOZNANÝ objekt BLOB pro zařazování (binární rozsáhlý objekt) zobrazením nezpracovaného binárního obsahu. Následující kód například ukazuje, jak je zobrazen zařazovací objekt BLOB vygenerovaný programem jazyka C#:

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```il
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

Od .NET Framework 4,5 nástroj *Ildasm. exe* zobrazí atributy, které jsou aplikovány na implementace rozhraní, jak je znázorněno v následujícím výňatku z výstupu *Ildasm. exe* :

```il
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

Následující příkaz způsobí, že metadata a zpětně přeložený kód pro soubor `MyHello.exe` PE se zobrazí ve výchozím grafickém uživatelském rozhraní *Ildasm. exe* .

```console
ildasm myHello.exe
```

Následující příkaz zpětně přeloží soubor `MyFile.exe` a uloží výsledný text IL Assembler do souboru *MyFile.Il*.

```console
ildasm MyFile.exe /output:MyFile.il
```

Následující příkaz zpětně přeloží soubor `MyFile.exe` a zobrazí výsledný text IL Assembler v okně konzoly.

```console
ildasm MyFile.exe /text
```

Pokud soubor `MyApp.exe` obsahuje vložené spravované a nespravované prostředky, vytvoří následující příkaz čtyři soubory: *MyApp.Il*, *MyApp. res*, *ikony. Resources*a *Message. Resources*:

```console
ildasm MyApp.exe /output:MyApp.il
```

Následující příkaz zpětně přeloží metodu `MyMethod` v rámci třídy `MyClass` v `MyFile.exe` a zobrazí výstup do okna konzoly.

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

V předchozím příkladu může existovat několik metod s názvem `MyMethod` s různými podpisy. Následující příkaz zpětně přeloží `MyMethod` metodu instance s návratovým typem **void** a typy parametrů **Int32** a **String**.

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> V .NET Framework verzích 1,0 a 1,1 musí být levá závorka, která následuje za názvem metody, vyrovnávána pravou závorkou za signaturou: `MyMethod(instance void(int32))`. Počínaje .NET Framework 2,0 musí být uzavírací závorka vynechána: `MyMethod(instance void(int32)`.

Chcete-li `static` načíst metodu`Shared` (metodu v Visual Basic), vynechejte `instance`klíčové slovo. Typy tříd, které nejsou primitivní typy jako `int32` a `string` musí obsahovat obor názvů a musí předcházet klíčové slovo `class`. Před externími typy musí být uveden název knihovny v hranatých závorkách. Následující příkaz zpětně přeloží statickou metodu s názvem `MyMethod` , která má jeden parametr typu <xref:System.AppDomain> a <xref:System.AppDomain>má návratový typ.

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

Před vnořeným typem musí být uvedena třída, která jej obsahuje, oddělená lomítkem. Například pokud `MyNamespace.MyClass` třída obsahuje vnořenou třídu s názvem `NestedClass`, vnořená třída je identifikována takto: `class MyNamespace.MyClass/NestedClass`.

## <a name="see-also"></a>Viz také:

- [Nástroje](index.md)
- [Ilasm.exe (IL Assembler)](ilasm-exe-il-assembler.md)
- [Proces spravovaného spuštění](../../standard/managed-execution-process.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)

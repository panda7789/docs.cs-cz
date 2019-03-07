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
ms.openlocfilehash: 3e96f86e516e7b741aa9fbf67efd1683d0845101
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488510"
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (IL Disassembler)

IL Disassembler je doprovodný nástroj k nástroji IL Assembler (*Ilasm.exe*). *Ildasm.exe* přebírá soubor (PE portable executable) obsahující kód (IL intermediate language) a vytváří textový soubor vhodný jako vstup do *Ilasm.exe*.

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```
ildasm [options] [PEfilename] [options]
```

## <a name="parameters"></a>Parametry

Tyto možnosti jsou k dispozici pro *.exe*, *.dll*, *.obj*, *lib*, a *.winmd* soubory.

| Možnost | Popis |
| ------ | ----------- |
|**/ out =** `filename`|Vytvoří výstupní soubor se zadaným `filename`, namísto zobrazení výsledků v grafickém uživatelském rozhraní.|
|**/rtf**|Vytvoří výstup ve formátu RTF (Rich Text Format). Neplatná s **/text** možnost.|
|**/text**|Zobrazí výsledky v okně konzoly namísto grafického uživatelského rozhraní nebo výstupního souboru.|
|**/html**|Vytvoří výstup ve formátu HTML. Platný s **/output** jen možnost.|
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|

K dispozici pro následující další možnosti *.exe*, *.dll*, a *.winmd* soubory.

| Možnost | Popis |
| ------ | ----------- |
|**/bytes**|Zobrazí skutečné bajty v šestnáctkovém formátu jako komentáře k instrukcím.|
|**/caverbal**|Vytvoří objekty blob vlastních atributů ve slovním vyjádření. Výchozím nastavením je binární vyjádření.|
|**/linenum**|Zahrne odkazy do původních zdrojových řádků.|
|**/nobar**|Potlačí místní okno indikátoru průběhu zpětného překladu.|
|**/noca**|Potlačí výstup vlastních atributů.|
|**/project**|Zobrazí metadata tak, jak se spravovaným kódem, místo tak, jak se zobrazuje v nativní [!INCLUDE[wrt](../../../includes/wrt-md.md)]. Pokud `PEfilename` není metadat Windows (*.winmd*) soubor, tato možnost nemá žádný vliv. Zobrazit [podpora rozhraní .NET Framework pro aplikace Windows Store a prostředí Windows Runtime](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).|
|**/pubonly**|Zpětně přeloží pouze veřejné typy a členy. Ekvivalentní **/visibility:PUB**.|
|**/quoteallnames**|Vloží všechny názvy do jednoduchých uvozovek.|
|**/raweh**|Zobrazí klauzule zpracování výjimek v nezpracovaném tvaru.|
|**/ Source**|Zobrazí původní zdrojové řádky jako komentáře.|
|**/ tokens**|Zobrazí tokeny metadat pro třídy a členy.|
|**/Visibility:** `vis`[+`vis`...]|Zpětně přeloží pouze typy nebo členy se zadanou viditelností. Platné hodnoty jsou následující `vis`:<br /><br /> **Publikování a odběru** – veřejné<br /><br /> **PRI** – privátní<br /><br /> **Služba FAM** – řada<br /><br /> **ASM** – sestavení<br /><br /> **Zákon FAA** – Family a Assembly<br /><br /> **FOA** – Family nebo Assembly<br /><br /> **PSC** – soukromý obor<br /><br /> Definice těchto modifikátorů viditelnosti naleznete v tématu <xref:System.Reflection.MethodAttributes> a <xref:System.Reflection.TypeAttributes>.|

Následující možnosti jsou platné pro *.exe*, *.dll*, a *.winmd* soubory pro soubor nebo pouze výstup konzoly.

| Možnost | Popis |
| ------ | ----------- |
|**/ all**|Určí kombinaci možností **/header**, **/bytes**, **toto**, **/classlist**, a **/tokens** Možnosti.|
|**/classlist**|Zahrne seznam tříd definovaných v modulu.|
|**/ vpřed**|Použije dopřednou deklaraci tříd.|
|**/headers**|Zahrne do výstupu informace z hlavičky souboru.|
|**/item:** `class`[**::** `member`[`(sig`]]|V závislosti na zadaných argumentech zpětně přeloží následující:<br /><br /> -Zpětně přeloží zadanou `class`.<br />-Zpětně přeloží zadanou `member` z `class`.<br />-Zpětně přeloží `member` z `class` se zadaným podpisem `sig`. Formát `sig` je:<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)<br />     **Poznámka:** v rozhraní .NET Framework verze 1.0 a 1.1, `sig` musí být následován pravou závorkou: `(sig)`. Počínaje rozhraním .NET Framework 2.0 pravou závorkou musí být vynechána: (`sig`.|
|**/noil**|Potlačí výstup kódu sestavení jazyka IL.|
|**Toto**|Vloží statistiky o bitové kopii.|
|**/typelist**|Vytvoří úplný seznam typů pro zachování řazení typů při přenosu.|
|**Unicode**|Použije pro výstup kódování Unicode.|
|**/utf8**|Použije pro výstup kódování UTF-8. Výchozím je ANSI.|

Následující možnosti jsou platné pro *.exe*, *.dll*, *.obj*, *lib*, a *.winmd* soubory pro soubor nebo pouze výstup konzoly.

| Možnost | Popis |
| ------ | ----------- |
|**/metadata**[=`specifier`]|Zobrazí metadata, kde `specifier` je:<br /><br /> **MDHEADER** – zobrazí informace hlavičky metadat a velikosti.<br /><br /> **HEXADECIMÁLNÍ** – zobrazí informace v šestnáctkové soustavě stejně jako v slova.<br /><br /> **Sdílený svazek clusteru** – zobrazí počty záznamů a velikosti hald.<br /><br /> **UNREX** – zobrazí nerozpoznané externí typy.<br /><br /> **SCHÉMA** – zobrazí informace hlavičky a schéma metadat.<br /><br /> **NEZPRACOVANÁ** – zobrazí tabulky nezpracovaných metadat.<br /><br /> **HALDY** – zobrazí nezpracované haldy.<br /><br /> **Ověřit** – ověří konzistentnost metadat.<br /><br /> Můžete zadat **/metadata** několikrát s různými hodnotami parametru `specifier`.|

Následující možnosti jsou platné pro *lib* soubory pro soubor nebo pouze výstup konzoly.

| Možnost | Popis |
| ------ | ----------- |
|**/objectfile**=`filename`|Zobrazí metadata souboru jednoho objektu v zadané knihovně.|

> [!NOTE]
> Všechny možnosti pro *Ildasm.exe* jsou malá a velká písmena rozpoznávány dle prvních tří písmen. Například **/quo** je ekvivalentní **/quoteallnames**. Možnosti s argumenty přijímají jako oddělovač mezi možností a argumentem dvojtečku (:) nebo symbol rovná se (=). Například **/output:** *filename* je ekvivalentní **/output =** *filename*.

## <a name="remarks"></a>Poznámky

*Ildasm.exe* pracuje pouze se soubory PE na disku. Nepracuje se soubory nainstalovanými do globální mezipaměti sestavení.

Textový soubor vytvářených *Ildasm.exe* lze použít jako vstup pro nástroj IL Assembler (*Ilasm.exe*). Toho lze využít například při kompilování kódu v programovacím jazyce, který nepodporuje všechny atributy modulu runtime. Po zkompilování kódu a zpracování výstupu nástrojem *Ildasm.exe*, lze výsledný textový soubor IL ručně upravit a přidat chybějící atributy. Poté lze tento textový soubor zpracovat nástrojem IL Assembler a vytvořit konečný spustitelný soubor.

> [!NOTE]
> Momentálně nelze tuto techniku použít se soubory PE obsahujícími vložený nativní kód (například PE soubory vytvořené jazykem Visual C++).  

Chcete-li zobrazit metadata a zpětně přeložený kód libovolného existujícího souboru PE v hierarchickém stromovém zobrazení, lze použít výchozí grafické uživatelské rozhraní nástroje IL Disassembler. Chcete-li použít grafické uživatelské rozhraní, zadejte **ildasm** příkazového řádku bez zadání *PEfilename* argument nebo jakýchkoli možností. Z **souboru** nabídky, se můžete dostat přenositelného Spustitelného souboru, který chcete načíst do *Ildasm.exe*. Chcete-li uložit metadata a zpětně přeložený kód pro vybrané PE, vyberte **výpisu paměti** příkaz **souboru** nabídky. Uložte hierarchické stromové zobrazení pouze, vyberte **vypsat stromové zobrazení** příkaz **souboru** nabídky. Podrobné pokyny k načítání souboru do *Ildasm.exe* a interpretaci výstupu, podívejte se *Ildasm.exe* kurz, umístěný ve složce Samples, která se dodává s [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

Pokud zadáte *Ildasm.exe* s *PEfilename* argument, který obsahuje vložené prostředky, nástroj vytvoří několik výstupních souborů: textový soubor obsahující kód IL a pro každý vložený spravovaný prostředek, soubor .resources vytvořený za použití názvu prostředku z metadat. Pokud je součástí nespravovaný prostředek *PEfilename*, soubor .res je vytvořen pomocí názvu souboru určeného pro výstup IL **/output** možnost.

> [!NOTE]
> *Ildasm.exe* zobrazuje pouze popisů metadat pro *.obj* a *lib* vstupních souborů. Kód IL není pro tyto typy souborů zpětně překládán.

Můžete spustit *Ildasm.exe* přes an.exe nebo *.dll* soubor k určení, zda je soubor spravovaný. Není-li soubor spravovaný, nástroj zobrazí zprávu oznamující, že soubor neobsahuje žádnou platnou hlavičku modulu CLR a nelze jej zpětně přeložit. Pokud soubor spravovaný je, nástroj se úspěšně spustí.

## <a name="version-information"></a>Informace o verzi

Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], *Ildasm.exe* zpracovává nerozpoznané zařazovací objekty BLOB (binární rozsáhlý objekt) zobrazením nezpracovaného binárního obsahu. Následující kód například ukazuje, jak je zobrazen zařazovací objekt BLOB vygenerovaný programem jazyka C#:

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], *Ildasm.exe* zobrazuje atributy, které se použijí pro implementaci rozhraní tak, jak je znázorněno v následujícím výtažku z *Ildasm.exe* výstup:

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

Pomocí následujícího příkazu způsobí, že metadata a zpětně přeloženého kódu pro soubor PE `MyHello.exe` zobrazíte v *Ildasm.exe* výchozí grafické uživatelské rozhraní.

```console
ildasm myHello.exe
```

Následující příkaz zpětně přeloží soubor `MyFile.exe` a uloží výsledný text nástroje IL Assembler do souboru *MyFile.il*.

```console
ildasm MyFile.exe /output:MyFile.il
```

Následující příkaz zpětně přeloží soubor `MyFile.exe` a zobrazí výsledný text nástroje IL Assembler v okně konzoly.

```console
ildasm MyFile.exe /text
```

Pokud soubor `MyApp.exe` obsahuje vložené spravované nebo nespravované prostředky, vytvoří následující příkaz čtyři soubory: *MyApp.il*, *MyApp.res*, *Icons.resources*, a *Message.resources*:

```console
ildasm MyApp.exe /output:MyApp.il
```

Následující příkaz zpětně přeloží metodu `MyMethod` v rámci třídy `MyClass` v `MyFile.exe` a zobrazí výstup do okna konzoly.

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

V předchozím příkladu, může být několik metod pojmenovaných `MyMethod` s různými signaturami. Následující příkaz zpětně přeloží metodu instance `MyMethod` s návratovým typem **void** a typy parametrů **int32** a **řetězec**.

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> V rozhraní .NET Framework verze 1.0 a 1.1, levá závorka metody název musí být s vyrovnáváním pravou závorkou za signaturou: `MyMethod(instance void(int32))`. Od verze rozhraní .NET Framework 2.0 pravou závorkou musí být vynechána: `MyMethod(instance void(int32)`.

K načtení `static` – metoda (`Shared` metody v jazyce Visual Basic), vynechejte klíčové slovo `instance`. Typy, které nejsou primitivními typy jako třídy `int32` a `string` musí obsahovat obor názvů a musí být předcházen klíčového slova `class`. Před externími typy musí být uveden název knihovny v hranatých závorkách. Následující příkaz zpětně přeloží statickou metodu pojmenovanou `MyMethod` , který má jeden parametr typu <xref:System.AppDomain> a má typ vrácené hodnoty <xref:System.AppDomain>.

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

Před vnořeným typem musí být uvedena třída, která jej obsahuje, oddělená lomítkem. Například pokud `MyNamespace.MyClass` třída obsahuje vnořenou třídu pojmenovanou `NestedClass`, vnořená třída identifikována takto: `class MyNamespace.MyClass/NestedClass`.

## <a name="see-also"></a>Viz také:

- [Nástroje](../../../docs/framework/tools/index.md)
- [Ilasm.exe (IL Assembler)](../../../docs/framework/tools/ilasm-exe-il-assembler.md)
- [Proces spravovaného spuštění](../../../docs/standard/managed-execution-process.md)
- [Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

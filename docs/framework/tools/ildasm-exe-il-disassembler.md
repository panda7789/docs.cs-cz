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
ms.openlocfilehash: f23f8c48a31dffa7d350c872aed7505da7a36861
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105060"
---
# <a name="ildasmexe-il-disassembler"></a>Ildasm.exe (IL Disassembler)

Il Disassembler je doprovodný nástroj k IL Assembleru (*Ilasm.exe).* *Ildasm.exe* přebírá přenosný spustitelný soubor (PE), který obsahuje kód zprostředkujícího jazyka (IL) a vytvoří textový soubor vhodný jako vstup pro *soubor Ilasm.exe*.

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```console
ildasm [options] [PEfilename] [options]
```

## <a name="parameters"></a>Parametry

Následující možnosti jsou k dispozici pro soubory *EXE*, *DLL*, *.obj*, *.lib*a *.winmd.*

| Možnost | Popis |
| ------ | ----------- |
|**/out=**`filename`|Vytvoří výstupní soubor se `filename`zadaným souborem , nikoli zobrazením výsledků v grafickém uživatelském rozhraní.|
|**/rtf**|Vytvoří výstup ve formátu RTF (Rich Text Format). Neplatný s parametrem **/text.**|
|**/text**|Zobrazí výsledky v okně konzoly namísto grafického uživatelského rozhraní nebo výstupního souboru.|
|**/html**|Vytvoří výstup ve formátu HTML. Platí pouze s možností **/output.**|
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|

Pro soubory *EXE*, *DLL*a *.winmd* jsou k dispozici následující další možnosti.

| Možnost | Popis |
| ------ | ----------- |
|**/bajtů**|Zobrazí skutečné bajty v šestnáctkovém formátu jako komentáře k instrukcím.|
|**/caverbální**|Vytvoří objekty blob vlastních atributů ve slovním vyjádření. Výchozím nastavením je binární vyjádření.|
|**/linenum**|Zahrne odkazy do původních zdrojových řádků.|
|**/nobar**|Potlačí místní okno indikátoru průběhu zpětného překladu.|
|**/noca**|Potlačí výstup vlastních atributů.|
|**/projekt**|Zobrazí metadata tak, jak se zobrazí spravovanému kódu, namísto způsobu, jakým se zobrazují v nativním prostředí Windows Runtime. Pokud `PEfilename` není soubor metadat systému Windows (*.winmd*), tato možnost nemá žádný vliv. Viz [podpora rozhraní .NET Framework pro aplikace pro Windows Store a prostředí Windows Runtime](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).|
|**/pubonly**|Zpětně přeloží pouze veřejné typy a členy. Ekvivalent **/visibility:PUB**.|
|**/quoteallnames**|Vloží všechny názvy do jednoduchých uvozovek.|
|**/raweh**|Zobrazí klauzule zpracování výjimek v nezpracovaném tvaru.|
|**/zdroj**|Zobrazí původní zdrojové řádky jako komentáře.|
|**/tokeny**|Zobrazí tokeny metadat pro třídy a členy.|
|**/viditelnost:** `vis`[+`vis`...]|Zpětně přeloží pouze typy nebo členy se zadanou viditelností. Následující hodnoty jsou `vis`platné pro :<br /><br /> **PUB** — Veřejná<br /><br /> **PRI** – soukromé<br /><br /> **FAM** – Rodina<br /><br /> **ASM** – Montáž<br /><br /> **FAA** – Rodina a montáž<br /><br /> **FOA** – rodina nebo montáž<br /><br /> **PsC** – soukromý obor<br /><br /> Definice těchto modifikátorů viditelnosti <xref:System.Reflection.MethodAttributes> <xref:System.Reflection.TypeAttributes>naleznete v tématu a .|

Následující možnosti platí pouze pro soubory *EXE*, *DLL*a *.winmd* pouze pro výstup souborů nebo konzoly.

| Možnost | Popis |
| ------ | ----------- |
|**/vše**|Určuje kombinaci možností **/header**, **/bytes**, **/stats**, **/classlist**a **/tokens.**|
|**/seznam tříd**|Zahrne seznam tříd definovaných v modulu.|
|**/vpřed**|Použije dopřednou deklaraci tříd.|
|**/záhlaví**|Zahrne do výstupu informace z hlavičky souboru.|
|**/položka:** `class`[**::** `member`[`(sig`]]|V závislosti na zadaných argumentech zpětně přeloží následující:<br /><br /> - Demontuje zadaný `class`.<br />- Demontuje specifikované `member` `class`.<br />- Demontuje `member` je `class` se zadaným podpisem `sig`. Formát `sig` je:<br />     [`instance`] `returnType`(`parameterType1`, `parameterType2`, …, `parameterTypeN`)<br />     **Poznámka:** V rozhraní .NET Framework verze 1.0 `sig` a 1.1 musí následovat uzavírací závorka: `(sig)`. Počínaje net frameworkem 2.0 musí být uzavírací závorka vynechána: `(sig`.|
|**/noil**|Potlačí výstup kódu sestavení jazyka IL.|
|**/statistiky**|Vloží statistiky o bitové kopii.|
|**/typelist**|Vytvoří úplný seznam typů pro zachování řazení typů při přenosu.|
|**/unicode**|Použije pro výstup kódování Unicode.|
|**/utf8**|Použije pro výstup kódování UTF-8. Výchozím je ANSI.|

Následující možnosti platí pouze pro soubory *EXE*, *DLL*, *Obj*, *.lib*a *.winmd.*

| Možnost | Popis |
| ------ | ----------- |
|**/metadata**[=`specifier`]|Zobrazuje metadata, `specifier` kde je:<br /><br /> **MDHEADER** — Zobrazit informace záhlaví metadat a velikosti.<br /><br /> **HEX** — Zobrazit informace v hex, stejně jako ve slovech.<br /><br /> **CSV** – Zobrazí počty záznamů a velikosti hald.<br /><br /> **UNREX** — Zobrazit nevyřešené externí.<br /><br /> **SCHEMA** – Zobrazí informace záhlaví metadat a schématu.<br /><br /> **RAW** – Zobrazí tabulky nezpracovaných metadat.<br /><br /> **HEAPS** — Zobrazit surové hromady.<br /><br /> **OVĚŘENÍ** – Ověření konzistence metadat.<br /><br /> **/metadata** můžete zadat vícekrát s `specifier`různými hodnotami pro .|

Následující možnosti platí pouze pro soubory *LIB* pouze pro výstup souboru nebo konzoly.

| Možnost | Popis |
| ------ | ----------- |
|**/objectfile**=`filename`|Zobrazí metadata souboru jednoho objektu v zadané knihovně.|

> [!NOTE]
> Všechny možnosti pro *Ildasm.exe* jsou malá a velká písmena a rozpoznána prvními třemi písmeny. Například **/quo** je ekvivalentní **/quoteallnames**. Možnosti s argumenty přijímají jako oddělovač mezi možností a argumentem dvojtečku (:) nebo symbol rovná se (=). Například **/output:** *název_souboru* je ekvivalentní **/output=** *název_souboru*.

## <a name="remarks"></a>Poznámky

*Ildasm.exe* pracuje pouze na PE soubory na disku. Nepracuje se soubory nainstalovanými do globální mezipaměti sestavení.

Textový soubor vytvořený nástrojem *Ildasm.exe* lze použít jako vstup do il assembleru (*Ilasm.exe).* Toho lze využít například při kompilování kódu v programovacím jazyce, který nepodporuje všechny atributy modulu runtime. Po kompilaci kódu a spuštění jeho výstupu prostřednictvím *ildasm.exe*, výsledný il textový soubor lze ručně upravit přidat chybějící atributy. Poté lze tento textový soubor zpracovat nástrojem IL Assembler a vytvořit konečný spustitelný soubor.

> [!NOTE]
> Momentálně nelze tuto techniku použít se soubory PE obsahujícími vložený nativní kód (například PE soubory vytvořené jazykem Visual C++).  

Chcete-li zobrazit metadata a zpětně přeložený kód libovolného existujícího souboru PE v hierarchickém stromovém zobrazení, lze použít výchozí grafické uživatelské rozhraní nástroje IL Disassembler. Chcete-li použít grafické uživatelské rozhraní, zadejte **ildasm** na příkazovém řádku bez zadání argumentu *PEfilename* nebo jakýchkoli možností. V nabídce **Soubor** můžete přejít na soubor PE, který chcete načíst do *souboru Ildasm.exe*. Chcete-li uložit metadata a rozložený kód zobrazený pro vybrané pe, vyberte příkaz **Výpis** z nabídky **Soubor.** Chcete-li uložit pouze hierarchické zobrazení stromu, vyberte příkaz **Dump Treeview** z nabídky **Soubor.** Podrobný průvodce načtení souboru do *ildasm.exe* a interpretace výstupu naleznete v kurzu *Ildasm.exe,* který se nachází ve složce Ukázky, která je dodávána s sadou Windows SDK.

Pokud poskytnete *ildasm.exe* s *argumentem PEfilename,* který obsahuje vložené prostředky, nástroj vytvoří více výstupních souborů: textový soubor, který obsahuje kód IL a pro každý vložený spravovaný prostředek soubor .resources vytvořený pomocí názvu prostředku z metadat. Pokud je nespravovaný prostředek vložen do *pefilename*, soubor RES je vytvořen pomocí názvu souboru určeného pro výstup IL volbou **/output.**

> [!NOTE]
> *Ildasm.exe* zobrazuje pouze popisy metadat pro vstupní soubory *OBJ* a *LIB.* Kód IL není pro tyto typy souborů zpětně překládán.

Chcete-li zjistit, zda je soubor spravován, můžete spustit soubor *Ildasm.exe* prostředněc an.exe nebo *DLL.* Není-li soubor spravovaný, nástroj zobrazí zprávu oznamující, že soubor neobsahuje žádnou platnou hlavičku modulu CLR a nelze jej zpětně přeložit. Pokud soubor spravovaný je, nástroj se úspěšně spustí.

## <a name="version-information"></a>Informace o verzi

Počínaje rozhraním .NET Framework 4.5 *ildasm.exe* zpracovává nerozpoznaný objekt BLOB maršála (binární velký objekt) zobrazením nezpracovaného binárního obsahu. Následující kód například ukazuje, jak je zobrazen zařazovací objekt BLOB vygenerovaný programem jazyka C#:

```csharp
public void Test([MarshalAs((short)70)] int test) { }
```

```il
// IL from Ildasm.exe output
.method public hidebysig instance void Test(int32  marshal({ 46 }) test) cil managed
```

Počínaje rozhraním .NET Framework 4.5 zobrazí *program Ildasm.exe* atributy, které jsou použity pro implementace rozhraní, jak je znázorněno v následujícím výňatku z výstupu *ildasm.exe:*

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

Následující příkaz způsobí, že metadata a rozložený `MyHello.exe` kód souboru PE se zobrazí ve výchozím grafickém uživatelském rozhraní *Ildasm.exe.*

```console
ildasm myHello.exe
```

Následující příkaz rozebere soubor `MyFile.exe` a uloží výsledný text IL Assembler do souboru *MyFile.il*.

```console
ildasm MyFile.exe /output:MyFile.il
```

Následující příkaz rozebere soubor `MyFile.exe` a zobrazí výsledný text IL Assembler do okna konzoly.

```console
ildasm MyFile.exe /text
```

Pokud soubor `MyApp.exe` obsahuje vložené spravované a nespravované prostředky, vytvoří následující příkaz čtyři soubory: *MyApp.il*, *MyApp.res*, *Icons.resources*a *Message.resources*:

```console
ildasm MyApp.exe /output:MyApp.il
```

Následující příkaz rozebírá `MyMethod` metodu `MyClass` v `MyFile.exe` rámci třídy a zobrazuje výstup do okna konzoly.

```console
ildasm /item:MyClass::MyMethod MyFile.exe /text
```

V předchozím příkladu může být `MyMethod` několik metod pojmenovaných s různými podpisy. Následující `MyMethod` příkaz rozebírá metodu instance s návratovým typem **void** a typy parametrů **int32** a **string**.

```console
ildasm /item:"MyClass::MyMethod(instance void(int32,string)" MyFile.exe /text
```

> [!NOTE]
> V rozhraní .NET Framework verze 1.0 a 1.1 musí být levá závorka, která následuje za `MyMethod(instance void(int32))`názvem metody, vyvážena pravou závorkou za podpisem: . Počínaje rozhraním .NET Framework 2.0 musí být vynechaná uzavírací závorka vynechána: `MyMethod(instance void(int32)`.

Chcete-li `static` načíst metodu (metodu`Shared` v `instance`jazyce Visual Basic), vynechte klíčové slovo . Typy tříd, které nejsou `int32` `string` primitivní typy jako a musí obsahovat `class`obor názvů a musí předcházet klíčové slovo . Před externími typy musí být uveden název knihovny v hranatých závorkách. Následující příkaz demontuje statickou `MyMethod` metodu s názvem, která má jeden parametr typu <xref:System.AppDomain> a má návratový <xref:System.AppDomain>typ .

```console
ildasm /item:"MyClass::MyMethod(class [mscorlib]System.AppDomain(class [mscorlib]System.AppDomain)" MyFile.exe /text
```

Před vnořeným typem musí být uvedena třída, která jej obsahuje, oddělená lomítkem. Pokud například `MyNamespace.MyClass` třída obsahuje vnořenou třídu s názvem `NestedClass`, `class MyNamespace.MyClass/NestedClass`je vnořená třída identifikována takto: .

## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [Ilasm.exe (IL Assembler)](ilasm-exe-il-assembler.md)
- [Proces spravovaného spouštění](../../standard/managed-execution-process.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)

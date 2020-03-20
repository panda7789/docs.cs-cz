---
title: Ilasm.exe (IL Assembler)
ms.date: 03/30/2017
helpviewer_keywords:
- MSIL generators
- metadata, MSIL Assembler
- MSIL Assembler
- portable executable files, MSIL Assembler
- PE files, MSIL Assembler
- MSIL
- Ilasm.exe
- verifying MSIL performance
ms.assetid: 4ca3a4f0-4400-47ce-8936-8e219961c76f
ms.openlocfilehash: cb995e78e534048043886070536ef0dd0a45c057
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73105093"
---
# <a name="ilasmexe-il-assembler"></a>Ilasm.exe (IL Assembler)

Nástroj IL Assembler generuje přenositelný spustitelný (PE) soubor z převodního jazyka (IL; Intermediate Language). (Další informace o IL, naleznete [v tématu proces ustálené spuštění](../../standard/managed-execution-process.md).) Můžete spustit výsledný spustitelný soubor, který obsahuje IL a požadovaná metadata, chcete-li zjistit, zda IL provádí podle očekávání.

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li nástroj spustit, použijte příkazový řádek pro vývojáře pro sadu Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace naleznete v [příkazových koncích](developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a>Parametry

| Argument | Popis |
| -------- | ----------- |
|`filename`|Název zdrojového souboru .il. Soubor sestává z deklaračních direktiv metadat a symbolických instrukcí IL. K vytvoření jednoho souboru PE pomocí souboru *Ilasm.exe*lze zadat více argumentů zdrojového souboru. **Poznámka:** Ujistěte se, že poslední řádek kódu ve zdrojovém souboru .il má koncové prázdné znaky nebo znak konce řádku.|

| Možnost | Popis |
| ------ | ----------- |
|**/32bitpreferred /32bitpreferred /32bitpreferred /3**|Vytvoří bitovou kopii s upřednostněním 32bitového kódu (PE32).|
|**/zarovnání:**`integer`|Nastaví zarovnání souborů `integer` na hodnotu určenou v volitelné hlavičce NT. Je-li v souboru zadána direktiva IL .alignment, tato možnost ji přepisuje.|
|**/kontejner aplikace**|Vytvoří soubor *DLL* nebo *EXE,* který běží v kontejneru aplikací pro Windows jako výstup.|
|**/rameno**|Určí jako cílový procesor architekturu Advanced RISC Machine (ARM).<br /><br /> Pokud není zadána žádná bitová vztažnost obrazu, je výchozí hodnota **/32bitpreferred**.|
|**/základna:**`integer`|Nastaví imagebase na `integer` hodnotu určenou v volitelné masce NT. Je-li v souboru zadána direktiva IL .imagebase, tato možnost ji přepisuje.|
|**/hodiny**|Měří a oznamuje následující časy kompilace v milisekundách pro zadaný zdrojový soubor .il:<br /><br /> **Celkový běh**: Celkový čas strávený prováděním všech konkrétních operací, které následují.<br /><br /> **Spuštění**: Načítání a otevírání souboru.<br /><br /> **Emitting MD**: Emitující metadata.<br /><br /> **Ref to Def Rozlišení**: Řešení odkazů na definice v souboru.<br /><br /> **Generování souborů ve výjaku**: Generování obrazu souboru v paměti.<br /><br /> **Psaní souboru PE**: Zápis obrazu do souboru PE.|
|**/ladění**[:**IMPL**&#124;**OPT**]|Zahrnuje informace o ladění (názvy místních proměnných a argumentů a čísla řádků). Vytvoří soubor PDB.<br /><br /> **/debug** bez další hodnoty zakáže optimalizaci JIT a použije sekvenční body ze souboru PDB.<br /><br /> **IMPL** zakáže optimalizaci JIT a používá implicitní sekvenční body.<br /><br /> **OPT** umožňuje optimalizaci JIT a používá implicitní sekvenční body.|
|**/dll**|Vytvoří soubor *DLL* jako výstup.|
|**/enc:**`file`|Vytvoří ze zadaného zdrojového souboru rozdíly pro funkci Upravit a pokračovat.<br /><br /> Tento argument slouží pouze k akademickému použití a při komerčním použití není podporován.|
|**/exe**|Vytvoří jako výstup spustitelný soubor. Toto nastavení je výchozí.|
|**/příznaky:**`integer`|Nastaví ImageFlags na `integer` hodnotu určenou v záhlaví běžného jazyka runtime. Je-li v souboru zadána direktiva IL .corflags, tato možnost ji přepisuje. Seznam platných hodnot pro celé číslo naleznete *v*COMIMAGE_FLAGS corhdr.h.|
|**/přeložení**|Sloučí identická těla metod do jednoho.|
|/**highentropieva**|Vytvoří výstupní spustitelný soubor podporující funkci ASLR s vysokou entropií. (Výchozí pro **/appcontainer**.)|
|**/zahrnout:**`includePath`|Nastaví cestu k hledání `#include`souborů, které jsou součástí aplikace .|
|**/itanium**|Určí jako cílový procesor Intel Itanium.<br /><br /> Pokud není zadána žádná bitová vzbitost obrazu, je výchozí **hodnota /pe64**.|
|**/klíč:**`keyFile`|Zkompiluje `filename` se silným podpisem `keyFile`pomocí soukromého klíče obsaženého v .|
|**/klíč:** @`keySource`|Zkompiluje `filename` se silným podpisem `keySource`pomocí soukromého klíče vytvořeného na adrese .|
|**/výpis**|Vytvoří na standardním výstupu soubor výpisu. Vynecháte-li tuto možnost, není vytvořen žádný soubor výpisu.<br /><br /> Tento parametr není podporován v rozhraní .NET Framework 2.0 a vyšším.|
|**/mdv:**`versionString`|Nastaví řetězec verze metadat.|
|**/msv:** `major`.`minor`|Nastaví verzi datového `major` proudu `minor` metadat, kde a jsou celá čísla.|
|**/noautoinherit**|Zakáže výchozí <xref:System.Object> dědičnost z doby, kdy není zadána žádná základní třída.|
|**/nocorstub**|Potlačí generování zástupné procedury CORExeMain.|
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|
|**/výstup:**`file.ext`|Určuje název výstupního souboru a příponu. Ve výchozím nastavení je název výstupního souboru shodný s názvem prvního zdrojového souboru. Výchozí rozšíření je *.exe*. Pokud zadáte možnost **/dll,** bude výchozí rozšíření *.dll*. **Poznámka:** Zadání **/output**:myfile.dll nenastaví **/dll** možnost. Pokud nezadáte **/dll**, výsledkem bude spustitelný soubor s názvem *myfile.dll*.|
|**/optimalizovat**|Optimalizuje dlouhé instrukce na krátké. Například `br` do `br.s`.|
|**/pe64**|Vytvoří 64bitovou kopii (PE32+).<br /><br /> Pokud není zadán žádný cílový `/itanium`procesor, výchozí hodnota je .|
|**/pdb**|Vytvoří soubor PDB bez povolení sledování informací o ladění.|
|**/tichý**|Určuje tichý režim, který neoznamuje průběh sestavení.|
|**/zdroj:**`file.res`|Zadaný soubor prostředků \*ve formátu RES zahrne do výsledného souboru *EXE* nebo *DLL.* Pomocí možnosti **/resource** lze zadat pouze jeden soubor RES.|
|**/ssver:** `int`.`int`|Nastaví číslo verze podsystému ve volitelné hlavičce NT. Pro **/appcontainer** a **/arm** je minimální číslo verze 6.02.|
|**/zásobník:**`stackSize`|Nastaví hodnotu SizeOfStackReserve v `stackSize`volitelné hlavičce NT na hodnotu .|
|**/stripreloc**|Určuje, že není zapotřebí žádné přemisťování základu.|
|**/subsystém:**`integer`|Nastaví podsystém na `integer` hodnotu určenou v volitelné hlavičce NT. Je-li v souboru zadána direktiva IL .subsystem, tento příkaz ji přepíše. Seznam platných hodnot pro soubor naleznete v `integer`souboru winnt.h IMAGE_SUBSYSTEM.|
|**/x64**|Určí jako cílový procesor 64bitový procesor společnosti AMD.<br /><br /> Pokud není zadána žádná bitová vzbitost obrazu, je výchozí **hodnota /pe64**.|
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|

> [!NOTE]
> Všechny možnosti pro *ilasm.exe* jsou malá a velká písmena a rozpoznána prvními třemi písmeny. Například **/lis** je ekvivalentní **/listing** a **/res**:myresfile.res je ekvivalentní **/resource**:myresfile.res. Možnosti, které určují argumenty, přijímají dvojtečku (:) nebo rovnítko (=) jako oddělovač mezi volbou a argumentem. Například **/output**:*file.ext* je ekvivalentní **/output**=*file.ext*.

## <a name="remarks"></a>Poznámky

Nástroj IL Assembler pomáhá dodavatelům nástrojů navrhovat a implementovat generátory IL. Pomocí *nástroje Ilasm.exe*se vývojáři nástrojů a kompilátorů mohou soustředit na generování IL a metadat, aniž by se zabývali vyzařováním IL ve formátu SOUBORU PE.

Podobně jako u jiných kompilátorů, které cílí na runtime, například C# a Visual Basic, *ilasm.exe* nevytváří zprostředkující objekt soubory a nevyžaduje propojení fázi tvořit soubor PE.

Nástroj IL Assembler dokáže vyjádřit všechna existující metadata a funkce IL programovacích jazyků zaměřených na modul runtime. To umožňuje, aby byl spravovaný kód napsaný v některém z těchto programovacích jazyků adekvátně vyjádřen v IL Assembleru a kompilován pomocí *ilasm.exe*.

> [!NOTE]
> Kompilace může skončit neúspěchem, neobsahuje-li poslední řádek kódu ve zdrojovém souboru .il prázdný znak nebo znak ukončení řádku.

Nástroj *Ilasm.exe* můžete použít ve spojení s doprovodným nástrojem [*Ildasm.exe*](ildasm-exe-il-disassembler.md). *Ildasm.exe* přebírá soubor PE, který obsahuje IL kód a vytvoří textový soubor vhodný jako vstup pro *ilasm.exe*. Toho lze využít například při kompilování kódu v programovacím jazyce, který nepodporuje všechny atributy modulu runtime. Po kompilaci kódu a spuštění výstupu prostřednictvím *ildasm.exe*, výsledný il textový soubor lze ručně upravit přidat chybějící atributy. Tento textový soubor pak můžete spustit prostřednictvím souboru *Ilasm.exe* a vytvořit tak konečný spustitelný soubor.

Tuto techniku lze také použít pro sloučení několika souborů PE původně vygenerovaných různými kompilátory do jediného souboru PE.

> [!NOTE]
> Momentálně nelze tuto techniku použít se soubory PE obsahujícími vložený nativní kód (například PE soubory vytvořené jazykem Visual C++).

Aby toto kombinované použití *Ildasm.exe* a *Ilasm.exe* co nejpřesnější, ve výchozím nastavení assembler nenahrazuje krátké kódování pro dlouhé ty, které jste napsali ve zdrojích IL (nebo které mohou být emitovány jiným kompilátorem). Použijte **možnost /optimize** k nahrazení krátkých kódování, kdykoli je to možné.

> [!NOTE]
> *Ildasm.exe* pracuje pouze se soubory na disku. Nepracuje se soubory nainstalovanými do globální mezipaměti sestavení.

Další informace o gramatické ml naleznete v souboru asmparse.grammar v sadě Windows SDK.

## <a name="version-information"></a>Informace o verzi

Počínaje rozhraním .NET Framework 4.5 můžete k implementaci rozhraní připojit vlastní atribut pomocí kódu podobného následujícímu:

```il
.class interface public abstract auto ansi IMyInterface
{
  .method public hidebysig newslot abstract virtual
    instance int32 method1() cil managed
  {
  } // end of method IMyInterface::method1
} // end of class IMyInterface
.class public auto ansi beforefieldinit MyClass
  extends [mscorlib]System.Object
  implements IMyInterface
  {
    .interfaceimpl type IMyInterface
    .custom instance void
      [mscorlib]System.Diagnostics.DebuggerNonUserCodeAttribute::.ctor() = ( 01 00 00 00 )
      …
```

Počínaje rozhraním .NET Framework 4.5 můžete určit libovolný objekt BLOB zařazování (binární velký objekt) pomocí jeho nezpracované binární reprezentace, jak je znázorněno v následujícím kódu:

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

Další informace o gramatické ml naleznete v souboru asmparse.grammar v sadě Windows SDK.

## <a name="examples"></a>Příklady

Následující příkaz sestavuje *soubor* IL myTestFile.il a vytvoří spustitelný *soubor myTestFile.exe*.

```console
ilasm myTestFile
```

Následující příkaz sestavuje *soubor* IL myTestFile.il a vytvoří soubor *DLL* *myTestFile.dll*.

```console
ilasm myTestFile /dll
```

Následující příkaz sestavuje *soubor* IL myTestFile.il a vytvoří soubor *DLL* *myNewTestFile.dll*.

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

Následující příklad kódu ukazuje velmi jednoduchou aplikaci, která zobrazuje "Hello World!" „Hello, World!“. Tento kód můžete zkompilovat a potom pomocí nástroje [*Ildasm.exe*](ildasm-exe-il-disassembler.md) vygenerovat soubor IL.

```csharp
using System;

public class Hello
{
    public static void Main(String[] args)
    {
        Console.WriteLine("Hello World!");
    }
}
```

Následující příklad kódu IL odpovídá předchozí ukázce kódu C#. Tento kód můžete zkompilovat do sestavení pomocí nástroje IL Assembler. Příklady kódu IL i C# zobrazují "Hello World!" „Hello, World!“.

```il
// Metadata version: v2.0.50215
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 2:0:0:0
}
.assembly sample
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module sample.exe
// MVID: {A224F460-A049-4A03-9E71-80A36DBBBCD3}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x02F20000

// =============== CLASS MEMBERS DECLARATION ===================

.class public auto ansi beforefieldinit Hello
       extends [mscorlib]System.Object
{
  .method public hidebysig static void  Main(string[] args) cil managed
  {
    .entrypoint
    // Code size       13 (0xd)
    .maxstack  8
    IL_0000:  nop
    IL_0001:  ldstr      "Hello World!"
    IL_0006:  call       void [mscorlib]System.Console::WriteLine(string)
    IL_000b:  nop
    IL_000c:  ret
  } // end of method Hello::Main

  .method public hidebysig specialname rtspecialname
          instance void  .ctor() cil managed
  {
    // Code size       7 (0x7)
    .maxstack  8
    IL_0000:  ldarg.0
    IL_0001:  call       instance void [mscorlib]System.Object::.ctor()
    IL_0006:  ret
  } // end of method Hello::.ctor

} // end of class Hello
```

## <a name="see-also"></a>Viz také

- [Nástroje](index.md)
- [*Ildasm.exe* (IL Disassembler)](ildasm-exe-il-disassembler.md)
- [Proces spravovaného spouštění](../../standard/managed-execution-process.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)

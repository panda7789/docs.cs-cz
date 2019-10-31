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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73105093"
---
# <a name="ilasmexe-il-assembler"></a>Ilasm.exe (IL Assembler)

Nástroj IL Assembler generuje přenositelný spustitelný (PE) soubor z převodního jazyka (IL; Intermediate Language). (Další informace o IL najdete v tématu [spravovaný proces spuštění](../../standard/managed-execution-process.md).) Můžete spustit výsledný spustitelný soubor, který obsahuje IL a požadovaná metadata, abyste zjistili, jestli IL funguje podle očekávání.

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit nástroj, použijte Developer Command Prompt pro Visual Studio (nebo příkazový řádek sady Visual Studio v systému Windows 7). Další informace najdete v tématu [výzvy k zadání příkazu](developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```console
ilasm [options] filename [[options]filename...]
```

## <a name="parameters"></a>Parametry

| Argument | Popis |
| -------- | ----------- |
|`filename`|Název zdrojového souboru .il. Soubor sestává z deklaračních direktiv metadat a symbolických instrukcí IL. K vytvoření jednoho souboru PE pomocí *Ilasm. exe*lze zadat více argumentů zdrojového souboru. **Poznámka:** Ujistěte se, že poslední řádek kódu ve zdrojovém souboru. Il má buď koncovou mezeru, nebo znak konce řádku.|

| Možnost | Popis |
| ------ | ----------- |
|**/32bitpreferred**|Vytvoří bitovou kopii s upřednostněním 32bitového kódu (PE32).|
|**/alignment:** `integer`|Nastaví zarovnání souborů na hodnotu určenou `integer` v volitelné hlavičce NT. Je-li v souboru zadána direktiva IL .alignment, tato možnost ji přepisuje.|
|**/AppContainer**|Vytvoří soubor *. dll* nebo *. exe* , který je spuštěn v kontejneru aplikace systému Windows, jako výstup.|
|**/arm**|Určí jako cílový procesor architekturu Advanced RISC Machine (ARM).<br /><br /> Pokud není zadán žádný obrázek bitová verze, výchozí hodnota je **/32bitpreferred**.|
|**/Base:** `integer`|Nastaví ImageBase na hodnotu zadanou parametrem `integer` v volitelné hlavičce NT. Je-li v souboru zadána direktiva IL .imagebase, tato možnost ji přepisuje.|
|**/clock**|Měří a oznamuje následující časy kompilace v milisekundách pro zadaný zdrojový soubor .il:<br /><br /> **Celková doba spuštění**: celkový čas strávený prováděním všech konkrétních operací, které následují.<br /><br /> **Po spuštění**: načítání a otevírání souboru.<br /><br /> **Generování MD**: generování metadat<br /><br /> **Odkaz na def rozlišení**: řešení odkazů na definice v souboru.<br /><br /> **CEE generace souborů**: generování image souboru v paměti.<br /><br /> **Zápis do souboru PE**: zápis image do souboru PE.|
|**/Debug**[:**impl**&#124;**opt**]|Zahrnuje informace o ladění (názvy místních proměnných a argumentů a čísla řádků). Vytvoří soubor PDB.<br /><br /> **/Debug** bez další hodnoty ZAKÁŽE optimalizaci JIT a použije body sekvence ze souboru PDB.<br /><br /> **Impl** ZAKÁŽE optimalizaci JIT a použije implicitní body sekvence.<br /><br /> Možnost **opt** POVOLÍ optimalizaci JIT a použije implicitní body sekvence.|
|**/DLL**|Vytvoří jako výstup soubor *. dll* .|
|**/ENC:** `file`|Vytvoří ze zadaného zdrojového souboru rozdíly pro funkci Upravit a pokračovat.<br /><br /> Tento argument slouží pouze k akademickému použití a při komerčním použití není podporován.|
|**/exe**|Vytvoří jako výstup spustitelný soubor. Toto nastavení je výchozí.|
|**/Flags:** `integer`|Nastaví ImageFlags na hodnotu zadanou parametrem `integer` v hlavičce společného jazykového modulu runtime. Je-li v souboru zadána direktiva IL .corflags, tato možnost ji přepisuje. Seznam platných hodnot pro *celé číslo*získáte v tématu corhdr. h, COMIMAGE_FLAGS.|
|**/fold**|Sloučí identická těla metod do jednoho.|
|/**HIGHENTROPYVA**|Vytvoří výstupní spustitelný soubor podporující funkci ASLR s vysokou entropií. (Výchozí pro **/AppContainer**.)|
|**/include:** `includePath`|Nastaví cestu pro vyhledávání souborů, které jsou součástí `#include`.|
|**/itanium**|Určí jako cílový procesor Intel Itanium.<br /><br /> Pokud není zadán žádný obrázek bitová verze, výchozí hodnota je **/pe64**.|
|**/Key:** `keyFile`|Zkompiluje `filename` se silným podpisem pomocí privátního klíče obsaženého v `keyFile`.|
|**/Key:**  @`keySource`|Zkompiluje `filename` se silným podpisem pomocí privátního klíče vytvořeného při `keySource`.|
|**/listing**|Vytvoří na standardním výstupu soubor výpisu. Vynecháte-li tuto možnost, není vytvořen žádný soubor výpisu.<br /><br /> Tento parametr není podporován v rozhraní .NET Framework 2.0 a vyšším.|
|**/MDV:** `versionString`|Nastaví řetězec verze metadat.|
|**/MSV:** `major`.`minor`|Nastaví verzi streamu metadat, kde `major` a `minor` jsou celá čísla.|
|**/noautoinherit**|Zakáže výchozí dědění z <xref:System.Object>, pokud není zadána žádná základní třída.|
|**/nocorstub**|Potlačí generování zástupné procedury CORExeMain.|
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|
|**/output:** `file.ext`|Určuje název výstupního souboru a příponu. Ve výchozím nastavení je název výstupního souboru shodný s názvem prvního zdrojového souboru. Výchozí přípona je *. exe*. Pokud zadáte možnost **/DLL** , je výchozí příponou *. dll*. **Poznámka:** Zadání **/Output**: MyFile. dll nenastavuje možnost **/DLL** . Pokud nezadáte **/DLL**, bude výsledkem spustitelný soubor s názvem *MyFile. dll*.|
|**/optimize**|Optimalizuje dlouhé instrukce na krátké. Například `br` `br.s`.|
|**/pe64**|Vytvoří 64bitovou kopii (PE32+).<br /><br /> Pokud není zadaný žádný cílový procesor, výchozí hodnota je `/itanium`.|
|**/PDB**|Vytvoří soubor PDB bez povolení sledování informací o ladění.|
|**/quiet**|Určuje tichý režim, který neoznamuje průběh sestavení.|
|**/Resource:** `file.res`|Obsahuje zadaný soubor prostředků ve formátu \*. res ve výsledném souboru *. exe* nebo *. dll* . Pomocí možnosti **/Resource** lze zadat pouze jeden soubor. res.|
|**/ssver:** `int`.`int`|Nastaví číslo verze podsystému ve volitelné hlavičce NT. Pro **/AppContainer** a **/ARM** minimální číslo verze je 6,02.|
|**/stack:** `stackSize`|Nastaví hodnotu SizeOfStackReserve v volitelné hlavičce NT na `stackSize`.|
|**/stripreloc**|Určuje, že není zapotřebí žádné přemisťování základu.|
|**/SUBSYSTEM:** `integer`|Nastaví podsystém na hodnotu zadanou parametrem `integer` v volitelné hlavičce NT. Je-li v souboru zadána direktiva IL .subsystem, tento příkaz ji přepíše. Seznam platných hodnot pro `integer`najdete v souboru Winnt. h IMAGE_SUBSYSTEM.|
|**/x64**|Určí jako cílový procesor 64bitový procesor společnosti AMD.<br /><br /> Pokud není zadán žádný obrázek bitová verze, výchozí hodnota je **/pe64**.|
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|

> [!NOTE]
> Všechny možnosti pro *Ilasm. exe* rozlišují velká a malá písmena, která jsou rozpoznána prvními třemi písmeny. Například **/lis** je ekvivalentem **/listing** a **/res**: myresfile. res je ekvivalentem **/Resource**: myresfile. res. Možnosti, které určují argumenty, přijímají buď dvojtečku (:) nebo symbol rovná se (=) jako oddělovač mezi možností a argumentem. Například **/Output**:*File. ext* je ekvivalentem **/Output**=*souboru. ext*.

## <a name="remarks"></a>Poznámky

Nástroj IL Assembler pomáhá dodavatelům nástrojů navrhovat a implementovat generátory IL. Pomocí *Ilasm. exe*můžou vývojáři nástrojů a kompilátoru soustředit na generování Il a metadat, aniž by se museli zabývat tím, že vydávají Il ve formátu souboru PE.

Podobně jako jiné kompilátory, které cílí na modul runtime, C# například a Visual Basic, *Ilasm. exe* nevytváří zprostředkující soubory objektů a nevyžaduje fázi propojování pro vytvoření souboru PE.

Nástroj IL Assembler dokáže vyjádřit všechna existující metadata a funkce IL programovacích jazyků zaměřených na modul runtime. To umožňuje spravovanému kódu napsanému v některém z těchto programovacích jazyků odpovídajícím způsobem vyjádřit v IL Assembler a zkompilován pomocí *Ilasm. exe*.

> [!NOTE]
> Kompilace může skončit neúspěchem, neobsahuje-li poslední řádek kódu ve zdrojovém souboru .il prázdný znak nebo znak ukončení řádku.

*Ilasm. exe* lze použít ve spojení s jeho doprovodným nástrojem [*Ildasm. exe*](ildasm-exe-il-disassembler.md). *Ildasm. exe* používá soubor PE, který obsahuje kód Il a vytvoří textový soubor vhodný jako vstup do *Ilasm. exe*. Toho lze využít například při kompilování kódu v programovacím jazyce, který nepodporuje všechny atributy modulu runtime. Po zkompilování kódu a spuštění výstupu prostřednictvím programu *Ildasm. exe*lze výsledný textový soubor IL ručně upravit a přidat chybějící atributy. Pak můžete tento textový soubor spustit pomocí nástroje *Ilasm. exe* a vytvořit konečný spustitelný soubor.

Tuto techniku lze také použít pro sloučení několika souborů PE původně vygenerovaných různými kompilátory do jediného souboru PE.

> [!NOTE]
> Momentálně nelze tuto techniku použít se soubory PE obsahujícími vložený nativní kód (například PE soubory vytvořené jazykem Visual C++).

Aby bylo toto kombinované použití programů *Ildasm. exe* a *Ilasm. exe* co nejpřesnější, ve výchozím nastavení nástroj Assembler nenahradí krátká kódování pro dlouhé hodnoty, které jste nastavili ve vašich zdrojích Il (nebo které mohou být vygenerovány jiným kompilátorem). Pokud je to možné, použijte možnost **/optimize** k nahrazení krátkých kódování.

> [!NOTE]
> Nástroj *Ildasm. exe* pracuje pouze se soubory na disku. Nepracuje se soubory nainstalovanými do globální mezipaměti sestavení.

Další informace o gramatice IL najdete v souboru asmparse. gramatiky v Windows SDK.

## <a name="version-information"></a>Informace o verzi

Počínaje .NET Framework 4,5 můžete k implementaci rozhraní připojit vlastní atribut pomocí kódu podobného následujícímu:

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

Počínaje .NET Framework 4,5 můžete určit libovolný objekt BLOB pro zařazování (binární rozsáhlý objekt) pomocí jeho nezpracované binární reprezentace, jak je znázorněno v následujícím kódu:

```il
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

Další informace o gramatice IL najdete v souboru asmparse. gramatiky v Windows SDK.

## <a name="examples"></a>Příklady

Následující příkaz sestaví soubor IL *myTestFile.Il* a vytvoří spustitelný *myTestFile. exe*.

```console
ilasm myTestFile
```

Následující příkaz sestaví soubor IL *myTestFile.Il* a vytvoří soubor *DLL* *myTestFile. dll*.

```console
ilasm myTestFile /dll
```

Následující příkaz sestaví soubor IL *myTestFile.Il* a vytvoří soubor *DLL* *myNewTestFile. dll*.

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

Následující příklad kódu ukazuje extrémně jednoduchou aplikaci, která zobrazuje "Hello World!" do konzoly. Tento kód můžete zkompilovat a pak pomocí nástroje [*Ildasm. exe*](ildasm-exe-il-disassembler.md) vygenerovat soubor Il.

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

Následující příklad kódu IL odpovídá předchozí ukázce kódu C#. Tento kód můžete zkompilovat do sestavení pomocí nástroje IL Assembler. V obou příkladech IL i kód se C# zobrazuje "Hello World!" do konzoly.

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

## <a name="see-also"></a>Viz také:

- [Nástroje](index.md)
- [*Ildasm. exe* (IL Disassembler)](ildasm-exe-il-disassembler.md)
- [Proces spravovaného spuštění](../../standard/managed-execution-process.md)
- [Příkazové řádky](developer-command-prompt-for-vs.md)

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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0b149f21a2cb51740f0027f6b01984c628723939
ms.sourcegitcommit: a36cfc9dbbfc04bd88971f96e8a3f8e283c15d42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/11/2019
ms.locfileid: "54221753"
---
# <a name="ilasmexe-il-assembler"></a>Ilasm.exe (IL Assembler)

Nástroj IL Assembler generuje přenositelný spustitelný (PE) soubor z převodního jazyka (IL; Intermediate Language). (Další informace o jazyku IL naleznete v tématu [Managed Execution Process](../../../docs/standard/managed-execution-process.md).) Výsledný spustitelný soubor obsahující jazyk IL a potřebná metadata lze spustit, a určit tak, zda IL funguje dle očekávání.

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Ke spuštění nástroje, použijte příkazový řádek pro vývojáře pro Visual Studio (nebo příkazový řádek Visual Studio ve Windows 7). Další informace najdete v tématu [příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```console
ilasm [options] filename [[options]filename...]
```

#### <a name="parameters"></a>Parametry

| Argument | Popis |
| -------- | ----------- |
|`filename`|Název zdrojového souboru .il. Soubor sestává z deklaračních direktiv metadat a symbolických instrukcí IL. Lze je zadat několik argumentů zdrojového souboru, k vytvoření jediného souboru PE pomocí *Ilasm.exe*. **Poznámka:** Ujistěte se, že poslední řádek kódu ve zdrojovém souboru .il neobsahuje prázdný znak ani znak ukončení řádku.|

| Možnost | Popis |
| ------ | ----------- |
|**/32bitpreferred**|Vytvoří bitovou kopii s upřednostněním 32bitového kódu (PE32).|
|**/ Alignment:** `integer`|Nastaví hodnotu FileAlignment na hodnotu zadanou pomocí `integer` ve volitelné hlavičce NT. Je-li v souboru zadána direktiva IL .alignment, tato možnost ji přepisuje.|
|**/ appcontainer**|Vytvoří *.dll* nebo *.exe* soubor, který běží v kontejneru pro aplikace Windows, jako výstup.|
|**/arm**|Určí jako cílový procesor architekturu Advanced RISC Machine (ARM).<br /><br /> Pokud není zadán žádný počet bitů bitové kopie, výchozí hodnota je **/32bitpreferred**.|
|**propojovacího:** `integer`|Nastaví hodnotu ImageBase na hodnotu zadanou pomocí `integer` ve volitelné hlavičce NT. Je-li v souboru zadána direktiva IL .imagebase, tato možnost ji přepisuje.|
|**/Clock**|Měří a oznamuje následující časy kompilace v milisekundách pro zadaný zdrojový soubor .il:<br /><br /> **Total Run**: Celkový čas strávený provádění určitých operací, které následují.<br /><br /> **Po spuštění**: Načtení a otevírání souboru.<br /><br /> **Emitting MD**: Generování metadat.<br /><br /> **REF to Def Resolution**: Vyhodnocování odkazů na definice v souboru.<br /><br /> **CEE File Generation**: Generuje se bitová kopie souboru v paměti.<br /><br /> **PE File Writing**: Zápis bitové kopie do souboru PE.|
|**/ debug**[:**IMPL**&#124;**OPT**]|Zahrnuje informace o ladění (názvy místních proměnných a argumentů a čísla řádků). Vytvoří soubor PDB.<br /><br /> **/ debug** bez dalších hodnot zakáže optimalizaci JIT a použije body posloupnosti ze souboru PDB.<br /><br /> **IMPL** zakáže optimalizaci JIT a použije implicitní body posloupnosti.<br /><br /> **OPT** povolí optimalizaci JIT a použije implicitní body posloupnosti.|
|**/ DLL**|Vytvoří *.dll* soubor jako výstup.|
|**/ENC:** `file`|Vytvoří ze zadaného zdrojového souboru rozdíly pro funkci Upravit a pokračovat.<br /><br /> Tento argument slouží pouze k akademickému použití a při komerčním použití není podporován.|
|**/exe**|Vytvoří jako výstup spustitelný soubor. Toto nastavení je výchozí.|
|**Flags:** `integer`|Nastaví hodnotu ImageFlags na hodnotu zadanou pomocí `integer` v hlavičce modulu CLR. Je-li v souboru zadána direktiva IL .corflags, tato možnost ji přepisuje. Zobrazit Comimage_flags corhdr.h seznam platných hodnot pro *celé číslo*.|
|**/fold**|Sloučí identická těla metod do jednoho.|
|/**highentropyva**|Vytvoří výstupní spustitelný soubor podporující funkci ASLR s vysokou entropií. (Výchozí pro **/appcontainer**.)|
|**/ include:** `includePath`|Nastavuje cestu pro vyhledávání souborů zahrnutých v `#include`.|
|**/Itanium**|Určí jako cílový procesor Intel Itanium.<br /><br /> Pokud není zadán žádný počet bitů bitové kopie, výchozí hodnota je **/pe64**.|
|**uveden:** `keyFile`|Zkompiluje `filename` se silným podpisem za použití soukromého klíče obsaženého v `keyFile`.|
|**uveden:** @`keySource`|Zkompiluje `filename` se silným podpisem pomocí soukromého klíče vytvořeného ve `keySource`.|
|**/ výpis**|Vytvoří na standardním výstupu soubor výpisu. Vynecháte-li tuto možnost, není vytvořen žádný soubor výpisu.<br /><br /> Tento parametr není podporován v rozhraní .NET Framework 2.0 a vyšším.|
|**/MDV:** `versionString`|Nastaví řetězec verze metadat.|
|**/mSv:** `major`.`minor`|Nastaví verzi datového proudu metadat, kam `major` a `minor` jsou celá čísla.|
|**/noautoinherit**|Zakáže výchozí dědění ze <xref:System.Object> Pokud je zadaný žádnou základní třídu.|
|**/nocorstub**|Potlačí generování zástupné procedury CORExeMain.|
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|
|**/ output:** `file.ext`|Určuje název výstupního souboru a příponu. Ve výchozím nastavení je název výstupního souboru shodný s názvem prvního zdrojového souboru. Výchozí příponou je *.exe*. Pokud zadáte **/dll** možnost, je výchozí příponou *.dll*. **Poznámka:** Určení **/output**: myfile.dll není nastavený **/dll** možnost. Pokud nezadáte **/dll**, výsledkem bude spustitelný soubor s názvem *soubor.dll*.|
|**/optimize**|Optimalizuje dlouhé instrukce na krátké. Například `br` k `br.s`.|
|**/pe64**|Vytvoří 64bitovou kopii (PE32+).<br /><br /> Pokud není zadán žádný cílový procesor, výchozí hodnota je `/itanium`.|
|**/ pdb**|Vytvoří soubor PDB bez povolení sledování informací o ladění.|
|**/quiet**|Určuje tichý režim, který neoznamuje průběh sestavení.|
|**/ Resource:** `file.res`|Zahrnuje soubor zadaný prostředek v \*res formátu ve výsledné *.exe* nebo *.dll* souboru. Je možné zadat jenom jeden soubor. res při **/Resource** možnost.|
|**/ssver:** `int`.`int`|Nastaví číslo verze podsystému ve volitelné hlavičce NT. Pro **/appcontainer** a **/arm** je minimálním číslem verze 6.02.|
|**/ Stack:** `stackSize`|Nastaví hodnotu SizeOfStackReserve ve volitelné hlavičce NT na `stackSize`.|
|**/stripreloc**|Určuje, že není zapotřebí žádné přemisťování základu.|
|**/ Subsystem:** `integer`|Nastaví hodnotu subsystem na hodnotu zadanou pomocí `integer` ve volitelné hlavičce NT. Je-li v souboru zadána direktiva IL .subsystem, tento příkaz ji přepíše. Viz soubor winnt.h, IMAGE_SUBSYSTEM seznam platných hodnot pro `integer`.|
|**/x64**|Určí jako cílový procesor 64bitový procesor společnosti AMD.<br /><br /> Pokud není zadán žádný počet bitů bitové kopie, výchozí hodnota je **/pe64**.|
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|

> [!NOTE]
> Všechny možnosti pro *Ilasm.exe* jsou malá a velká písmena rozpoznávány dle prvních tří písmen. Například **/lis** je ekvivalentní **/listing** a **/res**: myresfile.res je ekvivalentní možnosti **/Resource**: myresfile.res. Možnosti s argumenty přijímají jako oddělovač mezi možností a argumentem dvojtečku (:) nebo symbol rovná se (=). Například **/output**:*file.ext* je ekvivalentní **/output**=*file.ext*.

## <a name="remarks"></a>Poznámky

Nástroj IL Assembler pomáhá dodavatelům nástrojů navrhovat a implementovat generátory IL. Pomocí *Ilasm.exe*, vývojáři nástrojů a kompilátorů umožňuje soustředit se na IL a generování metadat bez nutnosti zabývat se generováním kódu IL v souborovém formátu PE.

Podobně jako jiné kompilátory cílené na modul runtime, jako například C# a Visual Basic, *Ilasm.exe* nevytváří soubory objektů a nevyžaduje souboru PE propojovací fázi.

Nástroj IL Assembler dokáže vyjádřit všechna existující metadata a funkce IL programovacích jazyků zaměřených na modul runtime. To umožňuje spravovaného kódu napsaného v libovolném z těchto programovacích jazyků v nástroji IL Assembler adekvátní vyjádření a zkompilovaná *Ilasm.exe*.

> [!NOTE]
> Kompilace může skončit neúspěchem, neobsahuje-li poslední řádek kódu ve zdrojovém souboru .il prázdný znak nebo znak ukončení řádku.

Můžete použít *Ilasm.exe* ve spojení s jeho doprovodným nástrojem [ *Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md). *Ildasm.exe* přijímá soubory PE obsahující kód IL a vytváří textový soubor vhodný jako vstup do *Ilasm.exe*. Toho lze využít například při kompilování kódu v programovacím jazyce, který nepodporuje všechny atributy modulu runtime. Po zkompilování kódu a zpracování výstupu nástrojem *Ildasm.exe*, lze výsledný textový soubor IL ručně upravit a přidat chybějící atributy. Poté lze tento textový soubor *Ilasm.exe* a vytvořit konečný spustitelný soubor.

Tuto techniku lze také použít pro sloučení několika souborů PE původně vygenerovaných různými kompilátory do jediného souboru PE.

> [!NOTE]
> Momentálně nelze tuto techniku použít se soubory PE obsahujícími vložený nativní kód (například PE soubory vytvořené jazykem Visual C++).

Chcete-li toto kombinované použití *Ildasm.exe* a *Ilasm.exe* co nejpřesnější, ve výchozím nastavení assembler nenahrazuje krátká kódování pro dlouhé ty kódování napsaná ve zdrojích IL (nebo který může být vygenerována jiným kompilátorem). Použití **/ optimize** možnost nahradit krátká kódování, kdykoli je to možné.

> [!NOTE]
> *Ildasm.exe* pracuje pouze se soubory na disku. Nepracuje se soubory nainstalovanými do globální mezipaměti sestavení.

Další informace o gramatice jazyka IL, najdete v souboru asmparse.Grammar sady [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

## <a name="version-information"></a>Informace o verzi

Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], můžete přidat vlastní atribut na implementaci rozhraní pomocí kódu podobného následujícímu:

```
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

Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], můžete zadat libovolný zařazovací objekt BLOB (binární rozsáhlý objekt) s použitím jeho nezpracované binární reprezentace, jak je znázorněno v následujícím kódu:

```
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

Další informace o gramatice jazyka IL, najdete v souboru asmparse.Grammar sady [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

## <a name="examples"></a>Příklady

Následující příkaz sestaví soubor IL *myTestFile.il* a vytvoří spustitelný soubor *myTestFile.exe*.

```console
ilasm myTestFile
```

Následující příkaz sestaví soubor IL *myTestFile.il* a vytvoří *.dll* souboru *myTestFile.dll*.

```console
ilasm myTestFile /dll
```

Následující příkaz sestaví soubor IL *myTestFile.il* a vytvoří *.dll* souboru *myNewTestFile.dll*.

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

Následující příklad kódu ukazuje velice jednoduchou aplikaci, která se zobrazí "Hello World!" do konzoly. Můžete tento kód zkompilovat a pak použít [ *Ildasm.exe* ](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nástroj pro vygenerování souboru IL.

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

Následující příklad kódu IL odpovídá předchozí ukázce kódu C#. Tento kód lze zkompilovat do sestavení pomocí nástroje IL Assembler. Obě IL a C# příklady kódu zobrazí "Hello World!" do konzoly.

```
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

[Nástroje](../../../docs/framework/tools/index.md)  
[*Ildasm.exe* (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)  
[Proces spravovaného spuštění](../../../docs/standard/managed-execution-process.md)  
[Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

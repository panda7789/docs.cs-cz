---
title: Ilasm.exe (IL Assembler)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "41"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2507acc7ddf41d921af0b86622b1e85208191767
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ilasmexe-il-assembler"></a>Ilasm.exe (IL Assembler)

Nástroj IL Assembler generuje přenositelný spustitelný (PE) soubor z převodního jazyka (IL; Intermediate Language). (Další informace o IL najdete v tématu [spravovat proces spuštění](../../../docs/standard/managed-execution-process.md).) Výsledný spustitelný soubor obsahující jazyk IL a potřebná metadata lze spustit, a určit tak, zda IL funguje dle očekávání.

Tento nástroj je automaticky nainstalován se sadou Visual Studio. Chcete-li spustit tento nástroj, použijte příkazový řádek vývojáře (nebo příkazový řádek Visual Studio v systému Windows 7). Další informace najdete v tématu [příkazového řádku](../../../docs/framework/tools/developer-command-prompt-for-vs.md).

V příkazovém řádku zadejte následující:

## <a name="syntax"></a>Syntaxe

```console
ilasm [options] filename [[options]filename...]
```

#### <a name="parameters"></a>Parametry

| Argument | Popis |
| -------- | ----------- |
|`filename`|Název zdrojového souboru .il. Soubor sestává z deklaračních direktiv metadat a symbolických instrukcí IL. Můžete je nutné zadat několik argumentů zdrojového souboru k vytvoření jednoho souboru PE s *Ilasm.exe*. **Poznámka:** zajistěte, aby poslední řádek kódu ve zdrojovém souboru .il prázdné znaky nebo znakem konec řádku.|

| Možnost | Popis |
| ------ | ----------- |
|**/32bitpreferred**|Vytvoří bitovou kopii s upřednostněním 32bitového kódu (PE32).|
|**/ Alignment:**`integer`|Nastaví na hodnotu zadanou pomocí FileAlignment `integer` v hlavičce NT volitelné. Je-li v souboru zadána direktiva IL .alignment, tato možnost ji přepisuje.|
|**/appcontainer**|Vytváří *.dll* nebo *.exe* soubor, který běží v kontejneru aplikace systému Windows, jako výstup.|
|**/arm**|Určí jako cílový procesor architekturu Advanced RISC Machine (ARM).<br /><br /> Pokud není zadaný žádný obrázek počtu bitů, výchozí hodnota je **/32bitpreferred**.|
|**/ Základní:**`integer`|Nastaví na hodnotu zadanou pomocí ImageBase `integer` v hlavičce NT volitelné. Je-li v souboru zadána direktiva IL .imagebase, tato možnost ji přepisuje.|
|**/Clock**|Měří a oznamuje následující časy kompilace v milisekundách pro zadaný zdrojový soubor .il:<br /><br /> **Celkový počet spuštění**: celkový čas strávený, provádění určitých operací, které následují.<br /><br /> **Spuštění**: načítání a soubor otevřít.<br /><br /> **Emitování MD**: generování metadat.<br /><br /> **REF Def řešení**: řešení odkazy na definice v souboru.<br /><br /> **Generování souboru CEE**: generování souboru bitové kopie v paměti.<br /><br /> **Zápis souboru PE**: zápis do souboru PE bitovou kopii.|
|**/ debug**[:**IMPL**&#124; **OPT**]|Zahrnuje informace o ladění (názvy místních proměnných a argumentů a čísla řádků). Vytvoří soubor PDB.<br /><br /> **/ debug** bez další hodnoty zakáže optimalizace JIT a používá pořadí body ze souboru PDB.<br /><br /> **IMPL** zakáže optimalizace JIT a používá implicitní pořadí body.<br /><br /> **VÝSLOVNÝ** umožňuje optimalizaci JIT a používá implicitní pořadí body.|
|**/ DLL**|Vytváří *.dll* souboru jako výstup.|
|**/ENC:**`file`|Vytvoří ze zadaného zdrojového souboru rozdíly pro funkci Upravit a pokračovat.<br /><br /> Tento argument slouží pouze k akademickému použití a při komerčním použití není podporován.|
|**/exe**|Vytvoří jako výstup spustitelný soubor. Toto nastavení je výchozí.|
|**/ flags:**`integer`|Nastaví na hodnotu zadanou pomocí ImageFlags `integer` v hlavičce běžné runtime jazyka. Je-li v souboru zadána direktiva IL .corflags, tato možnost ji přepisuje. V tématu CorHdr.h COMIMAGE_FLAGS seznam platných hodnot pro *celé číslo*.|
|**/fold**|Sloučí identická těla metod do jednoho.|
|/**highentropyva**|Vytvoří výstupní spustitelný soubor podporující funkci ASLR s vysokou entropií. (Výchozí pro **/appcontainer**.)|
|**/ include:**`includePath`|Nastaví cestu k vyhledávání souborů, které jsou součástí `#include`.|
|**/Itanium**|Určí jako cílový procesor Intel Itanium.<br /><br /> Pokud není zadaný žádný obrázek počtu bitů, výchozí hodnota je **/pe64**.|
|**/ klíče:**`keyFile`|Zkompiluje `filename` silné podpisem pomocí privátní klíče součástí `keyFile`.|
|**/Key:** @`keySource`|Zkompiluje `filename` silné podpisem pomocí soukromého klíče vytvořeného v `keySource`.|
|**/ výpis**|Vytvoří na standardním výstupu soubor výpisu. Vynecháte-li tuto možnost, není vytvořen žádný soubor výpisu.<br /><br /> Tento parametr není podporován v rozhraní .NET Framework 2.0 a vyšším.|
|**/MDV:**`versionString`|Nastaví řetězec verze metadat.|
|**/mSv:** `major`.`minor`|Nastaví verze datového proudu metadata, kde `major` a `minor` jsou celá čísla.|
|**/noautoinherit**|Zakáže výchozí dědění ze <xref:System.Object> Pokud je zadán žádný základní třídy.|
|**/nocorstub**|Potlačí generování zástupné procedury CORExeMain.|
|**/nologo**|Potlačí zobrazení úvodního nápisu společnosti Microsoft.|
|**/ výstup:**`file.ext`|Určuje název výstupního souboru a příponu. Ve výchozím nastavení je název výstupního souboru shodný s názvem prvního zdrojového souboru. Výchozí přípona je *.exe*. Pokud zadáte **/dll** možnost, je výchozí rozšíření *.dll*. **Poznámka:** zadání **/výstup**: soubor.dll nenastaví **/dll** možnost. Pokud nezadáte **/dll**, výsledkem bude spustitelný soubor s názvem *soubor.dll*.|
|**/optimize**|Optimalizuje dlouhé instrukce na krátké. Například `br` k `br.s`.|
|**/pe64**|Vytvoří 64bitovou kopii (PE32+).<br /><br /> Pokud není zadaný žádný cílový procesor, výchozí hodnota je `/itanium`.|
|**/ pdb**|Vytvoří soubor PDB bez povolení sledování informací o ladění.|
|**/quiet**|Určuje tichý režim, který neoznamuje průběh sestavení.|
|**/ Resource:**`file.res`|Obsahuje soubor zadaný prostředek v \*.res formátu výsledná *.exe* nebo *.dll* souboru. S lze zadat pouze jeden soubor .res **/Resource** možnost.|
|**/ssver:** `int`.`int`|Nastaví číslo verze podsystému ve volitelné hlavičce NT. Pro **/appcontainer** a **/arm** číslo minimální verze je 6.02.|
|**/ stack:**`stackSize`|Nastaví hodnotu SizeOfStackReserve v hlavičce NT volitelné k `stackSize`.|
|**/stripreloc**|Určuje, že není zapotřebí žádné přemisťování základu.|
|**/Subsystem:**`integer`|Nastaví na hodnotu zadanou pomocí subsystému `integer` v hlavičce NT volitelné. Je-li v souboru zadána direktiva IL .subsystem, tento příkaz ji přepíše. Najdete v souboru winnt.h, IMAGE_SUBSYSTEM seznam platných hodnot pro `integer`.|
|**/x64**|Určí jako cílový procesor 64bitový procesor společnosti AMD.<br /><br /> Pokud není zadaný žádný obrázek počtu bitů, výchozí hodnota je **/pe64**.|
|**/?**|Zobrazí syntaxi příkazu a možnosti nástroje.|

> [!NOTE]
> Všechny možnosti pro *Ilasm.exe* jsou velká a malá písmena a rozpoznaný podle prvních tří písmen. Například **/lis** je ekvivalentní **/výpis** a **/res**: myresfile.res je ekvivalentní **/Resource**: myresfile.res. Možnosti s argumenty přijímají jako oddělovač mezi možností a argumentem dvojtečku (:) nebo symbol rovná se (=). Například **/výstup**:*file.ext* je ekvivalentní **/výstup**=*file.ext*.

## <a name="remarks"></a>Poznámky

Nástroj IL Assembler pomáhá dodavatelům nástrojů navrhovat a implementovat generátory IL. Pomocí *Ilasm.exe*, nástroje a kompilátoru vývojářům umožní soustředit se na IL a metadata generování bez se problémem generování IL ve formátu souboru PE.

Podobně jako ostatní kompilátory, které používají modul runtime, jako je například C# a Visual Basic, *Ilasm.exe* nevytváří soubory mezilehlých objektů a nevyžaduje serveru linking fáze k vytvoření souboru PE.

Nástroj IL Assembler dokáže vyjádřit všechna existující metadata a funkce IL programovacích jazyků zaměřených na modul runtime. To umožňuje spravovaný kód napsaný v některé z těchto programovacích jazyků adekvátní vyjádřeno v IL assembleru a kompilovat s *Ilasm.exe*.

> [!NOTE]
> Kompilace může skončit neúspěchem, neobsahuje-li poslední řádek kódu ve zdrojovém souboru .il prázdný znak nebo znak ukončení řádku.

Můžete použít *Ilasm.exe* ve spojení s nástrojem jeho doprovodné [ *Ildasm.exe*](../../../docs/framework/tools/ildasm-exe-il-disassembler.md). *Ildasm.exe* trvá PE souboru, který obsahuje kód IL a vytvoří textový soubor vhodný jako vstup pro *Ilasm.exe*. Toho lze využít například při kompilování kódu v programovacím jazyce, který nepodporuje všechny atributy modulu runtime. Po kompilaci kódu a spouštění výstup *Ildasm.exe*, bude výsledný soubor IL text může být ručně upravovat přidat chybějící atributy. Potom můžete spustit tohoto textového souboru *Ilasm.exe* k vytvoření konečné spustitelný soubor.

Tuto techniku lze také použít pro sloučení několika souborů PE původně vygenerovaných různými kompilátory do jediného souboru PE.

> [!NOTE]
> Momentálně nelze tuto techniku použít se soubory PE obsahujícími vložený nativní kód (například PE soubory vytvořené jazykem Visual C++).

To lze provést kombinaci použití *Ildasm.exe* a *Ilasm.exe* co nejpřesnější, ve výchozím nastavení assembleru není nahradit krátký kódování pro dlouho ty, které jsou možná jste napsali v vašich zdrojů IL (nebo který může být vygenerované pomocí jiného kompilátoru). Použití **/ optimize** možnost nahradit krátký kódování, pokud je to možné.

> [!NOTE]
> *Ildasm.exe* funguje pouze na soubory na disku. Nepracuje se soubory nainstalovanými do globální mezipaměti sestavení.

Další informace o gramatiky IL, naleznete v souboru asmparse.grammar v [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

## <a name="version-information"></a>Informace o verzi

Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], vlastní atribut k implementaci rozhraní můžete připojit pomocí kódu podobný následujícímu:

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

Od verze [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], můžete zadat libovolný zařazování BLOB (binární rozsáhlý objekt) pomocí jeho Nezpracovaná binární reprezentace, jak je znázorněno v následujícím kódu:

```
.method public hidebysig abstract virtual
        instance void
        marshal({ 38 01 02 FF })
        Test(object A_1) cil managed
```

Další informace o gramatiky IL, naleznete v souboru asmparse.grammar v [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)].

## <a name="examples"></a>Příklady

Následující příkaz sestaví soubor IL *myTestFile.il* a vytvoří spustitelný soubor *myTestFile.exe*.

```console
ilasm myTestFile
```

Následující příkaz sestaví soubor IL *myTestFile.il* a vytvoří *.dll* soubor *myTestFile.dll*.

```console
ilasm myTestFile /dll
```

Následující příkaz sestaví soubor IL *myTestFile.il* a vytvoří *.dll* soubor *myNewTestFile.dll*.

```console
ilasm myTestFile /dll /output:myNewTestFile.dll
```

Následující příklad kódu ukazuje velmi jednoduché aplikace, která zobrazuje "Hello, World!" ke konzole. Můžete zkompilovat tento kód a potom pomocí [ *Ildasm.exe* ](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) nástroj pro generování IL souboru.

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

Následující příklad kódu IL odpovídá předchozí ukázce kódu C#. Tento kód můžete zkompilovat do sestavení pomocí nástroje assembleru IL. Příklady kódu IL a C# zobrazit "Hello, World!" ke konzole.

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

## <a name="see-also"></a>Viz také

[Nástroje](../../../docs/framework/tools/index.md)  
[*Ildasm.exe* (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)  
[Proces spravovaného spuštění](../../../docs/standard/managed-execution-process.md)  
[Příkazové řádky](../../../docs/framework/tools/developer-command-prompt-for-vs.md)

---
title: 'Postup: Zobrazení obsahu sestavení'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, viewing information
- Ildasm.exe
- MSIL Disassembler
- assemblies [.NET Framework], viewing contents
- viewing assembly information
- MSIL
- viewing MSIL information
ms.assetid: fb7baaab-4c0d-47ad-8fd3-4591cf834709
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 179b240bb06a319ff71009e14323d5c8f2740e5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187391"
---
# <a name="how-to-view-assembly-contents"></a>Postup: Zobrazení obsahu sestavení

[Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) můžete použít k zobrazení informací o zprostředkujícím jazyce Microsoft (MSIL) v souboru. Pokud je zkoumaný soubor sestavením, mohou tyto informace obsahovat atributy sestavení a odkazy na jiné moduly a sestavení. Tyto informace mohou být užitečné při určování, zda je soubor sestavení nebo součástí sestavení a zda soubor obsahuje odkazy na jiné moduly nebo sestavení.

Chcete-li zobrazit obsah sestavy pomocí *aplikace Ildasm.exe*, zadejte **název sestavy ildasmu \<>** na příkazovém řádku. Například následující příkaz rozebírá sestavení *Hello.exe.*

```cmd
ildasm Hello.exe
```

Chcete-li zobrazit informace o manifestu sestavení, poklepejte na ikonu **Manifest** u okna Disassembler msil.

## <a name="example"></a>Příklad

Následující příklad začíná základním programem "Hello World". Po kompilaci programu použijte *ildasm.exe* k demontáži sestavení *Hello.exe* a zobrazení manifestu sestavení.

```cpp
using namespace System;

class MainApp
{
public:
    static void Main()
    {
        Console::WriteLine("Hello World using C++/CLI!");
    }
};

int main()
{
    MainApp::Main();
}
```

```csharp
using System;

class MainApp
{
    public static void Main()
    {
        Console.WriteLine("Hello World using C#!");
    }
}
```

```vb
Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

Spuštění příkazu *ildasm.exe* v sestavení *Hello.exe* a poklepáním na ikonu **Manifest** v okně MSIL Disassembler vytvoří následující výstup:

```output
// Metadata version: v4.0.30319
.assembly extern mscorlib
{
  .publickeytoken = (B7 7A 5C 56 19 34 E0 89 )                         // .z\V.4..
  .ver 4:0:0:0
}
.assembly Hello
{
  .custom instance void [mscorlib]System.Runtime.CompilerServices.CompilationRelaxationsAttribute::.ctor(int32) = ( 01 00 08 00 00 00 00 00 )
  .custom instance void [mscorlib]System.Runtime.CompilerServices.RuntimeCompatibilityAttribute::.ctor() = ( 01 00 01 00 54 02 16 57 72 61 70 4E 6F 6E 45 78   // ....T..WrapNonEx
                                                                                                             63 65 70 74 69 6F 6E 54 68 72 6F 77 73 01 )       // ceptionThrows.
  .hash algorithm 0x00008004
  .ver 0:0:0:0
}
.module Hello.exe
// MVID: {7C2770DB-1594-438D-BAE5-98764C39CCCA}
.imagebase 0x00400000
.file alignment 0x00000200
.stackreserve 0x00100000
.subsystem 0x0003       // WINDOWS_CUI
.corflags 0x00000001    //  ILONLY
// Image base: 0x00600000
```

Následující tabulka popisuje každou direktivu v manifestu sestavení sestavení *Hello.exe* použitého v příkladu:

|Směrnice|Popis|
|---------------|-----------------|
|**Název sestavení \<.assembly extern>**|Určuje jiné sestavení, které obsahuje položky odkazované aktuálním modulem (v tomto příkladu). `mscorlib`|
|**>tokenu \<tokenu .publickeytoken**|Určuje token skutečného klíče odkazovaného sestavení.|
|**Číslo \<verze .ver>**|Určuje číslo verze odkazovaného sestavení.|
|**>\<názvu sestavení sestavení .assembly**|Určuje název sestavení.|
|**hodnota algoritmu \<.hash int32>**|Určuje použitý algoritmus hash.|
|**Číslo \<verze .ver>**|Určuje číslo verze sestavení.|
|**>\<názvu souboru modulu**|Určuje název modulů, které tvoří sestavení. V tomto příkladu se sestavení skládá pouze z jednoho souboru.|
|**Hodnota .subsystému \<>**|Určuje prostředí aplikace požadované pro program. V tomto příkladu hodnota 3 označuje, že tento spustitelný soubor je spuštěn z konzoly.|
|**.corflags**|Aktuálně vyhrazené pole v metadatech.|

Manifest sestavení může obsahovat řadu různých směrnic v závislosti na obsahu sestavení. Rozsáhlý seznam směrnic v manifestu sestavení naleznete v dokumentaci Ecma, zejména "Oddíl II: Definice metadat a sémantika" a "Oddíl III: SADA instrukcí CIL":

- [Standardy ECMA C# a společné jazykové infrastruktury](../components.md#applicable-standards)
- [Standardní ECMA-335 – společná jazyková infrastruktura (CLI)](http://www.ecma-international.org/publications/standards/Ecma-335.htm)

## <a name="see-also"></a>Viz také

- [Aplikační domény a sestavení](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [Aplikační domény a sestavení s tématy s postupy](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md)

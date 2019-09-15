---
title: 'Postupy: Zobrazit obsah sestavení'
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
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 8f27afafde0b83dfe886d218f3148d8ff07b30cb
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973024"
---
# <a name="how-to-view-assembly-contents"></a>Postupy: Zobrazit obsah sestavení
K zobrazení informací o jazyce MSIL (Microsoft Intermediate Language) v souboru můžete použít nástroj [Ildasm. exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) . Pokud je testovaný soubor sestavení, mohou tyto informace obsahovat atributy sestavení a také odkazy na jiné moduly a sestavení. Tyto informace mohou být užitečné při určování, zda je soubor sestavením nebo součástí sestavení a zda má soubor odkazy na jiné moduly nebo sestavení.  
  
Chcete-li zobrazit **obsah sestavení pomocí** \<programu *Ildasm. exe*, zadejte text *název sestavení*> na příkazovém řádku. Například následující příkaz zpětně přeloží sestavení *Hello. exe* .  

```cmd
ildasm Hello.exe  
```  

Chcete-li zobrazit informace o manifestu sestavení, dvakrát klikněte na ikonu **manifestu** v okně MSIL Disassembler.  
  
## <a name="example"></a>Příklad  
Následující příklad začíná základním programem "Hello World". Po zkompilování programu použijte program *Ildasm. exe* pro zpětný překlad sestavení *Hello. exe* a zobrazení manifestu sestavení.  

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
Imports System

Class MainApp
    Public Shared Sub Main()
        Console.WriteLine("Hello World using Visual Basic!")
    End Sub
End Class
```

Spuštěním příkazu *Ildasm. exe* v sestavení *Hello. exe* a dvojím kliknutím na ikonu **manifestu** v okně MSIL Disassembler se vytvoří následující výstup:  

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
  
 Následující tabulka popisuje každou direktivu v manifestu sestavení sestavení *Hello. exe* používaného v příkladu.  
  
|– Direktiva|Popis|  
|---------------|-----------------|  
|*název*  **\< externího sestavení. Assembly** **>**|Určuje jiné sestavení, které obsahuje položky, na které se odkazuje aktuální modul (v `mscorlib`tomto příkladu).|  
|*token* **. \< PublicKeyToken** **>**|Určuje token skutečného klíče odkazovaného sestavení.|  
|*číslo verze* **. ver \<** **>**|Určuje číslo verze odkazovaného sestavení.|  
|*název sestavení* **. sestavení \<** **>**|Určuje název sestavení.|  
|*hodnota Int32*  **\< algoritmu hash** **>**|Určuje použitý algoritmus hash.|  
|*číslo verze* **. ver \<** **>**|Určuje číslo verze sestavení.|  
|*název souboru* **. Module \<** **>**|Určuje název modulů, které tvoří sestavení. V tomto příkladu se sestavení skládá pouze z jednoho souboru.|  
|**. hodnota \< subsystému** **>**|Určuje prostředí aplikace vyžadované pro program. V tomto příkladu hodnota 3 znamená, že se tento spustitelný soubor spustí z konzoly.|  
|**.corflags**|Aktuálně rezervované pole v metadatech.|  
  
 Manifest sestavení může obsahovat několik různých direktiv v závislosti na obsahu sestavení. Rozsáhlý seznam direktiv v manifestu sestavení naleznete v dokumentaci ECMA, obzvláště "partition II: Definice metadat a sémantika "a" partition III: Sada instrukcí CIL Dokumentace je k dispozici online. V [tématu C# ECMA and Common Language Infrastructure Standards](https://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a na [Standard ECMA-335-Common Language Infrastructure (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) na webu ECMA International.  
  
## <a name="see-also"></a>Viz také:

- [Aplikační domény a sestavení](../../framework/app-domains/application-domains.md#application-domains-and-assemblies)
- [Témata s návody k doménám a sestavením aplikací](../../framework/app-domains/application-domains-and-assemblies-how-to-topics.md)
- [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md)

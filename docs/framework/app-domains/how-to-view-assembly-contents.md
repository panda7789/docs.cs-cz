---
title: 'Postupy: Zobrazení obsahu sestavení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
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
ms.openlocfilehash: abe4c130fb5da49ed0f53c776e23dba8fb5b15f7
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44514170"
---
# <a name="how-to-view-assembly-contents"></a>Postupy: Zobrazení obsahu sestavení
Můžete použít [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) k zobrazení informací Microsoft intermediate language (MSIL) v souboru. Pokud je soubor zkoumají sestavení, můžete tyto informace zahrnout sestavení atributy, jakož i odkazy na jiných modulů a sestavení. Tyto informace mohou být užitečné při určování, zda je soubor sestavení nebo součástí sestavení, a zda soubor obsahuje odkazy na další moduly nebo sestavení.  
  
### <a name="to-display-the-contents-of-an-assembly-using-ildasmexe"></a>K zobrazení obsahu sestavení pomocí Ildasm.exe  
  
1.  Typ **ildasm** \< *název sestavení*> na příkazovém řádku. Například následující příkaz zpětně přeloží `Hello.exe` sestavení.  
  
    ```  
    ildasm Hello.exe  
    ```  
  
### <a name="to-view-assembly-manifest-information"></a>Chcete-li zobrazit informace o manifestu sestavení  
  
1.  Dvakrát klikněte na ikonu MANIFESTU v okně MSIL Disassembler.  
  
## <a name="example"></a>Příklad  
 Následující příklad začíná základní program "Hello, World". Po kompilaci programu, použijte Ildasm.exe pro převod ze strojového kódu Hello.exe sestavení a v manifestu sestavení.  
  
 [!code-cpp[Conceptual.Assembly.Contents#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.contents/cpp/source.cpp#1)]
 [!code-csharp[Conceptual.Assembly.Contents#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.contents/cs/source.cs#1)]
 [!code-vb[Conceptual.Assembly.Contents#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.contents/vb/source.vb#1)]  
  
 Spuštění příkazu ildasm.exe Hello.exe sestavení a dvojitým kliknutím na ikonu MANIFESTU v okně IL DASM vytvoří následující výstup:  
  
```  
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
  
 Následující tabulka popisuje jednotlivé direktivy v manifestu sestavení ze sestavení Hello.exe použitých v příkladu.  
  
|– Direktiva|Popis|  
|---------------|-----------------|  
|**.Assembly extern \<**  *název sestavení* **>**|Určuje další sestavení, který obsahuje položky, které odkazuje aktuální modul (v tomto příkladu `mscorlib`).|  
|**.PublicKeyToken \<**  *tokenu* **>**|Určuje token skutečného klíče odkazovaných sestavení.|  
|**ver \<**  *číslo verze* **>**|Určuje číslo verze odkazovaného sestavení.|  
|**.Assembly \<**  *název sestavení* **>**|Určuje název sestavení.|  
|**algoritmus .hash \<**  *hodnotu int32* **>**|Určuje použitý algoritmus hash.|  
|**ver \<**  *číslo verze* **>**|Určuje číslo verze sestavení.|  
|**.Module \<**  *název souboru* **>**|Určuje název moduly, které tvoří sestavení. V tomto příkladu se sestavení skládá pouze jeden soubor.|  
|**.Subsystem \<**  *hodnota* **>**|Určuje prostředí aplikace, které jsou potřebné pro program. V tomto příkladu hodnota 3 označuje, že je tento spustitelný soubor spustit z konzoly.|  
|**.corflags**|Aktuálně vyhrazené pole v metadatech.|  
  
 Manifest sestavení může obsahovat několik různých direktivy, v závislosti na obsah sestavení. Rozsáhlý seznam direktivy v manifestu sestavení naleznete v dokumentaci ECMA, zejména "Oddíl II: Metadata definice a sémantika" a "Oddílu III: soubor CIL se NAČTE sadu instrukcí". Dokumentace je k dispozici online; Zobrazit [ECMA C# a společné normy jazykové infrastruktury](https://go.microsoft.com/fwlink/?LinkID=99212) na webu MSDN a [Standard ECMA-335 – společné jazykové infrastruktury (CLI)](https://go.microsoft.com/fwlink/?LinkID=65552) na webu Ecma International.  
  
## <a name="see-also"></a>Viz také  
 [Domény a sestavení aplikací](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)  
 [Témata s návody k doménám a sestavením aplikací](../../../docs/framework/app-domains/application-domains-and-assemblies-how-to-topics.md)  
 [Ildasm.exe (IL Disassembler)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md)

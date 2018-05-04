---
title: 'Postupy: Vytváření vícesouborového sestavení'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- assemblies [.NET Framework], multifile
- entry point for assembly
- compiling assemblies
- Al.exe
- command-line compilers
- assembly manifest, multifile assemblies
- assemblies [.NET Framework], compiling
- Assembly Linker
- code modules
- multifile assemblies
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 916db7ec9bee0c85db1f2fcf4db7a9f8a61f9be3
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-build-a-multifile-assembly"></a>Postupy: Vytváření vícesouborového sestavení
Tento článek vysvětluje, jak vytvořit vícesouborového sestavení a poskytuje kód, který znázorňuje každý krok v postupu.  
  
> [!NOTE]
>  Visual Studio IDE pro C# a Visual Basic slouží pouze k vytvoření sestavení tvořená jedním souborem. Pokud chcete vytvořit vícesouborového sestavení, musíte použít kompilátory příkazového řádku nebo Visual Studio s Visual C++.  
  
### <a name="to-create-a-multifile-assembly"></a>Chcete-li vytvořit vícesouborového sestavení  
  
1.  Zkompilujte všechny soubory, které obsahují obory názvů odkazovat z ostatních modulů v sestavení do moduly kódu. Výchozí rozšíření pro moduly kódu je .netmodule.  
  
     Předpokládejme například, že `Stringer` soubor má obor názvů s názvem `myStringer`, což zahrnuje třídy s názvem `Stringer`. `Stringer` Třída obsahuje metodu s názvem `StringerMethod` jeden řádek, zapíše do konzoly.  
  
     [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
     [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
     [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]  
  
     Tento kód kompilace použijte následující příkaz:  
  
     [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
     [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
     [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]  
  
     Určení *modulu* parametr s **/t:** – možnost kompilátoru označuje, že soubor by měl být zkompilovány jako modul a nikoli jako sestavení. Kompilátor vytvoří modul s názvem `Stringer.netmodule`, které mohou být přidány do sestavení.  
  
2.  Zkompilujte všechny ostatní moduly pomocí nezbytných možností kompilátoru k označení modulů, které se odkazuje v kódu. Tento krok používá **/addmodule** – možnost kompilátoru.  
  
     V následujícím příkladu kódu modul byl volán `Client` má vstupní bod `Main` metoda, která odkazuje na metodu v `Stringer.dll` modulu vytvořili v kroku 1.  
  
     [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
     [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
     [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]  
  
     Tento kód kompilace použijte následující příkaz:  
  
     [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
     [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
     [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]  
  
     Zadejte **/t: Module** možnost, protože tento modul bude přidán k sestavení v příštím kroku. Zadejte **/addmodule** možnost protože kód v `Client` odkazuje na obor názvů vytvořený kód v `Stringer.netmodule`. Kompilátor vytvoří modul s názvem `Client.netmodule` obsahující odkaz na jiný modul, `Stringer.netmodule`.  
  
    > [!NOTE]
    >  C# a Visual Basic kompilátory podporují přímo vytváření vícesouborového sestavení s využitím následující dva různé syntaxe.  
    >   
    >  -   Dvě kompilace vytvořit dva souboru sestavení:  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
      [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
      [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]  
    > -   Jedna kompilace vytvoří dvě souboru sestavení:  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
      [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
      [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]  
  
3.  Použití [Linker sestavení (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) vytvoření výstupního souboru, který obsahuje manifest sestavení. Tento soubor obsahuje referenční informace pro všechny moduly nebo prostředky, které jsou součástí sestavení.  
  
     V příkazovém řádku zadejte následující příkaz:  
  
     **Al** \< *název modulu*> \<*název modulu*>... **/ main:**\<*název metody*> **/out:**\<*název souboru*>   **/target :**\<*typ souboru sestavení*>  
  
     V tomto příkazu *název modulu* argumenty zadejte název každého modulu, které chcete zahrnout do sestavení. **/Main:** možnost určuje název metody, která je sestavení vstupní bod. **/Out:** možnost určuje název souboru výstupního souboru, který bude obsahovat metadata sestavení. **/Target:** možnost určuje, že je sestavení spustitelný soubor (.exe) soubor aplikace konzoly, spustitelný soubor (.win) souboru systému Windows nebo soubor knihovny (LIB).  
  
     V následujícím příkladu vytvoří Al.exe sestavení, které je spustitelný soubor konzolové aplikace volá `myAssembly.exe`. Aplikace se skládá ze dvou modulů s názvem `Client.netmodule` a `Stringer.netmodule`, spustitelný soubor s názvem `myAssembly.exe,` obsahující jenom metadata sestavení. Vstupní bod sestavení je `Main` metodu v třídě `MainClientApp`, který se nachází v `Client.dll`.  
  
    ```  
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe   
    ```  
  
     Můžete použít [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) zkontrolujte obsah sestavení nebo určit, zda je soubor sestavení nebo modul.  
  
## <a name="see-also"></a>Viz také  
 [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)  
 [Postupy: Zobrazení obsahu sestavení](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)  
 [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)  
 [Vícesouborová sestavení](../../../docs/framework/app-domains/multifile-assemblies.md)

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
ms.openlocfilehash: 5f7bbbb2a0c0344d1da1e26d2eb35a65a56a80d5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54534433"
---
# <a name="how-to-build-a-multifile-assembly"></a>Postupy: Vytváření vícesouborového sestavení
Tento článek vysvětluje, jak vytvořit vícesouborové sestavení a obsahuje kód, který ukazuje každý krok v postupu.  
  
> [!NOTE]
>  Visual Studio IDE rozhraním C# a Visual Basic můžete použít jenom k vytvoření jednosouborového sestavení. Pokud chcete vytvořit vícesouborové sestavení, musíte použít kompilátory příkazového řádku nebo Visual Studio s Visual C++.  
  
### <a name="to-create-a-multifile-assembly"></a>K vytvoření vícesouborového sestavení  
  
1.  Zkompilujte všechny soubory, které obsahují obory názvů odkazované jinými moduly v sestavení, do modulů kódu. Výchozí přípona pro moduly kódu je .netmodule.  
  
     Předpokládejme například, že `Stringer` soubor má obor názvů s názvem `myStringer`, který obsahuje třídy nazvané `Stringer`. `Stringer` Třída obsahuje metodu nazvanou `StringerMethod` jeden řádek, který zapisuje do konzoly.  
  
     [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
     [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
     [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]  
  
     Chcete-li tento kód zkompilovat, použijte následující příkaz:  
  
     [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
     [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
     [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]  
  
     Zadání *modulu* parametr **t:** – možnost kompilátoru označuje, že soubor by měl být zkompilován jako modul, nikoli jako sestavení. Kompilátor vytvoří modul s názvem `Stringer.netmodule`, který lze přidat do sestavení.  
  
2.  Zkompilujte všechny ostatní moduly pomocí nezbytných možností kompilátoru k označení modulů, které jsou odkazovány v kódu. Tento krok používá **/addmodule** – možnost kompilátoru.  
  
     V následujícím příkladu se modul kódu s názvem `Client` má vstupní bod `Main` metodu, která odkazuje na metodu v `Stringer.dll` modulu vytvořili v kroku 1.  
  
     [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
     [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
     [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]  
  
     Chcete-li tento kód zkompilovat, použijte následující příkaz:  
  
     [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
     [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
     [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]  
  
     Zadejte **/t: Module** možnost, protože tento modul bude přidán do sestavení v příštím kroku. Zadejte **/addmodule** možnost, protože kód v `Client` odkazuje na obor názvů vytvořený kódem v `Stringer.netmodule`. Kompilátor vytvoří modul s názvem `Client.netmodule` , který obsahuje odkaz na jiný modul `Stringer.netmodule`.  
  
    > [!NOTE]
    >  C# a kompilátory jazyka Visual Basic podporují přímé vytváření vícesouborových sestavení pomocí dvou následujících různých syntaxí.  
    >   
    >  -   Dvě kompilace vytvoří dvousouborové sestavení:  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
      [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
      [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]  
    > -   Jedna kompilace vytvoří dvousouborové sestavení:  
    >   
    >      [!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
      [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
      [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]  
  
3.  Použití [Assembly Linker (Al.exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) se vytvořit výstupní soubor, který obsahuje manifest sestavení. Tento soubor obsahuje referenční informace pro všechny moduly nebo prostředky, které jsou součástí sestavení.  
  
     V příkazovém řádku zadejte následující příkaz:  
  
     **Al** \< *název modulu*> \<*název modulu*>... **/ main:**\<*název metody*> **/out:**\<*název_souboru*>   **/target :**\<*typ souboru sestavení*>  
  
     V tomto příkazu *název modulu* argumenty určují název každého modulu, který chcete zahrnout do sestavení. **/Main:** Určuje název metody, která je vstupním bodem sestavení. **/Out:** parametr určuje název výstupního souboru, který obsahuje metadata sestavení. **/Target:** možnost určuje, že je sestavení spustitelný soubor (.exe) soubor konzoly aplikace, soubor Windows (.win) spustitelný soubor nebo soubor knihovny (.lib).  
  
     V následujícím příkladu vytvoří Al.exe sestavení, které je spustitelným souborem konzolové aplikace volá `myAssembly.exe`. Aplikace se skládá ze dvou modulů s názvy `Client.netmodule` a `Stringer.netmodule`, spustitelný soubor s názvem `myAssembly.exe,` obsahující jenom metadata sestavení. Vstupní bod sestavení je `Main` metody ve třídě `MainClientApp`, který se nachází v `Client.dll`.  
  
    ```  
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe   
    ```  
  
     Můžete použít [MSIL Disassembler (Ildasm.exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) zkontrolovat obsah sestavení nebo zjistit, zda je soubor sestavení nebo modulu.  
  
## <a name="see-also"></a>Viz také:
- [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)
- [Postupy: Zobrazení obsahu sestavení](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)
- [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Vícesouborová sestavení](../../../docs/framework/app-domains/multifile-assemblies.md)

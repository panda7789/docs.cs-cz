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
ms.openlocfilehash: a964e73cc41cebad33a3edc34b89ef240fbc62c8
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70040859"
---
# <a name="how-to-build-a-multifile-assembly"></a>Postupy: Vytváření vícesouborového sestavení

Tento článek vysvětluje, jak vytvořit vícesouborové sestavení a poskytuje kód, který ukazuje každý krok v proceduře.

> [!NOTE]
> Integrované vývojové prostředí (IDE C# ) sady Visual Studio pro a Visual Basic lze použít pouze k vytváření sestavení s jedním souborem. Chcete-li vytvořit vícesouborové sestavení, je nutné použít kompilátory příkazového řádku nebo aplikaci Visual Studio se sadou Visual C++Studio.

### <a name="to-create-a-multifile-assembly"></a>Vytvoření vícesouborového sestavení

01. Zkompilujte všechny soubory, které obsahují obory názvů odkazované jinými moduly v sestavení, do modulů kódu. Výchozím rozšířením pro moduly kódu je. netmodule.

    Řekněme například, že `Stringer` soubor obsahuje obor názvů s názvem `myStringer`, který obsahuje třídu s názvem `Stringer`. Třída obsahuje metodu s názvem `StringerMethod` , která zapisuje jednu čáru do konzoly. `Stringer`

    [!code-cpp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#1)]
    [!code-csharp[Conceptual.Assembly.Multifile#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#1)]
    [!code-vb[Conceptual.Assembly.Multifile#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#1)]

    Pro zkompilování tohoto kódu použijte následující příkaz:

    [!code-cpp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/stringer.cpp#2)]
    [!code-csharp[Conceptual.Assembly.Multifile#2](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/stringer.cs#2)]
    [!code-vb[Conceptual.Assembly.Multifile#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/stringer.vb#2)]

    Zadání parametru *Module* s možností kompilátoru **/t:** označuje, že soubor by měl být zkompilován jako modul, nikoli jako sestavení. Kompilátor vytvoří modul s názvem `Stringer.netmodule`, který lze přidat do sestavení.

02. Zkompilujte všechny ostatní moduly pomocí nezbytných možností kompilátoru k označení dalších modulů, které jsou odkazovány v kódu. Tento krok používá možnost kompilátoru **/addmodule** .

    V následujícím příkladu má modul kódu s názvem `Client` metodu vstupního bodu `Main` , která `Stringer.dll` odkazuje na metodu v modulu vytvořenou v kroku 1.

    [!code-cpp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#3)]
    [!code-csharp[Conceptual.Assembly.Multifile#3](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#3)]
    [!code-vb[Conceptual.Assembly.Multifile#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#3)]

    Pro zkompilování tohoto kódu použijte následující příkaz:

    [!code-cpp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#4)]
    [!code-csharp[Conceptual.Assembly.Multifile#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#4)]
    [!code-vb[Conceptual.Assembly.Multifile#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#4)]

    Zadejte možnost **/t: Module** , protože tento modul se přidá do sestavení v budoucím kroku. Určete možnost **/addmodule** , protože kód v `Client` odkazuje na obor názvů vytvořený kódem v. `Stringer.netmodule` Kompilátor vytvoří modul s názvem `Client.netmodule` , který obsahuje odkaz na jiný modul,. `Stringer.netmodule`

    >[!NOTE]
    >Kompilátory C# a Visual Basic podporují přímé vytváření vícesouborového sestavení pomocí následujících dvou různých syntaxí.
    >
    >- Dvě kompilace vytvoří sestavení se dvěma soubory:[!code-cpp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#5)]
    >  [!code-csharp[Conceptual.Assembly.Multifile#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#5)]
    >  [!code-vb[Conceptual.Assembly.Multifile#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#5)]
    >
    >- Jedna kompilace vytvoří sestavení se dvěma soubory:[!code-cpp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.assembly.multifile/cpp/client.cpp#6)]
    >  [!code-csharp[Conceptual.Assembly.Multifile#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.assembly.multifile/cs/client.cs#6)]
    >  [!code-vb[Conceptual.Assembly.Multifile#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.assembly.multifile/vb/client.vb#6)]

03. Použijte [linker sestavení (Al. exe)](../../../docs/framework/tools/al-exe-assembly-linker.md) k vytvoření výstupního souboru, který obsahuje manifest sestavení. Tento soubor obsahuje referenční informace pro všechny moduly nebo prostředky, které jsou součástí sestavení.

    V příkazovém řádku zadejte následující příkaz:

    **Al** \<*název modulu*název modulu >...> \< **/Main:** \<*název***metody/out:** název souboru/target:\<*typ souboru* sestavení\<> > >

    V tomto příkazu argumenty *názvu modulu* určují název každého modulu, který chcete zahrnout do sestavení. Parametr **/Main:** Určuje název metody, která je vstupním bodem sestavení. Možnost **/out:** Určuje název výstupního souboru, který obsahuje metadata sestavení. Možnost **/target:** určuje, že sestavení je spustitelný soubor aplikace konzoly (. exe), spustitelný soubor systému Windows (. Win) nebo soubor knihovny (. lib).

    V následujícím příkladu Al. exe vytvoří sestavení, které je spustitelný soubor aplikace konzoly s názvem `myAssembly.exe`. Aplikace se skládá ze dvou modulů `Client.netmodule` nazvaných `Stringer.netmodule`a a spustitelného souboru s `myAssembly.exe,` názvem, který obsahuje pouze metadata sestavení. Vstupním bodem sestavení je `Main` metoda ve třídě `MainClientApp`, která je umístěna v `Client.dll`.

    ```
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    Můžete použít [jazyk MSIL Disassembler (Ildasm. exe)](../../../docs/framework/tools/ildasm-exe-il-disassembler.md) k prohlédnutí obsahu sestavení nebo určení, zda je soubor sestavením nebo modulem.

## <a name="see-also"></a>Viz také:

- [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)
- [Postupy: Zobrazit obsah sestavení](../../../docs/framework/app-domains/how-to-view-assembly-contents.md)
- [Jak běhové prostředí vyhledává sestavení](../../../docs/framework/deployment/how-the-runtime-locates-assemblies.md)
- [Vícesouborová sestavení](../../../docs/framework/app-domains/multifile-assemblies.md)

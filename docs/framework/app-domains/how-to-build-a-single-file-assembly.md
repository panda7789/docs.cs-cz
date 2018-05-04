---
title: 'Postupy: Vytváření sestavení s jediným souborem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6aa39671da519ebf54dad52638ab940897209517
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-build-a-single-file-assembly"></a>Postupy: Vytváření sestavení s jediným souborem
Jeden soubor sestavení, které je nejjednodušší typ sestavení, obsahuje informace o typu a implementace, a taky [manifest sestavení](../../../docs/framework/app-domains/assembly-manifest.md). Můžete použít kompilátory příkazového řádku nebo [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] vytvořit jeden soubor sestavení. Ve výchozím nastavení vytvoří kompilátor soubor sestavení s příponou .exe.  
  
> [!NOTE]
>  [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] pro C# a Visual Basic lze použít pouze k vytvoření sestavení tvořená jedním souborem. Pokud chcete vytvořit vícesouborového sestavení, musíte použít kompilátory příkazového řádku nebo [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] pro Visual C++.  
  
 Následující postupy ukazují, jak vytvořit jeden soubor sestavení pomocí kompilátory příkazového řádku.  
  
### <a name="to-create-an-assembly-with-an-exe-extension"></a>Chcete-li vytvořit sestavení s příponou .exe  
  
1.  V příkazovém řádku zadejte následující příkaz:  
  
     \<*příkaz kompilátoru*> \<*název modulu*>  
  
     V tomto příkazu *kompilátoru příkaz* je příkaz kompilátoru pro jazyk použitý v modulu kódu, a *název modulu* je název modulu kódu ke kompilaci do sestavení.  
  
 Následující příklad vytvoří sestavení s názvem `myCode.exe` z modulu kódu názvem `myCode`.  
  
```console
csc myCode.cs  
```  

```console
vbc myCode.vb  
```  
  
#### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>Vytvoření sestavení s příponou .exe a zadejte název výstupního souboru  
  
1.  V příkazovém řádku zadejte následující příkaz:  
  
     \<*příkaz kompilátoru*> **/out:**\<*název souboru*> \<*název modulu*>  
  
     V tomto příkazu *kompilátoru příkaz* je příkaz kompilátoru pro jazyk použitý v modulu kódu, *název souboru* je název výstupního souboru, a *název modulu* je název modul kódu ke kompilaci do sestavení.  
  
 Následující příklad vytvoří sestavení s názvem `myAssembly.exe` z modulu kódu názvem `myCode`.  
  
```console  
csc -out:myAssembly.exe myCode.cs  
```  
  
```console
vbc -out:myAssembly.exe myCode.vb  
```  
  
## <a name="creating-library-assemblies"></a>Vytváření sestavení knihovny  
 Sestavení knihovny je podobná knihovny tříd. Obsahuje typy, které se odkazuje ostatních sestavení, ale nemá žádné vstupní bod zahájit provádění.  
  
#### <a name="to-create-a-library-assembly"></a>Chcete-li vytvořit sestavení knihovny  
  
1.  V příkazovém řádku zadejte následující příkaz:  
  
     \<*příkaz kompilátoru*> **- t: Knihovna** \< *název modulu*>  
  
     V tomto příkazu *kompilátoru příkaz* je příkaz kompilátoru pro jazyk použitý v modulu kódu, a *název modulu* je název modulu kódu ke kompilaci do sestavení. Můžete také použít jiné možnosti kompilátoru, jako **-out:** možnost.  
  
 Následující příklad vytvoří sestavení knihovny s názvem `myCodeAssembly.dll` z modulu kódu názvem `myCode`.  
  
```console  
csc -out:myCodeLibrary.dll -t:library myCode.cs  
```  
  
```console
vbc -out:myCodeLibrary.dll -t:library myCode.vb  
```  
  
## <a name="see-also"></a>Viz také  
 [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)  
 [Vícesouborová sestavení](../../../docs/framework/app-domains/multifile-assemblies.md)  
 [Postupy: Vytváření vícesouborového sestavení](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)  
 [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)

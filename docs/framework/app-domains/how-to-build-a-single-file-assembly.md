---
title: 'Postupy: Sestavení s jediným souborem'
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
ms.openlocfilehash: b5c0b5dc2e001121ab54447bae4a5eed3290a580
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54597837"
---
# <a name="how-to-build-a-single-file-assembly"></a>Postupy: Sestavení s jediným souborem

Jeden soubor sestavení, které se o nejjednodušší typ sestavení, obsahuje informace o typu a implementaci, jakož i [manifestu sestavení](../../../docs/framework/app-domains/assembly-manifest.md). Kompilátory příkazového řádku nebo Visual Studio můžete použít k vytvoření jednosouborového sestavení. Ve výchozím nastavení kompilátor vytvoří sestavení soubor s příponou .exe.

> [!NOTE]
> Visual Studio pro C# a Visual Basic lze použít pouze k vytvoření jednosouborového sestavení. Pokud chcete vytvořit vícesouborové sestavení, musíte použít kompilátory příkazového řádku nebo Visual C++.

Následující postupy ukazují, jak vytvořit jeden soubor sestavení použití kompilátorů příkazového řádku.

## <a name="to-create-an-assembly-with-an-exe-extension"></a>K vytvoření sestavení s příponou .exe

1.  V příkazovém řádku zadejte následující příkaz:

     \<*příkaz kompilátoru*> \<*název modulu*>

     V tomto příkazu *kompilátoru příkaz* je příkaz kompilátor pro jazyk používaný v modulu kódu, a *název modulu* je název modulu kódu zkompilovat do sestavení.

 Následující příklad vytvoří sestavení s názvem `myCode.exe` z modulu kódu volá `myCode`.

```console
csc myCode.cs
```

```console
vbc myCode.vb
```

### <a name="to-create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>K vytvoření sestavení s příponou .exe a určuje název výstupního souboru

1.  V příkazovém řádku zadejte následující příkaz:

     \<*příkaz kompilátoru*> **/out:**\<*název_souboru*> \<*název modulu*>

     V tomto příkazu *kompilátoru příkaz* je příkaz kompilátor pro jazyk používaný v modulu kódu, *název_souboru* je název výstupního souboru a *název modulu* je název Kód modulu je kompilována do sestavení.

 Následující příklad vytvoří sestavení s názvem `myAssembly.exe` z modulu kódu volá `myCode`.

```console
csc -out:myAssembly.exe myCode.cs
```

```console
vbc -out:myAssembly.exe myCode.vb
```

## <a name="creating-library-assemblies"></a>Vytváření sestavení knihovny
 Sestavení knihovny je podobný knihovny tříd. Obsahuje typy, které se odkazuje jiná sestavení, ale nemá žádný vstupní bod zahájit provádění.

### <a name="to-create-a-library-assembly"></a>Chcete-li vytvořit sestavení knihovny

1.  V příkazovém řádku zadejte následující příkaz:

     \<*příkaz kompilátoru*> **- t: Knihovna** \< *název modulu*>

     V tomto příkazu *kompilátoru příkaz* je příkaz kompilátor pro jazyk používaný v modulu kódu, a *název modulu* je název modulu kódu zkompilovat do sestavení. Můžete také použít jiné možnosti kompilátoru, jako **-out:** možnost.

 Následující příklad vytvoří sestavení knihovny s názvem `myCodeAssembly.dll` z modulu kódu volá `myCode`.

```console
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```console
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>Viz také:

- [Vytváření sestavení](../../../docs/framework/app-domains/create-assemblies.md)
- [Vícesouborová sestavení](../../../docs/framework/app-domains/multifile-assemblies.md)
- [Postupy: Vytváření vícesouborového sestavení](../../../docs/framework/app-domains/how-to-build-a-multifile-assembly.md)
- [Programování se sestaveními](../../../docs/framework/app-domains/programming-with-assemblies.md)
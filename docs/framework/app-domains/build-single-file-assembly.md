---
title: 'Postupy: sestavení .NET Framework sestavení s jedním souborem'
ms.date: 08/20/2019
helpviewer_keywords:
- assembly manifest, single-file assemblies
- library assemblies
- command-line compilers
- assemblies [.NET Framework], single-file
- output file name for assemblies
- code modules
- single-file assemblies
dev_langs:
- csharp
- vb
ms.assetid: a6063221-43a5-4d3e-814c-288a4ec69aec
ms.openlocfilehash: b7cb06da74a21dab6f60f0d4c3ac1748fcbe4526
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644304"
---
# <a name="how-to-build-a-net-framework-single-file-assembly"></a>Postupy: sestavení .NET Framework sestavení s jedním souborem

Sestavení s jedním souborem, což je nejjednodušší typ sestavení, obsahuje informace o typu a implementaci a také [manifest sestavení](../../standard/assembly/manifest.md). Pomocí kompilátorů příkazového řádku nebo sady Visual Studio můžete vytvořit sestavení s jedním souborem, které cílí na .NET Framework. Ve výchozím nastavení kompilátor vytvoří soubor sestavení s příponou *. exe* .

> [!NOTE]
> Visual Studio pro C# a Visual Basic lze použít pouze k vytváření sestavení s jedním souborem. Chcete-li vytvořit vícesouborové sestavení, je nutné použít kompilátory příkazového řádku nebo Visual C++.

Následující postupy ukazují, jak vytvořit sestavení s jedním souborem pomocí kompilátorů příkazového řádku.

## <a name="create-an-assembly-with-an-exe-extension"></a>Vytvoření sestavení s příponou. exe

Do příkazového řádku zadejte následující příkaz:

\<*compiler command*> \<*název modulu* příkazu kompilátoru>

V tomto příkazu je *příkaz kompilátoru* příkazem kompilátoru pro jazyk použitý v modulu kódu a *název modulu* je název modulu kódu, který se má kompilovat do sestavení.

Následující příklad vytvoří sestavení s názvem *myCode. exe* z modulu Code s názvem `myCode`.

```csharp
csc myCode.cs
```

```vb
vbc myCode.vb
```

## <a name="create-an-assembly-with-an-exe-extension-and-specify-the-output-file-name"></a>Vytvořte sestavení s příponou. exe a zadejte název výstupního souboru.

Do příkazového řádku zadejte následující příkaz:

\<*příkaz*> **kompilátoru/out:**\<název*souboru*> \<–*název modulu*>

V tomto příkazu je *příkaz kompilátoru* příkazem kompilátoru pro jazyk používaný v modulu kódu, *název souboru* je název výstupního souboru a *název modulu* je název modulu kódu, který má být zkompilován do sestavení.

Následující příklad vytvoří sestavení s názvem *MyAssembly. exe* z modulu Code s názvem `myCode`.

```csharp
csc -out:myAssembly.exe myCode.cs
```

```vb
vbc -out:myAssembly.exe myCode.vb
```

## <a name="create-library-assemblies"></a>Vytváření sestavení knihovny
 Sestavení knihovny je podobné knihovně tříd. Obsahuje typy, které budou odkazovány jinými sestaveními, ale nemá žádný vstupní bod k zahájení provádění.

Chcete-li vytvořit sestavení knihovny, zadejte na příkazovém řádku následující příkaz:

\<*příkaz*> kompilátoru **–** \< *název modulu* t:Library>

V tomto příkazu je *příkaz kompilátoru* příkazem kompilátoru pro jazyk použitý v modulu kódu a *název modulu* je název modulu kódu, který se má kompilovat do sestavení. Můžete také použít další možnosti kompilátoru, jako je například možnost **-out:** .

Následující příklad vytvoří sestavení knihovny s názvem *myCodeAssembly. dll* z modulu kódu s názvem `myCode`.

```csharp
csc -out:myCodeLibrary.dll -t:library myCode.cs
```

```vb
vbc -out:myCodeLibrary.dll -t:library myCode.vb
```

## <a name="see-also"></a>Viz také

- [Vytváření sestavení](../../standard/assembly/create.md)
- [Vícesouborové sestavení](multifile-assemblies.md)
- [Postupy: sestavení vícesouborového sestavení](build-multifile-assembly.md)
- [Programování se sestaveními](../../standard/assembly/index.md)

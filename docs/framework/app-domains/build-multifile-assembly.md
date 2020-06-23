---
title: 'Postupy: Vytváření vícesouborového sestavení'
description: Naučte se vytvářet (vytvářet) vícesouborové sestavení v .NET pomocí ukázkového kódu k ilustraci každého kroku v proceduře.
ms.date: 08/20/2019
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
dev_langs:
- csharp
- vb
- cpp
ms.assetid: 261c5583-8a76-412d-bda7-9b8ee3b131e5
ms.openlocfilehash: a4c298284950ba2989bb73e6d3383b3c4024e6e7
ms.sourcegitcommit: 1c37a894c923bea021a3cc38ce7cba946357bbe1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2020
ms.locfileid: "85104952"
---
# <a name="how-to-build-a-multifile-assembly"></a>Postupy: Vytváření vícesouborového sestavení

Tento článek vysvětluje, jak vytvořit vícesouborové sestavení a poskytuje kód, který ukazuje každý krok v proceduře.

> [!NOTE]
> Integrované vývojové prostředí (IDE) sady Visual Studio pro C# a Visual Basic lze použít pouze k vytváření sestavení s jedním souborem. Chcete-li vytvořit vícesouborové sestavení, je nutné použít kompilátory příkazového řádku nebo aplikaci Visual Studio s Visual C++. Vícesouborové sestavení jsou podporována pouze .NET Framework.

## <a name="create-a-multifile-assembly"></a>Vytvoření vícesouborového sestavení

1. Zkompilujte všechny soubory, které obsahují obory názvů odkazované jinými moduly v sestavení, do modulů kódu. Výchozím rozšířením pro moduly kódu je *. netmodule*.

   Řekněme například, že `Stringer` soubor obsahuje obor názvů s názvem `myStringer` , který obsahuje třídu s názvem `Stringer` . `Stringer`Třída obsahuje metodu s názvem `StringerMethod` , která zapisuje jednu čáru do konzoly.

   ```cpp
   // Assembly building example in the .NET Framework.
   using namespace System;

   namespace myStringer
   {
       public ref class Stringer
       {
       public:
           void StringerMethod()
           {
               System::Console::WriteLine("This is a line from StringerMethod.");
           }
       };
   }
   ```

   ```csharp
   // Assembly building example in the .NET Framework.
   using System;

   namespace myStringer
   {
       public class Stringer
       {
           public void StringerMethod()
           {
               System.Console.WriteLine("This is a line from StringerMethod.");
           }
       }
   }
   ```

   ```vb
   ' Assembly building example in the .NET Framework.
   Namespace myStringer
       Public Class Stringer
           Public Sub StringerMethod()
               System.Console.WriteLine("This is a line from StringerMethod.")
           End Sub
       End Class
   End Namespace
   ```

2. Pro zkompilování tohoto kódu použijte následující příkaz:

   ```cpp
   cl /clr:pure /LN Stringer.cpp
   ```

   ```csharp
   csc /t:module Stringer.cs
   ```

   ```vb
   vbc /t:module Stringer.vb
   ```

   Zadání parametru *Module* s možností kompilátoru **/t:** označuje, že soubor by měl být zkompilován jako modul, nikoli jako sestavení. Kompilátor vytvoří modul s názvem *Stringer. netmodule*, který lze přidat do sestavení.

3. Zkompilujte všechny ostatní moduly pomocí nezbytných možností kompilátoru k označení dalších modulů, které jsou odkazovány v kódu. Tento krok používá možnost kompilátoru **/addmodule** .

   V následujícím příkladu má modul kódu s názvem *klient* metodu vstupního bodu `Main` , která odkazuje na metodu v modulu *Stringer.dll* vytvořeném v kroku 1.

   ```cpp
   #using "Stringer.netmodule"

   using namespace System;
   using namespace myStringer; //The namespace created in Stringer.netmodule.

   ref class MainClientApp
   {
       // Static method Main is the entry point method.
   public:
       static void Main()
       {
           Stringer^ myStringInstance = gcnew Stringer();
           Console::WriteLine("Client code executes");
           myStringInstance->StringerMethod();
       }
   };

   int main()
   {
       MainClientApp::Main();
   }
   ```

   ```csharp
   using System;
   using myStringer;

   class MainClientApp
   {
       // Static method Main is the entry point method.
       public static void Main()
       {
           Stringer myStringInstance = new Stringer();
           Console.WriteLine("Client code executes");
           myStringInstance.StringerMethod();
       }
   }
   ```

   ```vb
   Imports myStringer

   Class MainClientApp
       ' Static method Main is the entry point method.
       Public Shared Sub Main()
           Dim myStringInstance As New Stringer()
           Console.WriteLine("Client code executes")
           myStringInstance.StringerMethod()
       End Sub
   End Class
   ```

4. Pro zkompilování tohoto kódu použijte následující příkaz:

   ```cpp
   cl /clr:pure /FUStringer.netmodule /LN Client.cpp
   ```

   ```csharp
   csc /addmodule:Stringer.netmodule /t:module Client.cs
   ```

   ```vb
   vbc /addmodule:Stringer.netmodule /t:module Client.vb
   ```

   Zadejte možnost **/t: Module** , protože tento modul se přidá do sestavení v budoucím kroku. Určete možnost **/addmodule** , protože kód v *klientovi* odkazuje na obor názvů vytvořený kódem v *Stringer. netmodule*. Kompilátor vytvoří modul s názvem *Client. netmodule* , který obsahuje odkaz na jiný modul *Stringer. netmodule*.

   > [!NOTE]
   > Kompilátory jazyka C# a Visual Basic podporují přímé vytváření vícesouborového sestavení pomocí následujících dvou různých syntaxí.
   >
   > Dvě kompilace vytvoří sestavení se dvěma soubory:
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /t:module Stringer.cs
   >   csc Client.cs /addmodule:Stringer.netmodule
   >   ```
   >
   >   ```vb
   >   vbc /t:module Stringer.vb
   >   vbc Client.vb /addmodule:Stringer.netmodule
   >   ```
   >
   > Jedna kompilace vytvoří sestavení se dvěma soubory:
   >
   >   ```cpp
   >   cl /clr:pure /LN Stringer.cpp
   >   cl /clr:pure Client.cpp /link /ASSEMBLYMODULE:Stringer.netmodule
   >   ```
   >
   >   ```csharp
   >   csc /out:Client.exe Client.cs /out:Stringer.netmodule Stringer.cs
   >   ```
   >
   >   ```vb
   >   vbc /out:Client.exe Client.vb /out:Stringer.netmodule Stringer.vb
   >   ```

5. Použijte [linker sestavení (Al.exe)](../tools/al-exe-assembly-linker.md) k vytvoření výstupního souboru, který obsahuje manifest sestavení. Tento soubor obsahuje referenční informace pro všechny moduly nebo prostředky, které jsou součástí sestavení.

    Do příkazového řádku zadejte následující příkaz:

    **Al** \<*module name*> . \<*module name*> .. **/Main:** \<*method name*> **/out:** \<*file name*> **/target:**\<*assembly file type*>

    V tomto příkazu argumenty *názvu modulu* určují název každého modulu, který chcete zahrnout do sestavení. Parametr **/Main:** Určuje název metody, která je vstupním bodem sestavení. Možnost **/out:** Určuje název výstupního souboru, který obsahuje metadata sestavení. Možnost **/target:** určuje, že sestavení je spustitelný soubor aplikace konzoly (*. exe*), spustitelný soubor systému Windows (*. Win*) nebo soubor knihovny (*. lib*).

    V následujícím příkladu *Al.exe* vytvoří sestavení, které je spustitelný soubor aplikace konzoly s názvem *myAssembly.exe*. Aplikace se skládá ze dvou modulů s názvem *Client. netmodule* a *Stringer. netmodule*a spustitelný soubor s názvem *myAssembly.exe*, který obsahuje pouze metadata sestavení. Vstupním bodem sestavení je `Main` Metoda ve třídě `MainClientApp` , která je umístěna v *Client.dll*.

    ```cmd
    al Client.netmodule Stringer.netmodule /main:MainClientApp.Main /out:myAssembly.exe /target:exe
    ```

    Můžete použít [jazyk MSIL Disassembler (Ildasm.exe)](../tools/ildasm-exe-il-disassembler.md) k prohlédnutí obsahu sestavení nebo určení, zda je soubor sestavením nebo modulem.

## <a name="see-also"></a>Viz také

- [Vytváření sestavení](../../standard/assembly/create.md)
- [Postupy: zobrazení obsahu sestavení](../../standard/assembly/view-contents.md)
- [Způsob, jakým modul runtime vyhledává sestavení](../deployment/how-the-runtime-locates-assemblies.md)
- [Vícesouborová sestavení](multifile-assemblies.md)

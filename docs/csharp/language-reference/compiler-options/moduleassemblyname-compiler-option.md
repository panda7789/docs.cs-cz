---
title: "-moduleassemblyname (možnost kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c8ebd6f7498adead4586c9e90ec58ca8efe81aaa
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="moduleassemblyname-c-compiler-option"></a>/moduleassemblyname (Možnost kompilátoru C#)
Určuje sestavení, jehož neveřejným typům .netmodule přístup.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
 `assembly_name`  
 Název sestavení, jejichž neveřejný typy .netmodule mají přístup.  
  
## <a name="remarks"></a>Poznámky  
 **/ moduleassemblyname** by měl použít při vytváření .netmodule, a tam, kde platí následující podmínky:  
  
-   .netmodule potřebuje přístup k neveřejným typům v existujícím sestavení.  
  
-   Víte, název sestavení, do které budou vytvořeny .netmodule.  
  
-   Existující sestavení udělil přátelských sestavení přístup do sestavení, do které budou vytvořeny .netmodule.  
  
 Další informace o vytváření .netmodule najdete v tématu [/target: module (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 Další informace o přátelských sestavení najdete v tématu [přátelských sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
 Tato možnost není k dispozici v rámci vývojového prostředí; je k dispozici pouze při kompilaci z příkazového řádku.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.  
  
## <a name="example"></a>Příklad  
 Tato ukázka vytvoří sestavení s typem privátní a sestavení s názvem csman_an_assembly udávající přátelských sestavení přístup.  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: /target:library  
using System;  
using System.Runtime.CompilerServices;  
  
[assembly:InternalsVisibleTo ("csman_an_assembly")]  
  
class An_Internal_Class   
{  
    public void Test()   
    {   
        Console.WriteLine("An_Internal_Class.Test called");   
    }  
}  
```  
  
## <a name="example"></a>Příklad  
 Tato ukázka vytvoří .netmodule, který přistupuje k typu neveřejný v sestavení moduleassemblyname_1.dll. Musíte znát, že tento .netmodule bude vytvořen v sestavení nazvaném csman_an_assembly, můžeme určit **/moduleassemblyname**, což .netmodule pro přístup k neveřejný typy v sestavení, které má povolen přátelských sestavení přístup k csman_an_assembly.  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: /moduleassemblyname:csman_an_assembly /target:module /reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad vytvoří sestavení csman_an_assembly, odkazy na dříve vytvořené sestavení a .netmodule.  
  
```csharp  
// csman_an_assembly.cs  
// compile with: /addmodule:moduleassemblyname_2.netmodule /reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
 **An_Internal_Class.test názvem**  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

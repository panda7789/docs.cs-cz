---
description: -moduleassemblyname – (možnost kompilátoru C#)
title: -moduleassemblyname – (možnost kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: d669a1687abe496b921d5670b9149b0e933b2d95
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125251"
---
# <a name="-moduleassemblyname-c-compiler-option"></a>-moduleassemblyname – (možnost kompilátoru C#)
Určuje sestavení, jehož neveřejné typy a. netmodule mají přístup.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Argumenty  
 `assembly_name`  
 Název sestavení, jehož neveřejné typy má. netmodule, ke kterému má přístup.  
  
## <a name="remarks"></a>Poznámky  
 **-moduleassemblyname –** by měla být použita při sestavování. netmodule a kde jsou splněné následující podmínky:  
  
- Modul. netmodule potřebuje přístup k neveřejným typům v existujícím sestavení.  
  
- Znáte název sestavení, do kterého bude sestaven. netmodule.  
  
- Existující sestavení má udělený přístup pro sestavení typu Friend k sestavení, do kterého bude sestaven. netmodule.  
  
 Další informace o vytváření. netmodule naleznete v tématu [-target: Module (možnosti kompilátoru C#)](./target-module-compiler-option.md).  
  
 Další informace o Friend sestaveních naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend.md).  
  
 Tato možnost není k dispozici v rámci vývojového prostředí; je k dispozici pouze při kompilaci z příkazového řádku.  
  
 Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.  
  
## <a name="example"></a>Příklad  
 Tato ukázka sestaví sestavení s privátním typem a poskytuje přítel přístup k sestavení s názvem csman_an_assembly.  
  
```csharp  
// moduleassemblyname_1.cs  
// compile with: -target:library  
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
 Tato ukázka sestaví. netmodule, který přistupuje k neveřejnému typu v sestavení moduleassemblyname_1.dll. Díky tomu, že tento modul netmodule bude sestaven do sestavení s názvem csman_an_assembly, můžeme specifikovat **-moduleassemblyname –**, což umožňuje rozhraní. netmodule přístup k neveřejným typům v sestavení, kterým bylo uděleno oprávnění typu Friend assembly pro csman_an_assembly.  
  
```csharp  
// moduleassemblyname_2.cs  
// compile with: -moduleassemblyname:csman_an_assembly -target:module -reference:moduleassemblyname_1.dll  
class B {  
    public void Test() {  
        An_Internal_Class x = new An_Internal_Class();  
        x.Test();  
    }  
}  
```  
  
## <a name="example"></a>Příklad  
 Tento vzorový kód sestaví csman_an_assembly sestavení a odkazuje na dřív sestavené sestavení a. netmodule.  
  
```csharp  
// csman_an_assembly.cs  
// compile with: -addmodule:moduleassemblyname_2.netmodule -reference:moduleassemblyname_1.dll  
class A {  
    public static void Main() {  
        B bb = new B();  
        bb.Test();  
    }  
}  
```  
  
**An_Internal_Class. test volal**

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

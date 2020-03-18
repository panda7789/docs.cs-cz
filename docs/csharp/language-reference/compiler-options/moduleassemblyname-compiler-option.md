---
title: -moduleassemblyname (C# Compiler Option)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: 1477eeb0f2e16e18cb86009739bc8e7d9dee2ac0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173715"
---
# <a name="-moduleassemblyname-c-compiler-option"></a>-moduleassemblyname (C# Compiler Option)
Určuje sestavení, jehož neveřejné typy .netmodule přístup.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Argumenty  
 `assembly_name`  
 Název sestavení, jehož neveřejné typy .netmodule přístup.  
  
## <a name="remarks"></a>Poznámky  
 **-moduleassemblyname** by měl být použit při vytváření .netmodule a kde jsou splněny následující podmínky:  
  
- Modul .netmodul potřebuje přístup k neveřejným typům v existujícím sestavení.  
  
- Znáte název sestavení, do kterého bude vytvořen modul .netmodule.  
  
- Existující sestavení udělilo friend assembly přístup k sestavení, do kterého bude vytvořen modul .netmodule.  
  
 Další informace o vytváření .netmodule naleznete v tématu [-target:module (C# Compiler Options)](./target-module-compiler-option.md).  
  
 Další informace o sestaveních přátel naleznete v tématu [Friend Assemblies](../../../standard/assembly/friend.md).  
  
 Tato možnost není k dispozici z vývojového prostředí. je k dispozici pouze při kompilaci z příkazového řádku.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nelze ji programově změnit.  
  
## <a name="example"></a>Příklad  
 Tato ukázka vytvoří sestavení s privátním typem a která poskytuje přátelské sestavení přístup k sestavení s názvem csman_an_assembly.  
  
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
 Tato ukázka vytvoří .netmodule, který přistupuje k neveřejnému typu v sestavení moduleassemblyname_1.dll. Vědomím, že tento .netmodule bude integrován do sestavení s názvem csman_an_assembly, můžeme zadat **-moduleassemblyname**, což umožňuje .netmodule pro přístup k neveřejným typům v sestavení, které udělilo přístup k sestavení friend csman_an_assembly.  
  
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
 Tento ukázkový kód vytvoří sestavení csman_an_assembly, odkazující na dříve sestavené sestavení a .netmodule.  
  
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
  
**An_Internal_Class.Test volal**

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

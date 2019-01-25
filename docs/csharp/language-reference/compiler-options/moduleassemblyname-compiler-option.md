---
title: -moduleassemblyname (možnost kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /moduleassemblyname
helpviewer_keywords:
- moduleassemblyname compiler option [C#]
- /moduleassemblyname compiler option [C#]
- .moduleassemblyname compiler option [C#]
ms.assetid: d464d9b9-f18d-423b-95e9-66c7878fd53a
ms.openlocfilehash: bc1bc1376271b3a01d9b720dd85f812ea55cf34c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54665042"
---
# <a name="-moduleassemblyname-c-compiler-option"></a>-moduleassemblyname (možnost kompilátoru C#)
Určuje sestavení, jejichž typy neveřejným .netmodule můžete získat přístup.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-moduleassemblyname:assembly_name  
```  
  
## <a name="arguments"></a>Arguments  
 `assembly_name`  
 Název sestavení, jejichž neveřejné typy .netmodule můžete přistupovat.  
  
## <a name="remarks"></a>Poznámky  
 **-moduleassemblyname** by měla sloužit při sestavování .netmodule, a pokud jsou splněny následující podmínky:  
  
-   .netmodule potřebuje přístup k neveřejným typům v existující sestavení.  
  
-   Znáte jeho název sestavení, do které budou vytvořeny modul .NET.  
  
-   Existující sestavení má udělen Přátelský přístup sestavení k sestavení, do které budou vytvořeny modul .NET.  
  
 Další informace o vytváření .netmodule, naleznete v tématu [-target: module (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md).  
  
 Další informace o přátelských sestavení naleznete v tématu [přátelských sestavení](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
 Tato možnost není k dispozici v rámci vývojového prostředí; je dostupná jenom při kompilaci z příkazového řádku.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.  
  
## <a name="example"></a>Příklad  
 Tato ukázka vytvoří sestavení s privátním reprezentacím a, který poskytuje přístup typu friend sestavení k sestavení nazvané csman_an_assembly.  
  
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
 Tato ukázka vytvoří .netmodule přistupující k neveřejným typ v sestavení moduleassemblyname_1.dll. Podle vědomím, že bude tento modul .NET integrované do sestavení nazvané csman_an_assembly, můžeme určit **- moduleassemblyname**, umožňuje modul .NET pro přístup k neveřejné typy v sestavení, která má udělená sestavení typu friend přístup k csman_an_assembly.  
  
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
 Tento vzorový kód vytvoří sestavení csman_an_assembly, odkazující na dříve vytvořené sestavení a modul .NET.  
  
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
  
**Volá se, An_Internal_Class.test**

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

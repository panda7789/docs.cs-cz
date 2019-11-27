---
title: -Target (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: af7bd917f57c8752a2026fbb98aa8b22adc98db7
ms.sourcegitcommit: 81ad1f09b93f3b3e6706a7f2e4ddf50ef229ea3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/20/2019
ms.locfileid: "74204517"
---
# <a name="-target-c-compiler-options"></a>-Target (C# možnosti kompilátoru)
Možnost kompilátoru **-target** lze zadat v jednom ze čtyř forem:  
  
 [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)  
 Pro vytvoření souboru. exe pro aplikace Windows 8. x Store.  
  
 [-target:exe](./target-exe-compiler-option.md)  
 Pro vytvoření souboru. exe.  
  
 [-target:library](./target-library-compiler-option.md)  
 Chcete-li vytvořit knihovnu kódu.  
  
 [-target:module](./target-module-compiler-option.md)  
 Vytvořit modul.  
  
 [-target:winexe](./target-winexe-compiler-option.md)  
 Pro vytvoření programu systému Windows.  
  
 [-target:winmdobj](./target-winmdobj-compiler-option.md)  
 Pro vytvoření zprostředkujícího souboru. winmdobj.  
  
 Pokud nezadáte **cíl: modul**, **-target** způsobí umístění manifestu .NET Framework sestavení do výstupního souboru. Další informace naleznete v tématu [sestavení v rozhraní .NET](../../../standard/assembly/index.md) a [běžné atributy](../../programming-guide/concepts/attributes/common-attributes.md).  
  
 Manifest sestavení je umístěn v prvním výstupním souboru. exe v kompilaci nebo v první knihovně DLL, pokud není k dispozici výstupní soubor. exe. Například v následujícím příkazovém řádku se manifest umístí do `1.exe`:  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Kompilátor vytvoří pro každou kompilaci pouze jeden manifest sestavení. Informace o všech souborech v kompilaci jsou umístěny v manifestu sestavení. Všechny výstupní soubory kromě těch, které byly vytvořeny pomocí **-target: modul** může obsahovat manifest sestavení. Při vytváření více výstupních souborů na příkazovém řádku lze vytvořit pouze jeden manifest sestavení a musí přejít do prvního výstupního souboru zadaného v příkazovém řádku. Bez ohledu na to, co je první výstupní soubor ( **-target: exe**, **-target: winexe**, **-target: Library** nebo **-target: Module**), všechny ostatní výstupní soubory vytvořené ve stejné kompilaci musí být moduly ( **-target: Module**).  
  
 Vytvoříte-li sestavení, můžete označit, že veškerý nebo část kódu je kompatibilní se specifikací CLS s atributem <xref:System.CLSCompliantAttribute>.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Další informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
- [-subsystemversion (C# možnosti kompilátoru)](./subsystemversion-compiler-option.md)

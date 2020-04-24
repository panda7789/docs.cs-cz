---
title: -target (Možnosti kompilátoru Jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: ea5481810e629d911c4d5aba62e60c98d0783f34
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81644348"
---
# <a name="-target-c-compiler-options"></a>-target (Možnosti kompilátoru Jazyka C#)
Možnost kompilátoru **-target** lze zadat v jednom ze čtyř formulářů:  
  
 [-target:appcontainerexe](./target-appcontainerexe-compiler-option.md)  
 Vytvoření souboru EXE pro aplikace pro Windows 8.x Store.  
  
 [-target:exe](./target-exe-compiler-option.md)  
 Vytvoření souboru EXE.  
  
 [-target:library](./target-library-compiler-option.md)  
 Chcete-li vytvořit knihovnu kódu.  
  
 [-target:module](./target-module-compiler-option.md)  
 Chcete-li vytvořit modul.  
  
 [-target:winexe](./target-winexe-compiler-option.md)  
 Vytvoření programu systému Windows.  
  
 [-target:winmdobj](./target-winmdobj-compiler-option.md)  
 Chcete-li vytvořit zprostředkující soubor .winmdobj.  
  
 Pokud nezadáte **-target:module**, **-target** způsobí, že manifest sestavení rozhraní .NET Framework bude umístěn do výstupního souboru. Další informace naleznete [v tématech Sestavení v rozhraní .NET](../../../standard/assembly/index.md) a [Common Attributes](../attributes/global.md).  
  
 Manifest sestavení je umístěn v prvním výstupním souboru EXE v kompilaci nebo v první dll, pokud neexistuje žádný výstupní soubor EXE. Například v následujícím příkazovém řádku bude `1.exe`manifest umístěn do :  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Kompilátor vytvoří pouze jeden manifest sestavení na kompilaci. Informace o všech souborech v kompilaci jsou umístěny v manifestu sestavení. Všechny výstupní soubory s výjimkou těch, které byly vytvořeny pomocí **modulu -target:module,** mohou obsahovat manifest sestavení. Při vytváření více výstupních souborů na příkazovém řádku lze vytvořit pouze jeden manifest sestavení a musí přejít do prvního výstupního souboru určeného na příkazovém řádku. Bez ohledu na to, co je první výstupní soubor (**-target:exe**, **-target:winexe**, **-target:library** nebo **-target:module**), musí být všechny ostatní výstupní soubory vytvořené ve stejné kompilaci moduly (**-target:module**).  
  
 Pokud vytvoříte sestavení, můžete označit, že celý kód nebo jeho <xref:System.CLSCompliantAttribute> část je kompatibilní s atributem CLS.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Další informace o programovém nastavení této <xref:VSLangProj80.ProjectProperties3.OutputType%2A>možnosti kompilátoru naleznete v tématu .  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)
- [-subsystemversion (Možnosti kompilátoru Jazyka C#)](./subsystemversion-compiler-option.md)

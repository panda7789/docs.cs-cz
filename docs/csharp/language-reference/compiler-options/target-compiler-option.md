---
title: "-target (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 44dd99ef834f98a1a918c659d3057f8f6f91805a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="-target-c-compiler-options"></a>-target (možnosti kompilátoru C#)
**-Cíl** – možnost kompilátoru lze zadat v jedné ze čtyř podob:  
  
 [-target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 Chcete-li vytvořit soubor .exe pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikace.  
  
 [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 Chcete-li vytvořit soubor s příponou .exe.  
  
 [-target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 K vytvoření knihovny kódu.  
  
 [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 Chcete-li vytvořit modul.  
  
 [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 K vytvoření programu systému Windows.  
  
 [-target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 Vytvořit soubor zprostředkující .winmdobj.  
  
 Pokud nezadáte **-target: module**, **-cíl** způsobí umístit do výstupního souboru manifestu sestavení rozhraní .NET Framework. Další informace najdete v tématu [sestavení v modulu Common Language Runtime](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) a [běžné atributy](../../programming-guide/concepts/attributes/common-attributes.md).  
  
 Manifest sestavení je umístěn v první výstupní soubor .exe v kompilace nebo v první knihovny DLL, pokud není dostupný žádný výstupní soubor .exe. Například v příkazovém řádku následující manifest bude uložena v umístění `1.exe`:  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Kompilátor vytvoří pouze jeden manifest sestavení kompilace. Informace o všechny soubory v kompilaci je umístěn v manifestu sestavení. Všechny soubory kromě těch vytvořené pomocí výstup **-target: module** může obsahovat manifest sestavení. Při vytváření více výstupních souborů na příkazovém řádku, lze vytvořit pouze jeden manifest sestavení a musí být umístěn do prvního výstupního souboru zadat na příkazovém řádku. Bez ohledu na to, co je první výstupní soubor (**-target: exe**, **-target: winexe**, **-target: library** nebo **-target: module**) ani jiné výstupní soubory vytvořené ve stejné kompilaci musí být moduly (**-target: module**).  
  
 Pokud vytvoříte sestavení, můžete určit, že nebo jeho část kódu je kompatibilní se specifikací CLS <xref:System.CLSCompliantAttribute> atribut.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Další informace o nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)  
 [-subsystemversion (C# Compiler Options)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)

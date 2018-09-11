---
title: -target (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: a337ecbc614ff40eda42fc5263dbb52aa92b905f
ms.sourcegitcommit: 67de6cb5dd66a19f2180ba7e4d7aecc697f8a963
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339588"
---
# <a name="-target-c-compiler-options"></a>-target (možnosti kompilátoru C#)
**-Target** – možnost kompilátoru je zadat v jednom ze čtyř formuláře:  
  
 [-target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 Chcete-li vytvořit soubor s příponou .exe pro [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)] aplikace.  
  
 [-target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 Chcete-li vytvořit soubor s příponou .exe.  
  
 [-target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 Pro vytvoření knihovny kódu.  
  
 [-target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 Jak vytvořit modul.  
  
 [-target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 K vytvoření programu Windows.  
  
 [-target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 Chcete-li vytvořit přechodného souboru .winmdobj.  
  
 Pokud nezadáte **-target: module**, **-target** způsobí, že budou umístěny ve výstupním souboru manifestu sestavení rozhraní .NET Framework. Další informace najdete v tématu [sestavení v modulu Common Language Runtime](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) a [společné atributy](../../programming-guide/concepts/attributes/common-attributes.md).  
  
 Manifest sestavení je umístěn v první výstupní soubor .exe v kompilaci nebo v rámci DLL. první, pokud neexistuje žádný výstupní soubor .exe. Například v příkazovém řádku následující manifest budou umístěny v `1.exe`:  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 Kompilátor vytvoří jenom jeden manifest sestavení za kompilace. Informace o všech souborech v kompilaci je umístěn v manifestu sestavení. Všechny výstupní soubory s výjimkou těch, vytvořené pomocí **-target: module** může obsahovat manifest sestavení. Při vytváření několika výstupních souborů na příkazovém řádku, je možné vytvořit pouze jeden manifest sestavení a musí přejít do první výstupní soubor zadán v příkazovém řádku. Bez ohledu na to, co je první výstupní soubor (**-target: exe**, **-target: winexe**, **-target: library** nebo **-target: module**) ani jiné výstupní soubory vytvořené ve stejné kompilaci musí být moduly (**-target: module**).  
  
 Pokud vytvoříte sestavení, můžete určit, že všechny nebo část kódu je kompatibilní se Specifikací CLS se <xref:System.CLSCompliantAttribute> atribut.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Další informace o nastavení této možnosti kompilátoru prostřednictvím kódu programu najdete v tématu <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="see-also"></a>Viz také  

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)  
- [-subsystemversion (možnosti kompilátoru C#)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)

---
title: -linkresource – (C# možnosti kompilátoru)
ms.date: 07/20/2015
f1_keywords:
- /linkresource
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
ms.openlocfilehash: 454915454f3faf15933257f3e3e221afec51d0ee
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606763"
---
# <a name="-linkresource-c-compiler-options"></a>-linkresource – (C# možnosti kompilátoru)
Vytvoří odkaz na prostředek .NET Framework ve výstupním souboru. Soubor prostředků se nepřidá do výstupního souboru. To se liší od možnosti [-Resource](./resource-compiler-option.md) , která vloží soubor prostředků do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 .NET Framework soubor prostředků, na který chcete propojit ze sestavení.  
  
 `identifier`volitelné  
 Logický název prostředku; název, který se použije k načtení prostředku. Výchozí hodnota je název souboru.  
  
 `accessibility-modifier`volitelné  
 Přístupnost prostředku: Public nebo Private. Výchozí hodnota je Public.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení jsou propojené prostředky v sestavení veřejné, když jsou vytvořeny pomocí C# kompilátoru. Chcete-li zajistit soukromí prostředků, `private` zadejte jako modifikátor přístupnosti. Žádný jiný modifikátor `public` `private` není povolený.  
  
 **-linkresource –** vyžaduje jednu z možností [TARGETu](./target-compiler-option.md) s výjimkou **target: Module**.  
  
 Pokud `filename` je vytvořen soubor prostředků .NET Framework, například pomocí nástroje [Resgen. exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu přistupovat <xref:System.Resources> pomocí členů v oboru názvů. Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Pro všechny ostatní prostředky použijte `GetManifestResource` metody <xref:System.Reflection.Assembly> ve třídě pro přístup k prostředku v době běhu.  
  
 Soubor určený v `filename` může být libovolného formátu. Například můžete chtít vytvořit nativní knihovnu DLL součásti sestavení, aby mohla být nainstalována do globální mezipaměti sestavení (GAC) a zpřístupněna ze spravovaného kódu v sestavení. Druhý z následujících příkladů ukazuje, jak to provést. Stejnou věc lze provést v linkeru sestavení. Třetí z následujících příkladů ukazuje, jak to provést. Další informace naleznete v tématu [Al. exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) a [práce se sestaveními a globální mezipamětí sestavení](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).  
  
 **-linkres –** je krátká forma **-linkresource –** .  
  
 Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.  
  
## <a name="example"></a>Příklad  
 Kompilovat `in.cs` a propojit se souborem `rf.resource`prostředků:  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Příklad  
 Zkompilujte `A.cs` do knihovny DLL, připojte se k nativní knihovně DLL N. dll a vložte výstup do globální mezipaměti sestavení (GAC). V tomto příkladu se knihovna DLL a N. dll nachází v globální mezipaměti sestavení (GAC).  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad provede stejnou věc jako předchozí, ale pomocí možností linkeru sestavení.  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Al.exe (linker sestavení)](../../../framework/tools/al-exe-assembly-linker.md)
- [Práce se sestaveními a s globální pamětí sestavení](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

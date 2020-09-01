---
description: -linkresource – (možnosti kompilátoru C#)
title: -linkresource – (možnosti kompilátoru C#)
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
ms.openlocfilehash: 162baad57397b6d992dcf8f03f0b3661e0105cb8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125342"
---
# <a name="-linkresource-c-compiler-options"></a>-linkresource – (možnosti kompilátoru C#)
Vytvoří odkaz na prostředek .NET Framework ve výstupním souboru. Soubor prostředků se nepřidá do výstupního souboru. To se liší od možnosti [-Resource](./resource-compiler-option.md) , která vloží soubor prostředků do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 .NET Framework soubor prostředků, na který chcete propojit ze sestavení.  
  
 `identifier` (volitelné)  
 Logický název prostředku; název, který se použije k načtení prostředku. Výchozí hodnota je název souboru.  
  
 `accessibility-modifier` (volitelné)  
 Přístupnost prostředku: Public nebo Private. Výchozí hodnota je Public.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení jsou propojené prostředky v sestavení veřejné, když jsou vytvořeny pomocí kompilátoru jazyka C#. Chcete-li zajistit soukromí prostředků, zadejte `private` jako modifikátor přístupnosti. Žádný jiný modifikátor `public` `private` není povolený.  
  
 **-linkresource –** vyžaduje jednu z možností [TARGETu](./target-compiler-option.md) s výjimkou **target: Module**.  
  
 Pokud `filename` je vytvořen soubor prostředků .NET Framework, například [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu přistupovat pomocí členů v <xref:System.Resources> oboru názvů. Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Pro všechny ostatní prostředky použijte `GetManifestResource` metody ve <xref:System.Reflection.Assembly> třídě pro přístup k prostředku v době běhu.  
  
 Soubor určený v `filename` může být libovolného formátu. Například můžete chtít vytvořit nativní knihovnu DLL součásti sestavení, aby mohla být nainstalována do globální mezipaměti sestavení (GAC) a zpřístupněna ze spravovaného kódu v sestavení. Druhý z následujících příkladů ukazuje, jak to provést. Stejnou věc lze provést v linkeru sestavení. Třetí z následujících příkladů ukazuje, jak to provést. Další informace naleznete v tématu [Al.exe (linker sestavení)](../../../framework/tools/al-exe-assembly-linker.md) a [práce se sestaveními a globální mezipamětí sestavení](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).  
  
 **-linkres –** je krátká forma **-linkresource –**.  
  
 Tato možnost kompilátoru není v aplikaci Visual Studio k dispozici a nelze ji změnit programově.  
  
## <a name="example"></a>Příklad  
 Kompilovat `in.cs` a propojit se souborem prostředků `rf.resource` :  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Příklad  
 Zkompilujte `A.cs` do knihovny DLL, připojte se k nativní knihovně dll N.dll a vložte výstup do globální mezipaměti sestavení (GAC). V tomto příkladu se budou v globální mezipaměti sestavení (GAC) nacházet jak A.dll, tak N.dll.  
  
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
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Al.exe (linker sestavení)](../../../framework/tools/al-exe-assembly-linker.md)
- [Práce se sestaveními a s globální pamětí sestavení](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

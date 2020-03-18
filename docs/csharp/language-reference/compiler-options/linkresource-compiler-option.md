---
title: -linkresource (C# Možnosti kompilátoru)
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
ms.openlocfilehash: 41af8e0ba8ffebd07d3cb1d2bc5fbc04b8cd595d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173728"
---
# <a name="-linkresource-c-compiler-options"></a>-linkresource (C# Možnosti kompilátoru)
Vytvoří odkaz na prostředek rozhraní .NET Framework ve výstupním souboru. Soubor prostředků není přidán do výstupního souboru. To se liší od [-resource](./resource-compiler-option.md) možnost, která se vložit soubor prostředků ve výstupním souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Soubor prostředku rozhraní .NET Framework, ke kterému chcete vytvořit propojení ze sestavení.  
  
 `identifier` (volitelné)  
 Logický název prostředku; název, který se používá k načtení prostředku. Výchozí je název souboru.  
  
 `accessibility-modifier` (volitelné)  
 Dostupnost zdroje: veřejné nebo soukromé. Výchozí hodnota je veřejná.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení jsou propojené prostředky veřejné v sestavení při jejich vytvoření pomocí kompilátoru Jazyka C#. Chcete-li prostředky jako `private` modifikátor usnadnění zadat jako soukromý. Žádný jiný modifikátor než `public` nebo `private` je povolen.  
  
 **-linkresource** vyžaduje jednu z možností [-target](./target-compiler-option.md) než **-target:module**.  
  
 Pokud `filename` je soubor prostředků rozhraní .NET Framework vytvořený například [programem Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu přistupovat pomocí členů v oboru <xref:System.Resources> názvů. Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Pro všechny ostatní prostředky `GetManifestResource` použijte <xref:System.Reflection.Assembly> metody ve třídě pro přístup k prostředku za běhu.  
  
 Soubor zadaný `filename` v může být libovolný formát. Můžete například chtít vytvořit nativní součást sestavení DLL, aby mohla být nainstalována do globální mezipaměti sestavení a přístupná ze spravovaného kódu v sestavení. Druhý z následujících příkladů ukazuje, jak to provést. Totéž můžete provést v propojovacím zařízení sestavení. Třetí z následujících příkladů ukazuje, jak to provést. Další informace naleznete v [tématu Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) a [práce se sestaveními a globální mezipaměti sestavení](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).  
  
 **-linkres** je krátká forma **-linkresource**.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nelze ji programově změnit.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` a propojení `rf.resource`se souborem prostředků :  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Příklad  
 Kompilace `A.cs` do dll, odkaz na nativní DLL N.dll a umístit výstup do globální mezipaměti sestavení (GAC). V tomto příkladu bude v gac umístěny a.dll i N.dll.  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad dělá totéž jako předchozí, ale pomocí možnosti propojovacího nástroje sestavení.  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Al.exe (linker sestavení)](../../../framework/tools/al-exe-assembly-linker.md)
- [Práce se sestaveními a s globální pamětí sestavení](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

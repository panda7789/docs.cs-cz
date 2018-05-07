---
title: -linkresource (možnosti kompilátoru C#)
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
ms.openlocfilehash: 5c666b1c6440ac323830780ca5ca6930327ad9d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-linkresource-c-compiler-options"></a>-linkresource (možnosti kompilátoru C#)
Vytvoří odkaz na prostředek rozhraní .NET Framework ve výstupním souboru. Souboru prostředků nebyla přidána do výstupního souboru. Tím se liší od [– prostředek](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) možnost, která vložení zdrojového souboru do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Soubor prostředků rozhraní .NET Framework, do kterého chcete propojit ze sestavení.  
  
 `identifier` (volitelné)  
 Logický název prostředku; název, který se používá k načtení prostředku. Výchozí hodnota je název souboru.  
  
 `accessibility-modifier` (volitelné)  
 Usnadnění prostředku: veřejné nebo soukromé. Výchozí hodnota je veřejná.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení jsou propojené prostředky při jejich vytváření pomocí kompilátor jazyka C# veřejné v sestavení. Chcete-li prostředky privátní, zadejte `private` jako modifikátor dostupnosti. Žádný jiný modifikátor kromě `public` nebo `private` je povolen.  
  
 **-linkresource** vyžaduje jednu z [-cíl](../../../csharp/language-reference/compiler-options/target-compiler-option.md) možnosti jiné než **-target: module**.  
  
 Pokud `filename` je soubor prostředků rozhraní .NET Framework, který je vytvořen, například pomocí [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí k němu se členy v <xref:System.Resources> oboru názvů. Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. U všech ostatních prostředků, použijte `GetManifestResource` metody v <xref:System.Reflection.Assembly> třídy pro přístup k prostředku v době běhu.  
  
 V souboru určeném v `filename` může být libovolného formátu. Například můžete chtít nativní knihovny DLL součástí sestavení, ujistěte se, aby mohli být nainstalován do globální mezipaměti sestavení a získat přístup ze spravovaného kódu v sestavení. Druhý následující příklady ukazuje, jak to udělat. Můžete to samé v Linker sestavení. Třetí následující příklady ukazuje, jak to udělat. Další informace najdete v tématu [Al.exe (Linker sestavení)](../../../framework/tools/al-exe-assembly-linker.md) a [práce se sestaveními a globální mezipaměť sestavení](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).  
  
 **-linkres** je zkratka pro **- linkresource**.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` a odkaz na soubor prostředků `rf.resource`:  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Příklad  
 Kompilace `A.cs` do knihovny DLL, odkaz tuto knihovnu nativní knihovny DLL knihovnou n.dll a umístí výstup v globální mezipaměti sestavení (GAC). V tomto příkladu bude A.dll i N.dll nacházet v mezipaměti GAC.  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad provede stejnou akci, jako předchozí, ale s použitím možnosti Linker sestavení.  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Al.exe (linker sestavení)](../../../framework/tools/al-exe-assembly-linker.md)  
 [Práce se sestaveními a s globální pamětí sestavení](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

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
ms.openlocfilehash: 699ae27df2423638f38a22cc17dc83b828383394
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662735"
---
# <a name="-linkresource-c-compiler-options"></a>-linkresource (možnosti kompilátoru C#)
Ve výstupním souboru vytvoří odkaz na prostředek rozhraní .NET Framework. Soubor prostředků se nepřidal do výstupního souboru. Tím se liší od [-prostředků](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) možnost, která vložit soubor prostředků do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Soubor prostředků rozhraní .NET Framework, na který chcete propojit ze sestavení.  
  
 `identifier` (volitelné)  
 Logický název prostředku. název, který se používá k načtení prostředku. Výchozí hodnota je název souboru.  
  
 `accessibility-modifier` (volitelné)  
 Dostupnost prostředku: veřejné nebo soukromé. Výchozí hodnota je veřejná.  
  
## <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení jsou propojené prostředky v sestavení veřejné při jejich vytváření pomocí kompilátoru jazyka C#. Aby se mohly prostředky privátní, zadejte `private` jako modifikátor přístupnosti. Žádný jiný modifikátor jiných než `public` nebo `private` je povolen.  
  
 **-linkresource** vyžaduje jednu z [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) možností jiných než **-target: module**.  
  
 Pokud `filename` je soubor prostředků rozhraní .NET Framework vytvořený, například podle [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, můžete přistupovat pomocí členů z <xref:System.Resources> oboru názvů. Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. U všech ostatních prostředků, použijte `GetManifestResource` metody v <xref:System.Reflection.Assembly> pro přístup k prostředku v době běhu.  
  
 Soubor zadaný v `filename` může být libovolný formát. Můžete například vytvořit nativní knihovna DLL stane součástí sestavení, takže může být nainstalováno do globální mezipaměti sestavení a získat přístup ze spravovaného kódu v sestavení. Druhá následující příklady ukazuje, jak to provést. Můžete provést totéž v Linkeru sestavení. Třetí následující příklady ukazuje, jak to provést. Další informace najdete v tématu [Al.exe (Linker sestavení)](../../../framework/tools/al-exe-assembly-linker.md) a [práce se sestaveními a s globální pamětí sestavení](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).  
  
 **-linkres** je zkratka pro **- linkresource**.  
  
 Tato možnost kompilátoru není k dispozici v sadě Visual Studio a nemůže být změněna programově.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` a odkaz na soubor prostředků `rf.resource`:  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Příklad  
 Kompilace `A.cs` do knihovny DLL, odkaz tuto knihovnu nativní knihovny DLL knihovnou n.dll a umístí výstup v globální mezipaměti sestavení (GAC). V tomto příkladu A.dll i N.dll bude nacházet v mezipaměti GAC.  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>Příklad  
 V tomto příkladu udělá to stejné jako předchozí, ale pomocí možností propojovacího programu sestavení.  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [Al.exe (linker sestavení)](../../../framework/tools/al-exe-assembly-linker.md)
- [Práce se sestaveními a s globální pamětí sestavení](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

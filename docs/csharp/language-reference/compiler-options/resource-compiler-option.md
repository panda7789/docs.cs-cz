---
title: -resource (možnosti kompilátoru C#)
ms.date: 07/20/2015
f1_keywords:
- /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
ms.openlocfilehash: e02eda66ab9fadbc7b5b042c8940096c70ef6a03
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/11/2018
ms.locfileid: "44353759"
---
# <a name="-resource-c-compiler-options"></a>-resource (možnosti kompilátoru C#)
Vloží zadaný prostředek do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Soubor prostředků rozhraní .NET Framework, který chcete vložit do výstupního souboru.  
  
 `identifier` (volitelné)  
 Logický název prostředku. název, který se používá k načtení prostředku. Výchozí hodnota je název názvu souboru.  
  
 `accessibility-modifier` (volitelné)  
 Dostupnost prostředku: veřejné nebo soukromé. Výchozí hodnota je veřejná.  
  
## <a name="remarks"></a>Poznámky  
 Použití [- linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) propojení prostředku sestavení a nelze přidat soubor prostředků do výstupního souboru.  
  
 Ve výchozím nastavení jsou prostředky v sestavení veřejné při jejich vytváření pomocí kompilátoru jazyka C#. Aby se mohly prostředky privátní, zadejte `private` jako modifikátor přístupnosti. Žádné další usnadnění jiných než `public` nebo `private` je povolen.  
  
 Pokud `filename` je soubor prostředků rozhraní .NET Framework vytvořený, například podle [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, můžete přistupovat pomocí členů z <xref:System.Resources> oboru názvů. Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. U všech ostatních prostředků, použijte `GetManifestResource` metody v <xref:System.Reflection.Assembly> pro přístup k prostředku v době běhu.  
  
 **-res** je zkratka pro **-prostředků**.  
  
 Pořadí zdrojů do výstupního souboru je určen podle pořadí zadaném v příkazovém řádku.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Přidejte soubor prostředků do vašeho projektu.  
  
2.  Vyberte soubor, který chcete vložit **Průzkumníka řešení**.  
  
3.  Vyberte **akce sestavení** souborem v **vlastnosti** okna.  
  
4.  Nastavte **akce sestavení** k **vloženého prostředku**.  
  
 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.FileProperties2.BuildAction%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` a připojte soubor prostředků `rf.resource`:  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Viz také  

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

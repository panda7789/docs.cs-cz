---
title: "-resource (možnosti kompilátoru C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 726956275436e22723bc32b98b2b8b7c7df5fb12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="resource-c-compiler-options"></a>/resource (Možnosti kompilátoru C#)
Vloží zadaný prostředek do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
/resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 Soubor prostředků rozhraní .NET Framework, který chcete vložit do výstupního souboru.  
  
 `identifier`(volitelné)  
 Logický název prostředku; název, který se používá k načtení prostředku. Výchozí hodnota je název názvu souboru.  
  
 `accessibility-modifier`(volitelné)  
 Usnadnění prostředku: veřejné nebo soukromé. Výchozí hodnota je veřejná.  
  
## <a name="remarks"></a>Poznámky  
 Použití [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) a propojit prostředku sestavení není přidejte soubor prostředků do výstupního souboru.  
  
 Ve výchozím nastavení jsou prostředky při jejich vytváření pomocí kompilátor jazyka C# veřejné v sestavení. Chcete-li prostředky privátní, zadejte `private` jako modifikátor dostupnosti. Žádné další usnadnění jinak než `public` nebo `private` je povolen.  
  
 Pokud `filename` je soubor prostředků rozhraní .NET Framework, který je vytvořen, například pomocí [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí k němu se členy v <xref:System.Resources> oboru názvů. Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. U všech ostatních prostředků, použijte `GetManifestResource` metody v <xref:System.Reflection.Assembly> třídy pro přístup k prostředku v době běhu.  
  
 **/ res** je zkratka pro **/Resource**.  
  
 Pořadí zdrojů ve výstupním souboru je určen podle pořadí zadaném v příkazovém řádku.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1.  Přidání zdrojového souboru do projektu.  
  
2.  Vyberte soubor, který chcete vložit **Průzkumníku řešení**.  
  
3.  Vyberte **akce sestavení** soubor na **vlastnosti** okno.  
  
4.  Nastavit **akce sestavení** k **vložený zdroj**.  
  
 Informace o tom, jak nastavení této možnosti kompilátoru programu najdete v tématu <xref:VSLangProj80.FileProperties2.BuildAction%2A>.  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` a připojte soubor prostředků `rf.resource`:  
  
```console  
csc /resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Viz také  
 [Možnosti kompilátoru C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

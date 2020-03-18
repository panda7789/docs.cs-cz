---
title: -resource (C# Možnosti kompilátoru)
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
ms.openlocfilehash: e14bf59f5922a918b627af22c052c8efd9081e84
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69602522"
---
# <a name="-resource-c-compiler-options"></a>-resource (C# Možnosti kompilátoru)
Vloží zadaný prostředek do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Soubor prostředků rozhraní .NET Framework, který chcete vložit do výstupního souboru.  
  
 `identifier` (volitelné)  
 Logický název prostředku; název, který se používá k načtení prostředku. Výchozí je název souboru.  
  
 `accessibility-modifier` (volitelné)  
 Dostupnost zdroje: veřejné nebo soukromé. Výchozí hodnota je veřejná.  
  
## <a name="remarks"></a>Poznámky  
 Pomocí [prostředku -link](./linkresource-compiler-option.md) můžete propojit prostředek s sestavením a nepřidávat soubor prostředků do výstupního souboru.  
  
 Ve výchozím nastavení jsou prostředky veřejné v sestavení při jejich vytvoření pomocí kompilátoru Jazyka C#. Chcete-li prostředky jako `private` modifikátor usnadnění zadat jako soukromý. Žádná jiná přístupnost než `public` nebo `private` je povolena.  
  
 Pokud `filename` je soubor prostředků rozhraní .NET Framework vytvořený například [programem Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu přistupovat pomocí členů v oboru <xref:System.Resources> názvů. Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Pro všechny ostatní prostředky `GetManifestResource` použijte <xref:System.Reflection.Assembly> metody ve třídě pro přístup k prostředku za běhu.  
  
 **-res** je krátká forma **-resource**.  
  
 Pořadí zdrojů ve výstupním souboru je určeno podle pořadí určeného na příkazovém řádku.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Přidejte do projektu soubor zdrojů.  
  
2. Vyberte soubor, který chcete vložit do **Průzkumníka řešení**.  
  
3. V okně **Vlastnosti** vyberte **Vytvořit akci** pro soubor.  
  
4. Nastavte **akci sestavení** na **vložený prostředek**.  
  
 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.FileProperties2.BuildAction%2A>kompilátoru programově, naleznete v tématu .  
  
## <a name="example"></a>Příklad  
 Kompilace `in.cs` a `rf.resource`připojení souboru prostředků :  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

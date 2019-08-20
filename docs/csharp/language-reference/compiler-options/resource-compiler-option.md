---
title: -Resource (C# možnosti kompilátoru)
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
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602522"
---
# <a name="-resource-c-compiler-options"></a>-Resource (C# možnosti kompilátoru)
Vloží zadaný prostředek do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 .NET Framework soubor prostředků, který chcete vložit do výstupního souboru.  
  
 `identifier`volitelné  
 Logický název prostředku; název, který se použije k načtení prostředku. Výchozí hodnota je název souboru.  
  
 `accessibility-modifier`volitelné  
 Přístupnost prostředku: Public nebo Private. Výchozí hodnota je Public.  
  
## <a name="remarks"></a>Poznámky  
 Použijte [-linkresource –](./linkresource-compiler-option.md) k propojení prostředku se sestavením a nepřidejte soubor prostředků do výstupního souboru.  
  
 Ve výchozím nastavení jsou prostředky v sestavení veřejné, když jsou vytvořeny pomocí C# kompilátoru. Chcete-li zajistit soukromí prostředků, `private` zadejte jako modifikátor přístupnosti. Žádná jiná přístupnost `public` `private` není povolena.  
  
 Pokud `filename` je vytvořen soubor prostředků .NET Framework, například pomocí nástroje [Resgen. exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu přistupovat <xref:System.Resources> pomocí členů v oboru názvů. Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Pro všechny ostatní prostředky použijte `GetManifestResource` metody <xref:System.Reflection.Assembly> ve třídě pro přístup k prostředku v době běhu.  
  
 **-res** je krátká forma **prostředku**.  
  
 Pořadí prostředků ve výstupním souboru je určeno z pořadí zadaného na příkazovém řádku.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Přidejte soubor prostředků do projektu.  
  
2. Vyberte soubor, který chcete vložit do **Průzkumník řešení**.  
  
3. Vyberte **akci sestavení** pro soubor v okně **vlastnosti** .  
  
4. Nastavte **akci sestavení** na **Integrovaný prostředek**.  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete <xref:VSLangProj80.FileProperties2.BuildAction%2A>v tématu.  
  
## <a name="example"></a>Příklad  
 Zkompilovat `in.cs` a připojit soubor `rf.resource`prostředků:  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

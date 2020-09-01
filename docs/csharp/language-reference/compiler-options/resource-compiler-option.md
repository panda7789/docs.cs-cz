---
description: -Resource (možnosti kompilátoru C#)
title: -Resource (možnosti kompilátoru C#)
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
ms.openlocfilehash: 963004820f56272b4f1b1d92ccc4d0a60493a4a0
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128696"
---
# <a name="-resource-c-compiler-options"></a>-Resource (možnosti kompilátoru C#)
Vloží zadaný prostředek do výstupního souboru.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 .NET Framework soubor prostředků, který chcete vložit do výstupního souboru.  
  
 `identifier` (volitelné)  
 Logický název prostředku; název, který se použije k načtení prostředku. Výchozí hodnota je název souboru.  
  
 `accessibility-modifier` (volitelné)  
 Přístupnost prostředku: Public nebo Private. Výchozí hodnota je Public.  
  
## <a name="remarks"></a>Poznámky  
 Použijte [-linkresource –](./linkresource-compiler-option.md) k propojení prostředku se sestavením a nepřidejte soubor prostředků do výstupního souboru.  
  
 Ve výchozím nastavení jsou prostředky v sestavení veřejné, když jsou vytvořeny pomocí kompilátoru jazyka C#. Chcete-li zajistit soukromí prostředků, zadejte `private` jako modifikátor přístupnosti. Žádná jiná přístupnost není `public` `private` povolena.  
  
 Pokud `filename` je vytvořen soubor prostředků .NET Framework, například [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) nebo ve vývojovém prostředí, lze k němu přistupovat pomocí členů v <xref:System.Resources> oboru názvů. Další informace naleznete v tématu <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Pro všechny ostatní prostředky použijte `GetManifestResource` metody ve <xref:System.Reflection.Assembly> třídě pro přístup k prostředku v době běhu.  
  
 **-res** je krátká forma **prostředku**.  
  
 Pořadí prostředků ve výstupním souboru je určeno z pořadí zadaného na příkazovém řádku.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Přidejte soubor prostředků do projektu.  
  
2. Vyberte soubor, který chcete vložit do **Průzkumník řešení**.  
  
3. Vyberte **akci sestavení** pro soubor v okně **vlastnosti** .  
  
4. Nastavte **akci sestavení** na **Integrovaný prostředek**.  
  
 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.FileProperties2.BuildAction%2A> .  
  
## <a name="example"></a>Příklad  
 Zkompilovat `in.cs` a připojit soubor prostředků `rf.resource` :  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

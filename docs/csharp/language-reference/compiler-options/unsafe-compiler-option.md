---
title: -unsafe (Možnosti kompilátoru Jazyka C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 146299fda103567b111c66400c17edf36addd843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "65877996"
---
# <a name="-unsafe-c-compiler-options"></a>-unsafe (Možnosti kompilátoru Jazyka C#)

Možnost **-unsafe** kompilátor umožňuje kód, který používá [nebezpečné](../keywords/unsafe.md) klíčové slovo ke kompilaci.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a>Poznámky

Další informace o nebezpečném kódu naleznete v [tématu Nebezpečný kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **Vlastnosti** projektu.  
  
2. Klikněte na stránku vlastností **Sestavení.**  
  
3. Zaškrtněte **políčko Povolit nebezpečný kód.**  
  
### <a name="to-add-this-option-in-a-csproj-file"></a>Přidání této možnosti do souboru csproj

Otevřete soubor CSProJ pro projekt a přidejte následující prvky:

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>kompilátoru programově, naleznete v tématu .  
  
## <a name="example"></a>Příklad

Kompilace `in.cs` pro nebezpečný režim:  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

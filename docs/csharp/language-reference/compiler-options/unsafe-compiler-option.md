---
title: -unsafe (možnosti kompilátoru C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 146299fda103567b111c66400c17edf36addd843
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65877996"
---
# <a name="-unsafe-c-compiler-options"></a>-unsafe (možnosti kompilátoru C#)

**-Unsafe** – možnost kompilátoru umožňuje kód, který se používá [nebezpečné](../keywords/unsafe.md) ke kompilaci klíčové slovo.  
  
## <a name="syntax"></a>Syntaxe  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a>Poznámky

Další informace o nebezpečný kód, naleznete v tématu [nezabezpečený kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete v projektu **vlastnosti** stránky.  
  
2. Klikněte na tlačítko **sestavení** stránku vlastností.  
  
3. Vyberte **povolit nezabezpečený kód** zaškrtávací políčko.  
  
### <a name="to-add-this-option-in-a-csproj-file"></a>Chcete-li přidat tuto možnost v souboru csproj

Otevřete soubor .csproj projektu a přidejte následující prvky:

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.  
  
## <a name="example"></a>Příklad

Kompilace `in.cs` pro nezabezpečeného režimu:  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

---
description: -unsafe (možnosti kompilátoru C#)
title: -unsafe (možnosti kompilátoru C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 0f6d94dd25a020d96430746c4b5e7aefd0f679da
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89140838"
---
# <a name="-unsafe-c-compiler-options"></a>-unsafe (možnosti kompilátoru C#)

Možnost kompilátoru **-unsafe** umožňuje kód, který používá klíčové slovo [unsafe](../keywords/unsafe.md) ke kompilaci.  
  
## <a name="syntax"></a>Syntax  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a>Poznámky

Další informace o nebezpečném kódu naleznete v tématu [nezabezpečený kód a ukazatele](../../programming-guide/unsafe-code-pointers/index.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru kompilátoru ve vývojovém prostředí Visual Studio  
  
1. Otevřete stránku **vlastností** projektu.  
  
2. Klikněte na stránku vlastností **Build (sestavit** ).  
  
3. Zaškrtněte políčko **Povolení nezabezpečeného kódu** .  
  
### <a name="to-add-this-option-in-a-csproj-file"></a>Přidání této možnosti do souboru csproj

Otevřete soubor. csproj pro projekt a přidejte následující prvky:

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A> .  
  
## <a name="example"></a>Příklad

Kompilovat `in.cs` pro nezabezpečený režim:  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

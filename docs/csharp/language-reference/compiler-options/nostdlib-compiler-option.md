---
title: -nostdlib (C# Compiler Options)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: cf87d8d2ac4531142288a8637f7fbeb9139382ea
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662644"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (C# Compiler Options)

**-nostdlib** brání import mscorlib.dll, která definuje obor názvů celého systému.

## <a name="syntax"></a>Syntaxe

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a>Poznámky

Tuto možnost použijte, pokud chcete definovat nebo vytvořit vlastní System – obor názvů a objekty.

Pokud nezadáte **- nostdlib**, soubor mscorlib.dll je importována do programu (stejné jako zadání **- nostdlib –**). Určení **- nostdlib** je stejné jako zadání **- nostdlib +**.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Nastavení této možnosti kompilátoru v sadě Visual Studio

> [!NOTE]
> Tyto pokyny platí pro Visual Studio 2015 (a starší verze) jenom. **Neodkazovat na mscorlib.dll** vlastnost sestavení neexistuje v sadě Visual Studio 2017.

1. Otevřít **vlastnosti** stránky pro projekt.

2. Klikněte na tlačítko **sestavení** stránku vlastností.

3. Klikněte na tlačítko **Upřesnit** tlačítko.

4. Upravit **Neodkazovat na mscorlib.dll** vlastnost.

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

Informace o tom, jak prostřednictvím kódu programu nastavení tohoto parametru kompilátoru najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)

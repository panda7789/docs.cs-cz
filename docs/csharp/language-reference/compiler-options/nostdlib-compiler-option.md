---
title: -nostdlib (C# Možnosti kompilátoru)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: ad8a2b5fc87dd7beee86d96331cf3961315be533
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75345080"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (C# Možnosti kompilátoru)

**-nostdlib** zabraňuje importu souboru mscorlib.dll, který definuje celý obor názvů System.

## <a name="syntax"></a>Syntaxe

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a>Poznámky

Tuto možnost použijte, pokud chcete definovat nebo vytvořit vlastní systémový obor názvů a objekty.

Pokud nezadáte **-nostdlib**, bude do programu importován soubor mscorlib.dll (stejně jako zadání **-nostdlib-**). Zadání **-nostdlib** je stejné jako zadání **-nostdlib+**.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Nastavení této možnosti kompilátoru v sadě Visual Studio

> [!NOTE]
> Následující pokyny platí pouze pro Visual Studio 2015 (a starší verze). Neodkazují na vlastnost sestavení **mscorlib.dll** neexistuje v novějších verzích sady Visual Studio.

1. Otevřete stránku **Vlastnosti** projektu.

2. Klikněte na stránku **Vlastnosti sestavení.**

3. Klepněte na tlačítko **Upřesnit.**

4. Upravte vlastnost **Neodkazovat na soubor mscorlib.dll.**

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

Informace o tom, jak nastavit tuto možnost <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>kompilátoru programově, naleznete v tématu .

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)

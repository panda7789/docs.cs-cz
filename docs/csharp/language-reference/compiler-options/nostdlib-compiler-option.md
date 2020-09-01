---
description: -nostdlib (možnosti kompilátoru C#)
title: -nostdlib (možnosti kompilátoru C#)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 214918b32f1f1276eb936e66daba3d372a1e9228
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125095"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (možnosti kompilátoru C#)

**-nostdlib** zabraňuje importu mscorlib.dll, který definuje celý obor názvů System.

## <a name="syntax"></a>Syntax

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a>Poznámky

Tuto možnost použijte, pokud chcete definovat nebo vytvořit vlastní obor názvů a objekty systému.

Pokud nezadáte **-nostdlib**, mscorlib.dll se do programu importuje (totéž jako určení **-nostdlib-**). Zadání **-nostdlib** je stejné jako zadání **-nostdlib +**.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Nastavení této možnosti kompilátoru v sadě Visual Studio

> [!NOTE]
> Následující pokyny platí pouze pro Visual Studio 2015 (a starší verze). Vlastnost do **Not reference mscorlib.dll** Build neexistuje v novějších verzích sady Visual Studio.

1. Otevřete stránku **vlastností** projektu.

2. Klikněte na stránku vlastností **sestavení** .

3. Klikněte na tlačítko **Upřesnit** .

4. Upravte vlastnost **do not reference mscorlib.dll** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A> .

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)

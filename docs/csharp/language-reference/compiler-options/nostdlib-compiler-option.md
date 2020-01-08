---
title: -nostdlib (C# možnosti kompilátoru)
ms.date: 12/20/2019
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: ad8a2b5fc87dd7beee86d96331cf3961315be533
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75345080"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (C# možnosti kompilátoru)

**-nostdlib** zabraňuje importu knihovny mscorlib. dll, která definuje celý obor názvů System.

## <a name="syntax"></a>Syntaxe

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a>Poznámky

Tuto možnost použijte, pokud chcete definovat nebo vytvořit vlastní obor názvů a objekty systému.

Pokud nezadáte **-nostdlib**, mscorlib. dll se naimportuje do programu (totéž jako určení **-nostdlib-** ). Zadání **-nostdlib** je stejné jako zadání **-nostdlib +** .

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Nastavení této možnosti kompilátoru v sadě Visual Studio

> [!NOTE]
> Následující pokyny platí pouze pro Visual Studio 2015 (a starší verze). V novějších verzích sady Visual Studio neexistuje vlastnost sestavení **neodkazující na knihovnu mscorlib. dll** .

1. Otevřete stránku **vlastností** projektu.

2. Klikněte na stránku vlastností **sestavení** .

3. Klikněte na tlačítko **Upřesnit** .

4. Upravte vlastnost **Neodkazovat na knihovnu mscorlib. dll** .

### <a name="to-set-this-compiler-option-programmatically"></a>Programové nastavení tohoto parametru kompilátoru

Informace o tom, jak nastavit tuto možnost kompilátoru programově, najdete v tématu <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)

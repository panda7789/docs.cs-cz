---
title: -netcf
ms.date: 03/13/2018
f1_keywords:
- /netcf
- -netcf
helpviewer_keywords:
- -netcf compiler option [Visual Basic]
- netcf compiler option [Visual Basic]
- /netcf compiler option [Visual Basic]
ms.assetid: db7cfa59-c315-401c-a59b-0daf355343d6
ms.openlocfilehash: d7c3bcba8e62d62904ed778a48d0e8ae6738ce00
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793992"
---
# <a name="-netcf"></a>-netcf

Nastaví kompilátor k cíli [!INCLUDE[Compact](~/includes/compact-md.md)].

## <a name="syntax"></a>Syntaxe

```
-netcf
```

## <a name="remarks"></a>Poznámky

`-netcf` Možnost způsobí, že kompilátor jazyka Visual Basic k cíli [!INCLUDE[Compact](~/includes/compact-md.md)] místo úplné [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]. Funkce jazyka, které je k dispozici pouze v úplném [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] je zakázaná.

`-netcf` Možnost je určena pro použití s [- sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md). Funkce jazyka zakázal `-netcf` jsou stejné funkce jazyka, není k dispozici v souborech cílem `-sdkpath`.

> [!NOTE]
> `-netcf` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku. `-netcf` Nastavena možnost při načtení projektu Visual Basic zařízení.

`-netcf` Možnost změní následující funkce jazyka:

- [End \<– klíčové slovo > příkaz](../../../visual-basic/language-reference/statements/end-keyword-statement.md) klíčové slovo ukončí provádění programu, je zakázaná. Následující program zkompiluje a spustí bez `-netcf` , ale selže v době kompilace s `-netcf`.

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- Pozdní vazba v všechny formuláře je zakázaná. Chyby při kompilaci jsou generovány, pokud nedojde k rozpoznaný scénáře pozdní vazbu. Následující program zkompiluje a spustí bez `-netcf` , ale selže v době kompilace s `-netcf`.

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- [Automaticky](../../../visual-basic/language-reference/modifiers/auto.md), [Ansi](../../../visual-basic/language-reference/modifiers/ansi.md), a [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) modifikátory jsou zakázané. Syntaxe [deklaraci příkazu](../../../visual-basic/language-reference/statements/declare-statement.md) příkaz také upraví tak `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`. Následující kód demonstruje účinek `-netcf` v kompilaci.

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- Pomocí klíčových slov jazyka Visual Basic 6.0, které byly odebrány z jazyka Visual Basic generuje různé chyby při `-netcf` se používá. Tato akce ovlivní chybové zprávy pro následující klíčová slova:

  - `Open`

  - `Close`

  - `Put`

  - `Print`

  - `Write`

  - `Input`

  - `Lock`

  - `Unlock`

  - `Seek`

  - `Width`

  - `Name`

  - `FreeFile`

  - `EOF`

  - `Loc`

  - `LOF`

  - `Line`

## <a name="example"></a>Příklad

Následující kód zkompiluje `Myfile.vb` s [!INCLUDE[Compact](~/includes/compact-md.md)], použití verze knihovny mscorlib.dll a Microsoft.VisualBasic.dll součástí výchozí instalační adresář [!INCLUDE[Compact](~/includes/compact-md.md)] na jednotce C:. Obvykle byste použili nejnovější verzi [!INCLUDE[Compact](~/includes/compact-md.md)].

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [-sdkpath](../../../visual-basic/reference/command-line-compiler/sdkpath.md)

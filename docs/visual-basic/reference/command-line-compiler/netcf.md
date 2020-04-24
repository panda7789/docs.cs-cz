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
ms.openlocfilehash: 7f14ce07a2928f4dbffd3aa57f8cdd514b75694c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75716719"
---
# <a name="-netcf"></a>-netcf

Nastaví kompilátor pro cílení na prostředí .NET Compact Framework.

## <a name="syntax"></a>Syntaxe

```console
-netcf
```

## <a name="remarks"></a>Poznámky

`-netcf` Možnost způsobí, že kompilátor Visual Basic cílí na prostředí .NET Compact Framework, nikoli na úplný .NET Framework. Funkce jazyka, které jsou k dispozici pouze v plném .NET Framework, jsou zakázány.

`-netcf` Možnost je navržena pro použití s parametrem [-SdkPath –](../../../visual-basic/reference/command-line-compiler/sdkpath.md). Funkce jazyka zakázané nástrojem `-netcf` jsou stejné funkce jazyka, které nejsou k dispozici v souborech `-sdkpath`cílících na.

> [!NOTE]
> Tato `-netcf` možnost není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku. `-netcf` Možnost je nastavena při načtení projektu Visual Basic zařízení.

`-netcf` Možnost změní následující jazykové funkce:

- Klíčové [slovo \<koncového slova> příkazu](../../../visual-basic/language-reference/statements/end-keyword-statement.md) , které ukončí provádění programu, je zakázané. Následující program zkompiluje a spustí bez `-netcf` chyby v době kompilace s. `-netcf`

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- Pozdní vazba je ve všech formulářích zakázaná. Chyby při kompilaci jsou generovány při zjištění rozpoznaných scénářů s pozdní vazbou. Následující program zkompiluje a spustí bez `-netcf` chyby v době kompilace s. `-netcf`

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- Modifikátory [auto](../../../visual-basic/language-reference/modifiers/auto.md), [ANSI](../../../visual-basic/language-reference/modifiers/ansi.md)a [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md) jsou zakázané. Syntaxe [příkazu Declare](../../../visual-basic/language-reference/statements/declare-statement.md) je také změněna na `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]`. Následující kód ukazuje účinek `-netcf` na kompilaci.

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- Pomocí klíčových slov Visual Basic 6,0 odebraných z Visual Basic vygeneruje při `-netcf` použití jinou chybu. To má vliv na chybové zprávy pro následující klíčová slova:

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

Následující kód `Myfile.vb` se zkompiluje s prostředí .NET Compact Framework pomocí verzí knihovny mscorlib. dll a Microsoft. VisualBasic. dll, která se nachází ve výchozím instalačním adresáři prostředí .NET Compact Framework na jednotce C. Obvykle byste použili nejnovější verzi prostředí .NET Compact Framework.

```console
vbc -netcf -sdkpath:"c:\Program Files\Microsoft Visual Studio .NET 2003\CompactFrameworkSDK\v1.0.5000\Windows CE " myfile.vb
```

## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [– SdkPath –](../../../visual-basic/reference/command-line-compiler/sdkpath.md)

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
ms.openlocfilehash: 16fb6b3b63c848ea6c09cc18b0fcc488670f0926
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397472"
---
# <a name="-netcf"></a>-netcf

Nastaví kompilátor pro cílení na prostředí .NET Compact Framework.

## <a name="syntax"></a>Syntaxe

```console
-netcf
```

## <a name="remarks"></a>Poznámky

`-netcf`Možnost způsobí, že kompilátor Visual Basic cílí na prostředí .NET Compact Framework, nikoli na úplný .NET Framework. Funkce jazyka, které jsou k dispozici pouze v plném .NET Framework, jsou zakázány.

`-netcf`Možnost je navržena pro použití s parametrem [-SdkPath –](sdkpath.md). Funkce jazyka zakázané nástrojem `-netcf` jsou stejné funkce jazyka, které nejsou k dispozici v souborech cílících na `-sdkpath` .

> [!NOTE]
> Tato `-netcf` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku. `-netcf`Možnost je nastavena při načtení projektu Visual Basic zařízení.

`-netcf`Možnost změní následující jazykové funkce:

- Klíčové slovo [End \<keyword> příkaz](../../language-reference/statements/end-keyword-statement.md) , který ukončí provádění programu, je zakázané. Následující program zkompiluje a spustí bez `-netcf` chyby v době kompilace s `-netcf` .

  [!code-vb[VbVbalrCompiler#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/netcf.vb#34)]

- Pozdní vazba je ve všech formulářích zakázaná. Chyby při kompilaci jsou generovány při zjištění rozpoznaných scénářů s pozdní vazbou. Následující program zkompiluje a spustí bez `-netcf` chyby v době kompilace s `-netcf` .

  [!code-vb[VbVbalrCompiler#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#35)]

- Modifikátory [auto](../../language-reference/modifiers/auto.md), [ANSI](../../language-reference/modifiers/ansi.md)a [Unicode](../../language-reference/modifiers/unicode.md) jsou zakázané. Syntaxe [příkazu Declare](../../language-reference/statements/declare-statement.md) je také změněna na `Declare Sub|Function name Lib "library" [Alias "alias"] [([arglist])]` . Následující kód ukazuje účinek `-netcf` na kompilaci.

  [!code-vb[VbVbalrCompiler#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#36)]

- Pomocí klíčových slov Visual Basic 6,0 odebraných z Visual Basic vygeneruje při použití jinou chybu `-netcf` . To má vliv na chybové zprávy pro následující klíčová slova:

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

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
- [-sdkpath](sdkpath.md)

---
title: -optioncompare
ms.date: 07/20/2015
f1_keywords:
- /optioncompare
- -optioncompare
helpviewer_keywords:
- optioncompare compiler option [Visual Basic]
- -optioncompare compiler option [Visual Basic]
- /optioncompare compiler option [Visual Basic]
ms.assetid: 7237b766-b44d-4cc5-9a3c-885348a7d9e4
ms.openlocfilehash: ac385880f8c13c23dffff67fc2a1ecc5609fd189
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72581419"
---
# <a name="-optioncompare"></a>-optioncompare

Určuje, jak se provádí porovnávání řetězců.

## <a name="syntax"></a>Syntaxe

```console
-optioncompare:{binary | text}
```

## <a name="remarks"></a>Poznámky

Můžete zadat `-optioncompare` v jednom ze dvou forem: `-optioncompare:binary` Chcete-li použít porovnávání binárních řetězců `-optioncompare:text` a použít porovnávání textových řetězců. Ve výchozím nastavení používá `-optioncompare:binary`kompilátor.

V systému Microsoft Windows aktuální znaková stránka Určuje binární pořadí řazení. Typickým binárním pořadím řazení je následující:

`A < B < E < Z < a < b < e < z < À < Ê < Ø < à < ê < ø`

Textové porovnávání řetězců je založeno na pořadí řazení textu bez rozlišování velkých a malých písmen, které určuje národní prostředí vašeho systému. Typický způsob řazení textu je následující:

`(A = a) < (À = à) < (B=b) < (E=e) < (Ê = ê) < (Z=z) < (Ø = ø)`

### <a name="to-set--optioncompare-in-the-visual-studio-ide"></a>Nastavení-OptionCompare – v integrovaném vývojovém prostředí sady Visual Studio

1. Máte projekt vybraný v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **vlastnosti**.

2. Klikněte na kartu **kompilovat** .

3. Upravte hodnotu v poli **Porovnat možnost** .

### <a name="to-set--optioncompare-programmatically"></a>Programové nastavení – OptionCompare –

Viz [příkaz Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md).

## <a name="example"></a>Příklad

Následující kód kompiluje `ProjFile.vb` a používá porovnávání binárních řetězců.

```console
vbc -optioncompare:binary projFile.vb
```

## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [– OptionExplicit –](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [– OptionStrict –](../../../visual-basic/reference/command-line-compiler/optionstrict.md)
- [– optioninfer –](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Příkaz Option Compare](../../../visual-basic/language-reference/statements/option-compare-statement.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)

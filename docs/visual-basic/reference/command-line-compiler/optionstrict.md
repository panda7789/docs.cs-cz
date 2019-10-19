---
title: -optionstrict
ms.date: 07/20/2015
f1_keywords:
- -optionstrict
helpviewer_keywords:
- -optionstrict compiler option [Visual Basic]
- optionstrict compiler option [Visual Basic]
- /optionstrict compiler option [Visual Basic]
ms.assetid: c7b10086-0fa4-49db-b3c8-4ae0db5957da
ms.openlocfilehash: 469e22aef9d746fc55e04ba884d17d60d8baa85a
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583079"
---
# <a name="-optionstrict"></a>-optionstrict

Vynutila striktní sémantiku typu pro omezení implicitních převodů typu.

## <a name="syntax"></a>Syntaxe

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a>Arguments

`+` &#124; `-`  
Volitelné. Možnost `-optionstrict+` omezuje implicitní převod typu. Výchozí hodnota pro tuto možnost je `-optionstrict-`. Možnost `-optionstrict+` je stejná jako `-optionstrict`. Pro sémantiku typu lze použít obojí.

`custom`  
Požadováno. Zobrazit upozornění, pokud není respektována striktní sémantika jazyka

## <a name="remarks"></a>Poznámky

Pokud je platný `-optionstrict+`, lze implicitně převést pouze rozšiřující převody typů. Implicitně zúžené převody typů, jako je například přiřazení objektu typu `Decimal` k objektu typu Integer, jsou hlášeny jako chyby.

Chcete-li generovat upozornění pro implicitní zužující převody typů, použijte `-optionstrict:custom`. Pomocí `-nowarn:numberlist` můžete ignorovat konkrétní upozornění a `-warnaserror:numberlist` pro považovat konkrétní upozornění za chyby.

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Nastavení-OptionStrict – v integrovaném vývojovém prostředí sady Visual Studio

1. Máte projekt vybraný v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **Vlastnosti.**

2. Klikněte na kartu **kompilovat** .

3. Upravte hodnotu v poli **Option Strict** .

### <a name="to-set--optionstrict-programmatically"></a>Programové nastavení – OptionStrict –

Viz [příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md).

## <a name="example"></a>Příklad

Následující kód zkompiluje `Test.vb` pomocí sémantiky striktního typu.

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [-optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)
- [-optionexplicit](../../../visual-basic/reference/command-line-compiler/optionexplicit.md)
- [-optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)
- [-nowarn](../../../visual-basic/reference/command-line-compiler/nowarn.md)
- [-warnaserror – (Visual Basic)](../../../visual-basic/reference/command-line-compiler/warnaserror.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Příkaz Option Strict](../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)

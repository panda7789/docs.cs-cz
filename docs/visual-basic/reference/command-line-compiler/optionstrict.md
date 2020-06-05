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
ms.openlocfilehash: 3dd12971a082869c32b6292ed45e2014b8b0e2c0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400536"
---
# <a name="-optionstrict"></a>-optionstrict

Vynutila striktní sémantiku typu pro omezení implicitních převodů typu.

## <a name="syntax"></a>Syntaxe

```console
-optionstrict[+ | -]
-optionstrict[:custom]
```

## <a name="arguments"></a>Argumenty

`+`&#124;`-`  
Nepovinný parametr. `-optionstrict+`Možnost omezuje implicitní převod typu. Výchozí hodnota pro tuto možnost je `-optionstrict-` . `-optionstrict+`Možnost je stejná jako `-optionstrict` . Pro sémantiku typu lze použít obojí.

`custom`  
Povinná hodnota. Zobrazit upozornění, pokud není respektována striktní sémantika jazyka

## <a name="remarks"></a>Poznámky

`-optionstrict+`V důsledku toho je možné implicitně převést pouze rozšiřující převody typů. Implicitně zúžené převody typů, jako je například přiřazení `Decimal` objektu typu k objektu typu Integer, jsou hlášeny jako chyby.

Chcete-li generovat upozornění pro implicitní zužující převody typů, použijte `-optionstrict:custom` . Slouží `-nowarn:numberlist` k ignorování konkrétních upozornění a `-warnaserror:numberlist` k považovat konkrétní upozornění za chyby.

### <a name="to-set--optionstrict-in-the-visual-studio-ide"></a>Nastavení-OptionStrict – v integrovaném vývojovém prostředí sady Visual Studio

1. Máte projekt vybraný v **Průzkumník řešení**. V nabídce **projekt** klikněte na příkaz **Vlastnosti.**

2. Klikněte na kartu **kompilovat** .

3. Upravte hodnotu v poli **Option Strict** .

### <a name="to-set--optionstrict-programmatically"></a>Programové nastavení – OptionStrict –

Viz [příkaz Option Strict](../../language-reference/statements/option-strict-statement.md).

## <a name="example"></a>Příklad

Následující kód je zkompilován `Test.vb` pomocí sémantiky striktního typu.

```console
vbc -optionstrict+ test.vb
```

## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [-optioncompare](optioncompare.md)
- [-optionexplicit](optionexplicit.md)
- [-optioninfer](optioninfer.md)
- [-nowarn](nowarn.md)
- [-warnaserror – (Visual Basic)](warnaserror.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)
- [Option Strict – příkaz](../../language-reference/statements/option-strict-statement.md)
- [Výchozí hodnoty pro Visual Basic, Projekty, dialogové okno Možnosti](/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)

---
title: -quiet
ms.date: 07/20/2015
f1_keywords:
- -quiet
- quiet
helpviewer_keywords:
- -quiet compiler option [Visual Basic]
- /quiet compiler option [Visual Basic]
- quiet compiler option [Visual Basic]
ms.assetid: 5d77fa23-4c50-4708-8535-649912b098e8
ms.openlocfilehash: a22773e2e37eb60ab6f1e88305266f41764311e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61788840"
---
# <a name="-quiet"></a>-quiet

Zabrání zobrazení kódu pro syntaxi související chyby a upozornění kompilátoru.

## <a name="syntax"></a>Syntaxe

```
-quiet
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení `-quiet` není platná. Pokud kompilátor ohlásí syntaxe související chyby nebo upozornění, také výstup řádku ze zdrojového kódu. U aplikací, které parsovat výstup kompilátoru může být vhodnější pro kompilátor výstup jenom text diagnostiky.

V následujícím příkladu `Module1` výstupy chybu, která obsahuje zdrojový kód při kompilaci bez `-quiet`.

```vb
Module Module1
    Sub Main()
        x()
    End Sub
End Module
```

Výstup:

```console
C:\projects\vb2.vb(3) : error BC30451: 'x' is not declared. It may be inaccessible due to its protection level.

        x()
        ~
```

Zkompilované s `-quiet`, kompilátor uloží jenom následující:

```
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> `-quiet` Možnost není k dispozici v rámci vývojového prostředí sady Visual Studio; je k dispozici jenom při kompilaci z příkazového řádku.

## <a name="example"></a>Příklad

Následující kód zkompiluje `T2.vb` a nezobrazuje kód pro diagnostiku kompilátoru související syntaxi:

```
vbc -quiet t2.vb
```

## <a name="see-also"></a>Viz také:

- [Visual Basic Command-Line Compiler](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

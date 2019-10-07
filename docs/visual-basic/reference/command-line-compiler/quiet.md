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
ms.openlocfilehash: 6e773c60469e8426956c92a5aa377741ba5af4d3
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005280"
---
# <a name="-quiet"></a>-quiet

Zabraňuje kompilátoru v zobrazení kódu pro chyby a upozornění související se syntaxí.

## <a name="syntax"></a>Syntaxe

```console
-quiet
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení není `-quiet` v platnosti. Když kompilátor ohlásí chybu nebo upozornění související se syntaxí, vypíše také řádek ze zdrojového kódu. Pro aplikace, které analyzují výstup kompilátoru, může být vhodnější, aby kompilátor vyoutput pouze text diagnostiky.

V následujícím příkladu `Module1` výstupy chyby, která obsahuje zdrojový kód při kompilaci bez `-quiet`.

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

Kompilováno s `-quiet`, kompilátor výstupuje pouze následující:

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> Možnost `-quiet` není k dispozici ve vývojovém prostředí sady Visual Studio; je k dispozici pouze při kompilaci z příkazového řádku.

## <a name="example"></a>Příklad

Následující kód zkompiluje `T2.vb` a nezobrazuje kód pro diagnostiku kompilátoru související s syntaxí:

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a>Viz také:

- [Visual Basic Kompilátor příkazového řádku](../../../visual-basic/reference/command-line-compiler/index.md)
- [Příkazové řádky ukázkové kompilace](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)

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
ms.openlocfilehash: f894ed6a778e026ffd3976a63fe3b677eb6a9557
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400523"
---
# <a name="-quiet"></a>-quiet

Zabraňuje kompilátoru v zobrazení kódu pro chyby a upozornění související se syntaxí.

## <a name="syntax"></a>Syntaxe

```console
-quiet
```

## <a name="remarks"></a>Poznámky

Ve výchozím nastavení `-quiet` není platná. Když kompilátor ohlásí chybu nebo upozornění související se syntaxí, vypíše také řádek ze zdrojového kódu. Pro aplikace, které analyzují výstup kompilátoru, může být vhodnější, aby kompilátor vyoutput pouze text diagnostiky.

V následujícím příkladu `Module1` výstup obsahuje chybu, která zahrnuje zdrojový kód, pokud je zkompilován bez `-quiet` .

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

Kompilováno s `-quiet` , kompilátor výstupuje pouze následující:

```console
E:\test\t2.vb(3) : error BC30451: Name 'x' is not declared.
```

> [!NOTE]
> Tato `-quiet` možnost není k dispozici ve vývojovém prostředí sady Visual Studio. je k dispozici pouze při kompilaci z příkazového řádku.

## <a name="example"></a>Příklad

Následující kód zkompiluje `T2.vb` a nezobrazuje kód pro diagnostiku kompilátoru související s syntaxí:

```console
vbc -quiet t2.vb
```

## <a name="see-also"></a>Viz také

- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)

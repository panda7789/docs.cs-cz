---
description: -pathmap (možnosti kompilátoru C#)
title: -pathmap (možnosti kompilátoru C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 707a37c6946cfcaf429552f0aeece6b87f3ad71d
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125004"
---
# <a name="-pathmap-c-compiler-options"></a>-pathmap (možnosti kompilátoru C#)

Možnost kompilátoru **-pathmap** určuje, jak namapovat fyzické cesty na výstup názvů zdrojových cest kompilátorem.

## <a name="syntax"></a>Syntaxe

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>Argumenty

 `path1` Úplná cesta ke zdrojovým souborům v aktuálním prostředí

 `sourcePath1` Cesta ke zdroji nahrazena pro `path1` všechny výstupní soubory.

Chcete-li zadat více mapovaných zdrojových cest, oddělte je čárkami.

## <a name="remarks"></a>Poznámky

Kompilátor zapíše zdrojovou cestu do výstupu z následujících důvodů:

1. Zdrojová cesta je nahrazena argumentem, pokud <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> je použita na volitelný parametr.
1. Zdrojová cesta je vložena do souboru PDB.
1. Cesta k souboru PDB je vložena do souboru PE (přenositelného spustitelného souboru).

Tato možnost mapuje každou fyzickou cestu v počítači, kde je kompilátor spuštěn, na odpovídající cestu, která by měla být zapsána do výstupních souborů.

## <a name="example"></a>Příklad

Zkompilujte `t.cs` v adresáři **C: \\ pracovní \\ testy** a namapujte tento adresář na **\publish** ve výstupu:

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

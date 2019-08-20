---
title: -pathmap (C# možnosti kompilátoru)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 48e96d2ec2ccbea83d573c0eb3630b1591c407a9
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606623"
---
# <a name="-pathmap-c-compiler-options"></a>-pathmap (C# možnosti kompilátoru)

Možnost kompilátoru **-pathmap** určuje, jak namapovat fyzické cesty na výstup názvů zdrojových cest kompilátorem.

## <a name="syntax"></a>Syntaxe

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>Arguments

 `path1`Úplná cesta ke zdrojovým souborům v aktuálním prostředí

 `sourcePath1`Cesta ke zdroji nahrazena pro `path1` všechny výstupní soubory.

Chcete-li zadat více mapovaných zdrojových cest, oddělte je čárkami.

## <a name="remarks"></a>Poznámky

Kompilátor zapíše zdrojovou cestu do výstupu z následujících důvodů:

1. Zdrojová cesta je nahrazena argumentem, pokud <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> je použita na volitelný parametr.
1. Zdrojová cesta je vložena do souboru PDB.
1. Cesta k souboru PDB je vložena do souboru PE (přenositelného spustitelného souboru).

Tato možnost mapuje každou fyzickou cestu v počítači, kde je kompilátor spuštěn, na odpovídající cestu, která by měla být zapsána do výstupních souborů.

## <a name="example"></a>Příklad

Zkompilujte `t.cs` v adresáři **C:\\\\pracovní testy** a namapujte tento adresář na **\publish** ve výstupu:

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

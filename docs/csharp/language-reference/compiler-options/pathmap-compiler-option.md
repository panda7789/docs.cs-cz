---
title: -pathmap (možnosti kompilátoru C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 063cee694e8367a86fead2f1258c3cbda5ab7018
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61662592"
---
# <a name="-pathmap-c-compiler-options"></a>-pathmap (možnosti kompilátoru C#)

**- Pathmap** – možnost kompilátoru určuje způsob mapování fyzické cesty do zdrojové cesty názvy výstupu kompilátorem.

## <a name="syntax"></a>Syntaxe

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>Arguments

 `path1` Úplná cesta ke zdrojovým souborům v aktuálním prostředí

 `sourcePath1` Zdrojová cesta nahrazené za `path1` v všechny výstupní soubory.

Chcete-li určit víc cest připojené zdroje, oddělte každou čárkou.

## <a name="remarks"></a>Poznámky

Kompilátor zapíše zdrojovou cestu do jeho výstup z následujících důvodů:

1. Zdrojová cesta je nahrazen pro argument při <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> platí pro volitelný parametr.
1. Zdrojová cesta se vloží do souboru PDB.
1. Cesta k souboru PDB se vloží do souboru PE (portable executable).

Tato možnost mapuje každý fyzickou cestu na počítači, ve kterém kompilátor spuštěná na odpovídající cestu, která by měly být napsány v výstupní soubory.

## <a name="example"></a>Příklad

Kompilace `t.cs` v adresáři **C:\\fungovat\\testy** a mapování tomuto adresáři **\publish** ve výstupu:

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>Viz také:

- [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

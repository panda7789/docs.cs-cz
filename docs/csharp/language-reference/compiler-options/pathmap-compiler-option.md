---
title: -pathmap (možnosti kompilátoru C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 36196ffea19cfde7ff5f830ea358d2bd83edf419
ms.sourcegitcommit: 77d9a94dac4c05827ed0663d95e0f9ad35d6682e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/24/2018
---
# <a name="-pathmap-c-compiler-options"></a>-pathmap (možnosti kompilátoru C#)

**- Pathmap** – možnost kompilátoru určuje způsob namapování fyzické cesty k umístění zdroje cesta názvy výstupu kompilátorem.

## <a name="syntax"></a>Syntaxe

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>Arguments

 `path1` Úplná cesta ke zdrojovým souborům v aktuálním prostředí

 `sourcePath1` Zdrojová cesta nahrazena pro `path1` v jakékoli výstupní soubory.

Chcete-li určit víc cest namapované zdroje, oddělte každý oddělujte čárkami.

## <a name="remarks"></a>Poznámky

Kompilátor zapisuje zdrojovou cestu cestu do jeho výstup z následujících důvodů:

1. Zdrojová cesta je nahrazena pro argument při <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> se použije na volitelný parametr.
1. Zdrojová cesta je vložen do souboru PDB.
1. Cestu k souboru PDB vložené do souboru PE (přenosné spustitelný soubor).

Tato možnost mapuje každou fyzickou cestu v počítači, kde probíhá odpovídající cestu, která budou zasílány výstupní soubory kompilátoru.

## <a name="example"></a>Příklad

Kompilace `t.cs` v adresáři **C:\\pracovní\\testy** a mapovat tomuto adresáři svěřuje **\publish** ve výstupu:

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>Viz také

 [Možnosti kompilátoru jazyka C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

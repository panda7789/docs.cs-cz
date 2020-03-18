---
title: -pathmap (Možnosti kompilátoru Jazyka C#)
ms.date: 05/16/2018
f1_keywords:
- /pathmap
helpviewer_keywords:
- -pathmap compiler option [C#]
- pathmap compiler option [C#]
- /pathmap compiler option [C#]
ms.openlocfilehash: 48e96d2ec2ccbea83d573c0eb3630b1591c407a9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69606623"
---
# <a name="-pathmap-c-compiler-options"></a>-pathmap (Možnosti kompilátoru Jazyka C#)

Volba kompilátoru **-pathmap** určuje, jak mapovat fyzické cesty na zdrojové názvy cest, které kompilátor vyvodí.

## <a name="syntax"></a>Syntaxe

```console
-pathmap:path1=sourcePath1,path2=sourcePath2
```

## <a name="arguments"></a>Argumenty

 `path1`Úplná cesta ke zdrojovým souborům v aktuálním prostředí

 `sourcePath1`Zdrojová cesta nahrazená `path1` ve všech výstupních souborech.

Chcete-li určit více mapovaných zdrojových cest, oddělte je čárkou.

## <a name="remarks"></a>Poznámky

Kompilátor zapíše zdrojovou cestu do výstupu z následujících důvodů:

1. Zdrojová cesta je nahrazena argumentem, <xref:System.Runtime.CompilerServices.CallerFilePathAttribute> pokud je použit a volitelný parametr.
1. Zdrojová cesta je vložena do souboru PDB.
1. Cesta k souboru PDB je vložena do souboru PE (přenosný spustitelný) soubor.

Tato možnost mapuje každou fyzickou cestu v počítači, kde kompilátor běží na odpovídající cestu, která by měla být zapsána ve výstupních souborech.

## <a name="example"></a>Příklad

Kompilace `t.cs` v adresáři **C:\\pracovní\\testy** a mapování tohoto adresáře na **\publish** ve výstupu:

```console
csc -pathmap:C:\work\tests=\publish t.cs
```

## <a name="see-also"></a>Viz také

- [Možnosti kompilátoru jazyka C#](./index.md)
- [Správa vlastností projektů a řešení](/visualstudio/ide/managing-project-and-solution-properties)

---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: c11d83ff37da41faa3dc6b66a87e2c52c5f6c7ac
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582876"
---
# <a name="-refout-visual-basic"></a>-refout (Visual Basic)

Možnost **-refout** Určuje cestu k souboru, kde by měl být výstup referenčního sestavení.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Syntaxe

```console
-refout:filepath
```

## <a name="arguments"></a>Arguments

`filepath`  
Cesta a název souboru referenčního sestavení. Obvykle by měla být v podsložce primárního sestavení. Doporučená konvence (používaná nástrojem MSBuild) slouží k umístění referenčního sestavení do podsložky ref/v relativní vzhledem k primárnímu sestavení. Musí existovat všechny složky v `filepath`. kompilátor je nevytváří.

## <a name="remarks"></a>Poznámky

Visual Basic podporuje přepínač `-refout` počínaje verzí 15,3.

Referenční sestavení jsou pouze metadata sestavení, která obsahují metadata, ale nemají kód implementace. Zahrnují informace o typu a členu pro vše kromě anonymních typů. Jejich těla metod jsou nahrazeny jediným příkazem `throw null`. Důvodem použití `throw null` tělo metody (na rozdíl od žádného těla) je, aby bylo možné spustit a předat nástroj PEverify (čímž se ověří úplnost metadat).

Referenční sestavení obsahují atribut [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) na úrovni sestavení. Tento atribut může být zadán ve zdroji (pak ho kompilátor nebude muset syntetizovat). Z důvodu tohoto atributu modul runtime odmítne načíst referenční sestavení ke spuštění (ale mohou být i nadále načteny v kontextu pouze pro reflexi). Nástroje, které reflektují sestavení, musí zajistit, aby načetly referenční sestavení pouze pro reflexi. v opačném případě modul runtime vyvolá <xref:System.BadImageFormatException>.

Možnosti `-refout` a [`-refonly`](refonly-compiler-option.md) se vzájemně vylučují.

## <a name="see-also"></a>Viz také:

- [-refonly](refonly-compiler-option.md)
- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)

---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- /refout
helpviewer_keywords:
- refout compiler option [Visual Basic]
- /refout compiler option [Visual Basic]
- -refout compiler option [Visual Basic]
ms.openlocfilehash: 552e611f222bfcc3ce12520ecdb891fd7b8b21de
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72775552"
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

Referenční sestavení jsou speciálním typem sestavení, který obsahuje pouze minimální velikost metadat, která je vyžadována pro reprezentaci veřejného povrchu rozhraní API knihovny. Zahrnují deklarace pro všechny členy, které jsou významné při odkazování na sestavení v nástrojích sestavení, ale vyloučí všechny implementace členů a deklarace privátních členů, které nemají žádný pozor na jejich kontrakty rozhraní API. Další informace najdete v tématu [referenční sestavení](../../../standard/assembly/reference-assemblies.md) v příručce .NET.

Možnosti `-refout` a [`-refonly`](refonly-compiler-option.md) se vzájemně vylučují.

## <a name="see-also"></a>Viz také:

- [-refonly](refonly-compiler-option.md)
- [Visual Basic Kompilátor příkazového řádku](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)

---
title: -refonly
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
ms.openlocfilehash: b906178abf8d159083d95e41448596d512e857de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348578"
---
# <a name="-refonly-visual-basic"></a>-refonly (Visual Basic)

The **-refonly** option indicates that the primary output of the compilation should be a reference assembly instead of an implementation assembly. The `-refonly` parameter silently disables outputting PDBs, as reference assemblies cannot be executed.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Syntaxe

```console
-refonly
```

## <a name="remarks"></a>Poznámky

Visual Basic supports the `-refonly` switch starting with version 15.3.

Reference assemblies are a special type of assembly that contain only the minimum amount of metadata required to represent the library's public API surface. They include declarations for all members that are significant when referencing an assembly in build tools, but exclude all member implementations and declarations of private members that have no observable impact on their API contract. For more information, see [Reference assemblies](../../../standard/assembly/reference-assemblies.md) in .NET Guide.

The `-refonly` and [`-refout`](refout-compiler-option.md) options are mutually exclusive.

## <a name="see-also"></a>Viz také:

- [-refout](refout-compiler-option.md)
- [Visual Basic Command-Line Compiler](index.md)
- [Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)

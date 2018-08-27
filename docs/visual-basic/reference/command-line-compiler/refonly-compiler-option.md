---
title: -refout (Visual Basic)
ms.date: 03/16/2018
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e8f6c15084ac9b1a07aef8a0311edfcc4a93337c
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932660"
---
# <a name="-refonly-visual-basic"></a>-refout (Visual Basic)

**- Refout** možnost znamená, že primární výstup tohoto sestavení by měl být referenční sestavení místo sestavení implementace. `-refonly` Parametr tiše zakáže generování souborů pdb, jako referenční sestavení nelze spustit.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Syntaxe

```console
-refonly
```

## <a name="remarks"></a>Poznámky

Visual Basic podporuje `-refout` přepnout od verze 15.3.

Referenční sestavení jsou pouze metadata sestavení, která obsahují metadata, ale žádný implementační kód. Patří mezi ně typů a členů informace pro všechno, co s výjimkou anonymních typů. Důvod pro použití `throw null` subjektů (na rozdíl od bez těla) je tak, aby PEVerify může spuštění a předání (tedy ověřování úplnost metadata).

Zahrnout odkaz na sestavení úrovni sestavení [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atribut. Tento atribut může být zadaný ve zdroji (a kompilátor nebude nutné tak, aby odpovídaly ho). Z důvodu tohoto atributu moduly runtime odmítne načíst referenční sestavení pro spuštění (ale stále může být načteny v kontextu pouze pro reflexi). Nástroje, které odpovídají na sestavení se muset ujistit, že se načítají referenční sestavení jako pouze pro reflexi; v opačném případě modul runtime vyvolá <xref:System.BadImageFormatException>.

`-refonly` a [ `-refout` ](refout-compiler-option.md) možnosti se vzájemně vylučují.

## <a name="see-also"></a>Viz také:
[-refout](refout-compiler-option.md)   
[Kompilátor příkazového řádku jazyka Visual Basic](index.md)  
[Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)   

---
title: -refonly (Visual Basic)
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
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-refonly-visual-basic"></a>-refonly (Visual Basic)

**- Refonly** možnost znamená, že primární výstup kompilace by měl být referenční sestavení místo implementace sestavení. `-refonly` Parametr bezobslužně zakáže výstup vytvořeného soubory PDB, jako referenční sestavení nelze provést.

[!INCLUDE[compiler-options](~/includes/compiler-options.md)]

## <a name="syntax"></a>Syntaxe

```console
-refonly
```

## <a name="remarks"></a>Poznámky

Podporuje jazyka Visual Basic `-refout` přepínače, počínaje verzí 15.3.

Referenční sestavení jsou pouze metadata sestavení, které obsahují metadata, ale žádný kód implementace. Obsahují informace o typu a členu pro všechno kromě anonymní typy. Důvod použití `throw null` těla (na rozdíl od žádné těla) je, aby PEVerify může spouštět a předat (tedy ověření úplnost metadat).

Zahrnout odkaz na sestavení úrovni sestavení [ReferenceAssembly](xref:System.Runtime.CompilerServices.ReferenceAssemblyAttribute) atribut. Tento atribut je možné zadat zdroj (pak kompilátor nebudete muset syntetizace ji). Z důvodu tohoto atributu moduly runtime odmítne načíst odkaz na sestavení pro spuštění (ale stále může být načteno do kontextu pouze pro reflexi). Nástroje, které odráží sestavení potřeba zajistit, že se načíst odkaz na sestavení jako pouze pro reflexi; jinak, modul runtime vyvolá <xref:System.BadImageFormatException>.

`-refonly` a [ `-refout` ](refout-compiler-option.md) možnosti se vzájemně vylučují.

## <a name="see-also"></a>Viz také
[-refout](refout-compiler-option.md)   
[Visual Basic – kompilátor příkazového řádku](index.md)  
[Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)   

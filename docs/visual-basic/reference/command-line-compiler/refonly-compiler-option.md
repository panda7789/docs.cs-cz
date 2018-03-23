---
title: -refonly (Visual Basic)
ms.date: 03/16/2018
ms.prod: .net
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- -refonly
helpviewer_keywords:
- /refonly compiler option [Visual Basic]
- -refonly compiler option [Visual Basic]
- refonly compiler option [Visual Basic]
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f5135ef4d33ddde27416e48c28425aa5b029237b
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/23/2018
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
[Visual Basic Command-Line Compiler](index.md)  
[Příkazové řádky ukázkové kompilace](sample-compilation-command-lines.md)   

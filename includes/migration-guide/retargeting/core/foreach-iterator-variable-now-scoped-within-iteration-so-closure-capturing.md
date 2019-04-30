---
ms.openlocfilehash: 1805c26f1eff46719f30de8a14ca6d35f01948a6
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61639450"
---
### <a name="foreach-iterator-variable-is-now-scoped-within-the-iteration-so-closure-capturing-semantics-are-different-in-c5"></a>Iterační proměnná foreach je nyní vymezeno v rámci iterace, tak, aby byly zachytávající sémantiku uzavření jiný (v jazyce C# 5)

|   |   |
|---|---|
|Podrobnosti|Od verze C# 5 (Visual Studio 2012) <code>foreach</code> oborem iterační proměnné v rámci iterace. To může způsobit přerušení, pokud kód byl dříve v závislosti na tom proměnné tak nebudou zahrnuty do <code>foreach</code>na ukončení. Příznak této změny je, že proměnná iterátoru předat delegáta je považován za se vytvoří hodnota má v době delegáta, nikoli hodnotu, kterou má v době, kdy je vyvolán delegát.|
|Doporučení|V ideálním případě by měl kód aktualizovat očekávat nové chování kompilátoru. Pokud původní sémantiku, iterační proměnná, lze nahradit zvláštní proměnná, která je explicitně umístěn mimo obor smyčky.|
|Rozsah|Hlavní|
|Version|4.5|
|Type|Změna cílení|

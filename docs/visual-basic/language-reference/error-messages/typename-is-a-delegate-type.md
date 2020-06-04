---
title: "'<typename>' je typ delegátu."
ms.date: 07/20/2015
f1_keywords:
- bc32008
- vbc32008
helpviewer_keywords:
- BC32008
ms.assetid: dc6abba0-a9ad-450f-8899-87265bc84abc
ms.openlocfilehash: 7056bbf2b4de26feba3bfbe0e02b3239311271c9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84382169"
---
# <a name="typename-is-a-delegate-type"></a>'\<typename>' je typ delegátu.
\<typename>je typ delegáta. Konstrukce delegáta povoluje jako seznam argumentů pouze jeden výraz AddressOf. Výraz AddressOf se často dá použít místo konstrukce delegáta.  
  
 `New`Klauzule vytvářející instanci třídy delegáta poskytuje neplatný seznam argumentů konstruktoru delegáta.  
  
 `AddressOf`Při vytváření nové instance delegáta můžete zadávat jenom jeden výraz.  
  
 Tato chyba může být způsobena tím, že nepředáte žádné argumenty konstruktoru delegáta, Pokud předáte více než jeden argument, nebo Pokud předáte jeden argument, který není platným `AddressOf` výrazem.  
  
 **ID chyby:** BC32008  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- `AddressOf`V seznamu argumentů pro třídu Delegate v klauzuli použijte jeden výraz `New` .  
  
## <a name="see-also"></a>Viz také

- [New – operátor](../operators/new-operator.md)
- [AddressOf – operátor](../operators/addressof-operator.md)
- [Delegáti](../../programming-guide/language-features/delegates/index.md)
- [Postupy: Volání metody delegáta](../../programming-guide/language-features/delegates/how-to-invoke-a-delegate-method.md)

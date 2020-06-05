---
title: Argumenty typu nelze odvodit z delegáta.
ms.date: 07/20/2015
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords:
- BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
ms.openlocfilehash: f29e92c8245e33c0418d9a387070b03f645c331e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84362745"
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>Argumenty typu nelze odvodit z delegáta.
Příkaz přiřazení používá `AddressOf` k přiřazení adresy obecného postupu delegátovi, ale neposkytuje žádné argumenty typu pro obecný postup.  
  
 Při vyvolání obecného typu obvykle zadáte argument typu pro každý parametr typu, který definuje obecný typ. Pokud nezadáte žádné argumenty typu, kompilátor se pokusí odvodit typy, které mají být předány do parametrů typu. Pokud kontext neposkytne dostatek informací pro kompilátor k odvození typů, je vygenerována chyba.  
  
 **ID chyby:** BC36564  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Zadejte argumenty typu pro obecný postup ve `AddressOf` výrazu.  
  
## <a name="see-also"></a>Viz také

- [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [AddressOf – operátor](../operators/addressof-operator.md)
- [Obecné procedury v jazyce Visual Basic](../../programming-guide/language-features/data-types/generic-procedures.md)
- [Seznam typů](../statements/type-list.md)
- [Metody rozšíření](../../programming-guide/language-features/procedures/extension-methods.md)

---
title: Klíčové slovo '<keyword>' je platné pouze v rámci metody instance.
ms.date: 07/20/2015
f1_keywords:
- bc30043
- vbc30043
helpviewer_keywords:
- BC30043
ms.assetid: 7973aa82-a681-440c-9bca-242627d7ba86
ms.openlocfilehash: 537689405ea30bdd7c075320eba58a8723a93cdb
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397399"
---
# <a name="keyword-is-valid-only-within-an-instance-method"></a>Klíčové slovo '\<keyword>' je platné pouze v rámci metody instance.
`Me` `MyClass` `MyBase` Klíčová slova, a odkazují na konkrétní instance třídy. Nemůžete je použít uvnitř sdíleného `Function` nebo `Sub` procedury.  
  
 **ID chyby:** BC30043  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Odeberte klíčové slovo z procedury nebo odeberte `Shared` klíčové slovo z deklarace procedury.  
  
## <a name="see-also"></a>Viz také

- [Přiřazení proměnné objektu](../../programming-guide/language-features/variables/object-variable-assignment.md)
- [Me, My, MyBase a MyClass](../../programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Základní informace o dědičnosti](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)

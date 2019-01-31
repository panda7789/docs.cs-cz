---
title: <type1> <typename> musí implementovat člena <membername> pro rozhraní <interfacename>.
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: de7dd9026e08495941a89be0db11ad4c68d2a748
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264229"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<Type1 >'\<typename >' musí implementovat '\<membername > "rozhraní"\<interfacename > "
"\<typename >' musí implementovat '\<membername >" rozhraní "\<interfacename >'. Implementující vlastnost musí mít odpovídající 'ReadOnly' / specifikátory 'Jen pro zápis'.  
  
 Třída nebo struktura, deklarací identity pro implementaci rozhraní, ale neimplementuje proceduru, vlastnost nebo událost definované rozhraní. Musíte implementovat každého člena rozhraní.  
  
 **ID chyby:** BC30154  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Deklarujte člena se stejným názvem a signaturou, jak jsou definovány v rozhraní. Nezapomeňte uvést alespoň `End Function`, `End Sub`, nebo `End Property` příkazu.  
  
2.  Přidat `Implements` klauzuli na konec objektu `Function`, `Sub`, `Property`, nebo `Event` příkazu. Příklad:  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  Při implementaci vlastnost, ujistěte se, že `ReadOnly` nebo `WriteOnly` se používá stejným způsobem jako v definici rozhraní.  
  
4.  Při implementaci vlastnost, deklarujte `Get` a `Set` postupy, podle potřeby.  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

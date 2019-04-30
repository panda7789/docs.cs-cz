---
title: <type1>"<typename>musí implementovat<membername>'pro rozhraní'<interfacename>.
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 86b0d46e0e27b2fd8d1fccb37f4a3c45e95f5f63
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61792090"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<Type1 >'\<typename >' musí implementovat '\<membername > "rozhraní"\<interfacename > "
"\<typename >' musí implementovat '\<membername >" rozhraní "\<interfacename >'. Implementující vlastnost musí mít odpovídající 'ReadOnly' / specifikátory 'Jen pro zápis'.  
  
 Třída nebo struktura, deklarací identity pro implementaci rozhraní, ale neimplementuje proceduru, vlastnost nebo událost definované rozhraní. Musíte implementovat každého člena rozhraní.  
  
 **ID chyby:** BC30154  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Deklarujte člena se stejným názvem a signaturou, jak jsou definovány v rozhraní. Nezapomeňte uvést alespoň `End Function`, `End Sub`, nebo `End Property` příkazu.  
  
2. Přidat `Implements` klauzuli na konec objektu `Function`, `Sub`, `Property`, nebo `Event` příkazu. Příklad:  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. Při implementaci vlastnost, ujistěte se, že `ReadOnly` nebo `WriteOnly` se používá stejným způsobem jako v definici rozhraní.  
  
4. Při implementaci vlastnost, deklarujte `Get` a `Set` postupy, podle potřeby.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

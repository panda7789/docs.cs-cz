---
title: <type1>"<typename>musí implementovat<methodname>'pro rozhraní'<interfacename>.
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 432f089bc77928308820d7456d930fba8dc513f7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59304906"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<Type1 >'\<typename >' musí implementovat '\<methodname > "rozhraní"\<interfacename > "
Třída nebo struktura, deklarací identity pro implementaci rozhraní, ale neimplementuje postupu definované rozhraní. Musíte implementovat každého člena rozhraní.  
  
 **ID chyby:** BC30149  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Procedura se stejným názvem a signaturou, jak jsou definovány v rozhraní deklarujte. Nezapomeňte uvést alespoň `End Function` nebo `End Sub` příkazu.  
  
2. Přidat `Implements` klauzuli na konec objektu `Function` nebo `Sub` příkazu. Příklad:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

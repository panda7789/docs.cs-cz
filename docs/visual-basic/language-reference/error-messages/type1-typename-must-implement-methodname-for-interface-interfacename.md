---
title: <type1> <typename> musí implementovat člena <methodname> pro rozhraní <interfacename>.
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: c5dd7c6889a3fb5344142ee9914f98e8922d748b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55264428"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<Type1 >'\<typename >' musí implementovat '\<methodname > "rozhraní"\<interfacename > "
Třída nebo struktura, deklarací identity pro implementaci rozhraní, ale neimplementuje postupu definované rozhraní. Musíte implementovat každého člena rozhraní.  
  
 **ID chyby:** BC30149  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Procedura se stejným názvem a signaturou, jak jsou definovány v rozhraní deklarujte. Nezapomeňte uvést alespoň `End Function` nebo `End Sub` příkazu.  
  
2.  Přidat `Implements` klauzuli na konec objektu `Function` nebo `Sub` příkazu. Příklad:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

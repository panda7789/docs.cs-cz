---
title: <type1>'<typename>' musí implementovat '<membername>' pro rozhraní '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 4ffe18e11c388a8c69ef0592bde1b78f5b219680
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84386851"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1>'\<typename>' musí implementovat '\<membername>' pro rozhraní '\<interfacename>'
' \<typename> ' musí implementovat ' \<membername> ' pro rozhraní ' \<interfacename> '. Implementující vlastnost musí mít párové specifikátory ReadOnly a WriteOnly.  
  
 Deklarace třídy nebo struktury pro implementaci rozhraní, ale neimplementuje proceduru, vlastnost nebo událost definovanou rozhraním. Je nutné implementovat všechny členy rozhraní.  
  
 **ID chyby:** BC30154  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Deklarujete člena se stejným názvem a signaturou, jak je definováno v rozhraní. Nezapomeňte zahrnout alespoň `End Function` `End Sub` příkaz, nebo `End Property` .  
  
2. Přidejte `Implements` klauzuli na konec `Function` `Sub` příkazu,, `Property` nebo `Event` . Příklad:  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. Při implementaci vlastnosti se ujistěte, že `ReadOnly` nebo `WriteOnly` je použita stejným způsobem jako v definici rozhraní.  
  
4. Při implementaci vlastnosti, deklarujte `Get` a `Set` procedury podle potřeby.  
  
## <a name="see-also"></a>Viz také

- [Implements – Příkaz](../statements/implements-statement.md)
- [Rozhraní](../../programming-guide/language-features/interfaces/index.md)

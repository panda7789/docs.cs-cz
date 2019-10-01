---
title: <type1>'<typename>' musí implementovat '<membername>' pro rozhraní '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: a824b66eaad964049ced5cae5eb2cc370d00ba7f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71696898"
---
# <a name="type1typename-must-implement-membername-for-interface-interfacename"></a>\<type1 > ' \<typename > ' musí implementovat ' \<membername > ' pro rozhraní ' \<interfacename > '
' \<typename > ' musí implementovat ' \<membername > ' pro rozhraní ' \<interfacename > '. Implementující vlastnost musí mít párové specifikátory ReadOnly a WriteOnly.  
  
 Deklarace třídy nebo struktury pro implementaci rozhraní, ale neimplementuje proceduru, vlastnost nebo událost definovanou rozhraním. Je nutné implementovat všechny členy rozhraní.  
  
 **ID chyby:** BC30154  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Deklarujete člena se stejným názvem a signaturou, jak je definováno v rozhraní. Nezapomeňte zahrnout alespoň příkaz `End Function`, `End Sub` nebo `End Property`.  
  
2. Přidejte klauzuli `Implements` na konec příkazu `Function`, `Sub`, `Property` nebo `Event`. Příklad:  
  
    ```vb  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3. Při implementaci vlastnosti se ujistěte, že se používá `ReadOnly` nebo `WriteOnly` stejným způsobem jako v definici rozhraní.  
  
4. Při implementaci vlastnosti deklaruje v případě potřeby postupy `Get` a `Set`.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

---
title: <type1>'<typename>musí implementovat<methodname>'pro rozhraní'<interfacename>.
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: c387b0225375f4675042bef593b23a084305b4fd
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591598"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<Type1 >'\<typename >' musí implementovat '\<methodname > 'rozhraní'\<interfacename > '
Deklarace třídy nebo struktury pro implementaci rozhraní, ale neimplementuje proceduru definovanou rozhraním. Je nutné implementovat všechny členy rozhraní.  
  
 **ID chyby:** BC30149  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Deklarujte proceduru se stejným názvem a signaturou, jak je definováno v rozhraní. Nezapomeňte zahrnout alespoň příkaz `End Function` nebo `End Sub`.  
  
2. Přidejte klauzuli `Implements` na konec příkazu `Function` nebo `Sub`. Příklad:  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

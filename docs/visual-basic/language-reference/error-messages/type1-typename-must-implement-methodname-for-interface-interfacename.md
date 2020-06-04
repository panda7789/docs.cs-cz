---
title: <type1>'<typename>' musí implementovat '<methodname>' pro rozhraní '<interfacename>'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: 90d2b6d70390bfb732af4a5868c935de61d18f94
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408494"
---
# <a name="type1typename-must-implement-methodname-for-interface-interfacename"></a>\<type1>'\<typename>' musí implementovat '\<methodname>' pro rozhraní '\<interfacename>'
Deklarace třídy nebo struktury pro implementaci rozhraní, ale neimplementuje proceduru definovanou rozhraním. Je nutné implementovat všechny členy rozhraní.  
  
 **ID chyby:** BC30149  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Deklarujte proceduru se stejným názvem a signaturou, jak je definováno v rozhraní. Nezapomeňte zahrnout alespoň `End Function` `End Sub` příkaz nebo.  
  
2. Přidejte `Implements` klauzuli na konec `Function` `Sub` příkazu or. Příklad:  
  
    ```vb  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Viz také

- [Implements – Příkaz](../statements/implements-statement.md)
- [Rozhraní](../../programming-guide/language-features/interfaces/index.md)

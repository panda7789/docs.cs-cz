---
title: '&lt;Type1&gt;&#39;&lt;typename&gt; &#39; musí implementovat &#39; &lt;methodname&gt; &#39; pro rozhraní &#39; &lt;interfacename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords:
- BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
ms.openlocfilehash: daeeab853f6a7f582542fa15ffc09ce749731d6f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594380"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;Type1&gt;&#39;&lt;typename&gt; &#39; musí implementovat &#39; &lt;methodname&gt; &#39; pro rozhraní &#39; &lt;interfacename&gt;&#39;
Třídu nebo strukturu pro implementaci rozhraní deklarace identity, ale neimplementuje procedury definované rozhraní. Každý člen rozhraní musí být implementována.  
  
 **ID chyby:** BC30149  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Procedura se stejným názvem a podpis definovaným v rozhraní deklarujte. Je nutné zahrnout alespoň `End Function` nebo `End Sub` příkaz.  
  
2.  Přidat `Implements` klauzule na konec `Function` nebo `Sub` příkaz. Příklad:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

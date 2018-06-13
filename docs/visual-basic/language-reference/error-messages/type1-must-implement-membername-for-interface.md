---
title: '&lt;Type1&gt;&#39;&lt;typename&gt; &#39; musí implementovat &#39; &lt;membername&gt; &#39; pro rozhraní &#39; &lt;interfacename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 0f93bd137bdc21268cbca139ae739843561350ac
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33596743"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;Type1&gt;&#39;&lt;typename&gt; &#39; musí implementovat &#39; &lt;membername&gt; &#39; pro rozhraní &#39; &lt;interfacename&gt;&#39;
'\<typename >' musí implementovat '\<členské jméno > "pro rozhraní '\<interfacename >'. Implementace vlastností musí mít odpovídající "jen pro čtení, nebo specifikátory 'WriteOnly'.  
  
 Třídu nebo strukturu pro implementaci rozhraní deklarace identity, ale neimplementuje postupu, vlastnost nebo událostí, které jsou definované rozhraní. Každý člen rozhraní musí být implementována.  
  
 **ID chyby:** BC30154  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Člena se stejným názvem a podpis definovaným v rozhraní deklarujte. Je nutné zahrnout alespoň `End Function`, `End Sub`, nebo `End Property` příkaz.  
  
2.  Přidat `Implements` klauzule na konec `Function`, `Sub`, `Property`, nebo `Event` příkaz. Příklad:  
  
    ```  
    Public Event ItHappened() Implements IBaseInterface.ItHappened  
    ```  
  
3.  Při implementaci vlastnost, ujistěte se, že `ReadOnly` nebo `WriteOnly` se používá stejným způsobem jako definice rozhraní.  
  
4.  Při implementaci vlastnost, deklarovat `Get` a `Set` postupy, podle potřeby.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

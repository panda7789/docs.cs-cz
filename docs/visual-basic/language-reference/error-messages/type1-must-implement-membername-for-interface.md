---
title: '&lt;Type1&gt;&#39;&lt;typename&gt; &#39; musí implementovat &#39; &lt;membername&gt; &#39; rozhraní &#39; &lt;interfacename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
ms.openlocfilehash: 14e7bd199215764676a4b563eafc68bd6dabadc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54574739"
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;Type1&gt;&#39;&lt;typename&gt; &#39; musí implementovat &#39; &lt;membername&gt; &#39; rozhraní &#39; &lt;interfacename&gt;&#39;
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

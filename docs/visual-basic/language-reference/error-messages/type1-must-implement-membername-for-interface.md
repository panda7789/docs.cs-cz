---
title: "&lt;Type1&gt;& č. 39;&lt; TypeName&gt;& č. 39; musí implementace & č. 39;&lt; MemberName&gt;& č. 39; pro rozhraní & č. 39;&lt; InterfaceName&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30154
- bc30154
helpviewer_keywords:
- BC30154
ms.assetid: 259afdfa-3608-4760-adcb-88ec0da5020d
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 05e0229d0259c519d4db265c017a5040b425c79a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmembernamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;Type1&gt;& č. 39;&lt; TypeName&gt;& č. 39; musí implementace & č. 39;&lt; MemberName&gt;& č. 39; pro rozhraní & č. 39;&lt; InterfaceName&gt;& č. 39;
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
 [Implements – příkaz](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

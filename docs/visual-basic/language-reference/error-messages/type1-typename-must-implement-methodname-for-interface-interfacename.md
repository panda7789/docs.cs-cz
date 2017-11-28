---
title: "&lt;Type1&gt;& č. 39;&lt; TypeName&gt;& č. 39; musí implementace & č. 39;&lt; methodName&gt;& č. 39; pro rozhraní & č. 39;&lt; InterfaceName&gt;& č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30149
- bc30149
helpviewer_keywords: BC30149
ms.assetid: 29d1b7f4-dca7-478c-bbe7-c657f342c183
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e803ec7d0054f2fa1b9ed2a731fd30c9c3060468
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lttype1gt39lttypenamegt39-must-implement-39ltmethodnamegt39-for-interface-39ltinterfacenamegt39"></a>&lt;Type1&gt;& č. 39;&lt; TypeName&gt;& č. 39; musí implementace & č. 39;&lt; methodName&gt;& č. 39; pro rozhraní & č. 39;&lt; InterfaceName&gt;& č. 39;
Třídu nebo strukturu pro implementaci rozhraní deklarace identity, ale neimplementuje procedury definované rozhraní. Každý člen rozhraní musí být implementována.  
  
 **ID chyby:** BC30149  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Procedura se stejným názvem a podpis definovaným v rozhraní deklarujte. Je nutné zahrnout alespoň `End Function` nebo `End Sub` příkaz.  
  
2.  Přidat `Implements` klauzule na konec `Function` nebo `Sub` příkaz. Příklad:  
  
    ```  
    Public Sub DoSomething() Implements IBaseInterface.DoSomething  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Implements – příkaz](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

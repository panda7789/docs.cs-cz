---
title: "Název proměnné rozsahu lze odvodit jen z jednoduchého nebo kvalifikovaného názvu bez argumentů."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c986fcf188482c526c53ddf3019cec5163d0b62
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>Název proměnné rozsahu lze odvodit jen z jednoduchého nebo kvalifikovaného názvu bez argumentů.
Programovací element, který má jeden nebo více argumentů je zahrnutý v dotazu LINQ. Kompilátor se nepodařilo odvodit z této programovací element proměnnou rozsahu.  
  
 **ID chyby:** BC36599  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zadáte explicitní název proměnné pro programovací element, jak je znázorněno v následujícím kódu:  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a>Viz také  
 [Úvod do LINQ v jazyku Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [Select – klauzule](../../../visual-basic/language-reference/queries/select-clause.md)

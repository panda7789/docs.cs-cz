---
title: Název proměnné rozsahu lze odvodit jen z jednoduchého nebo kvalifikovaného názvu bez argumentů.
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: a0b5633bb0efb3c67f73810552ef9a14ac3d0c70
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59331647"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>Název proměnné rozsahu lze odvodit jen z jednoduchého nebo kvalifikovaného názvu bez argumentů.
Programový element, který přijímá jeden nebo více argumentů je zahrnutý v dotazu LINQ. Kompilátor nedokáže odvodit proměnnou rozsahu z této programovací element.  
  
 **ID chyby:** BC36599  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zadejte explicitní název proměnné pro programový element, jak je znázorněno v následujícím kódu:  
  
```  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a>Viz také:

- [Představení technologie LINQ v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Select – klauzule](../../../visual-basic/language-reference/queries/select-clause.md)

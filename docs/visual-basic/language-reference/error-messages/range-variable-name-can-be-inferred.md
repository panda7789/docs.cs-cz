---
title: Název proměnné rozsahu lze odvodit jen z jednoduchého nebo kvalifikovaného názvu bez argumentů.
ms.date: 07/20/2015
f1_keywords:
- vbc36599
- bc36599
helpviewer_keywords:
- BC36599
ms.assetid: 17763dbe-f74f-4ccb-8086-cb7e45ec4d12
ms.openlocfilehash: f448f34dc5909b9128fc700abab5b4f00e911edf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701018"
---
# <a name="range-variable-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>Název proměnné rozsahu lze odvodit jen z jednoduchého nebo kvalifikovaného názvu bez argumentů.
Programovací prvek, který používá jeden nebo více argumentů, je obsažen v dotazu LINQ. Kompilátor nemůže odvodit proměnnou rozsahu z tohoto programovacího prvku.  
  
 **ID chyby:** BC36599  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Zadejte explicitní název proměnné pro programový element, jak je znázorněno v následujícím kódu:  
  
```vb  
Dim query = From var1 In collection1   
            Select VariableAlias= SampleFunction(var1), var1  
```  
  
## <a name="see-also"></a>Viz také:

- [Úvod do jazyka LINQ v Visual Basic](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [Klauzule Select](../../../visual-basic/language-reference/queries/select-clause.md)

---
title: Byl očekáván inicializátor.
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 1fa66a3c50b5c1eadd4c63b92c57ab60e1a11076
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595991"
---
# <a name="initializer-expected"></a>Byl očekáván inicializátor.
Pokusili jste se instanci třídy deklarovat pomocí inicializátoru objektu, ve kterém je prázdný, inicializační seznam, jak je znázorněno v následujícím příkladu.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 Aspoň jedno pole nebo vlastnost musí být inicializována v seznamu inicializátorů, jak je znázorněno v následujícím příkladu.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **ID chyby:** BC30996  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Inicializovat aspoň jedno pole nebo vlastnost v inicializátoru, nebo nepoužívejte inicializátoru objektu.  
  
## <a name="see-also"></a>Viz také:
- [Inicializátory objektů: Pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Postupy: Deklarace objektu pomocí inicializátoru objektů](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)

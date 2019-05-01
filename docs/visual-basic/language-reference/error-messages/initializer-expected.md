---
title: Byl očekáván inicializátor.
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 0795fdc1c4b177e13979d7555cd7588217b8cb4c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62013800"
---
# <a name="initializer-expected"></a>Byl očekáván inicializátor.
Pokusili jste se instanci třídy deklarovat pomocí inicializátoru objektu, ve kterém je prázdný, inicializační seznam, jak je znázorněno v následujícím příkladu.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 Aspoň jedno pole nebo vlastnost musí být inicializována v seznamu inicializátorů, jak je znázorněno v následujícím příkladu.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **ID chyby:** BC30996  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Inicializovat aspoň jedno pole nebo vlastnost v inicializátoru, nebo nepoužívejte inicializátoru objektu.  
  
## <a name="see-also"></a>Viz také:

- [Inicializátory objektů: Pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Postupy: Deklarace objektu pomocí inicializátoru objektů](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)

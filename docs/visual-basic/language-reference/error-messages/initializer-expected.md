---
title: Byl očekáván inicializátor.
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 9d786fd1e929129c420b7bec62efd0bd445d85eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586383"
---
# <a name="initializer-expected"></a>Byl očekáván inicializátor.
Pokusili jste se deklarujte instanci třídy pomocí inicializátoru objektu, ve kterém inicializace seznam je prázdný, jak je znázorněno v následujícím příkladu.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 Minimálně jedno pole nebo vlastnost musí být inicializován v inicializátoru seznamu, jak je znázorněno v následujícím příkladu.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **ID chyby:** BC30996  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Inicializace alespoň jednoho pole nebo vlastnost inicializátoru, nebo nepoužívejte inicializátoru objektu.  
  
## <a name="see-also"></a>Viz také  
 [Inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Postupy: Deklarace objektu pomocí inicializátoru objektu](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)

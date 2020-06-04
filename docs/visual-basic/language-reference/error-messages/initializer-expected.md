---
title: Byl očekáván inicializátor.
ms.date: 07/20/2015
f1_keywords:
- vbc30996
- bc30996
helpviewer_keywords:
- BC30996
ms.assetid: 6e183fe0-8888-43ed-a062-01571079455f
ms.openlocfilehash: 13fa8917f228661fc44f5e0920d91c596e250c38
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84402834"
---
# <a name="initializer-expected"></a>Byl očekáván inicializátor.
Pokusili jste se deklarovat instanci třídy pomocí inicializátoru objektu, ve kterém je seznam inicializace prázdný, jak je znázorněno v následujícím příkladu.  
  
 `' Not valid.`  
  
 `' Dim aStudent As New Student With {}`  
  
 Alespoň jedno pole nebo vlastnost musí být inicializovány v seznamu inicializátorů, jak je znázorněno v následujícím příkladu.  
  
 `Dim aStudent As New Student With {.year = "Senior"}`  
  
 **ID chyby:** BC30996  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1. Inicializujte alespoň jedno pole nebo vlastnost v inicializátoru, nebo nepoužívejte inicializátor objektu.  
  
## <a name="see-also"></a>Viz také

- [Inicializátory objektů: pojmenované a anonymní typy](../../programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Postupy: Deklarace objektu pomocí inicializátoru objektu](../../programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md)

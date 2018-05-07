---
title: Název člena anonymního typu lze odvodit pouze z jednoduchého nebo kvalifikovaného názvu bez argumentů.
ms.date: 07/20/2015
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
ms.openlocfilehash: f4f62a9ac97c6dbd8d2426f8bfd17afa66c4001a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="anonymous-type-member-name-can-be-inferred-only-from-a-simple-or-qualified-name-with-no-arguments"></a>Název člena anonymního typu lze odvodit pouze z jednoduchého nebo kvalifikovaného názvu bez argumentů.
Nelze odvodit název člena anonymního typu z složitý výraz.  
  
```vb  
Dim numbers() As Integer = {1, 2, 3, 4, 5}  
' Not valid.  
' Dim instanceName1 = New With {numbers(3)}  
```  
  
 Další informace o zdrojích, ze kterých můžete anonymní typy a nelze odvodit člen názvy a typy najdete v tématu [postupy: odvození názvů a typů vlastností v deklaracích anonymního typu](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md).  
  
 **ID chyby:** BC36556  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přiřadíte výraz jméno člena, jak je znázorněno v následujícím kódu:  
  
    ```  
    Dim instanceName2 = New With {.number = numbers(3)}  
    ```  
  
## <a name="see-also"></a>Viz také  
 [Anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 [Postupy: Odvození názvů a typů vlastností v deklaracích anonymního typu](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)

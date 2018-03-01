---
title: "Název člena anonymního typu lze odvodit pouze z jednoduchého nebo kvalifikovaného názvu bez argumentů."
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc36556
- bc36556
helpviewer_keywords:
- BC36556
ms.assetid: e3ba1f33-3a71-4f03-9b04-ed5ec17de17c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7068928a17ee5fdb7bf6b5e0a40aaa7e5ef32f11
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Postupy: odvození názvů a typů v deklaracích anonymního typu vlastností](../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)

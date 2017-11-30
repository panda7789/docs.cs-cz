---
title: "Argumenty typu nelze odvodit z delegáta."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36564
- vbc36564
helpviewer_keywords: BC36564
ms.assetid: 21312807-e1cd-4ac1-ae1c-c28a9c25164d
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 57a3a24af32d9eb85a0f905aa3a73a956723b6d4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="type-arguments-could-not-be-inferred-from-the-delegate"></a>Argumenty typu nelze odvodit z delegáta.
Pomocí příkazu přiřazení `AddressOf` přiřadit adresu obecný postup delegáta, ale neposkytuje žádné argumenty Typ na obecný postup.  
  
 Za normálních okolností při vyvolání obecného typu, můžete zadat typ argumentu pro každý typ parametr, který definuje obecného typu. Pokud nezadáte žádné argumenty typu, pokusí se kompilátor odvození typy, které mají být předána do parametrů. Pokud kontext nenabízí dostatek informací pro kompilátor odvození typů, je generována chyba.  
  
 **ID chyby:** BC36564  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zadejte argumenty typu pro obecný postup v `AddressOf` výraz.  
  
## <a name="see-also"></a>Viz také  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [AddressOf – operátor](../../../visual-basic/language-reference/operators/addressof-operator.md)  
 [Obecné procedury v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-procedures.md)  
 [Seznam typů](../../../visual-basic/language-reference/statements/type-list.md)  
 [Metody rozšíření](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

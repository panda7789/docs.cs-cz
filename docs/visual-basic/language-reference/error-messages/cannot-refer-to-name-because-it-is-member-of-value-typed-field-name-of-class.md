---
title: "Nemůže odkazovat na & č. 39; &lt;název&gt;& č. 39; protože je členem pole zadali hodnotu & č. 39;&lt; název&gt;& č. 39; třída & č. 39;&lt; Název třídy&gt;& č. 39; který má & č. 39; System.MarshalByRefObject & č. 39; jako základní třída"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a84811b9f0e706cf3ebede09e07c03bd7e4cea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>Nemůže odkazovat na & č. 39; &lt;název&gt;& č. 39; protože je členem pole zadali hodnotu & č. 39;&lt; název&gt;& č. 39; třída & č. 39;&lt; Název třídy&gt;& č. 39; který má & č. 39; System.MarshalByRefObject & č. 39; jako základní třída
`System.MarshalByRefObject` – Třída umožňuje aplikacím, které podporují vzdáleného přístupu k objektům napříč hranicemi domény aplikace. Typy musí dědit z `MarshalByRejectObject` třídy, pokud typ se používá napříč hranicemi domény aplikace. Stav objektu nesmí být zkopírována, protože členové objektu nejsou použitelné mimo doménu aplikace, v jakém byly vytvořeny.  
  
 **ID chyby:** BC30310  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte odkaz na zkontrolujte, zda člen odkazovaného je platný.  
  
2.  Explicitně kvalifikaci člena s `Me` – klíčové slovo.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.MarshalByRefObject>  
 [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md)

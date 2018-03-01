---
title: "& č. 39; &lt;typename&gt;& č. 39; nemůže Zdědit z &lt;typ&gt; & č. 39;&lt; basetypename&gt;& č. 39; protože rozšiřuje přístup základní &lt;typ&gt; mimo sestavení"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30910
- bc30910
helpviewer_keywords:
- BC30910
ms.assetid: 68fc05c5-5d55-4742-9a3b-ea04312594f4
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d01981d3136968ae2534539b8eccab4c5c535fbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="39lttypenamegt39-cannot-inherit-from-lttypegt-39ltbasetypenamegt39-because-it-expands-the-access-of-the-base-lttypegt-outside-the-assembly"></a>& č. 39; &lt;typename&gt;& č. 39; nemůže Zdědit z &lt;typ&gt; & č. 39;&lt; basetypename&gt;& č. 39; protože rozšiřuje přístup základní &lt;typ&gt; mimo sestavení
Třídy nebo rozhraní dědí vlastnosti ze základní třídy nebo rozhraní ale je méně omezující úroveň přístupu.  
  
 Například `Public` rozhraní dědí z `Friend` rozhraní, nebo `Protected` třída dědí z `Private` třídy. To zpřístupňuje základní třídy nebo rozhraní pro přístup k mimo určený úroveň.  
  
 **ID chyby:** BC30910  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Změníte úroveň přístupu tohoto odvozené třídy nebo rozhraní na omezující jako základní třídy nebo rozhraní.  
  
     -nebo-  
  
-   Pokud budete potřebovat méně omezující úroveň přístupu, odeberte `Inherits` příkaz. Nelze zdědit omezenější základní třídy nebo rozhraní.  
  
## <a name="see-also"></a>Viz také  
 [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Inherits – příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)

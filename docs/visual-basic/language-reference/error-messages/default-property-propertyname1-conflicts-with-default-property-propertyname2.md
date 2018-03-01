---
title: "Výchozí vlastnost & č. 39; &lt;propertyname1&gt;& č. 39; je v konfliktu s výchozí vlastnost & č. 39;&lt; Název_vlastnosti2&gt;& č. 39; v & č. 39;&lt; Název třídy&gt;& č. 39; a proto musí být deklarován & č. 39; Stínů & č. 39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af92c06f6d07b6ea64a05b9043547a46e3679111
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a>Výchozí vlastnost & č. 39; &lt;propertyname1&gt;& č. 39; je v konfliktu s výchozí vlastnost & č. 39;&lt; Název_vlastnosti2&gt;& č. 39; v & č. 39;&lt; Název třídy&gt;& č. 39; a proto musí být deklarován & č. 39; Stínů & č. 39;
Vlastnost je deklarován se stejným názvem jako vlastnost definovanou v základní třídě. V takovém případě by měl stínové vlastnost v této třídě vlastnost základní třídy.  
  
 Tato zpráva je upozornění. `Shadows`ve výchozím nastavení se předpokládá. Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40007  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přidat `Shadows` – klíčové slovo na deklaraci nebo změňte název vlastnosti je deklarován.  
  
## <a name="see-also"></a>Viz také  
 [Stínů](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)

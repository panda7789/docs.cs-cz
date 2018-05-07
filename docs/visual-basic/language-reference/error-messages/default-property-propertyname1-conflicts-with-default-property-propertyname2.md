---
title: Výchozí vlastnost &#39; &lt;propertyname1&gt; &#39; je v konfliktu s výchozí vlastnost &#39; &lt;Název_vlastnosti2&gt; &#39; v &#39; &lt;classname&gt; &#39;a proto musí být deklarován &#39;stínů&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: b305f7a59a9865ebeb6b6f53607757b719fb4d41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a>Výchozí vlastnost &#39; &lt;propertyname1&gt; &#39; je v konfliktu s výchozí vlastnost &#39; &lt;Název_vlastnosti2&gt; &#39; v &#39; &lt;classname&gt; &#39;a proto musí být deklarován &#39;stínů&#39;
Vlastnost je deklarován se stejným názvem jako vlastnost definovanou v základní třídě. V takovém případě by měl stínové vlastnost v této třídě vlastnost základní třídy.  
  
 Tato zpráva je upozornění. `Shadows` ve výchozím nastavení se předpokládá. Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40007  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přidat `Shadows` – klíčové slovo na deklaraci nebo změňte název vlastnosti je deklarován.  
  
## <a name="see-also"></a>Viz také  
 [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)

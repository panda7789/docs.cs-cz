---
title: Výchozí vlastnost &#39; &lt;propertyname1&gt; &#39; je v konfliktu s výchozí vlastností &#39; &lt;Název_vlastnosti2&gt; &#39; v &#39; &lt;classname&gt; &#39;a je třeba ji deklarovat &#39;stíny&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc40007
- bc40007
helpviewer_keywords:
- BC40007
ms.assetid: 692ccf76-5715-4f11-a972-84cf9de30bc1
ms.openlocfilehash: 3099467fa3c5a162c13c9235fb8d55375953ba3a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521423"
---
# <a name="default-property-39ltpropertyname1gt39-conflicts-with-default-property-39ltpropertyname2gt39-in-39ltclassnamegt39-and-so-should-be-declared-39shadows39"></a>Výchozí vlastnost &#39; &lt;propertyname1&gt; &#39; je v konfliktu s výchozí vlastností &#39; &lt;Název_vlastnosti2&gt; &#39; v &#39; &lt;classname&gt; &#39;a je třeba ji deklarovat &#39;stíny&#39;
Vlastnost je deklarována se stejným názvem jako vlastnost definována v základní třídě. V takovém případě by měl stínové vlastnosti v této třídě vlastnost základní třídy.  
  
 Tato zpráva je upozornění. `Shadows` předpokládá se ve výchozím nastavení. Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC40007  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Přidat `Shadows` – klíčové slovo na deklarace, nebo změňte název vlastnosti deklarované.  
  
## <a name="see-also"></a>Viz také:
- [Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)
- [Stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)

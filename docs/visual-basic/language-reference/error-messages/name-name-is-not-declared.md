---
title: Název &#39; &lt;název&gt; &#39; není deklarovaný
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30451
- vbc30451
helpviewer_keywords:
- BC30451
ms.assetid: 765f099b-e21e-47c6-a906-a065444e56b3
caps.latest.revision: 11
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 26245952a2dc5341dedba6c497c47773b882b49b
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="name-39ltnamegt39-is-not-declared"></a>Název &#39; &lt;název&gt; &#39; není deklarovaný
Příkaz odkazuje na programovací element, ale kompilátor nelze najít element s tímto názvem přesný.  
  
 **ID chyby:** BC30451  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte správnost názvu v odkazující příkazu. Visual Basic je velká a malá písmena, ale jiné variace v pravopis považuje za úplně jiný název. Všimněte si, že podtržítko (`_`) je součástí názvu a proto součástí pravopis.  
  
2.  Zkontrolujte, že máte operátor přístupu členů (`.`) mezi objektem a jejího člena. Pokud máte například <xref:System.Windows.Forms.TextBox> ovládací prvek s názvem `TextBox1`, přístup k jeho <xref:System.Windows.Forms.TextBoxBase.Text%2A> vlastnost byste měli zadat `TextBox1.Text`. Pokud místo toho zadáte `TextBox1Text`, jste vytvořili jiný název.  
  
3.  Pokud správně a syntaxe žádné přístup ke členu objektu je správný, ověřte deklarován element. Další informace najdete v tématu [deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/index.md).  
  
4.  Pokud bylo deklarováno programovací element, zkontrolujte, že je v oboru. Pokud příkaz odkazující mimo oblast deklarace programovací element, možná budete muset kvalifikaci název elementu. Další informace najdete v tématu [oboru v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="see-also"></a>Viz také  
 [Souhrn deklarací a konstant](../../../visual-basic/language-reference/keywords/declarations-and-constants-summary.md)  
 [Zásady vytváření názvů jazyka Visual Basic](../../../visual-basic/programming-guide/program-structure/naming-conventions.md)  
 [Deklarované názvy elementů](../../../visual-basic/programming-guide/language-features/declared-elements/declared-element-names.md)  
 [Odkazy na deklarované elementy](../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)

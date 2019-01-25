---
title: Proměnné &#39; &lt;NázevProměnné&gt; &#39; se použije dřív, než jí byla přiřazena hodnota
ms.date: 07/20/2015
f1_keywords:
- vbc42104
- BC42104
helpviewer_keywords:
- BC42104
ms.assetid: 6909aa0b-b4a1-46f5-a18c-ba3e565c1dd8
ms.openlocfilehash: f91343e850600c9e5f4b4b4eb2126798baf3d980
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647020"
---
# <a name="variable-39ltvariablenamegt39-is-used-before-it-has-been-assigned-a-value"></a>Proměnné &#39; &lt;NázevProměnné&gt; &#39; se použije dřív, než jí byla přiřazena hodnota
Proměnná '\<NázevProměnné >' se použije dřív, než jí byla přiřazena hodnota. Výjimka nulového odkazu by mohlo způsobit v době běhu.  
  
 Aplikace má alespoň jednu možných cest pomocí jeho kód, který načte proměnnou předtím, než je k němu přiřazen žádnou hodnotu.  
  
 Pokud proměnnou nikdy byla přiřazena hodnota, obsahuje výchozí hodnotu pro jeho datového typu. Pro datový typ odkazu, je tato výchozí hodnota [nic](../../../visual-basic/language-reference/nothing.md). Čtení odkaz na proměnnou, která má hodnotu `Nothing` může způsobit, že <xref:System.NullReferenceException> v některých případech.  
  
 Ve výchozím nastavení tato zpráva je upozornění. Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42104  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zkontrolujte logiku toku řízení a ujistěte se, že proměnná obsahuje platnou hodnotu před řízení se předá jakýkoli příkaz, který čte ho.  
  
-   Jedním ze způsobů zaručí, že má proměnná vždy platná hodnota je inicializovat ho jako součást její deklarace. Naleznete v části "Inicializace" v [Dim – příkaz](../../../visual-basic/language-reference/statements/dim-statement.md).  
  
## <a name="see-also"></a>Viz také:
- [Příkaz Dim](../../../visual-basic/language-reference/statements/dim-statement.md)
- [Deklarace proměnné](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Řešení potíží s proměnnými](../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)

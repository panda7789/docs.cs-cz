---
title: Vlastnost &#39; &lt;propertyname&gt; &#39; kódu&#39;t vrátí hodnotu ve všech cestách kódu.
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: b8059ebc9b6c1de685f2f04c3ee362ab8cf6d05e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54611251"
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a>Vlastnost &#39; &lt;propertyname&gt; &#39; kódu&#39;t vrátí hodnotu ve všech cestách kódu.
Vlastnost "\<propertyname >' nevrací hodnotu ve všech cestách kódu. V době běhu při použití vráceného výsledku může dojít k výjimce odkazem s hodnotou null.  
  
 Vlastnost `Get` postup obsahuje alespoň jeden možných cest pomocí jejího kódu, která nevrací hodnotu.  
  
 Může vrátit hodnotu z vlastnosti `Get` postup v některém z následujících způsobů:  
  
-   Přiřaďte hodnotu k názvu vlastnosti a pak proveďte `Exit Property` příkazu.  
  
-   Přiřaďte hodnotu k názvu vlastnosti a pak proveďte `End Get` příkazu.  
  
-   Hodnota v [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 Pokud řízení se předá `Exit Property` nebo `End Get` a jste ještě nepřiřadili žádné hodnoty názvu vlastnosti `Get` postup vrátí výchozí hodnotu vlastnosti datového typu. Další informace najdete v tématu "Chování" [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Ve výchozím nastavení tato zpráva je upozornění. Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42107  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zkontrolujte logiku toku řízení a ujistěte se, že přidělíte hodnotu před každý příkaz, který způsobí, že vrácení.  
  
     Je snazší zajistit, že každý návrat z procedury vrací hodnotu, pokud vždy používáte `Return` příkazu. Pokud to provedete, poslední příkaz před `End Get` by měl být `Return` příkazu.  
  
## <a name="see-also"></a>Viz také:
- [Procedury vlastnosti](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Get](../../../visual-basic/language-reference/statements/get-statement.md)

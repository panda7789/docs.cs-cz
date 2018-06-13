---
title: Vlastnost &#39; &lt;propertyname&gt; &#39; nemá&#39;t vrátit hodnotu na všechny cesty kódu
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 72bc7e45cadd2528f29c88bf6e80ee5f381052dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33594211"
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a>Vlastnost &#39; &lt;propertyname&gt; &#39; nemá&#39;t vrátit hodnotu na všechny cesty kódu
Vlastnost '\<propertyname >' nevrací hodnotu na všechny cesty kódu. Výjimka odkazu s hodnotou null mohlo dojít v době běhu, když se použije výsledek.  
  
 Vlastnost `Get` procedura nemá alespoň jednu cestu možný prostřednictvím jeho kód, který nevrací hodnotu.  
  
 Můžete vrátit hodnotu z vlastnosti `Get` postup v některém z následujících způsobů:  
  
-   Přiřadí hodnotu pro název vlastnosti a poté proveďte `Exit Property` příkaz.  
  
-   Přiřadí hodnotu pro název vlastnosti a poté proveďte `End Get` příkaz.  
  
-   Zahrnout hodnotu v [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
 Pokud ovládací prvek předává do `Exit Property` nebo `End Get` a nebyly přiřazeny žádnou hodnotu pro název vlastnosti `Get` postup vrátí výchozí hodnota vlastnosti datového typu. Další informace najdete v tématu "Chování" v [funkce příkaz](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Ve výchozím nastavení je tato zpráva upozornění. Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42107  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zkontrolujte logika toku řízení a ujistěte se, že přiřadit hodnotu před každý příkaz, který způsobí, že vrátit.  
  
     Je snazší zaručit, že každý vrátit v postupu vrací hodnotu, pokud je vždy použít `Return` příkaz. Pokud použijete tento, poslední příkaz před `End Get` by měla být `Return` příkaz.  
  
## <a name="see-also"></a>Viz také  
 [Procedury vlastnosti](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Příkaz Get](../../../visual-basic/language-reference/statements/get-statement.md)

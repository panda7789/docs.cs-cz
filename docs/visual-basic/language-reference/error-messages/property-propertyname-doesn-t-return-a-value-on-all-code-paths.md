---
title: "Vlastnost & č. 39; &lt;propertyname&gt;& č. 39; nemá & č. 39; t vrátit hodnotu na všechny cesty kódu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c9ef5b2ac62412f5684cbc78ab6bebf6bc7b6752
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="property-39ltpropertynamegt39-doesn39t-return-a-value-on-all-code-paths"></a>Vlastnost & č. 39; &lt;propertyname&gt;& č. 39; nemá & č. 39; t vrátit hodnotu na všechny cesty kódu
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
 [Procedury vlastností](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
 [Get – příkaz](../../../visual-basic/language-reference/statements/get-statement.md)

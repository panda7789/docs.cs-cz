---
title: Ve vlastnosti '<propertyname>' existují cesty kódu, které nevrací žádnou hodnotu.
ms.date: 07/20/2015
f1_keywords:
- bc42107
- vbc42107
helpviewer_keywords:
- BC42107
ms.assetid: 06800966-9c3b-4844-9f13-83ac95607d32
ms.openlocfilehash: 21a1c4dbab6e26cd1cb848e270bbda9a544c2a67
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400419"
---
# <a name="property-propertyname-doesnt-return-a-value-on-all-code-paths"></a>Ve vlastnosti '\<propertyname>' existují cesty kódu, které nevrací žádnou hodnotu.
Vlastnost \<propertyname> nevrací hodnotu ve všech cestách kódu. Při použití výsledku může při spuštění dojít k výjimce odkazu s hodnotou null.  
  
 Procedura vlastnosti `Get` má alespoň jednu možnou cestu prostřednictvím kódu, který nevrací hodnotu.  
  
 Můžete vrátit hodnotu z `Get` procedury vlastnosti některým z následujících způsobů:  
  
- Přiřaďte hodnotu k názvu vlastnosti a pak proveďte `Exit Property` příkaz.  
  
- Přiřaďte hodnotu k názvu vlastnosti a pak `End Get` příkaz proveďte.  
  
- Zahrňte hodnotu do [příkazu return](../statements/return-statement.md).  
  
 Pokud řízení projde `Exit Property` nebo `End Get` a Vy jste k názvu vlastnosti nepřiřadili žádnou hodnotu, `Get` procedura vrátí výchozí hodnotu datového typu vlastnosti. Další informace naleznete v tématu "Behavior" v [příkazu Function](../statements/function-statement.md).  
  
 Ve výchozím nastavení je tato zpráva upozornění. Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42107  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Zkontrolujte logiku toku ovládacích prvků a ujistěte se, že přiřadíte hodnotu před všemi příkazy, které způsobují návrat.  
  
     Je snazší zaručit, že při každém návratu z této procedury vrátí hodnotu, pokud vždy použijete `Return` příkaz. Pokud to uděláte, poslední příkaz před `End Get` by měl být `Return` příkaz.  
  
## <a name="see-also"></a>Viz také

- [Procedury vlastnosti](../../programming-guide/language-features/procedures/property-procedures.md)
- [Property – příkaz](../statements/property-statement.md)
- [Get – příkaz](../statements/get-statement.md)

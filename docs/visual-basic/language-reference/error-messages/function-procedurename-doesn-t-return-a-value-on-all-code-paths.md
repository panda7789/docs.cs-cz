---
title: Ve funkci '<procedurename>' existují cesty kódu, které nevrací žádnou hodnotu.
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: edb2195f4e83c2315aa929936aff8af88ca8556c
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374132"
---
# <a name="function-procedurename-doesnt-return-a-value-on-all-code-paths"></a>Ve funkci '\<procedurename>' existují cesty kódu, které nevrací žádnou hodnotu.
Funkce \<procedurename> ' ' nevrací hodnotu na všech cestách kódu. Nechybí příkaz return?  
  
 `Function`Procedura má k dispozici alespoň jednu možnou cestu prostřednictvím kódu, který nevrací hodnotu.  
  
 Můžete vrátit hodnotu z `Function` procedury v libovolném z následujících způsobů:  
  
- Zahrňte hodnotu do [příkazu return](../statements/return-statement.md).  
  
- Přiřaďte hodnotu k `Function` názvu procedury a pak `Exit Function` příkaz proveďte.  
  
- Přiřaďte hodnotu k `Function` názvu procedury a pak `End Function` příkaz proveďte.  
  
 Pokud řízení projde `Exit Function` nebo `End Function` a Vy jste k názvu procedury nepřiřadili žádnou hodnotu, procedura vrátí výchozí hodnotu návratového datového typu. Další informace naleznete v tématu "Behavior" v [příkazu Function](../statements/function-statement.md).  
  
 Ve výchozím nastavení je tato zpráva upozornění. Další informace o skrývání upozornění nebo zpracování upozornění jako chyb najdete v tématu [Konfigurace upozornění v Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42105  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Zkontrolujte logiku toku ovládacích prvků a ujistěte se, že přiřadíte hodnotu před všemi příkazy, které způsobují návrat.  
  
     Je snazší zaručit, že při každém návratu z této procedury vrátí hodnotu, pokud vždy použijete `Return` příkaz. Pokud to uděláte, poslední příkaz před `End Function` by měl být `Return` příkaz.  
  
## <a name="see-also"></a>Viz také

- [Procedury funkcí](../../programming-guide/language-features/procedures/function-procedures.md)
- [Function – příkaz](../statements/function-statement.md)
- [Stránka Kompilovat, návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)

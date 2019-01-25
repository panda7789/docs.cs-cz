---
title: Funkce &#39; &lt;název_procedury&gt; &#39; kódu&#39;t vrátí hodnotu ve všech cestách kódu.
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: b6cc5143aafb6c2554b183a1fc5fb3b1331ec5d0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54552187"
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a>Funkce &#39; &lt;název_procedury&gt; &#39; kódu&#39;t vrátí hodnotu ve všech cestách kódu.
Funkce "\<název_procedury >' nevrací hodnotu ve všech cestách kódu. Chybí příkaz 'Return'?  
  
 A `Function` postup obsahuje alespoň jeden možných cest pomocí jejího kódu, která nevrací hodnotu.  
  
 Může vrátit hodnotu z `Function` postup v některém z následujících způsobů:  
  
-   Hodnota v [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
-   Přiřadí hodnotu k `Function` postup pojmenujte a pak proveďte `Exit Function` příkazu.  
  
-   Přiřadí hodnotu k `Function` postup pojmenujte a pak proveďte `End Function` příkazu.  
  
 Pokud řízení se předá `Exit Function` nebo `End Function` a jste ještě nepřiřadili žádné hodnoty pro název procedury, postup vrátí návratový typ dat výchozí hodnotu. Další informace najdete v tématu "Chování" [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Ve výchozím nastavení tato zpráva je upozornění. Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42105  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zkontrolujte logiku toku řízení a ujistěte se, že přidělíte hodnotu před každý příkaz, který způsobí, že vrácení.  
  
     Je snazší zajistit, že každý návrat z procedury vrací hodnotu, pokud vždy používáte `Return` příkazu. Pokud to provedete, poslední příkaz před `End Function` by měl být `Return` příkazu.  
  
## <a name="see-also"></a>Viz také:
- [Procedury funkce](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Stránka Kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)

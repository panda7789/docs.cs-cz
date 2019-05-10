---
title: Ve funkci '<procedurename>' existují cesty kódu, které nevrací žádnou hodnotu.
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: 5564f95048f6b44a48229c7e5be9331839803439
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662107"
---
# <a name="function-procedurename-doesnt-return-a-value-on-all-code-paths"></a>Funkce "\<název_procedury >' nevrací hodnotu ve všech cestách kódu.
Funkce "\<název_procedury >' nevrací hodnotu ve všech cestách kódu. Chybí příkaz 'Return'?  
  
 A `Function` postup obsahuje alespoň jeden možných cest pomocí jejího kódu, která nevrací hodnotu.  
  
 Může vrátit hodnotu z `Function` postup v některém z následujících způsobů:  
  
- Hodnota v [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
- Přiřadí hodnotu k `Function` postup pojmenujte a pak proveďte `Exit Function` příkazu.  
  
- Přiřadí hodnotu k `Function` postup pojmenujte a pak proveďte `End Function` příkazu.  
  
 Pokud řízení se předá `Exit Function` nebo `End Function` a jste ještě nepřiřadili žádné hodnoty pro název procedury, postup vrátí návratový typ dat výchozí hodnotu. Další informace najdete v tématu "Chování" [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Ve výchozím nastavení tato zpráva je upozornění. Další informace o zobrazení nebo skrytí upozornění zpracování upozornění jako chyby, najdete v části [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42105  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Zkontrolujte logiku toku řízení a ujistěte se, že přidělíte hodnotu před každý příkaz, který způsobí, že vrácení.  
  
     Je snazší zajistit, že každý návrat z procedury vrací hodnotu, pokud vždy používáte `Return` příkazu. Pokud to provedete, poslední příkaz před `End Function` by měl být `Return` příkazu.  
  
## <a name="see-also"></a>Viz také:

- [Procedury funkce](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Stránka Kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)

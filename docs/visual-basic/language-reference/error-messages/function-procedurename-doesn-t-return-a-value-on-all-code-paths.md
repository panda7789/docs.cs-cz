---
title: Funkce &#39; &lt;procedurename&gt; &#39; nemá&#39;t vrátit hodnotu na všechny cesty kódu
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: 4c18c6229eb170e8a688aaa2734ae8fbfa081061
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33589981"
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a>Funkce &#39; &lt;procedurename&gt; &#39; nemá&#39;t vrátit hodnotu na všechny cesty kódu
Funkce '\<procedurename >' nevrací hodnotu na všechny cesty kódu. Chybějící příkaz 'Return'?  
  
 A `Function` procedura nemá alespoň jednu cestu možný prostřednictvím jeho kód, který nevrací hodnotu.  
  
 Můžete vrátit hodnotu z `Function` postup v některém z následujících způsobů:  
  
-   Zahrnout hodnotu v [příkaz Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
-   Přiřazení hodnoty k `Function` postup název a potom proveďte `Exit Function` příkaz.  
  
-   Přiřazení hodnoty k `Function` postup název a poté proveďte `End Function` příkaz.  
  
 Pokud ovládací prvek předává do `Exit Function` nebo `End Function` a hodnotou nebyly přiřazovány název procedury, postup vrátí výchozí hodnotu návratový datový typ. Další informace najdete v tématu "Chování" v [funkce příkaz](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Ve výchozím nastavení je tato zpráva upozornění. Další informace o zobrazení nebo skrytí upozornění práce upozornění jako chyby najdete v tématu [Konfigurace upozornění v jazyce Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID chyby:** BC42105  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Zkontrolujte logika toku řízení a ujistěte se, že přiřadit hodnotu před každý příkaz, který způsobí, že vrátit.  
  
     Je snazší zaručit, že každý vrátit v postupu vrací hodnotu, pokud je vždy použít `Return` příkaz. Pokud použijete tento, poslední příkaz před `End Function` by měla být `Return` příkaz.  
  
## <a name="see-also"></a>Viz také  
 [Procedury funkce](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Stránka Kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)

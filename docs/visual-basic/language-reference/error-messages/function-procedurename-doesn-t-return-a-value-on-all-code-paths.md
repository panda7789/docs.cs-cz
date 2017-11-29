---
title: "Funkce & č. 39; &lt;procedurename&gt;& č. 39; nemá & č. 39; t vrátit hodnotu na všechny cesty kódu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords: BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5244d97a79f2450f44fe05f63510369914375912
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="function-39ltprocedurenamegt39-doesn39t-return-a-value-on-all-code-paths"></a>Funkce & č. 39; &lt;procedurename&gt;& č. 39; nemá & č. 39; t vrátit hodnotu na všechny cesty kódu
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
 [Function – procedury](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)  
 [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  
 [Stránka kompilovat, Návrhář projektu (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)

---
title: "Při kompilování schémat XML v projektu došlo k chybám."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords: BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07233ed1c68f85878ffdd7131f64e30e158dc350
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>Při kompilování schémat XML v projektu došlo k chybám.
Při kompilování schémat XML v projektu došlo k chybám. Z toho důvodu XML IntelliSense není k dispozici.  
  
 V definici schématu XML (XSD) schémat, která je zahrnutý v projektu dojde k chybě. K této chybě dojde, když přidáte soubor XSD schématu (XSD), který je v konfliktu s existující schématu XSD nastavit pro projekt.  
  
 **ID chyby:** BC36810  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Klikněte dvakrát na upozornění v **seznamu chyb** okno. Visual Basic přejdete do umístění v souboru XSD, který je zdrojem upozornění. Opravte chybu ve schématu XSD.  
  
-   Zkontrolujte, že všechny požadované soubory XSD schématu (.xsd) jsou zahrnuty v projektu. Je třeba kliknout na **zobrazit všechny soubory** na **projektu** nabídky zobrazíte vaší XSD soubory v **Průzkumníku řešení**. Klikněte pravým tlačítkem na soubor XSD a pak klikněte na **zahrnout do projektu** zahrnout soubor ve vašem projektu.  
  
-   Pokud používáte Průvodce XML na schéma, této chybě může dojít, pokud jste schémata odvození více než jednou z jednoho zdroje. V takovém případě můžete odebrat existující soubory schématu XSD z projektu, přidat nové XML na schéma šablony položky a pak zadejte soubor XML na schéma průvodce s všechny příslušné zdroje XML pro projekt.  
  
-   Pokud žádná chyba, je definovaný v schéma XSD, kompilátoru XML nemusí mít dostatek informací k poskytování Podrobná chybová zpráva. Bude pravděpodobně možné získat podrobnější informace o chybě, pokud zajistíte, že obory názvů XML pro soubory XSD součástí vašeho projektu shodu obory názvů XML pro schéma XML nastavení v sadě Visual Studio.  
  
## <a name="see-also"></a>Viz také  
 [Okno Seznam chyb](/visualstudio/ide/reference/error-list-window)  
 [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)

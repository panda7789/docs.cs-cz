---
title: Při kompilování schémat XML v projektu došlo k chybám.
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 337fc1fb4dfc83c9b4814d3e45eb0cbe0758f7ce
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842522"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>Při kompilování schémat XML v projektu došlo k chybám.
Při kompilování schémat XML v projektu došlo k chybám. Z tohoto důvodu není k dispozici technologie IntelliSense jazyka XML.  
  
 Dojde k chybě ve schématu definice schématu XML (XSD), který je zahrnutý v projektu. K této chybě dochází, když přidáte souboru XSD schématu (XSD), který je v konfliktu s existující schéma XSD nastaven pro projekt.  
  
 **ID chyby:** BC36810  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Poklikejte na ikonu upozornění v **seznamu chyb** okna. Visual Basic přejdete do umístění v souboru XSD, které je zdrojem upozornění. Oprava chyby ve schématu XSD.  
  
-   Ujistěte se, že všechny požadované soubory XSD (XSD) schématu jsou součástí projektu. Budete muset kliknout na **zobrazit všechny soubory** na **projektu** nabídku zobrazte vaše XSD souborů **Průzkumníka řešení**. Klikněte pravým tlačítkem na soubor XSD a potom klikněte na tlačítko **zahrnout do projektu** k zahrnutí souboru do projektu.  
  
-   Pokud používáte Průvodce XML na schéma, této chybě může dojít, pokud jste schémata odvodit více než jednou ze stejného zdroje. V takovém případě existující soubory schématu XSD můžete odebrat z projektu, přidejte nový kód jazyka XML na schéma šablony položky a potom poskytnout XML na schéma průvodce všechny příslušné zdroje XML pro váš projekt.  
  
-   Pokud se najde žádná chyba ve schématu XSD, kompilátor XML nemusí mít dostatek informací, které poskytují Podrobná chybová zpráva. Je možné získat podrobnější informace o chybě, pokud je zajistit, že obory názvů XML pro soubory XSD součástí vašeho projektu zápasu obory názvů XML pro schéma XML, nastavte v sadě Visual Studio.  
  
## <a name="see-also"></a>Viz také:

- [Okno Seznam chyb](/visualstudio/ide/reference/error-list-window)
- [XML](../../../visual-basic/programming-guide/language-features/xml/index.md)

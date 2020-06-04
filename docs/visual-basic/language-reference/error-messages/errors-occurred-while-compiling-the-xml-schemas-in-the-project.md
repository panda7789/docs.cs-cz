---
title: Při kompilování schémat XML v projektu došlo k chybám.
ms.date: 07/20/2015
f1_keywords:
- bc36810
- vbc36810
helpviewer_keywords:
- BC36810
ms.assetid: 9323b5d2-ba14-4e49-91f1-9ad647162144
ms.openlocfilehash: 919c6873ba63addb776d756a58c44a3fe3f0ec3d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409622"
---
# <a name="errors-occurred-while-compiling-the-xml-schemas-in-the-project"></a>Při kompilování schémat XML v projektu došlo k chybám.
Při kompilování schémat XML v projektu došlo k chybám. Z tohoto důvodu není k dispozici XML IntelliSense.  
  
 V rámci schématu definice schématu XML (XSD), který je součástí projektu, je chyba. K této chybě dochází, když přidáte soubor schématu XSD (. XSD), který je v konfliktu s existující sadou schémat XSD pro projekt.  
  
 **ID chyby:** BC36810  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Dvakrát klikněte na upozornění v okně **Seznam chyb** . Visual Basic přejdete do umístění v souboru XSD, který je zdrojem upozornění. Opravte chybu ve schématu XSD.  
  
- Ujistěte se, že v projektu jsou zahrnuté všechny požadované soubory XSD schématu (. XSD). Možná budete muset kliknout na **Zobrazit všechny soubory** v nabídce **projekt** a zobrazit soubory. xsd v **Průzkumník řešení**. Klikněte pravým tlačítkem na soubor. xsd a potom kliknutím na možnost **zahrnout do projektu** zahrňte soubor do projektu.  
  
- Pokud používáte Průvodce XML na schéma, k této chybě může dojít, pokud ze stejného zdroje odvozujete schémata více než jednou. V takovém případě můžete odebrat existující soubory schématu XSD z projektu, přidat novou šablonu XML do šablony položky schématu a potom poskytnout Průvodce schématu XML pro všechny příslušné zdroje XML pro váš projekt.  
  
- Pokud ve schématu XSD není identifikována žádná chyba, kompilátor XML nemusí mít dostatek informací, aby mohl poskytovat podrobnou chybovou zprávu. Je možné získat podrobnější informace o chybách, pokud zajistíte, že obory názvů XML pro soubory. xsd zahrnuté ve vašem projektu odpovídají oborům názvů XML identifikovaným pro sadu schémat XML v sadě Visual Studio.  
  
## <a name="see-also"></a>Viz také

- [Seznam chyb okno](/visualstudio/ide/reference/error-list-window)
- [XML](../../programming-guide/language-features/xml/index.md)

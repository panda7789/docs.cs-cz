---
title: Při načítání nebo analýza XML2 zachování prázdných znaků
ms.date: 07/20/2015
ms.assetid: ef6518e0-2c8d-462c-8b92-a16e9dc737ad
ms.openlocfilehash: 3341bfae8ff9de5e17ba18273c60b525f77bff16
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>Zachování mezer při načítání nebo analýzu kódu XML
Toto téma popisuje, jak řídit chování mezer [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Běžný scénář je číst zobrazují odsazené XML, vytvořte ve stromu v paměti XML bez mezer text uzlů (tedy ne zachování mezer), provádění některých operací na soubor XML a potom uložte soubor XML s odsazení. Při serializaci XML s formátování se zachová jenom významné mezer ve stromové struktuře XML. Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Další z typických možností je číst a upravovat kód XML, který je už záměrně zobrazují odsazené. Možná chcete změnit toto odsazení žádným způsobem. To uděláte v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], zachovat mezer při načtení nebo analyzovat soubor XML a zakázat formátování při serializaci XML.  
  
 Toto téma popisuje chování mezer metody, která naplní stromy XML. Informace o řízení mezer při serializaci XML stromy najdete v tématu [zachování mezer při serializaci](../../../../visual-basic/programming-guide/concepts/linq/preserving-white-space-while-serializing.md).  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>Chování metod, která naplní stromy XML  
 Následující metody v <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XDocument> třídy naplnit strom XML. Ve stromu XML ze souboru, může naplnění <xref:System.IO.TextReader>, <xref:System.Xml.XmlReader>, nebo řetězec:  
  
-   <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 Pokud metoda nevyžaduje <xref:System.Xml.Linq.LoadOptions> jako argument, nebude metoda zachování zanedbatelný prázdné znaky.  
  
 Ve většině případů, pokud metoda přebírá <xref:System.Xml.Linq.LoadOptions> jako argument, můžete volitelně zachovat mezer zanedbatelný jako textové uzly ve stromové struktuře XML. Ale pokud metoda načítá XML z <xref:System.Xml.XmlReader>, pak se <xref:System.Xml.XmlReader> Určuje, zda bude zachována mezer, nebo ne. Nastavení <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> nebude mít žádný vliv.  
  
 Pomocí těchto metod, pokud je zachovají mezeru, mezer zanedbatelný vložena do stromu XML jako <xref:System.Xml.Linq.XText> uzlů. Pokud není zachovají mezeru, nejsou vložit textové uzly.  
  
 Ve stromu XML můžete vytvořit pomocí <xref:System.Xml.XmlWriter>. Uzly, které se zapisují do <xref:System.Xml.XmlWriter> zaplní se ve stromové struktuře. Při sestavování ve stromu XML pomocí této metody všechny uzly jsou však zachovaných bez ohledu na to, zda uzel je prázdný znak nebo Ne, nebo jestli je prázdné místo důležité nebo ne.  
  
## <a name="see-also"></a>Viz také  
 [Analýza kódu XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)

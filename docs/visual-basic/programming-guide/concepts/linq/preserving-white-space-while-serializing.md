---
title: Zachování mezer při Serializing2
ms.date: 07/20/2015
ms.assetid: 2d7abbd4-37f4-422b-89dd-0a694b5edc17
ms.openlocfilehash: e9b73089830bf7e6cb0ea9e469bf667f12c571d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396399"
---
# <a name="preserving-white-space-while-serializing"></a>Zachování prázdných znaků při serializaci
Toto téma popisuje, jak ovládat prázdné znaky při serializaci stromu XML.  
  
 Běžným scénářem je čtení odsazeného XML, vytvoření stromu XML v paměti bez jakýchkoli textových uzlů s prázdnými znaky (tj. bez zachovávání prázdných znaků), provedení některých operací v XML a následné uložení XML s odsazením. Při serializaci XML s formátováním je zachováno pouze významné prázdné znaky ve stromu XML. Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
 Dalším běžným scénářem je číst a upravovat kód XML, který již byl záměrně odsazen. Toto odsazení nebudete chtít nijak měnit. Chcete-li to provést v [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , zachováte prázdné místo při načítání nebo analýze XML a při serializaci kódu XML zakážete formátování.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>Chování prázdných znaků metod, které serializovat stromy XML  
 Následující metody v <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> třídách a SERIALIZOVAT strom XML. Strom XML lze serializovat do souboru, <xref:System.IO.TextReader> nebo <xref:System.Xml.XmlReader> . `ToString`Metoda je serializována do řetězce.  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [XElement. ToString ()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [XDocument. ToString ()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 Pokud metoda nepřijímá <xref:System.Xml.Linq.SaveOptions> jako argument, pak metoda naformátuje (odsadí) serializovaný kód XML. V tomto případě je zahozeno veškeré nevýznamné prázdné znaky ve stromu XML.  
  
 Pokud metoda převezme <xref:System.Xml.Linq.SaveOptions> jako argument, můžete určit, že metoda nebude formátovat (odsazovat) serializovaného XML. V tomto případě je zachováno veškeré prázdné znaky ve stromu XML.  
  
## <a name="see-also"></a>Viz také

- [Serializace stromů XML (Visual Basic)](serializing-xml-trees.md)

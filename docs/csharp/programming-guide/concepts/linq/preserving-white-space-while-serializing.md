---
title: Zachování prázdného místa při serializaci3
ms.date: 07/20/2015
ms.assetid: 0c4f8b98-483b-4cf8-86be-fa146eef90dc
ms.openlocfilehash: 6d357d40c13a66a152b3c8bb5f61e3a3374c4055
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484074"
---
# <a name="preserving-white-space-while-serializing"></a>Zachování prázdných znaků při serializaci
Toto téma popisuje, jak řídit prázdné místo při serializaci stromu XML.  
  
 Běžným scénářem je čtení odsazeného xml, vytvoření stromu XML v paměti bez neložených uzl (tj. nezachování prázdného místa), provedení některých operací v xml a následné uložení XML s odsazením. Při serializaci xml s formátováním se zachová pouze významné prázdné místo ve stromu XML. Toto je výchozí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]chování pro aplikace .  
  
 Dalším běžným scénářem je čtení a úprava xml, který již byl záměrně odsazen. Možná nebudete chtít změnit toto odsazení v žádném případě. Chcete-li [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]to provést v aplikace , zachovejte prázdné místo při načtení nebo analýzě xml a zakázat formátování při serializaci XML.  
  
## <a name="white-space-behavior-of-methods-that-serialize-xml-trees"></a>Prázdné místo Chování metod, které serializovat stromy XML  
 Následující metody v <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> a třídy serializovat strom XML. Strom XML můžete serializovat do souboru, stromu <xref:System.IO.TextReader>NEBO . <xref:System.Xml.XmlReader> Metoda `ToString` serializuje řetězec.  
  
- <xref:System.Xml.Linq.XElement.Save%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Save%2A?displayProperty=nameWithType>  
  
- [XElement.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
- [XDocument.ToString()](xref:System.Xml.Linq.XNode.ToString%2A?displayProperty=nameWithType)
  
 Pokud metoda nebere <xref:System.Xml.Linq.SaveOptions> jako argument, pak metoda bude formátovat (odsazení) serializované XML. V tomto případě jsou zahozeny všechny nevýznamné prázdné místo ve stromu XML.  
  
 Pokud metoda trvá <xref:System.Xml.Linq.SaveOptions> jako argument, můžete určit, že metoda není formátovat (odsazení) serializovanéXML. V tomto případě je zachováno všechny prázdné místo ve stromu XML.  

---
title: Zachování prázdných znaků při načítání nebo analýze XML
ms.date: 07/20/2015
ms.assetid: f3ff58c4-55aa-4fcd-b933-e3a2ee6e706c
ms.openlocfilehash: d015c21813df2224356bb49212fe282fa5372d03
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "69591551"
---
# <a name="preserving-white-space-while-loading-or-parsing-xml"></a>Zachování prázdných znaků při načítání nebo analýze XML
Toto téma popisuje, jak řídit chování [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]prázdného místa aplikace .  
  
 Běžným scénářem je čtení odsazeného xml, vytvoření stromu XML v paměti bez uzly prázdného textu (to znamená nezachování prázdného místa), provedení některých operací v xml a následné uložení XML s odsazením. Při serializaci xml s formátováním se zachová pouze významné prázdné místo ve stromu XML. Toto je výchozí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]chování pro aplikace .  
  
 Dalším běžným scénářem je čtení a úprava xml, který již byl záměrně odsazen. Možná nebudete chtít změnit toto odsazení v žádném případě. Chcete-li [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]to provést v aplikace , zachovejte prázdné místo při načtení nebo analýzě xml a zakázat formátování při serializaci XML.  
  
 Toto téma popisuje prázdné místo chování metod, které naplní stromy XML. Informace o řízení prázdného místa při serializaci stromů XML naleznete v tématu [Zachování prázdného místa při serializaci](./preserving-white-space-while-serializing.md).  
  
## <a name="behavior-of-methods-that-populate-xml-trees"></a>Chování metod, které naplní stromy XML  
 Následující metody v <xref:System.Xml.Linq.XElement> <xref:System.Xml.Linq.XDocument> a třídy naplnit strom XML. Strom XML můžete naplnit ze <xref:System.IO.TextReader>souboru <xref:System.Xml.XmlReader>, , nebo řetězce:  
  
- <xref:System.Xml.Linq.XElement.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Load%2A?displayProperty=nameWithType>  
  
- <xref:System.Xml.Linq.XDocument.Parse%2A?displayProperty=nameWithType>  
  
 Pokud metoda nebere <xref:System.Xml.Linq.LoadOptions> jako argument, metoda nezachová nevýznamné prázdné místo.  
  
 Ve většině případů, pokud <xref:System.Xml.Linq.LoadOptions> metoda trvá jako argument, můžete volitelně zachovat nevýznamné prázdné místo jako textové uzly ve stromu XML. Pokud však metoda načítá XML <xref:System.Xml.XmlReader>z <xref:System.Xml.XmlReader> aplikace , určuje, zda bude prázdné místo zachováno či nikoli. Nastavení <xref:System.Xml.Linq.LoadOptions.PreserveWhitespace> nebude mít žádný vliv.  
  
 S těmito metodami, pokud je zachováno prázdné místo, je <xref:System.Xml.Linq.XText> nevýznamné prázdné místo vloženo do stromu XML jako uzly. Pokud prázdné místo není zachováno, textové uzly nejsou vloženy.  
  
 Strom XML můžete vytvořit pomocí <xref:System.Xml.XmlWriter>aplikace . Uzly, které <xref:System.Xml.XmlWriter> jsou zapsány do jsou naplněny ve stromu. Však při vytváření stromu XML pomocí této metody jsou zachovány všechny uzly, bez ohledu na to, zda uzel je prázdné místo nebo ne, nebo zda je prázdné místo významné nebo ne.  
  
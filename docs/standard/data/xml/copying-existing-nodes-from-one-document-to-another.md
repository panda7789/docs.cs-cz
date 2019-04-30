---
title: Kopírování existujících uzlů z jednoho dokumentu do jiného
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 3caa78c1-3448-4b7b-b83c-228ee857635e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 744c97e8728d0a65bff8e7bb7a7dbb298afe1800
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934547"
---
# <a name="copying-existing-nodes-from-one-document-to-another"></a>Kopírování existujících uzlů z jednoho dokumentu do jiného
**ImportNode** metoda je mechanismus, podle kterého je zkopírován uzlu nebo celého uzlu podstrom z jednoho **XmlDocument** do jiného. Uzel vrácená z volání je kopie uzlu z zdrojový dokument, včetně hodnoty atributů, název uzlu, typ uzlu a všechny atributy oboru názvů souvisejících například předponu, místní název a obor názvů identifikátoru URI (Uniform Resource). Zdrojový dokument se nezmění. Po importu uzlu máte stále ho přidat do stromu pomocí jedné z metod používaných k vložení uzlů.  
  
 Když uzel je připojen k jeho nový dokument, nový dokument vlastní uzlu. Důvodem je, že každý uzel, po vytvoření má dokument vlastnící i v případě, že uzly se vytvoří v samostatných dokumentu fragmenty. To je požadavek z XML Document Object Model (DOM) a vynucování záměrné vytváření továrny na **XmlDocument** třídy. Například **CreateElement**, je jediný způsob, jak vytvořit nové uzly.  
  
 V závislosti na uzlu typu importované uzlu a hodnota *hloubkové* parametr, další informace se zkopíruje podle potřeby. Tato metoda se pokusí zrcadlí chování, pokud se fragment kódu XML nebo HTML zdroj byl zkopírován z jednoho dokumentu do jiného připadajících na skutečnost, že pro formát XML, může mít dva dokumenty jiného dokumentu typ definice (DTD).  
  
 Následující tabulka popisuje specifické chování pro každý typ uzlu, který lze naimportovat.  
  
|Typ uzlu|*hloubkové* parametr má hodnotu true|*hloubkové* parametr má hodnotu false|  
|---------------|------------------------------|-------------------------------|  
|XmlAttribute|<xref:System.Xml.XmlAttribute.Specified%2A> Je nastavena na **true** na XmlAttribute. Následníky zdroje **XmlAttribute** jsou sestaveny rekurzivně importovány a výsledné uzly k vytvoření odpovídající podstrom.|*Hloubkové* parametru se nedá použít u **XmlAttribute** uzly, proto, že vždy provádějí jejich podřízené uzly s nimi při importu.|  
|XmlCDataSection|Zkopíruje uzel, včetně jeho data.|Zkopíruje uzel, včetně jeho data.|  
|XmlComment|Zkopíruje uzel, včetně jeho data.|Zkopíruje uzel, včetně jeho data.|  
|XmlDocumentFragment|Zdrojový uzel následníky jsou rekurzivně importovány a výsledné uzly sestaveny a vytvoří odpovídající podstrom.|Prázdná **XmlDocumentFragment** se vytvoří.|  
|XmlDocumentType|Zkopíruje uzel, včetně jeho data.*|Zkopíruje uzel, včetně jeho data.*|  
|Třída XmlElement|Následníky elementu zdroje jsou rekurzivně importovány a výsledné uzly sestaveny a vytvoří odpovídající podstrom. **Poznámka:**  Výchozí atributy nejsou zkopírovány. Pokud dokument importují do definuje výchozí atributy pro tento název elementu, ty jsou přiřazeny.|Zadaný atribut uzly source element importují a vygenerovaný **XmlAttribute** uzly jsou připojeny k nového elementu. Nejsou zkopírovány podřízených uzlů. **Poznámka:**  Výchozí atributy nejsou zkopírovány. Pokud dokument importují do definuje výchozí atributy pro tento název elementu, ty jsou přiřazeny.|  
|XmlEntityReference|Protože dokumenty zdroj a cíl může mít definovány rozdílně entity, tato metoda pouze zkopíruje **XmlEntityReference** uzlu. Náhradní text není zahrnut. Pokud má dokument cílové entity definované, jeho hodnota přiřazena.|Protože dokumenty zdroj a cíl může mít definovány rozdílně entity, tato metoda pouze zkopíruje **XmlEntityReference** uzlu. Náhradní text není zahrnut. Pokud má dokument cílové entity definované, jeho hodnota přiřazena.|  
|XmlProcessingInstruction|Zkopíruje hodnoty cíle a dat z importovaných uzlu.|Zkopíruje hodnoty cíle a dat z importovaných uzlu.|  
|XmlText|Zkopíruje uzel, včetně jeho data.|Zkopíruje uzel, včetně jeho data.|  
|XmlSignificantWhitespace|Zkopíruje uzel, včetně jeho data.|Zkopíruje uzel, včetně jeho data.|  
|XmlWhitespace|Zkopíruje uzel, včetně jeho data.|Zkopíruje uzel, včetně jeho data.|  
|XmlDeclaration|Zkopíruje hodnoty cíle a dat z importovaných uzlu.|Zkopíruje hodnoty cíle a dat z importovaných uzlu.|  
|Všechny ostatní typy uzlů|Tyto typy uzlů se nedají importovat.|Tyto typy uzlů se nedají importovat.|  
  
> [!NOTE]
>  I když DocumentType uzly je možné importovat, dokument může mít pouze jeden DocumentType. Ano Jakmile naimportujete typ dokumentu před vložením do stromu, budete muset Ujistěte se, že neexistuje žádný dokument typ v dokumentu. Informace o odebírání uzlů najdete v tématu [odebrání uzlů, obsahu a hodnot z dokumentu XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

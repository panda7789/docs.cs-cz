---
title: Kopírování existujících uzlů z jednoho dokumentu do jiného
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 3caa78c1-3448-4b7b-b83c-228ee857635e
ms.openlocfilehash: 4ee3f8d280b8bf0f2de067e7529d777e62bff406
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711022"
---
# <a name="copying-existing-nodes-from-one-document-to-another"></a>Kopírování existujících uzlů z jednoho dokumentu do jiného
Metoda **ImportNode** je mechanismus, pomocí kterého se uzel nebo celý podstrom uzlu kopíruje z jednoho **XmlDocument** do jiného. Uzel vrácený voláním je kopie uzlu ze zdrojového dokumentu, včetně hodnot atributů, názvu uzlu, typu uzlu a všech atributů souvisejících s oborem názvů, jako je předpona, místní název a identifikátor URI (Uniform Resource Identifier). Zdrojový dokument se nemění. Po dokončení importu uzlu je stále nutné ho přidat do stromu pomocí jedné z metod, které se používají pro vkládání uzlů.  
  
 Když je uzel připojen k novému dokumentu, nový dokument vlastní daný uzel. Důvodem je, že každý uzel, který je vytvořen, má vlastní dokument, i když jsou uzly vytvořeny v samostatných fragmentech dokumentů. Toto je požadavek XML model DOM (Document Object Model) (DOM) a je vynutil návrhem vytváření továrny ve třídě **XmlDocument** . Například **CreateElement**je jediným způsobem, jak vytvořit nové uzly.  
  
 V závislosti na typu uzlu importovaného uzlu a hodnotě *hlubokého* parametru se další informace zkopírují podle potřeby. Tato metoda se pokusí zrcadlit očekávané chování v případě, že fragment kódu XML nebo HTML byl zkopírován z jednoho dokumentu do jiného, účetní oddělení pro skutečnost, že v jazyce XML mohou mít dva dokumenty různé definice typu dokumentu (DTD).  
  
 Následující tabulka popisuje konkrétní chování pro každý typ uzlu, který lze importovat.  
  
|Typ uzlu|*hluboký* parametr má hodnotu true.|*hluboký* parametr má hodnotu false.|  
|---------------|------------------------------|-------------------------------|  
|XmlAttribute|<xref:System.Xml.XmlAttribute.Specified%2A> je na atributu XmlAttribute nastaven na **hodnotu true** . Následníky zdroje **XmlAttribute** jsou rekurzivně importovány a výsledné uzly znovu sestaveny tak, aby tvořily odpovídající podstrom.|*Hluboký* parametr se nevztahuje na uzly **XmlAttribute** , protože při importu vždy přenesou jejich podřízené uzly.|  
|XmlCDataSection|Zkopíruje uzel, včetně jeho dat.|Zkopíruje uzel, včetně jeho dat.|  
|XmlComment|Zkopíruje uzel, včetně jeho dat.|Zkopíruje uzel, včetně jeho dat.|  
|XmlDocumentFragment|Následníky zdrojového uzlu jsou rekurzivně importovány a výsledné uzly znovu sestaveny tak, aby tvořily odpovídající podstrom.|Vytvoří se prázdná **XmlDocumentFragment** .|  
|XmlDocumentType|Zkopíruje uzel, včetně jeho dat. *|Zkopíruje uzel, včetně jeho dat. *|  
|Třída|Následníky zdrojového elementu jsou rekurzivně importováni a výsledné uzly znovu sestaveny tak, aby tvořily odpovídající podstrom. **Poznámka:**  Výchozí atributy se nekopírují. Pokud dokument, který je importován do, definuje výchozí atributy pro tento název elementu, jsou přiřazeny.|Určené uzly atributu zdrojového elementu jsou importovány a generované uzly **XmlAttribute** jsou připojeny k novému elementu. Podřízené uzly nejsou zkopírovány. **Poznámka:**  Výchozí atributy se nekopírují. Pokud dokument, který je importován do, definuje výchozí atributy pro tento název elementu, jsou přiřazeny.|  
|XmlEntityReference|Vzhledem k tomu, že zdrojové a cílové dokumenty mohou mít jiné definované entity, tato metoda zkopíruje pouze uzel **XmlEntityReference** . Náhradní text není zahrnutý. Je-li v cílovém dokumentu definována entita, je přiřazena jeho hodnota.|Vzhledem k tomu, že zdrojové a cílové dokumenty mohou mít jiné definované entity, tato metoda zkopíruje pouze uzel **XmlEntityReference** . Náhradní text není zahrnutý. Je-li v cílovém dokumentu definována entita, je přiřazena jeho hodnota.|  
|XmlProcessingInstruction|Zkopíruje cíl a datovou hodnotu z importovaného uzlu.|Zkopíruje cíl a datovou hodnotu z importovaného uzlu.|  
|XmlText|Zkopíruje uzel, včetně jeho dat.|Zkopíruje uzel, včetně jeho dat.|  
|XmlSignificantWhitespace|Zkopíruje uzel, včetně jeho dat.|Zkopíruje uzel, včetně jeho dat.|  
|XmlWhitespace|Zkopíruje uzel, včetně jeho dat.|Zkopíruje uzel, včetně jeho dat.|  
|XmlDeclaration|Zkopíruje cíl a datovou hodnotu z importovaného uzlu.|Zkopíruje cíl a datovou hodnotu z importovaného uzlu.|  
|Všechny ostatní typy uzlů|Tyto typy uzlů nelze importovat.|Tyto typy uzlů nelze importovat.|  
  
> [!NOTE]
> I když lze importovat uzly DocumentType, může mít dokument pouze jeden DocumentType. Takže po importu typu dokumentu před jeho vložením do stromu je nutné se ujistit, že v dokumentu není žádný typ dokumentu. Informace o odebírání uzlů najdete v tématu [Odebrání uzlů, obsahu a hodnot z dokumentu XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).  
  
## <a name="see-also"></a>Viz také:

- [Model DOM (Document Object Model) dokumentu XML](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

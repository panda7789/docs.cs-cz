---
title: LINQ to XML versus. DOM (C#)
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 44e5a4d00705d1cd7aff66e0a9be387d5c6c633a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54702428"
---
# <a name="linq-to-xml-vs-dom-c"></a>LINQ to XML versus. DOM (C#)
Tato část popisuje některé hlavní rozdíly mezi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] a aktuální převládající XML programování rozhraní API, W3C Document Object Model (DOM).  
  
## <a name="new-ways-to-construct-xml-trees"></a>Nové způsoby, jak vytvořit stromů XML  
 V modelu DOM W3C při vytváření stromu XML zdola; To znamená vytvořte dokument, vytvořit prvky a potom přidat prvky v dokumentu.  
  
 Například následující by typické způsob, jak vytvořit stromu XML pomocí modelu DOM, implementace Microsoft <xref:System.Xml.XmlDocument>:  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
XmlElement phone1 = doc.CreateElement("Phone");  
phone1.SetAttribute("Type", "Home");  
phone1.InnerText = "206-555-0144";          
XmlElement phone2 = doc.CreateElement("Phone");  
phone2.SetAttribute("Type", "Work");  
phone2.InnerText = "425-555-0145";          
XmlElement street1 = doc.CreateElement("Street1");          
street1.InnerText = "123 Main St";  
XmlElement city = doc.CreateElement("City");  
city.InnerText = "Mercer Island";  
XmlElement state = doc.CreateElement("State");  
state.InnerText = "WA";  
XmlElement postal = doc.CreateElement("Postal");  
postal.InnerText = "68042";  
XmlElement address = doc.CreateElement("Address");  
address.AppendChild(street1);  
address.AppendChild(city);  
address.AppendChild(state);  
address.AppendChild(postal);  
XmlElement contact = doc.CreateElement("Contact");  
contact.AppendChild(name);  
contact.AppendChild(phone1);  
contact.AppendChild(phone2);  
contact.AppendChild(address);  
XmlElement contacts = doc.CreateElement("Contacts");  
contacts.AppendChild(contact);  
doc.AppendChild(contacts);  
```  
  
 Tento styl psaní kódu vizuálně neposkytuje mnoho informací o struktuře stromu XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] podporuje tento přístup k sestavením stromu XML, ale také podporuje alternativním přístupem *funkční konstrukce*. Funkční konstrukce používá <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory k sestavení stromu XML.  
  
 Zde je, jak je vytvořit stejném stromu XML pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] funkční konstrukce:  
  
```csharp  
XElement contacts =  
    new XElement("Contacts",  
        new XElement("Contact",  
            new XElement("Name", "Patrick Hines"),  
            new XElement("Phone", "206-555-0144",   
                new XAttribute("Type", "Home")),  
            new XElement("phone", "425-555-0145",  
                new XAttribute("Type", "Work")),  
            new XElement("Address",  
                new XElement("Street1", "123 Main St"),  
                new XElement("City", "Mercer Island"),  
                new XElement("State", "WA"),  
                new XElement("Postal", "68042")  
            )  
        )  
    );  
```  
  
 Všimněte si, že odsazení kódu k sestavení kompletních stromu XML ukazuje strukturu základní XML.  
  
 Další informace najdete v tématu [vytváření stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="working-directly-with-xml-elements"></a>Práce přímo se elementů XML  
 Když je program s XML, hlavním cílem je obvykle na prvky XML a případně na atributy. V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], může spolupracovat přímo s XML elementů a atributů. Například můžete provést následující:  
  
-   Vytvořte prvky XML bez použití objektu dokumentu vůbec. Tato funkce usnadňuje programování v případě, že máte pro práci s fragmenty stromů XML.  
  
-   Zatížení `T:System.Xml.Linq.XElement` objekty přímo ze souboru XML.  
  
-   Serializace `T:System.Xml.Linq.XElement` objektů do souboru nebo datový proud.  
  
 Porovnejte W3C v modelu DOM, ve kterém se používá dokumentu XML jako logický kontejner pro stromové struktuře XML. V modelu DOM z uzlů XML, včetně elementů a atributů, musí být vytvořeny v rámci dokumentu XML. Tady je fragment kódu pro vytvoření názvu elementu v modelu DOM:  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 Pokud chcete použít prvek napříč více dokumentů, je nutné naimportovat uzly v dokumentech. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Tato vrstva složitost se vyhnete.  
  
 Při použití technologie LINQ to XML, je použít <xref:System.Xml.Linq.XDocument> třídy pouze v případě, že chcete přidat komentář nebo zpracování instrukcí na kořenové úrovni dokumentu.  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Zjednodušená zpracování názvy a obory názvů  
 Zpracování názvy oborů názvů a předpony oboru názvů je obecně komplexní součástí XML programování. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zjednodušuje názvy a obory názvů tím, že eliminuje požadavek na řešení předpony oboru názvů. Pokud chcete řídit předpony oboru názvů, můžete. Ale pokud se rozhodnete řízení předpon názvového prostoru, není explicitně [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] přiřadí předpony oboru názvů při serializaci, pokud jsou požadované, nebo se serializace pomocí výchozích názvových prostorů, pokud nejsou. Pokud se používají výchozí obory názvů, nebudou bez předpony oboru názvů ve výsledném dokumentu. Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Dalším problémem modelu DOM se, že neumožní můžete změnit název uzlu. Místo toho budete muset vytvořit nový uzel a zkopírujte všechny podřízené uzly, ztráty původní uzel identitu. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tomuto problému se vyhnete tím, že vám umožní nastavit <xref:System.Xml.Linq.XName> vlastnost uzlu.  
  
## <a name="static-method-support-for-loading-xml"></a>Podpora statické metody pro načítání dat XML  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umožňuje načíst XML pomocí statické metody, namísto metody instance. To zjednodušuje, načítání a analýzu. Další informace najdete v tématu [jak: Načtení XML ze souboru (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).  
  
## <a name="removal-of-support-for-dtd-constructs"></a>Odebrání podpory pro DTD konstrukce  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Další zjednodušuje programování tak, že odeberete podporu pro entity a odkazy na entity XML. Správa entit je složitá a zřídka se používá. Odebírá se jejich podpora zvyšuje výkon a zjednodušuje programovací rozhraní. Když [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] naplnění stromu, jsou rozbaleny všechny entity DTD.  
  
## <a name="support-for-fragments"></a>Podpora pro fragmenty  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] nenabízí ekvivalent pro `XmlDocumentFragment` třídy. V mnoha případech se však `XmlDocumentFragment` koncept zpracovat výsledek dotazu, který je zadán jako <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XNode>, nebo <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>.  
  
## <a name="support-for-xpathnavigator"></a>Podpora pro objektem XPathNavigator nastaveným na  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje podporu pro <xref:System.Xml.XPath.XPathNavigator> prostřednictvím metody rozšíření v <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů. Další informace naleznete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
## <a name="support-for-white-space-and-indentation"></a>Podpora pro prázdné znaky a odsazení  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zpracovává prázdných jednodušeji než modelu DOM.  
  
 Běžný scénář, kdy je pro čtení odsazený XML, vytvoření stromu XML v paměti bez ostatní uzly text prázdné znaky (tedy ne zachování prázdné znaky), provádění některých operací na XML a pak uložte soubor XML s odsazením. Při serializaci XML s formátováním je zachována pouze významný prázdný znak ve stromové struktuře XML. Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Další z typických možností je číst a upravovat kód XML, který již byl záměrně odsazeny. Nebudete chtít změnit tento odsazení žádným způsobem. V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete to provést tak, že zachování prázdných znaků při načtení nebo analyzovat kód XML a zakázání formátování při serializaci kódu XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ukládá prázdný znak jako <xref:System.Xml.Linq.XText> uzlu, namísto nutnosti specializovaný <xref:System.Xml.XmlNodeType.Whitespace> typ uzlu, jako v modelu DOM nemá.  
  
## <a name="support-for-annotations"></a>Podporu pro poznámky  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] prvky podporují rozšiřitelnou sadu poznámky. To je užitečné pro sledování různé informace o elementu, jako je například informace o schématu, informace o tom, zda elementu je vázán na uživatelské rozhraní nebo nějakých jiných informací druh specifické pro aplikaci. Další informace najdete v tématu [LINQ to XML poznámky](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-annotations.md).  
  
## <a name="support-for-schema-information"></a>Podpora pro informace o schématu  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje podporu pro ověření XSD prostřednictvím metody rozšíření v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů. Můžete ověřit, že stromu XML v souladu s XSD. Můžete naplnit stromu XML pomocí informační sadu po ověření (PSVI). Další informace najdete v tématu [jak: Ověření pomocí XSD](../../../../csharp/programming-guide/concepts/linq/how-to-validate-using-xsd-linq-to-xml.md) a <xref:System.Xml.Schema.Extensions>.  
  
## <a name="see-also"></a>Viz také:

- [Začínáme (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)

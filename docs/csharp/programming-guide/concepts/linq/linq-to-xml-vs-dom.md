---
title: Technologie LINQ to XML vs. MODEL DOM (C#)
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 819c507f02d6671592fd8c0239df50c1ea4325b5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="linq-to-xml-vs-dom-c"></a>Technologie LINQ to XML vs. MODEL DOM (C#)
Tato část popisuje některé hlavní rozdíly mezi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] a aktuální převládá XML programovací rozhraní API, W3C Model DOM (Document Object).  
  
## <a name="new-ways-to-construct-xml-trees"></a>Nové způsoby, jak vytvořit stromy XML  
 V modelu DOM W3C sestavení strom XML zdola nahoru; To znamená vytvoření dokumentu, můžete vytvořit elementy a poté přidejte elementy v dokumentu.  
  
 Například následující by typické způsob, jak vytvořit strom XML pomocí implementace Microsoft DOM, <xref:System.Xml.XmlDocument>:  
  
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
  
 Tento styl kódování neposkytuje vizuálně velkého množství informací o struktuře stromu XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] podporuje tento přístup k vytváření strom XML, ale také podporuje alternativní způsob, *funkční konstrukce*. Funkční konstrukce používá <xref:System.Xml.Linq.XElement> a <xref:System.Xml.Linq.XAttribute> konstruktory k sestavení strom XML.  
  
 Zde je, jak by vytvořit stejném stromu pro XML pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] funkční konstrukce:  
  
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
  
 Všimněte si, že odsazení kódu k vytvoření stromu XML ukazuje strukturu základní XML.  
  
 Další informace najdete v tématu [vytváření stromů XML (C#)](../../../../csharp/programming-guide/concepts/linq/creating-xml-trees.md).  
  
## <a name="working-directly-with-xml-elements"></a>Práce přímo se elementy XML  
 Když budete programu s XML, hlavním cílem je obvykle na elementy XML a případně na atributy. V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], může spolupracovat přímo s XML elementů a atributů. Například můžete provést následující:  
  
-   Vytvořte elementů XML pomocí objektu dokumentu vůbec. Tato funkce zjednodušuje programování při práci s fragmenty stromy XML.  
  
-   Zatížení `T:System.Xml.Linq.XElement` objekty přímo ze souboru XML.  
  
-   Serializovat `T:System.Xml.Linq.XElement` objekty do souboru nebo datový proud.  
  
 Výsledky porovnejte s DOM W3C, ve kterém se používá v dokumentu XML jako logický kontejner pro stromové struktuře XML. V modelu DOM musí být vytvořený z uzlů XML, včetně elementů a atributů, v rámci dokument XML. Zde je fragment kódu, chcete-li vytvořit název elementu v modelu DOM:  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 Pokud chcete použít element napříč více dokumentů, je nutné naimportovat uzly na dokumentech. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zabraňuje tuto vrstvu složitost.  
  
 Při použití technologie LINQ to XML, můžete použít <xref:System.Xml.Linq.XDocument> třídy pouze v případě, že chcete přidat instrukcí komentářů nebo zpracování na kořenové úrovni dokumentu.  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Zjednodušená zpracování názvy a obory názvů  
 Zpracování názvy, obory názvů a předpony oboru názvů je obecně komplexní součástí programování XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zjednodušuje názvy a obory názvů odstraněním požadavek jak nakládat s předpony oboru názvů. Pokud chcete řídit předpony oboru názvů, můžete. Ale pokud se rozhodnete řídit není explicitně předpony oboru názvů [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] přidělí předpony oboru názvů během serializace, pokud jsou požadované, nebo se serializovat pomocí výchozí obory názvů, pokud nejsou. Pokud se používají výchozí obory názvů, budou ve výsledném dokumentu existovat žádné předpony oboru názvů. Další informace najdete v tématu [práci s obory názvů XML (C#)](../../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md).  
  
 Dalším problémem s modelu DOM je, že ji neumožňuje změnit název uzlu. Místo toho budete muset vytvořit nový uzel a zkopírujte všechny podřízené uzly, došlo ke ztrátě identitě původní uzel. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] tomuto problému se vyhnete tím, že vám nastavit <xref:System.Xml.Linq.XName> vlastnost na uzlu.  
  
## <a name="static-method-support-for-loading-xml"></a>Podpora statickou metodu pro načítání dat XML  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] umožňuje načíst XML pomocí statické metody, namísto metody instance. Tato funkce zjednodušuje načítání a analýzu. Další informace najdete v tématu [postupy: načtení XML ze souboru (C#)](../../../../csharp/programming-guide/concepts/linq/how-to-load-xml-from-a-file.md).  
  
## <a name="removal-of-support-for-dtd-constructs"></a>Odebrání podpory pro DTD konstrukce  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Další zjednodušuje programování odebráním podporu pro entity a odkazy na entity XML. Správa entit je složitý a je používána zřídka. Odebrání jejich podpora zvyšuje výkon a zjednodušuje programovací rozhraní. Když [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] stromu je vyplněný, jsou všechny entity DTD rozšířit.  
  
## <a name="support-for-fragments"></a>Podpora pro fragmenty  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] neposkytuje ekvivalentní pro `XmlDocumentFragment` třídy. V mnoha případech ale `XmlDocumentFragment` koncept může zpracovávat výsledek dotazu, který je zadán jako <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XNode>, nebo <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>.  
  
## <a name="support-for-xpathnavigator"></a>Podpora pro objektem XPathNavigator nastaveným na  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje podporu pro <xref:System.Xml.XPath.XPathNavigator> prostřednictvím metody rozšíření v <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů. Další informace naleznete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
## <a name="support-for-white-space-and-indentation"></a>Podpora pro mezer a odsazení  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] zpracovává mezer jednodušeji než modelu DOM.  
  
 Běžný scénář je číst zobrazují odsazené XML, vytvořte ve stromu v paměti XML bez mezer text uzlů (tedy ne zachování mezer), provádění některých operací na soubor XML a potom uložte soubor XML s odsazení. Při serializaci XML s formátování se zachová jenom významné mezer ve stromové struktuře XML. Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].  
  
 Další z typických možností je číst a upravovat kód XML, který je už záměrně zobrazují odsazené. Možná chcete změnit toto odsazení žádným způsobem. V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], můžete to udělat zachování mezer při načtení nebo analyzovat soubor XML a zakázání formátování při serializaci XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ukládá mezer jako <xref:System.Xml.Linq.XText> uzlu, místo nutnosti specializované <xref:System.Xml.XmlNodeType.Whitespace> typ uzlu jako modelu DOM nemá.  
  
## <a name="support-for-annotations"></a>Podpora pro poznámky  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] elementy podporovat rozšiřitelnou sadu poznámky. To je užitečné pro sledování různé informace o elementu, například informace o schématu, informace o tom, jestli je vázána element uživatelského rozhraní nebo všechny ostatní informace druh specifické pro aplikaci. Další informace najdete v tématu [technologie LINQ to XML poznámky](http://msdn.microsoft.com/library/e2f0052d-61e2-48d4-9ea4-356c9cab35d5).  
  
## <a name="support-for-schema-information"></a>Podpora pro informace o schématu  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] poskytuje podporu pro ověření XSD prostřednictvím metody rozšíření v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů. Můžete ověřit, že ve stromu XML v souladu se XSD. Jej můžete naplnit stromu XML s informační sadu po schema ověření (PSVI). Další informace najdete v tématu [postupy: ověření pomocí XSD](http://msdn.microsoft.com/library/481a97fa-6e96-46f2-8c9a-415555fac33b) a <xref:System.Xml.Schema.Extensions>.  
  
## <a name="see-also"></a>Viz také  
 [Začínáme (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/getting-started-linq-to-xml.md)

---
title: LINQ na XML vs. DOM (C#)
ms.date: 07/20/2015
ms.assetid: 51c0e3d2-c047-4e6a-a423-d61a882400b7
ms.openlocfilehash: 92d0da494829d57517d52fe93a3cbcf1398fdbe4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79168386"
---
# <a name="linq-to-xml-vs-dom-c"></a>LINQ na XML vs. DOM (C#)
Tato část popisuje některé klíčové [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] rozdíly mezi a aktuální převládající XML programovací rozhraní API, W3C document object model (DOM).  
  
## <a name="new-ways-to-construct-xml-trees"></a>Nové způsoby vytváření stromů XML  
 V W3C DOM vytvoříte strom XML zdola nahoru; to znamená, že vytvoříte dokument, vytvoříte prvky a potom přidáte prvky do dokumentu.  
  
 Například následující by typický způsob, jak vytvořit strom XML pomocí implementace <xref:System.Xml.XmlDocument>Microsoft DOM, :  
  
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
  
 Tento styl kódování vizuálně neposkytuje mnoho informací o struktuře stromu XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]podporuje tento přístup k vytváření stromu XML, ale také podporuje alternativní přístup, *funkční konstrukce*. Funkční konstrukce <xref:System.Xml.Linq.XElement> používá <xref:System.Xml.Linq.XAttribute> konstruktory a k vytvoření stromu XML.  
  
 Zde je, jak byste vytvořit stejný [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] strom XML pomocí funkční konstrukce:  
  
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
  
 Všimněte si, že odsazení kódu pro vytvoření stromu XML ukazuje strukturu podkladového XML.  
  
 Další informace naleznete [v tématu Creating XML Trees (C#)](./linq-to-xml-overview.md).  
  
## <a name="working-directly-with-xml-elements"></a>Práce přímo s elementy XML  
 Při programování pomocí jazyka XML je primární zaměření obvykle na elementy XML a možná i na atributy. V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]aplikaci můžete pracovat přímo s prvky a atributy XML. Můžete například provést následující kroky:  
  
- Vytvořte elementy XML bez použití objektu dokumentu vůbec. To zjednodušuje programování, když budete muset pracovat s fragmenty stromů XML.  
  
- Načtěte `T:System.Xml.Linq.XElement` objekty přímo ze souboru XML.  
  
- Serialize `T:System.Xml.Linq.XElement` objektů do souboru nebo datového proudu.  
  
 Porovnejte to s W3C DOM, ve kterém je dokument XML použit jako logický kontejner pro strom XML. V dom uzly XML, včetně prvků a atributů, musí být vytvořeny v kontextu dokumentu XML. Zde je fragment kódu k vytvoření elementu názvu v DOM:  
  
```csharp  
XmlDocument doc = new XmlDocument();  
XmlElement name = doc.CreateElement("Name");  
name.InnerText = "Patrick Hines";  
doc.AppendChild(name);  
```  
  
 Pokud chcete použít prvek ve více dokumentech, musíte importovat uzly mezi dokumenty. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]této vrstvě složitosti.  
  
 Při použití LINQ do XML, použijte třídu pouze v <xref:System.Xml.Linq.XDocument> případě, že chcete přidat komentář nebo instrukce pro zpracování na kořenové úrovni dokumentu.  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Zjednodušené zpracování názvů a oborů názvů  
 Zpracování názvů, oborů názvů a předpon oboru názvů je obecně složitou součástí programování XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zjednodušuje názvy a obory názvů tím, že eliminuje požadavek na řešení předpon oboru názvů. Pokud chcete řídit předpony oboru názvů, můžete. Pokud se však rozhodnete explicitně neřídit předpony oboru názvů, přiřadí předpony oboru názvů během serializace, pokud jsou požadovány, nebo serializuje pomocí výchozích oborů názvů, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] pokud nejsou. Pokud jsou použity výchozí obory názvů, nebudou ve výsledném dokumentu žádné předpony oboru názvů. Další informace naleznete [v tématu Přehled oborů názvů (LINQ to XML) (C#)](namespaces-overview-linq-to-xml.md).  
  
 Dalším problémem s DOM je, že neumožňuje změnit název uzlu. Místo toho budete muset vytvořit nový uzel a zkopírovat všechny podřízené uzly do něj, ztrácí původní uzel identity. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zabraňuje tomuto problému tím, <xref:System.Xml.Linq.XName> že umožňuje nastavit vlastnost na uzlu.  
  
## <a name="static-method-support-for-loading-xml"></a>Podpora statické metody pro načítání XML  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]umožňuje načíst XML pomocí statických metod namísto metod instance. To zjednodušuje načítání a analýzu. Další informace naleznete v tématu [Jak načíst XML ze souboru (C#)](./how-to-load-xml-from-a-file.md).  
  
## <a name="removal-of-support-for-dtd-constructs"></a>Odstranění podpory pro DTD konstrukce  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]dále zjednodušuje programování XML odebráním podpory pro entity a odkazy na entity. Správa subjektů je složitá a používá se jen zřídka. Odebrání jejich podpory zvyšuje výkon a zjednodušuje programovací rozhraní. Při [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] naplnění stromu jsou rozbaleny všechny entity DTD.  
  
## <a name="support-for-fragments"></a>Podpora fragmentů  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]neposkytuje ekvivalent pro `XmlDocumentFragment` třídu. V mnoha případech však `XmlDocumentFragment` koncept může být zpracován a výsledkem <xref:System.Collections.Generic.IEnumerable%601> dotazu, který je zadán jako <xref:System.Xml.Linq.XNode>, nebo <xref:System.Collections.Generic.IEnumerable%601> . <xref:System.Xml.Linq.XElement>  
  
## <a name="support-for-xpathnavigator"></a>Podpora pro XPathNavigator  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje podporu <xref:System.Xml.XPath.XPathNavigator> pro metody <xref:System.Xml.XPath?displayProperty=nameWithType> rozšíření v oboru názvů. Další informace naleznete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
## <a name="support-for-white-space-and-indentation"></a>Podpora prázdného místa a odsazení  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zpracovává prázdné místo jednodušeji než dom.  
  
 Běžným scénářem je čtení odsazeného xml, vytvoření stromu XML v paměti bez uzly prázdného textu (to znamená nezachování prázdného místa), provedení některých operací v xml a následné uložení XML s odsazením. Při serializaci xml s formátováním se zachová pouze významné prázdné místo ve stromu XML. Toto je výchozí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]chování pro aplikace .  
  
 Dalším běžným scénářem je čtení a úprava xml, který již byl záměrně odsazen. Možná nebudete chtít změnit toto odsazení v žádném případě. V [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]aplikace to lze provést tak, že při načtení nebo analyzovat xml načtete nebo analyzujete prázdné místo a při serializaci xml ukázníte formátování.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ukládá prázdné místo <xref:System.Xml.Linq.XText> jako uzel, namísto <xref:System.Xml.XmlNodeType.Whitespace> specializovaného typu uzlu, jako to dělá DOM.  
  
## <a name="support-for-annotations"></a>Podpora pro poznámky  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]prvky podporují rozšiřitelnou sadu anotací. To je užitečné pro sledování různé informace o prvku, jako jsou informace o schématu, informace o tom, zda je prvek vázán na ui nebo jakýkoli jiný druh informací specifických pro aplikaci. Další informace naleznete v tématu [LINQ to XML Anotations](./linq-to-xml-annotations.md).  
  
## <a name="support-for-schema-information"></a>Podpora informací o schématu  
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje podporu pro ověření XSD <xref:System.Xml.Schema?displayProperty=nameWithType> prostřednictvím rozšiřujících metod v oboru názvů. Můžete ověřit, zda strom XML vyhovuje xsd. Strom XML můžete naplnit informační sadou psvi po ověření schématu. Další informace naleznete v [tématu Jak ověřit pomocí XSD](./how-to-validate-using-xsd-linq-to-xml.md) a <xref:System.Xml.Schema.Extensions>.
  
## <a name="see-also"></a>Viz také

- [Začínáme (LINQ to XML)](./linq-to-xml-overview.md)

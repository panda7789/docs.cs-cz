---
title: Technologie LINQ to XML vs. model DOM
ms.date: 07/20/2015
ms.assetid: 18c36130-d598-40b7-9007-828232252978
ms.openlocfilehash: 5813ca410e3e2b1ec284681451d0c0cec6f5e393
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84389329"
---
# <a name="linq-to-xml-vs-dom-visual-basic"></a>LINQ to XML vs. DOM (Visual Basic)
Tato část popisuje některé klíčové rozdíly mezi [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] a aktuální převládající rozhraní API pro programování XML, model DOM (Document Object Model) W3C (DOM).  
  
## <a name="new-ways-to-construct-xml-trees"></a>Nové způsoby vytváření stromů XML  
 Ve formátu W3C DOM sestavíte strom XML od dolní části. To znamená, že vytvoříte dokument, vytvoříte prvky a potom přidáte prvky do dokumentu.  
  
 Následující příklad by byl typický způsob, jak vytvořit strom XML pomocí implementace modelu DOM od společnosti Microsoft <xref:System.Xml.XmlDocument> :  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
Dim phone1 As XmlElement = doc.CreateElement("Phone")  
phone1.SetAttribute("Type", "Home")  
phone1.InnerText = "206-555-0144"  
Dim phone2 As XmlElement = doc.CreateElement("Phone")  
phone2.SetAttribute("Type", "Work")  
phone2.InnerText = "425-555-0145"  
Dim street1 As XmlElement = doc.CreateElement("Street1")  
street1.InnerText = "123 Main St"  
Dim city As XmlElement = doc.CreateElement("City")  
city.InnerText = "Mercer Island"  
Dim state As XmlElement = doc.CreateElement("State")  
state.InnerText = "WA"  
Dim postal As XmlElement = doc.CreateElement("Postal")  
postal.InnerText = "68042"  
Dim address As XmlElement = doc.CreateElement("Address")  
address.AppendChild(street1)  
address.AppendChild(city)  
address.AppendChild(state)  
address.AppendChild(postal)  
Dim contact As XmlElement = doc.CreateElement("Contact")  
contact.AppendChild(name)  
contact.AppendChild(phone1)  
contact.AppendChild(phone2)  
contact.AppendChild(address)  
Dim contacts As XmlElement = doc.CreateElement("Contacts")  
contacts.AppendChild(contact)  
doc.AppendChild(contacts)  
Console.WriteLine(doc.OuterXml)  
```  
  
 Tento styl kódování vizuálně neposkytuje mnoho informací o struktuře stromu XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]podporuje tento přístup k sestavení stromu XML, ale také podporuje alternativní přístup, *funkční konstrukci*. V Visual Basic konstrukce funkčnosti používá literály XML k sestavení stromu XML.  
  
 Tady je postup vytvoření stejného stromu XML pomocí [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] funkční konstrukce:  
  
```vb  
Dim contacts = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="Home">206-555-0144</Phone>  
            <Phone Type="Work">425-555-0145</Phone>  
            <Address>  
                <Street1>123 Main St</Street1>  
                <City>Mercer Island</City>  
                <State>WA</State>  
                <Postal>68042</Postal>  
            </Address>  
        </Contact>  
    </Contacts>  
```  
  
 Všimněte si, že odsazení kódu pro sestavení stromu XML ukazuje strukturu podkladového XML.  
  
 Další informace naleznete v tématu [vytváření stromů XML (Visual Basic)](creating-xml-trees.md).  
  
## <a name="working-directly-with-xml-elements"></a>Práce přímo s prvky XML  
 Při programování v jazyce XML je primární fokus obvykle na prvcích XML a případně na atributy. V aplikaci [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] můžete pracovat přímo s prvky a atributy XML. Můžete například provést následující akce:  
  
- Vytvářejte XML elementy bez použití objektu dokumentu vůbec. To zjednodušuje programování, pokud je třeba pracovat s fragmenty stromů XML.  
  
- Načíst `T:System.Xml.Linq.XElement` objekty přímo ze souboru XML.  
  
- Serializace `T:System.Xml.Linq.XElement` objektů do souboru nebo datového proudu.  
  
 Porovnejte je s konsorciem W3C DOM, ve kterém je dokument XML použit jako logický kontejner pro strom XML. V modelu DOM, uzly XML, včetně elementů a atributů, musí být vytvořeny v kontextu dokumentu XML. Tady je fragment kódu pro vytvoření elementu Name v modelu DOM:  
  
```vb  
Dim doc As XmlDocument = New XmlDocument()  
Dim name As XmlElement = doc.CreateElement("Name")  
name.InnerText = "Patrick Hines"  
doc.AppendChild(name)  
```  
  
 Chcete-li použít prvek v rámci více dokumentů, je nutné importovat uzly mezi dokumenty. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zabrání této vrstvě složitosti.  
  
 Při použití LINQ to XML použijte <xref:System.Xml.Linq.XDocument> třídu pouze v případě, že chcete přidat komentář nebo pokyn ke zpracování na kořenové úrovni dokumentu.  
  
## <a name="simplified-handling-of-names-and-namespaces"></a>Zjednodušené zpracování názvů a oborů názvů  
 Zpracování názvů, oborů názvů a předpon oboru názvů je všeobecně složitou součástí programování XML. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zjednodušuje názvy a obory názvů tím, že eliminuje nutnost zabývat se předponami oboru názvů. Pokud chcete řídit předpony oboru názvů, můžete. Ale pokud se rozhodnete, že nechcete explicitně řídit předpony oboru názvů, [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] přiřadí předpony oboru názvů během serializace, pokud jsou požadovány, nebo budou serializovány pomocí výchozích oborů názvů, pokud nejsou. Pokud jsou použity výchozí obory názvů, nebudou ve výsledném dokumentu žádné předpony oboru názvů. Další informace najdete v tématu [obory názvů Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).  
  
 Dalším problémem s modelem DOM je, že neumožňuje změnit název uzlu. Místo toho je nutné vytvořit nový uzel a zkopírovat do něj všechny podřízené uzly a ztratit tak původní identitu uzlu. [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]tomuto problému se vyhnete tím, že vám umožní nastavit <xref:System.Xml.Linq.XName> vlastnost na uzlu.  
  
## <a name="static-method-support-for-loading-xml"></a>Podpora statické metody pro načítání XML  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]umožňuje načíst XML pomocí statických metod namísto instančních metod. Tím se zjednodušuje načítání a analýza. Další informace najdete v tématu [Postup: načtení XML ze souboru (Visual Basic)](how-to-load-xml-from-a-file.md).  
  
## <a name="removal-of-support-for-dtd-constructs"></a>Odebrání podpory pro konstrukce DTD  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]dále zjednodušuje programování XML odebráním podpory entit a odkazů na entity. Správa entit je složitá a používá se zřídka. Odebrání podpory zvyšuje výkon a zjednodušuje programovací rozhraní. Po [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] naplnění stromu se rozšíří všechny entity DTD.  
  
## <a name="support-for-fragments"></a>Podpora fragmentů  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]neposkytuje ekvivalent pro `XmlDocumentFragment` třídu. V mnoha případech však `XmlDocumentFragment` koncept může být zpracován výsledkem dotazu, který je zadán jako <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XNode> nebo <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement> .  
  
## <a name="support-for-xpathnavigator"></a>Podpora pro XPathNavigator  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje podporu pro <xref:System.Xml.XPath.XPathNavigator> metody rozšíření v <xref:System.Xml.XPath?displayProperty=nameWithType> oboru názvů. Další informace naleznete v tématu <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType>.  
  
## <a name="support-for-white-space-and-indentation"></a>Podpora pro prázdné znaky a odsazení  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]zpracovává prázdné znaky více než DOM.  
  
 Běžným scénářem je čtení odsazeného XML, vytvoření stromu XML v paměti bez jakýchkoli textových uzlů s prázdnými znaky (tj. bez zachovávání prázdných znaků), provedení některých operací v XML a následné uložení XML s odsazením. Při serializaci XML s formátováním je zachováno pouze významné prázdné znaky ve stromu XML. Toto je výchozí chování pro [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .  
  
 Dalším běžným scénářem je číst a upravovat kód XML, který již byl záměrně odsazen. Toto odsazení nebudete chtít nijak měnit. V můžete [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] to provést tak, že zachováte prázdné místo při načítání nebo analýze XML a zakážete formátování při serializaci kódu XML.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]ukládá prázdné znaky jako <xref:System.Xml.Linq.XText> uzel namísto typu specializovaného <xref:System.Xml.XmlNodeType.Whitespace> uzlu jako Dom.  
  
## <a name="support-for-annotations"></a>Podpora poznámek  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]prvky podporují rozšiřitelnou sadu poznámek. To je užitečné pro sledování různých informací o prvku, například informace o schématu, informace o tom, zda je element svázán s uživatelským rozhraním, nebo jakýkoli jiný druh informací specifických pro aplikaci. Další informace najdete v tématu [LINQ to XML poznámky](linq-to-xml-annotations.md).  
  
## <a name="support-for-schema-information"></a>Podpora informací o schématu  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]poskytuje podporu pro ověřování XSD prostřednictvím metod rozšíření v <xref:System.Xml.Schema?displayProperty=nameWithType> oboru názvů. Můžete ověřit, že strom XML odpovídá XSD. Ke stromu XML můžete naplnit informační sadu po PSVI (post-Schema-Revalidace). Další informace naleznete v tématu [Postupy: ověřování pomocí XSD](how-to-validate-using-xsd-linq-to-xml.md) a <xref:System.Xml.Schema.Extensions> .  
  
## <a name="see-also"></a>Viz také

- [Začínáme (LINQ to XML)](getting-started-linq-to-xml.md)

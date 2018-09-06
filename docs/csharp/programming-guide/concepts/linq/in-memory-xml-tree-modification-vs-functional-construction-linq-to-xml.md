---
title: Změna stromu XML v paměti vs. Funkční konstrukce (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 836141185629683106698cc9b505c063de6c445e
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "44039553"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a>Změna stromu XML v paměti vs. Funkční konstrukce (LINQ to XML) (C#)
Změna stromu XML v místě je tradiční přístup na měnící tvar dokumentu XML. Typická aplikace načte dokument do úložiště dat, jako je například modelu DOM nebo [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; používá programovací rozhraní pro vložení uzlů, odstraňovat uzly nebo změnit obsah uzlů a pak uloží do souboru XML nebo přenáší přes síť.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] Další možností, které jsou užitečné v mnoha scénářích umožňuje *: funkční konstrukce*. Funkční konstrukce zpracovává změny dat, jako problém transformace, nikoli jako podrobné manipulaci s úložištěm dat. Pokud můžete vzít vyjádření data a transformovali je efektivní z jednoho formuláře do jiného, výsledek je stejný, jako by trvalo jednoho úložiště dat a manipulovat nějakým způsobem provést jiný tvar. Klíč k přístupu funkční konstrukce je předat výsledky dotazů pro <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement> konstruktory.  
  
 V mnoha případech můžete napsat kód transformace, jehož za zlomek času, který by to obnášelo k práci s úložišti dat a tento kód je robustní a jednodušší správu. V těchto případech i v případě, že transformace, jehož přístupu může trvat více výpočetního výkonu, je efektivnější způsob, jak upravovat data. Pokud vývojář zkušenosti s funkční přístup, je výsledný kód v mnoha případech lze snáze pochopit. Je snadné kód, který upravuje jednotlivých součástí stromu.  
  
 Místo, kde upravíte XML stromu místní přístup je více do hloubky na mnoho programátorů modelu DOM, zatímco kód napsané s využitím funkční přístup může být nevypadá to povědomě pro vývojáře, kteří ještě nerozumí tento přístup. Pokud je nutné provést pouze malé změny do velké stromu XML, přístup místo, kde upravíte stromu je v mnoha případech bude trvat méně času procesoru.  
  
 V tomto tématu poskytuje příklad, který implementuje pomocí obou metod.  
  
## <a name="transforming-attributes-into-elements"></a>Transformace atributů na prvky  
 V tomto příkladu předpokládejme, že chcete změnit následující jednoduchý dokument XML tak, aby atributy stát elementů. Toto téma představuje první přístup tradiční místní úpravy. Potom zobrazí funkční konstrukce přístup.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a>Změna stromu XML  
 Můžete napsat kód procedury k vytváření prvků z atributů a atributů, odstraňte následujícím způsobem:  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 Tento kód vytvoří následující výstup:  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a>Funkční konstrukce přístup  
 Naopak funkční přístup se skládá z kódu k vytvoření nové větve, výběru a Výběr elementů a atributů ze stromu zdrojového kódu a transformují je podle potřeby, jako jsou přidány do nového stromu. Funkční přístup vypadá takto:  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 V tomto příkladu vrátí stejné XML jako v prvním příkladu. Všimněte si však, že vidíte ve skutečnosti výsledný struktura nový kód XML v funkční přístup. Můžete zobrazit vytvořením `Root` elementu, kód, který si vyžádá `Child1` element ze stromu zdrojového kódu a kód, který transformuje atributy ze stromu zdrojového kódu na prvky do nového stromu.  
  
 Funkční příklad v tomto případě není žádná kratší než v prvním příkladu, a není ve skutečnosti jednodušší. Nicméně pokud máte mnoho změn tak, aby stromu XML nefunkční přístup se stanou poměrně složité a trochu obtuse. Naopak při použití funkční přístup, stále pouze formulář požadované XML vkládat dotazy a výrazy podle potřeby, aby se načetla požadovaný obsah. Funkční přístup poskytuje kód, který je snazší Údržba.  
  
 Všimněte si, že v tomto případě funkční přístup pravděpodobně nebude provádět úplně stejně přístup zpracování stromu. Hlavní problém je, že vytvoří funkční přístup více krátký povahy objekty. Výměnou za to však je efektivní jeden, pokud pomocí funkční přístup umožňuje vyšší produktivita programátorů.  
  
 To je velmi jednoduchý příklad, ale funguje zobrazíte filozofie rozdíl mezi dvěma přístupy. Funkční přístup poskytuje větší zvýšení produktivity pro transformaci větší dokumentů XML.  
  
## <a name="see-also"></a>Viz také

- [Změna stromů XML (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)

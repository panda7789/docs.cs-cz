---
title: Úprava stromu XML v paměti vs. funkční konstrukce (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 55eb95585bdd5d2c52175cacae2e6d049bd06f69
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "66484554"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a>Úprava stromu XML v paměti vs. funkční konstrukce (LINQ to XML) (C#)
Změna stromu XML na místě je tradiční přístup ke změně tvaru dokumentu XML. Typická aplikace načte dokument do úložiště dat, jako je například DOM nebo [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]; používá programovací rozhraní k vkládání uzlů, odstraňování uzlů nebo změně obsahu uzlů; a potom uloží XML do souboru nebo jej odešle v síti.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]umožňuje jiný přístup, který je užitečný v mnoha scénářích: *funkční konstrukce*. Funkční konstrukce považuje úpravy dat za problém transformace, nikoli jako podrobnou manipulaci s úložištěm dat. Pokud můžete vzít reprezentaci dat a efektivně je transformovat z jednoho formuláře do druhého, výsledek je stejný, jako kdybyste vzali jedno úložiště dat a nějakým způsobem s ním manipulovali, aby se vzal jiný tvar. Klíčem k přístupu funkce konstrukce je předat výsledky <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> dotazů a konstruktory.  
  
 V mnoha případech můžete napsat transformační kód ve zlomku času, který by trvalo manipulovat úložiště dat a že kód je robustnější a snadněji udržovat. V těchto případech i v případě, že transformační přístup může trvat více výpočetní výkon, je efektivnější způsob, jak upravit data. Pokud vývojář je obeznámen s funkční přístup, výsledný kód v mnoha případech je srozumitelnější. Je snadné najít kód, který upravuje každou část stromu.  
  
 Přístup, kde můžete upravit strom XML na místě je známější mnoho programátorů DOM, zatímco kód napsaný pomocí funkční ho přístupu může vypadat neznámé vývojáři, který ještě nerozumí, že přístup. Pokud máte provést pouze malé změny velké stromu XML, přístup, kde upravit strom na místě v mnoha případech bude trvat méně času procesoru.  
  
 Toto téma obsahuje příklad, který je implementován s oběma přístupy.  
  
## <a name="transforming-attributes-into-elements"></a>Transformace atributů na prvky  
 V tomto příkladu předpokládejme, že chcete upravit následující jednoduchý dokument XML tak, aby se atributy staly elementy. Toto téma nejprve představuje tradiční přístup změny na místě. To pak ukazuje funkční stavební přístup.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a>Úprava stromu XML  
 Můžete napsat nějaký procedurální kód pro vytvoření prvků z atributů a potom odstranit atributy takto:  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
foreach (XAttribute att in root.Attributes()) {  
    root.Add(new XElement(att.Name, (string)att));  
}  
root.Attributes().Remove();  
Console.WriteLine(root);  
```  
  
 Výsledkem tohoto kódu je následující výstup:  
  
```xml  
<Root>  
  <Child1>Content</Child1>  
  <Data1>123</Data1>  
  <Data2>456</Data2>  
</Root>  
```  
  
### <a name="functional-construction-approach"></a>Přístup k funkční konstrukci  
 Naproti tomu funkční přístup se skládá z kódu k vytvoření nového stromu, vychystávání a výběr u prvků a atributů ze zdrojového stromu a jejich transformace podle potřeby, jak jsou přidány do nového stromu. Funkční přístup vypadá takto:  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 Tento příklad vyvezuje stejný XML jako první příklad. Všimněte si však, že můžete skutečně zobrazit výslednou strukturu nového XML ve funkčním přístupu. Můžete vidět vytvoření `Root` prvku, kód, který vytáhne `Child1` prvek ze zdrojového stromu a kód, který transformuje atributy ze zdrojového stromu na prvky v novém stromu.  
  
 Funkční příklad v tomto případě není o nic kratší než první příklad a není to opravdu jednodušší. Pokud však máte mnoho změn, které chcete provést ve stromu XML, nefunkční přístup se stane poměrně složitým a poněkud tupým. Naproti tomu při použití funkčního přístupu stále tvoříte pouze požadovaný xml, vkládání dotazů a výrazů podle potřeby, chcete-li získat požadovaný obsah. Funkční přístup poskytuje kód, který je snadněji udržovat.  
  
 Všimněte si, že v tomto případě by funkční přístup pravděpodobně neprovedl tak dobře, jako přístup manipulace se stromem. Hlavním problémem je, že funkční přístup vytváří více krátkodobých objektů. Kompromis je však efektivní, pokud použití funkčního přístupu umožňuje větší produktivitu programátorů.  
  
 Jedná se o velmi jednoduchý příklad, ale slouží k zobrazení rozdílu ve filozofii mezi těmito dvěma přístupy. Funkční přístup přináší vyšší nárůst produktivity při transformaci větších dokumentů XML.  
  
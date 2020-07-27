---
title: Úprava struktury XML v paměti vs. konstrukce funkčnosti (LINQ to XML) (C#)
description: Tyto příklady změní tvar dokumentu XML úpravou na místě a pomocí LINQ to XML funkční konstrukce v jazyce C#.
ms.date: 07/20/2015
ms.assetid: b5afc31d-a325-4ec6-bf17-0ff90a20ffca
ms.openlocfilehash: 7a2e3d2ddcd452cf6a58e9d5cc886f3e8b8dd325
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165777"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-c"></a>Úprava struktury XML v paměti vs. konstrukce funkčnosti (LINQ to XML) (C#)
Úprava stromu XML na místě je tradiční přístup ke změně tvaru dokumentu XML. Typická aplikace načte dokument do úložiště dat, jako je DOM nebo [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ; používá programovací rozhraní pro vkládání uzlů, odstraňování uzlů nebo změnu obsahu uzlů a pak ukládá XML do souboru nebo ho přenáší přes síť.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]umožňuje další přístup, který je užitečný v mnoha scénářích: *konstrukce funkcí*. Funkční konstrukce zpracovává změny dat jako problém transformace, nikoli jako podrobnou manipulaci s úložištěm dat. Pokud můžete podniknout data a efektivně je transformovat z jednoho formuláře na jiný, výsledek je stejný jako v případě, že jste si pořídili jedno úložiště dat a manipulujete ho nějakým způsobem, aby byl jiný tvar. Klíč k přístupu k funkcím konstrukce je předání výsledků dotazů do <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> konstruktorů a.  
  
 V mnoha případech můžete napsat transformační kód za zlomek času, který by trval při manipulaci s úložištěm dat, a tento kód je robustnější a snazší ho udržovat. V těchto případech i v případě, že transformační přístup může trvat více výpočetní výkon, je efektivnější způsob, jak data upravovat. Pokud je vývojář obeznámen s funkcí přístupu, výsledný kód v mnoha případech je snazší pochopit. Je snadné najít kód, který upraví jednotlivé části stromu.  
  
 Přístup, při kterém upravíte strom XML na místě, je více známý pro mnoho programátorů modelu DOM, zatímco kód napsaný pomocí funkčního přístupu může vypadat neznámým vývojářům, kteří tento přístup ještě neznají. Pokud je třeba udělat pouze malou úpravu velkého stromu XML, přístup, který upravujete stromovou strukturu v mnoha případech, bude trvat méně času procesoru.  
  
 Toto téma poskytuje příklad, který je implementován pomocí obou přístupů.  
  
## <a name="transforming-attributes-into-elements"></a>Transformace atributů na elementy  
 V tomto příkladu Předpokládejme, že chcete upravit následující jednoduchý dokument XML, aby se atributy staly elementy. V tomto tématu se nejdřív prezentuje tradiční místní modifikace. Pak zobrazuje přístup k konstrukci funkčnosti.  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Root Data1="123" Data2="456">  
  <Child1>Content</Child1>  
</Root>  
```  
  
### <a name="modifying-the-xml-tree"></a>Úprava stromu XML  
 Můžete napsat nějaký procedurální kód pro vytvoření prvků z atributů a poté odstranit atributy následujícím způsobem:  
  
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
  
### <a name="functional-construction-approach"></a>Přístup k konstrukci funkčnosti  
 Naproti tomu funkční přístup se skládá z kódu pro vytvoření nové stromové struktury, výběru a výběru prvků a atributů ze zdrojového stromu a jejich transformaci podle potřeby, jak jsou přidány do nového stromu. Funkční přístup vypadá takto:  
  
```csharp  
XElement root = XElement.Load("Data.xml");  
XElement newTree = new XElement("Root",  
    root.Element("Child1"),  
    from att in root.Attributes()  
    select new XElement(att.Name, (string)att)  
);  
Console.WriteLine(newTree);  
```  
  
 Tento příklad vytvoří výstup stejného XML jako první příklad. Všimněte si však, že ve skutečnosti vidíte výslednou strukturu nového XML v rámci funkčního přístupu. Můžete zobrazit vytvoření `Root` elementu, kód, který přebírá `Child1` element ze zdrojového stromu, a kód, který transformuje atributy ze zdrojového stromu na prvky v novém stromu.  
  
 Funkční příklad v tomto případě není kratší než první příklad a není skutečně jednodušší. Nicméně pokud máte mnoho změn ve stromu XML, nefunkční přístup se stane poměrně složitým a trochu obtuse. Naopak pokud používáte funkční přístup, stále stačí vytvořit požadovaný kód XML, vložit dotazy a výrazy podle potřeby a vyžádat si požadovaný obsah. Funkční přístup poskytuje kód, který je snazší udržovat.  
  
 Všimněte si, že v takovém případě funkční přístup pravděpodobně nepracuje úplně stejně jako přístup ke stromové manipulaci. Hlavním problémem je to, že funkční přístup vytváří krátkodobé objekty pro dlouhodobé vyzkoušení. Kompromis je ale platný, pokud použití funkčního přístupu umožňuje větší produktivitu programátorů.  
  
 Toto je velmi jednoduchý příklad, ale slouží k zobrazení rozdílu v filozofie mezi dvěma přístupy. Funkční přístup poskytuje větší produktivitu při transformaci větších dokumentů XML.  
  
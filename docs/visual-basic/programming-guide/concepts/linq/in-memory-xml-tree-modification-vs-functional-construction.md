---
title: Změna stromu XML v paměti vs. funkční konstrukce (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: d91c4ebf-6549-43cc-9961-26d4a82f722b
ms.openlocfilehash: efdbf51efa0f502ac9991d520defe45bb95678b7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397606"
---
# <a name="in-memory-xml-tree-modification-vs-functional-construction-linq-to-xml-visual-basic"></a>Úprava struktury XML v paměti vs. konstrukce funkčnosti (LINQ to XML) (Visual Basic)
Úprava stromu XML na místě je tradiční přístup ke změně tvaru dokumentu XML. Typická aplikace načte dokument do úložiště dat, jako je DOM nebo [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] ; používá programovací rozhraní pro vkládání uzlů, odstraňování uzlů nebo změnu obsahu uzlů a pak ukládá XML do souboru nebo ho přenáší přes síť.  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]umožňuje další přístup, který je užitečný v mnoha scénářích *: konstrukce funkcí*. Funkční konstrukce zpracovává změny dat jako problém transformace, nikoli jako podrobnou manipulaci s úložištěm dat. Pokud můžete podniknout data a efektivně je transformovat z jednoho formuláře na jiný, výsledek je stejný jako v případě, že jste si pořídili jedno úložiště dat a manipulujete ho nějakým způsobem, aby byl jiný tvar. Klíč k přístupu k funkcím konstrukce je předání výsledků dotazů do <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> konstruktorů a.  
  
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
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
For Each att As XAttribute In root.Attributes()  
    root.Add(New XElement(att.Name, att.Value))  
Next  
root.Attributes().Remove()  
Console.WriteLine(root)  
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
  
```vb  
Dim root As XElement = XElement.Load("Data.xml")  
Dim newTree As XElement = _  
    <Root>  
        <%= root.<Child1> %>  
        <%= From att In root.Attributes() _  
            Select New XElement(att.Name, att.Value) %>  
    </Root>  
Console.WriteLine(newTree)  
```  
  
 Tento příklad vytvoří výstup stejného XML jako první příklad. Všimněte si však, že ve skutečnosti vidíte výslednou strukturu nového XML v rámci funkčního přístupu. Můžete zobrazit vytvoření `Root` elementu, kód, který přebírá `Child1` element ze zdrojového stromu, a kód, který transformuje atributy ze zdrojového stromu na prvky v novém stromu.  
  
 Funkční příklad v tomto případě není kratší než první příklad a není skutečně jednodušší. Nicméně pokud máte mnoho změn ve stromu XML, nefunkční přístup se stane poměrně složitým a trochu obtuse. Naopak pokud používáte funkční přístup, stále stačí vytvořit požadovaný kód XML, vložit dotazy a výrazy podle potřeby a vyžádat si požadovaný obsah. Funkční přístup poskytuje kód, který je snazší udržovat.  
  
 Všimněte si, že v takovém případě funkční přístup pravděpodobně nepracuje úplně stejně jako přístup ke stromové manipulaci. Hlavním problémem je to, že funkční přístup vytváří krátkodobé objekty pro dlouhodobé vyzkoušení. Kompromis je ale platný, pokud použití funkčního přístupu umožňuje větší produktivitu programátorů.  
  
 Toto je velmi jednoduchý příklad, ale slouží k zobrazení rozdílu v filozofie mezi dvěma přístupy. Funkční přístup poskytuje větší produktivitu při transformaci větších dokumentů XML.  
  
## <a name="see-also"></a>Viz také

- [Úprava stromů XML (LINQ to XML) (Visual Basic)](modifying-xml-trees-linq-to-xml.md)

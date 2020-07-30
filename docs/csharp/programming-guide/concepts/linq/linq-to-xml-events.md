---
title: Události LINQ to XML (C#)
description: Přidejte LINQ to XML události v C# do instance libovolné XObject. Obslužná rutina události přijímá události při změně stromu XML pro tento XObject.
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 576b0a5d0472bddd66e01d3bef8f3affa1c9458b
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165423"
---
# <a name="linq-to-xml-events-c"></a>Události LINQ to XML (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]události umožňují být upozorňovány při změně stromu XML.  
  
 Události můžete přidat do instance libovolné <xref:System.Xml.Linq.XObject> . Obslužná rutina události poté obdrží události pro úpravy tohoto <xref:System.Xml.Linq.XObject> a kteréhokoli z jeho potomků. Například můžete přidat obslužnou rutinu události do kořenového adresáře stromu a zpracovat všechny změny stromu z této obslužné rutiny události.  
  
 Příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] událostí naleznete v tématech <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed> .  
  
## <a name="types-and-events"></a>Typy a události  
 Při práci s událostmi můžete použít následující typy:  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Určuje typ události při vyvolání události pro <xref:System.Xml.Linq.XObject> .|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Poskytuje data pro <xref:System.Xml.Linq.XObject.Changing> události a <xref:System.Xml.Linq.XObject.Changed> .|  
  
 Při úpravě stromu XML jsou vyvolány následující události:  
  
|Událost|Popis|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Nastane těsně před tím, než <xref:System.Xml.Linq.XObject> se tato nebo kterákoli z jeho potomků změní.|  
|<xref:System.Xml.Linq.XObject.Changed>|Vyvolá se v případě, že došlo ke změně <xref:System.Xml.Linq.XObject> nebo některému z jeho potomků.|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Události jsou užitečné, pokud chcete zachovat některé agregované informace ve stromu XML. Například můžete chtít zachovat celkovou částku faktury, která je součtem položek řádků faktury. V tomto příkladu se používají události pro udržování celkového počtu všech podřízených elementů v rámci komplexního prvku `Items` .  
  
### <a name="code"></a>Kód  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Total", "0"),  
    new XElement("Items")  
);  
XElement total = root.Element("Total");  
XElement items = root.Element("Items");  
items.Changed += (object sender, XObjectChangeEventArgs cea) =>  
{  
    switch (cea.ObjectChange)  
    {  
        case XObjectChange.Add:  
            if (sender is XElement)  
                total.Value = ((int)total + (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total + (int)((XText)sender).Parent).ToString();  
            break;  
        case XObjectChange.Remove:  
            if (sender is XElement)  
                total.Value = ((int)total - (int)(XElement)sender).ToString();  
            if (sender is XText)  
                total.Value = ((int)total - Int32.Parse(((XText)sender).Value)).ToString();  
            break;  
    }  
    Console.WriteLine("Changed {0} {1}",  
      sender.GetType().ToString(), cea.ObjectChange.ToString());  
};  
items.SetElementValue("Item1", 25);  
items.SetElementValue("Item2", 50);  
items.SetElementValue("Item2", 75);  
items.SetElementValue("Item3", 133);  
items.SetElementValue("Item1", null);  
items.SetElementValue("Item4", 100);  
Console.WriteLine("Total:{0}", (int)total);  
Console.WriteLine(root);  
```  
  
### <a name="comments"></a>Komentáře  
 Výsledkem tohoto kódu je následující výstup:  
  
```output  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XText Remove  
Changed System.Xml.Linq.XText Add  
Changed System.Xml.Linq.XElement Add  
Changed System.Xml.Linq.XElement Remove  
Changed System.Xml.Linq.XElement Add  
Total:308  
<Root>  
  <Total>308</Total>  
  <Items>  
    <Item2>75</Item2>  
    <Item3>133</Item3>  
    <Item4>100</Item4>  
  </Items>  
</Root>  
```  
  
---
title: Události LINQ to XML (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 8e0cb4519dd0fc2bed443d9a62b9a2545d10e161
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253177"
---
# <a name="linq-to-xml-events-c"></a>Události LINQ to XML (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]události umožňují být upozorňovány při změně stromu XML.  
  
 Události můžete přidat do instance libovolné <xref:System.Xml.Linq.XObject>. Obslužná rutina události poté obdrží události pro úpravy tohoto <xref:System.Xml.Linq.XObject> a kteréhokoli z jeho potomků. Například můžete přidat obslužnou rutinu události do kořenového adresáře stromu a zpracovat všechny změny stromu z této obslužné rutiny události.  
  
 Příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] událostí naleznete v tématech <xref:System.Xml.Linq.XObject.Changing> a <xref:System.Xml.Linq.XObject.Changed>.  
  
## <a name="types-and-events"></a>Typy a události  
 Při práci s událostmi můžete použít následující typy:  
  
|type|Popis|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Určuje typ události při vyvolání události pro <xref:System.Xml.Linq.XObject>.|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Poskytuje data pro <xref:System.Xml.Linq.XObject.Changing> události a <xref:System.Xml.Linq.XObject.Changed> .|  
  
 Při úpravě stromu XML jsou vyvolány následující události:  
  
|Událost|Popis|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Nastane těsně před tím <xref:System.Xml.Linq.XObject> , než se tato nebo kterákoli z jeho potomků změní.|  
|<xref:System.Xml.Linq.XObject.Changed>|Vyvolá se v <xref:System.Xml.Linq.XObject> případě, že došlo ke změně nebo některému z jeho potomků.|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Události jsou užitečné, pokud chcete zachovat některé agregované informace ve stromu XML. Například můžete chtít zachovat celkovou částku faktury, která je součtem položek řádků faktury. V tomto příkladu se používají události pro udržování celkového počtu všech podřízených elementů v rámci komplexního prvku `Items`.  
  
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
 Tento kód generuje následující výstup:  
  
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
  
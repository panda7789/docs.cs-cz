---
title: LinQ na xml události (C#)
ms.date: 07/20/2015
ms.assetid: ce7de951-cba7-4870-9962-733eb01cd680
ms.openlocfilehash: 8e0cb4519dd0fc2bed443d9a62b9a2545d10e161
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "70253177"
---
# <a name="linq-to-xml-events-c"></a>LinQ na xml události (C#)
[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]události umožňují upozornění při změně stromu XML.  
  
 Události můžete přidat do instance <xref:System.Xml.Linq.XObject>libovolné aplikace . Obslužná rutina události pak <xref:System.Xml.Linq.XObject> obdrží události pro změny, které a všechny jeho potomci. Můžete například přidat obslužnou rutinu události do kořenového adresáře stromu a zpracovat všechny změny stromu z této obslužné rutiny události.  
  
 Příklady [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] událostí naleznete <xref:System.Xml.Linq.XObject.Changing> v <xref:System.Xml.Linq.XObject.Changed>tématu a .  
  
## <a name="types-and-events"></a>Typy a události  
 Při práci s událostmi se používají následující typy:  
  
|Typ|Popis|  
|----------|-----------------|  
|<xref:System.Xml.Linq.XObjectChange>|Určuje typ události, když je událost <xref:System.Xml.Linq.XObject>vyvolána pro .|  
|<xref:System.Xml.Linq.XObjectChangeEventArgs>|Poskytuje data <xref:System.Xml.Linq.XObject.Changing> pro <xref:System.Xml.Linq.XObject.Changed> události a.|  
  
 Při úpravě stromu XML jsou vyvolány následující události:  
  
|Událost|Popis|  
|-----------|-----------------|  
|<xref:System.Xml.Linq.XObject.Changing>|Vyskytuje se <xref:System.Xml.Linq.XObject> těsně před tím, než se toto nebo některý z jeho potomků změní.|  
|<xref:System.Xml.Linq.XObject.Changed>|Vyvolá se <xref:System.Xml.Linq.XObject> při změně nebo změně některého z jeho potomků.|  
  
## <a name="example"></a>Příklad  
  
### <a name="description"></a>Popis  
 Události jsou užitečné, pokud chcete zachovat některé souhrnné informace ve stromu XML. Můžete například chtít udržovat součet faktury, který je součtem řádkových položek faktury. Tento příklad používá události k udržení součtu všech podřízených prvků pod komplexníprvek `Items`.  
  
### <a name="code"></a>kód  
  
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
  
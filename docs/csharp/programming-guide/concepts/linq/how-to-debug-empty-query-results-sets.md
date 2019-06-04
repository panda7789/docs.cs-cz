---
title: 'Postupy: Ladění prázdných sad výsledků dotazu (C#)'
ms.date: 07/20/2015
ms.assetid: b569f0dc-425e-45a6-acbf-770fb761c981
ms.openlocfilehash: ba82e37ef4f57c78e7ba66676ba90312c2a9400f
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66485763"
---
# <a name="how-to-debug-empty-query-results-sets-c"></a>Postupy: Ladění prázdných sad výsledků dotazu (C#)
Jedním z nejběžnějších problémů při dotazování na stromy XML je, že pokud stromu XML má výchozí obor názvů, vývojář někdy zapíše dotaz jakoby nebyly v oboru názvů XML.  
  
 První sada příklady v tomto tématu ukazuje typické tak, že je načteno XML ve výchozím oboru názvů a dotazuje se nesprávně.  
  
 Druhá sada příklady ukazují potřebné opravy tak, aby můžete dát dotaz na XML v oboru názvů.  
  
 Další informace najdete v tématu [práce s názvovými prostory XML (C#)](../../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md).  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který vrací prázdný výsledek sadu.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
IEnumerable<XElement> c1 =  
    from el in root.Elements("Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 Tento příklad vytvoří následující výsledek:  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a>Příklad  
 Tento příklad ukazuje vytvoření XML v oboru názvů a dotaz, který je zakódovaný správně.  
  
 Řešením je deklarovat a inicializovat <xref:System.Xml.Linq.XNamespace> objektu a použít je při zadávání <xref:System.Xml.Linq.XName> objekty. V tomto případě, že argument <xref:System.Xml.Linq.XContainer.Elements%2A> metoda je <xref:System.Xml.Linq.XName> objektu.  
  
```csharp  
XElement root = XElement.Parse(  
@"<Root xmlns='http://www.adventure-works.com'>  
    <Child>1</Child>  
    <Child>2</Child>  
    <Child>3</Child>  
    <AnotherChild>4</AnotherChild>  
    <AnotherChild>5</AnotherChild>  
    <AnotherChild>6</AnotherChild>  
</Root>");  
XNamespace aw = "http://www.adventure-works.com";  
IEnumerable<XElement> c1 =  
    from el in root.Elements(aw + "Child")  
    select el;  
Console.WriteLine("Result set follows:");  
foreach (XElement el in c1)  
    Console.WriteLine((int)el);  
Console.WriteLine("End of result set");  
```  
  
 Tento příklad vytvoří následující výsledek:  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  

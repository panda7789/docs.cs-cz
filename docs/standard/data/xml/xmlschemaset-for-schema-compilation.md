---
title: XmlSchemaSet pro kompilaci schématu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 91835006925f9768c25ad1a984a3b189e3e4c58c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="xmlschemaset-for-schema-compilation"></a>XmlSchemaSet pro kompilaci schématu
Popisuje <xref:System.Xml.Schema.XmlSchemaSet>, mezipaměti, kde můžete ukládat a ověření schématu XML definition language (XSD) schémata.  
  
## <a name="the-xmlschemaset-class"></a>XmlSchemaSet – třída  
 <xref:System.Xml.Schema.XmlSchemaSet> Je mezipaměti, kde můžete ukládat a ověření schématu XML definition language (XSD) schémata.  
  
 V <xref:System.Xml?displayProperty=nameWithType> verze 1.0, schémat XML byly načteny do <xref:System.Xml.Schema.XmlSchemaCollection> třída jako Knihovna schémat. V <xref:System.Xml?displayProperty=nameWithType> verze 2.0, <xref:System.Xml.XmlValidatingReader> a <xref:System.Xml.Schema.XmlSchemaCollection> třídy jsou zastaralé a byly nahrazeny <xref:System.Xml.XmlReader.Create%2A> metody a <xref:System.Xml.Schema.XmlSchemaSet> třídy v uvedeném pořadí.  
  
 <xref:System.Xml.Schema.XmlSchemaSet> Je zavedený vyřešit řadu problémů, včetně kompatibility standardů, výkonu a zastaralé schéma formátu Microsoft XML-Data Reduced (XDR).  
  
 Následuje porovnání mezi <xref:System.Xml.Schema.XmlSchemaCollection> třídy a <xref:System.Xml.Schema.XmlSchemaSet> třídy.  
  
|Kolekci XmlSchemaCollection|XmlSchemaSet|  
|-------------------------|------------------|  
|Podporuje Microsoft XDR a W3C schémat XML.|Podporuje jenom schémata W3C XML.|  
|Kompilované schémata při <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metoda je volána.|Schémata nejsou kompilovat, kdy <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda je volána. To poskytuje zlepšení výkonu během vytváření knihovny schématu.|  
|Každý schématu generuje jednotlivých kompilované verze, která může mít za následek "schématu ostrovy." V důsledku toho všechny zahrnuje a importy jsou vymezeny pouze v rámci tohoto schématu.|Kompilované schémata generovat jediné logické schéma, "set" schémat. Importovaná schémata v rámci schématu, které jsou přidány do sady jsou přímo přidat do sady sami. To znamená, že všechny typy jsou k dispozici pro všechny schémat.|  
|V kolekci může existovat pouze jedno schéma pro konkrétní cílový obor názvů.|Více schématy pro stejný cílový obor názvů lze přidat, dokud nejsou konflikty typu.|  
  
## <a name="migrating-to-the-xmlschemaset"></a>Migrace na sadě XmlSchemaSet  
 Následující příklad kódu poskytuje návod k migraci na nové <xref:System.Xml.Schema.XmlSchemaSet> třídy z zastaralé <xref:System.Xml.Schema.XmlSchemaCollection> třídy. Příklad kódu ukazuje následující hlavní rozdíly mezi dvěma třídami.  
  
-   Na rozdíl od <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaCollection> třída, schémata nejsou kompilovány při volání metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Metodu <xref:System.Xml.Schema.XmlSchemaSet> je explicitně volána v ukázkovém kódu.  
  
-   Iterace nad <xref:System.Xml.Schema.XmlSchemaSet>, je nutné použít <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Toto je zastaralé <xref:System.Xml.Schema.XmlSchemaCollection> příklad kódu.  
  
```vb  
Dim schemaCollection As XmlSchemaCollection = New XmlSchemaCollection()  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema in schemaCollection  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaCollection schemaCollection = new XmlSchemaCollection();  
schemaCollection.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaCollection.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
  
foreach(XmlSchema schema in schemaCollection)  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
 Toto je ekvivalentem <xref:System.Xml.Schema.XmlSchemaSet> příklad kódu.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim schema As XmlSchema  
  
For Each schema in schemaSet.Schemas()  
  
   Console.WriteLine(schema.TargetNamespace)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
foreach(XmlSchema schema in schemaSet.Schemas())  
{  
   Console.WriteLine(schema.TargetNamespace);  
}  
```  
  
## <a name="adding-and-retrieving-schemas"></a>Přidávání a načítání schémat.  
 Schémata jsou přidány do <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet>. Po přidání schématu do <xref:System.Xml.Schema.XmlSchemaSet>, je přidružen cílový obor názvů identifikátor URI. Identifikátor URI, můžete buď zadat jako parametr pro cílový obor názvů <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda nebo pokud není zadán žádný cílový obor názvů, <xref:System.Xml.Schema.XmlSchemaSet> používá cílový obor názvů definováno ve schématu.  
  
 Schémata jsou načteny z <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Vlastnost <xref:System.Xml.Schema.XmlSchemaSet> umožňuje iterace <xref:System.Xml.Schema.XmlSchema> objekty obsažené v <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Vlastnost vrací buď všechny <xref:System.Xml.Schema.XmlSchema> objekty obsažené v <xref:System.Xml.Schema.XmlSchemaSet>, nebo zadaný cílový obor názvů parametrů, vrátí všechny <xref:System.Xml.Schema.XmlSchema> objekty, které patří do cílový obor názvů. Pokud `null` je zadána jako parametr cílový obor názvů <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost vrací všechny schémata bez oboru názvů.  
  
 Následující příklad přidá `books.xsd` schéma v `http://www.contoso.com/books` názvů <xref:System.Xml.Schema.XmlSchemaSet>, načte všechny schémat, které patří do `http://www.contoso.com/books` oboru názvů z <xref:System.Xml.Schema.XmlSchemaSet>a pak zapíše těchto schémat na <xref:System.Console>.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas("http://www.contoso.com/books")  
  
   schema.Write(Console.Out)  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas("http://www.contoso.com/books"))  
{  
   schema.Write(Console.Out);  
}  
```  
  
 Další informace o přidávání a načítání schémat ze <xref:System.Xml.Schema.XmlSchemaSet> objektu, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda a <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost referenční dokumentaci k nástroji.  
  
## <a name="compiling-schemas"></a>Kompilování schémat.  
 Schémata v <xref:System.Xml.Schema.XmlSchemaSet> kompilovány do jednoho logického schématu pomocí <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet>.  
  
> [!NOTE]
>  Na rozdíl od zastaralé <xref:System.Xml.Schema.XmlSchemaCollection> třídy, schémata nejsou kompilovat, kdy <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda je volána.  
  
 Pokud <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda provede úspěšně, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet> je nastaven na `true`.  
  
> [!NOTE]
>  <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> Vlastnost nemá vliv, pokud jsou upravit schémata během činnosti v <xref:System.Xml.Schema.XmlSchemaSet>. Aktualizace v jednotlivých schémat <xref:System.Xml.Schema.XmlSchemaSet> nejsou sledovat. V důsledku toho <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> lze vlastnost `true` to i v případě, že jeden z schémat obsažené v <xref:System.Xml.Schema.XmlSchemaSet> byla změněna, tak dlouho, dokud se žádná schémata přidat nebo odebrat z <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Následující příklad přidá `books.xsd` do souboru <xref:System.Xml.Schema.XmlSchemaSet> a potom zavolá <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/books", "books.xsd")  
schemaSet.Compile()  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/books", "books.xsd");  
schemaSet.Compile();  
```  
  
 Další informace o kompilování schémat v <xref:System.Xml.Schema.XmlSchemaSet>, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda referenční dokumentaci k nástroji.  
  
## <a name="reprocessing-schemas"></a>Opětovné zpracování schémat.  
 Opětovné zpracování schéma v <xref:System.Xml.Schema.XmlSchemaSet> provede všechny předběžného zpracování kroků prováděných na schématu při <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet> je volána. Pokud volání <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda proběhne úspěšně, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet> je nastaven na `false`.  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Metoda by měl být použit při schéma v <xref:System.Xml.Schema.XmlSchemaSet> bylo změněno po <xref:System.Xml.Schema.XmlSchemaSet> byla provedena kompilace.  
  
 Následující příklad ilustruje, opětovné zpracování schéma přidán do <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda. Po <xref:System.Xml.Schema.XmlSchemaSet> kompiluje pomocí <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda a schéma přidán do <xref:System.Xml.Schema.XmlSchemaSet> je změněn, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> je nastavena na `true` to i v případě schéma v <xref:System.Xml.Schema.XmlSchemaSet> byla změněna. Volání <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda provádí všechny předběžném zpracování provádí <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda a nastaví <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost `false`.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
Dim schema As XmlSchema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Compile()  
  
Dim element As XmlSchemaElement = New XmlSchemaElement()  
schema.Items.Add(element)  
element.Name = "book"  
element.SchemaTypeName = New XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema")  
  
schemaSet.Reprocess(schema)  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
XmlSchema schema = schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Compile();  
  
XmlSchemaElement element = new XmlSchemaElement();  
schema.Items.Add(element);  
element.Name = "book";  
element.SchemaTypeName = new XmlQualifiedName("string", "http://www.w3.org/2001/XMLSchema");  
  
schemaSet.Reprocess(schema);  
```  
  
 Další informace o opětovné zpracování schéma v <xref:System.Xml.Schema.XmlSchemaSet>, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda referenční dokumentaci k nástroji.  
  
## <a name="checking-for-a-schema"></a>Kontrola schéma.  
 Můžete použít <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet> ke kontrole, pokud je schéma obsažené v <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> Metoda přebírá buď cílový obor názvů nebo <xref:System.Xml.Schema.XmlSchema> objekt, který chcete vyhledávat. V obou případech <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metoda vrátí `true` Pokud schéma je obsažena v <xref:System.Xml.Schema.XmlSchemaSet>, jinak vrátí `false`.  
  
 Další informace o kontrole pro schéma, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metoda referenční dokumentaci k nástroji.  
  
## <a name="removing-schemas"></a>Odebrání schémat.  
 Schémata jsou odebrány z <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> a <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> Metoda odebere zadaný schématu z <xref:System.Xml.Schema.XmlSchemaSet>, při <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metoda odebere určené schéma a všechny schémata ho importovat z <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Následující příklad ilustruje, přidání více schématy k <xref:System.Xml.Schema.XmlSchemaSet>, pak pomocí <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metoda odebrat jedno z schémat a všechny schémat se importuje.  
  
```vb  
Dim schemaSet As XmlSchemaSet = New XmlSchemaSet()  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd")  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd")  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd")  
  
Dim schema As XmlSchema  
  
For Each schema In schemaSet.Schemas()  
  
   If schema.TargetNamespace = "http://www.contoso.com/music" Then  
      schemaSet.RemoveRecursive(schema)  
   End If  
  
Next  
```  
  
```csharp  
XmlSchemaSet schemaSet = new XmlSchemaSet();  
schemaSet.Add("http://www.contoso.com/retail", "http://www.contoso.com/retail.xsd");  
schemaSet.Add("http://www.contoso.com/books", "http://www.contoso.com/books.xsd");  
schemaSet.Add("http://www.contoso.com/music", "http://www.contoso.com/music.xsd");  
  
foreach (XmlSchema schema in schemaSet.Schemas())  
{  
   if (schema.TargetNamespace == "http://www.contoso.com/music")  
   {  
      schemaSet.RemoveRecursive(schema);  
   }  
}  
```  
  
 Další informace o odebrání schémat ze <xref:System.Xml.Schema.XmlSchemaSet>, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> a <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metody referenční dokumentace.  
  
## <a name="schema-resolution-and-xsimport"></a>Schéma řešení a xs:import  
 Následující příklady popisují <xref:System.Xml.Schema.XmlSchemaSet> chování pro import schémat, pokud existují více schématy pro daný obor názvů v <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Představte si třeba <xref:System.Xml.Schema.XmlSchemaSet> obsahující více schématy pro `http://www.contoso.com` oboru názvů. Schéma s následující `xs:import` – direktiva je přidán do <xref:System.Xml.Schema.XmlSchemaSet>.  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <xref:System.Xml.Schema.XmlSchemaSet> Pokusu o import schématu pro `http://www.contoso.com` obor názvů načtením z `http://www.contoso.com/schema.xsd` adresy URL. Schématu deklarace a typy, které jsou deklarované v dokument schématu jsou k dispozici v import schématu, i když se jiné schéma dokumenty pro pouze `http://www.contoso.com` oboru názvů v <xref:System.Xml.Schema.XmlSchemaSet>. Pokud `schema.xsd` soubor nemůže být v umístění `http://www.contoso.com/schema.xsd` adresu URL, žádné schéma pro `http://www.contoso.com` obor názvů je importovat do import schématu.  
  
## <a name="validating-xml-documents"></a>Ověření XML – dokumenty  
 Dokumenty XML může být ověřen pomocí schémat v <xref:System.Xml.Schema.XmlSchemaSet>. Ověřit dokument XML přidáním schéma, aby <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost <xref:System.Xml.XmlReaderSettings> objektu, nebo pomocí přidání <xref:System.Xml.Schema.XmlSchemaSet> k <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost <xref:System.Xml.XmlReaderSettings> objektu. <xref:System.Xml.XmlReaderSettings> Objektu je následně používán <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> třídy za účelem vytvoření <xref:System.Xml.XmlReader> objektu a ověření v dokumentu XML.  
  
 Další informace o ověření XML dokumenty pomocí <xref:System.Xml.Schema.XmlSchemaSet>, najdete v části [ověřování schématu XML (XSD) pomocí XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>  
 <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>  
 [XmlSchemaSet jako mezipaměti schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
 [Ověření schématu XML (XSD) s třídou XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)

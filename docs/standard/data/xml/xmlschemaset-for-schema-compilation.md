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
ms.openlocfilehash: c24fe637514ba773cecc7824de276b1707a4e90c
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44221685"
---
# <a name="xmlschemaset-for-schema-compilation"></a>XmlSchemaSet pro kompilaci schématu
Popisuje <xref:System.Xml.Schema.XmlSchemaSet>, mezipaměti, kde můžete ukládat a ověření schématu XML definice jazyk (XSD) schémata.  
  
## <a name="the-xmlschemaset-class"></a>Třída XmlSchemaSet  
 <xref:System.Xml.Schema.XmlSchemaSet> Je do mezipaměti, kde můžete ukládat a ověření schématu XML definice jazyk (XSD) schémata.  
  
 V <xref:System.Xml?displayProperty=nameWithType> verze 1.0, schémat XML byly načteny do <xref:System.Xml.Schema.XmlSchemaCollection> třídu jako knihovny schémat. V <xref:System.Xml?displayProperty=nameWithType> verze 2.0, <xref:System.Xml.XmlValidatingReader> a <xref:System.Xml.Schema.XmlSchemaCollection> třídy jsou zastaralé a byly nahrazeny <xref:System.Xml.XmlReader.Create%2A> metody a <xref:System.Xml.Schema.XmlSchemaSet> třídy v uvedeném pořadí.  
  
 <xref:System.Xml.Schema.XmlSchemaSet> Zavedl vyřešit řadu problémů, včetně kompatibility standardy, výkonu a zastaralý formát schématu Microsoft XML-Data Reduced (XDR).  
  
 Tady je porovnání mezi službou <xref:System.Xml.Schema.XmlSchemaCollection> třídy a <xref:System.Xml.Schema.XmlSchemaSet> třídy.  
  
|Třídou XmlSchemaCollection|Třída XmlSchemaSet|  
|-------------------------|------------------|  
|Podporuje schémata Microsoft XDR a W3C XML.|Podporuje se jenom schémata W3C XML.|  
|Schémata jsou zkompilovány při <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metoda je volána.|Schémata nejsou při kompilaci <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda je volána. To poskytuje vylepšení výkonu při vytváření knihovny schémat.|  
|Každý schématu generuje jednotlivých Kompilovaná verze, který může mít za následek "schéma ostrovy." V důsledku toho zahrnuje všechny a pouze v rámci tohoto schématu jsou omezená importy.|Zkompilovaných schémat generování jednoho logického schématu, "set" schémat. Žádné importované schémata v rámci schématu, které jsou přidány do sady jsou přímo přidat do sady samotné. To znamená, že všechny typy jsou k dispozici ke všem schématům.|  
|V kolekci může existovat pouze jedno schéma pro konkrétní cílový obor názvů.|Více schémat pro stejný cílový obor názvů je možné přidat, dokud nebyly zjištěny žádné konflikty typu.|  
  
## <a name="migrating-to-the-xmlschemaset"></a>Migrace na sadě XmlSchemaSet  
 Následující příklad kódu poskytuje návod pro migraci do nového <xref:System.Xml.Schema.XmlSchemaSet> třídy z zastaralý <xref:System.Xml.Schema.XmlSchemaCollection> třídy. Příklad kódu znázorňuje následující hlavní rozdíly mezi dvěma třídami.  
  
-   Na rozdíl od <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaCollection> třídy, schémata nejsou zkompilovány při volání <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Metodu <xref:System.Xml.Schema.XmlSchemaSet> je explicitně volána v příkladu kódu.  
  
-   K iteraci přes <xref:System.Xml.Schema.XmlSchemaSet>, je nutné použít <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Tady je zastaralý <xref:System.Xml.Schema.XmlSchemaCollection> příklad kódu.  
  
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
  
 Tady je ekvivalentem <xref:System.Xml.Schema.XmlSchemaSet> příklad kódu.  
  
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
  
## <a name="adding-and-retrieving-schemas"></a>Přidávání a načítání schémat  
 Schémata jsou přidány do <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet>. Při přidání schéma <xref:System.Xml.Schema.XmlSchemaSet>, je přidružen k cílový obor názvů identifikátoru URI. Cílový obor názvů identifikátoru URI může být buď určena jako parametr <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody nebo pokud není zadán žádný cílový obor názvů, <xref:System.Xml.Schema.XmlSchemaSet> používá cílový obor názvů definovaný ve schématu.  
  
 Schémata jsou načteny z <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Vlastnost <xref:System.Xml.Schema.XmlSchemaSet> umožňuje iterovat <xref:System.Xml.Schema.XmlSchema> objekty obsažené v <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Vlastnost vrací buď všechny <xref:System.Xml.Schema.XmlSchema> objekty obsažené v <xref:System.Xml.Schema.XmlSchemaSet>, nebo zadaný cílový obor názvů parametrů, vrátí všechny <xref:System.Xml.Schema.XmlSchema> objektů, které patří cílový obor názvů. Pokud `null` je zadána jako parametr cílový obor názvů <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost vrací všechna schémata bez oboru názvů.  
  
 Následující příklad přidá `books.xsd` schéma v `http://www.contoso.com/books` obor názvů, abyste <xref:System.Xml.Schema.XmlSchemaSet>, načte všechna schémata, které patří do `http://www.contoso.com/books` obor názvů z <xref:System.Xml.Schema.XmlSchemaSet>a pak zapíše tato schémata <xref:System.Console>.  
  
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
  
 Další informace o přidávání a načítání schémat ze <xref:System.Xml.Schema.XmlSchemaSet> objektu, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda a <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost referenční dokumentaci.  
  
## <a name="compiling-schemas"></a>Kompilování schémat  
 Schémata v <xref:System.Xml.Schema.XmlSchemaSet> jsou kompilovány do jedné logické schématu <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet>.  
  
> [!NOTE]
>  Na rozdíl od zastaralý <xref:System.Xml.Schema.XmlSchemaCollection> třídy, schémata nejsou při kompilaci <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda je volána.  
  
 Pokud <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda provedena úspěšně, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet> je nastavena na `true`.  
  
> [!NOTE]
>  <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> Vlastnost nemá vliv, pokud jsou upravovat schémata během činnosti v <xref:System.Xml.Schema.XmlSchemaSet>. Aktualizace v jednotlivých schémat <xref:System.Xml.Schema.XmlSchemaSet> nebudou pro účely. V důsledku toho <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost může být `true` i v případě, že jeden schémat součástí <xref:System.Xml.Schema.XmlSchemaSet> byla změněna, tak dlouho, dokud se přidaly nebo odebraly z žádná schémata <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Následující příklad přidá `books.xsd` do souboru <xref:System.Xml.Schema.XmlSchemaSet> a pak zavolá <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metody.  
  
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
  
 Další informace o kompilaci schémata v <xref:System.Xml.Schema.XmlSchemaSet>, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda referenční dokumentaci.  
  
## <a name="reprocessing-schemas"></a>Schémata se znovu zpracovávají  
 Přepracování schéma v <xref:System.Xml.Schema.XmlSchemaSet> provede všechny kroky předběžného zpracování provést ve schématu při <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet> je volána. Pokud volání <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda je úspěšná, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet> je nastavena na `false`.  
  
 <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> Metoda má být použit při schéma v <xref:System.Xml.Schema.XmlSchemaSet> byl změněn po <xref:System.Xml.Schema.XmlSchemaSet> provedl kompilace.  
  
 Následující příklad ukazuje přepracování schématu přidat do <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metody. Po <xref:System.Xml.Schema.XmlSchemaSet> je zkompilován pomocí <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda a přidá do schématu <xref:System.Xml.Schema.XmlSchemaSet> se změní, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> je nastavena na `true` i když schéma v <xref:System.Xml.Schema.XmlSchemaSet> byla změněna. Volání <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda provádí všechny předzpracování prováděné <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda a nastaví <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost `false`.  
  
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
  
 Další informace o opětovném zpracování schéma v <xref:System.Xml.Schema.XmlSchemaSet>, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metoda referenční dokumentaci.  
  
## <a name="checking-for-a-schema"></a>Kontrolují se schéma  
 Můžete použít <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet> ke kontrole, pokud je součástí schématu <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> Metoda přebírá buď cílový obor názvů nebo <xref:System.Xml.Schema.XmlSchema> objektu, který chcete vyhledat. V obou případech <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> vrátí metoda `true` Pokud schéma je obsažena v <xref:System.Xml.Schema.XmlSchemaSet>; v opačném případě vrátí `false`.  
  
 Další informace o kontrole pro schéma, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metoda referenční dokumentaci.  
  
## <a name="removing-schemas"></a>Odebrání schémata  
 Schémata jsou odebrány z <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> a <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> Metoda odstraní zadané schéma z <xref:System.Xml.Schema.XmlSchemaSet>, zatímco <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metoda odstraní zadané schéma a všechna schémata importy z <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Následující příklad ukazuje přidání více schémat, chcete-li <xref:System.Xml.Schema.XmlSchemaSet>, pak pomocí <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metoda odebrání jednoho ze schémat a všechna schémata importuje.  
  
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
  
 Další informace o odebrání schémata z <xref:System.Xml.Schema.XmlSchemaSet>, najdete v článku <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> a <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metody referenční dokumentaci.  
  
## <a name="schema-resolution-and-xsimport"></a>Schéma překlad IP adres a xs:import  
 Následující příklady popisují <xref:System.Xml.Schema.XmlSchemaSet> chování pro import schémat, pokud existuje více schémat pro daný obor názvů v <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Představte si třeba <xref:System.Xml.Schema.XmlSchemaSet> , který obsahuje více schémat pro `http://www.contoso.com` oboru názvů. Schéma s následující `xs:import` – direktiva se přidá do <xref:System.Xml.Schema.XmlSchemaSet>.  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <xref:System.Xml.Schema.XmlSchemaSet> Pokusu o import schématu pro `http://www.contoso.com` oboru názvů z načtením `http://www.contoso.com/schema.xsd` adresy URL. Pouze schéma deklarace a typy deklarované v dokumentu schématu jsou k dispozici v importu schématu, i když existují jiných schématu dokumentů pro `http://www.contoso.com` obor názvů v <xref:System.Xml.Schema.XmlSchemaSet>. Pokud `schema.xsd` soubor nemůže být umístěn v `http://www.contoso.com/schema.xsd` žádné schéma pro adresu URL `http://www.contoso.com` obor názvů se importuje do import schématu.  
  
## <a name="validating-xml-documents"></a>Ověření XML dokumenty  
 XML dokumenty můžou ověřovat na schémata v <xref:System.Xml.Schema.XmlSchemaSet>. Ověření dokumentu XML tak, že přidáte schématu a <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost <xref:System.Xml.XmlReaderSettings> objektu nebo přidáním <xref:System.Xml.Schema.XmlSchemaSet> k <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnost <xref:System.Xml.XmlReaderSettings> objektu. <xref:System.Xml.XmlReaderSettings> Objektu se potom využijí <xref:System.Xml.XmlReader.Create%2A> metodu <xref:System.Xml.XmlReader> třídy za účelem vytvoření <xref:System.Xml.XmlReader> objektu a ověření dokumentu XML.  
  
 Další informace o ověření XML dokumenty pomocí <xref:System.Xml.Schema.XmlSchemaSet>, naleznete v tématu [ověření schématu XML (XSD) s třídou XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>  
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>  
- [Třída XmlSchemaSet jako mezipaměť schémat](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)  
- [Ověření schématu XML (XSD) s třídou XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)

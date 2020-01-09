---
title: XmlSchemaSet pro kompilaci schématu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 55c4b175-3170-4071-9d60-dd5a42f79b54
ms.openlocfilehash: 55347de81c65b7390584415dd29044f4ca4ba02a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709813"
---
# <a name="xmlschemaset-for-schema-compilation"></a>XmlSchemaSet pro kompilaci schématu
Popisuje <xref:System.Xml.Schema.XmlSchemaSet>mezipaměť, kde lze uložit a ověřit schémata XML Schema Definition Language (XSD).  
  
## <a name="the-xmlschemaset-class"></a>Třída XmlSchemaSet  
 <xref:System.Xml.Schema.XmlSchemaSet> je mezipaměť, kde lze uložit a ověřit schémata XML Schema Definition Language (XSD).  
  
 V <xref:System.Xml?displayProperty=nameWithType> verze 1,0 byla schémata XML načtena do <xref:System.Xml.Schema.XmlSchemaCollection> třídy jako knihovna schémat. V <xref:System.Xml?displayProperty=nameWithType> verze 2,0 jsou <xref:System.Xml.XmlValidatingReader> a <xref:System.Xml.Schema.XmlSchemaCollection> třídy zastaralé a byly nahrazeny <xref:System.Xml.XmlReader.Create%2A> metodami a <xref:System.Xml.Schema.XmlSchemaSet>ou třídou v uvedeném pořadí.  
  
 <xref:System.Xml.Schema.XmlSchemaSet> byla zavedena za účelem opravy řady problémů, včetně kompatibility standardů, výkonu a zastaralých formátů schématu Microsoft XML-data redukovaná (XDR).  
  
 Následuje porovnání mezi <xref:System.Xml.Schema.XmlSchemaCollection> třídou a <xref:System.Xml.Schema.XmlSchemaSet>ou třídou.  
  
|XmlSchemaCollection|XmlSchemaSet|  
|-------------------------|------------------|  
|Podporuje schémata Microsoft XDR a W3C XML.|Podporuje pouze schémata W3C XML.|  
|Schémata jsou kompilována při volání metody <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A>.|Schémata nejsou kompilována při volání metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>. Tím je zajištěno zlepšení výkonu při vytváření knihovny schémat.|  
|Každé schéma generuje jednotlivé kompilované verze, které mohou mít za následek "ostrovy schemas". V důsledku toho jsou všechny zahrnutí a importy vymezeny pouze v rámci tohoto schématu.|Kompilovaná schémata generují jedno logické schéma, "sadu" schémat. Všechna importovaná schémata v rámci schématu, která jsou přidána do sady, jsou přímo přidána do samotné sady. To znamená, že všechny typy jsou k dispozici pro všechna schémata.|  
|V kolekci může existovat pouze jedno schéma pro určitý cílový obor názvů.|Více schémat stejného cílového oboru názvů lze přidat, pokud neexistují žádné konflikty typů.|  
  
## <a name="migrating-to-the-xmlschemaset"></a>Migrace do sady XmlSchemaSet  
 Následující příklad kódu poskytuje průvodce pro migraci na novou <xref:System.Xml.Schema.XmlSchemaSet> třídu z zastaralé <xref:System.Xml.Schema.XmlSchemaCollection> třídy. Příklad kódu ukazuje následující hlavní rozdíly mezi dvěma třídami.  
  
- Na rozdíl od metody <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> třídy <xref:System.Xml.Schema.XmlSchemaCollection> nejsou schémata kompilována při volání metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>. Metoda <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> <xref:System.Xml.Schema.XmlSchemaSet> je explicitně volána v příkladu kódu.  
  
- Chcete-li iterovat přes <xref:System.Xml.Schema.XmlSchemaSet>, je nutné použít vlastnost <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Následuje příklad zastaralého příkladu kódu <xref:System.Xml.Schema.XmlSchemaCollection>.  
  
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
  
 Níže je podobný příklad kódu <xref:System.Xml.Schema.XmlSchemaSet>.  
  
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
  
## <a name="adding-and-retrieving-schemas"></a>Přidání a načtení schémat  
 Schémata jsou přidána do <xref:System.Xml.Schema.XmlSchemaSet> pomocí metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>. Když je schéma přidáno do <xref:System.Xml.Schema.XmlSchemaSet>, je přidruženo k identifikátoru URI cílového oboru názvů. Identifikátor URI cílového oboru názvů může být buď zadán jako parametr metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>, nebo pokud není zadán žádný cílový obor názvů, <xref:System.Xml.Schema.XmlSchemaSet> používá cílový obor názvů definovaný ve schématu.  
  
 Schémata se načítají z <xref:System.Xml.Schema.XmlSchemaSet> pomocí vlastnosti <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet>. Vlastnost <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> <xref:System.Xml.Schema.XmlSchemaSet> umožňuje iterovat objekty <xref:System.Xml.Schema.XmlSchema> obsažené v <xref:System.Xml.Schema.XmlSchemaSet>. Vlastnost <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> buď vrátí všechny objekty <xref:System.Xml.Schema.XmlSchema> obsažené v <xref:System.Xml.Schema.XmlSchemaSet>, nebo s předaným parametrem cílového oboru názvů vrátí všechny objekty <xref:System.Xml.Schema.XmlSchema>, které patří do cílového oboru názvů. Pokud je jako parametr cílového oboru názvů zadán parametr `null`, vrátí vlastnost <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> všechna schémata bez oboru názvů.  
  
 Následující příklad přidá schéma `books.xsd` v oboru názvů `http://www.contoso.com/books` do <xref:System.Xml.Schema.XmlSchemaSet>, načte všechna schémata, která patří do oboru názvů `http://www.contoso.com/books` z <xref:System.Xml.Schema.XmlSchemaSet>, a pak tato schémata zapíše do <xref:System.Console>.  
  
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
  
 Další informace o přidání a načtení schémat z <xref:System.Xml.Schema.XmlSchemaSet> objektu naleznete v tématu metoda <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> a referenční dokumentace k vlastnosti <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>.  
  
## <a name="compiling-schemas"></a>Kompilace schémat  
 Schémata ve <xref:System.Xml.Schema.XmlSchemaSet> jsou kompilována do jednoho logického schématu <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodou <xref:System.Xml.Schema.XmlSchemaSet>.  
  
> [!NOTE]
> Na rozdíl od zastaralých <xref:System.Xml.Schema.XmlSchemaCollection> třídy nejsou schémata kompilována při volání metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>.  
  
 Pokud se metoda <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> úspěšně spustí, vlastnost <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> je nastavena na `true`.  
  
> [!NOTE]
> Vlastnost <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> není ovlivněna, pokud jsou schémata upravována v <xref:System.Xml.Schema.XmlSchemaSet>. Aktualizace jednotlivých schémat v <xref:System.Xml.Schema.XmlSchemaSet> nejsou sledovány. V důsledku toho může být vlastnost <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> `true`, i když jedno ze schémat obsažených v <xref:System.Xml.Schema.XmlSchemaSet> bylo změněno, pokud do <xref:System.Xml.Schema.XmlSchemaSet>nebyla přidána ani odebrána žádná schémata.  
  
 Následující příklad přidá soubor `books.xsd` do <xref:System.Xml.Schema.XmlSchemaSet> a pak zavolá metodu <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>.  
  
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
  
 Další informace o kompilaci schémat v <xref:System.Xml.Schema.XmlSchemaSet>naleznete v referenční dokumentaci k metodě <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>.  
  
## <a name="reprocessing-schemas"></a>Zpracování schémat  
 Rezpracování schématu ve <xref:System.Xml.Schema.XmlSchemaSet> provádí všechny kroky předzpracování provedené ve schématu při volání metody <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> <xref:System.Xml.Schema.XmlSchemaSet>. Pokud je volání metody <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> úspěšné, vlastnost <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> <xref:System.Xml.Schema.XmlSchemaSet> je nastavena na `false`.  
  
 Metoda <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> by měla být použita, pokud je schéma v <xref:System.Xml.Schema.XmlSchemaSet> změněno poté, co byla provedena kompilace <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Následující příklad ukazuje, jak znovu zpracovat schéma přidané do <xref:System.Xml.Schema.XmlSchemaSet> pomocí metody <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>. Po kompilaci <xref:System.Xml.Schema.XmlSchemaSet> pomocí metody <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> a změně schématu přidaného do <xref:System.Xml.Schema.XmlSchemaSet> je vlastnost <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> nastavena na `true`, i když bylo upraveno schéma v <xref:System.Xml.Schema.XmlSchemaSet>. Volání metody <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> provede všechny předzpracování prováděné metodou <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> a nastaví vlastnost <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> na `false`.  
  
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
  
 Další informace o přepracování schématu v <xref:System.Xml.Schema.XmlSchemaSet>naleznete v referenční dokumentaci k metodě <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>.  
  
## <a name="checking-for-a-schema"></a>Kontroluje se schéma.  
 Pomocí metody <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> <xref:System.Xml.Schema.XmlSchemaSet> můžete zjistit, zda je schéma obsaženo v <xref:System.Xml.Schema.XmlSchemaSet>. Metoda <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> přebírá buď cílový obor názvů, nebo objekt <xref:System.Xml.Schema.XmlSchema>, který se má ověřit. V obou případech metoda <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> vrátí `true`, pokud je schéma obsaženo v <xref:System.Xml.Schema.XmlSchemaSet>; v opačném případě vrátí `false`.  
  
 Další informace o kontrole schématu naleznete v referenční dokumentaci k metodě <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>.  
  
## <a name="removing-schemas"></a>Odebírání schémat  
 Schémata jsou odebrána z <xref:System.Xml.Schema.XmlSchemaSet> pomocí metod <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> a <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> <xref:System.Xml.Schema.XmlSchemaSet>. Metoda <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> Odstraní zadané schéma z <xref:System.Xml.Schema.XmlSchemaSet>, zatímco metoda <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> Odstraní zadané schéma a všechna schémata, která importuje z <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Následující příklad znázorňuje přidání více schémat do <xref:System.Xml.Schema.XmlSchemaSet>a následné použití metody <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> k odebrání jednoho ze schémat a všech schémat, která importuje.  
  
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
  
 Další informace o odebírání schémat z <xref:System.Xml.Schema.XmlSchemaSet>naleznete v referenční dokumentaci k metodám <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> a <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>.  
  
## <a name="schema-resolution-and-xsimport"></a>Rozlišení schématu a xs: Import  
 Následující příklady popisují chování <xref:System.Xml.Schema.XmlSchemaSet> pro import schémat, pokud v <xref:System.Xml.Schema.XmlSchemaSet>existuje více schémat pro daný obor názvů.  
  
 Zvažte například <xref:System.Xml.Schema.XmlSchemaSet>, který obsahuje více schémat pro `http://www.contoso.com` obor názvů. Do <xref:System.Xml.Schema.XmlSchemaSet>se přidá schéma s následující direktivou `xs:import`.  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <xref:System.Xml.Schema.XmlSchemaSet> se pokusí importovat schéma pro `http://www.contoso.com` oboru názvů načtením z adresy URL `http://www.contoso.com/schema.xsd`. Pouze deklarace schématu a typy deklarované v dokumentu schématu jsou k dispozici v rámci importu schématu, i když existují další dokumenty schématu pro obor názvů `http://www.contoso.com` v <xref:System.Xml.Schema.XmlSchemaSet>. Pokud `schema.xsd` soubor nejde najít na `http://www.contoso.com/schema.xsd` adrese URL, neimportuje se do importovaného schématu žádné schéma pro `http://www.contoso.com` obor názvů.  
  
## <a name="validating-xml-documents"></a>Ověřování dokumentů XML  
 Dokumenty XML lze ověřit proti schématům v <xref:System.Xml.Schema.XmlSchemaSet>. Můžete ověřit dokument XML přidáním schématu do vlastnosti <xref:System.Xml.Schema.XmlSchemaSet><xref:System.Xml.XmlReaderSettings.Schemas%2A> objektu <xref:System.Xml.XmlReaderSettings> nebo přidáním <xref:System.Xml.Schema.XmlSchemaSet> do vlastnosti <xref:System.Xml.XmlReaderSettings.Schemas%2A> objektu <xref:System.Xml.XmlReaderSettings>. Objekt <xref:System.Xml.XmlReaderSettings> je poté použit metodou <xref:System.Xml.XmlReader.Create%2A> třídy <xref:System.Xml.XmlReader> k vytvoření objektu <xref:System.Xml.XmlReader> a ověření dokumentu XML.  
  
 Další informace o ověřování dokumentů XML pomocí <xref:System.Xml.Schema.XmlSchemaSet>naleznete v tématu [ověřování schématu XML (XSD) pomocí sady XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [Třída XmlSchemaSet jako mezipaměť schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Ověření schématu XML (XSD) s třídou XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)

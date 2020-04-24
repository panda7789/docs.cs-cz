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
Popisuje mezipaměť <xref:System.Xml.Schema.XmlSchemaSet>, kde lze uložit a ověřit schémata XML Schema Definition Language (XSD).  
  
## <a name="the-xmlschemaset-class"></a>Třída XmlSchemaSet  
 <xref:System.Xml.Schema.XmlSchemaSet> Je mezipaměť, kde lze uložit a ověřit schémata XML Schema Definition Language (XSD).  
  
 Ve <xref:System.Xml?displayProperty=nameWithType> verzi 1,0 byly schémata XML načtena do <xref:System.Xml.Schema.XmlSchemaCollection> třídy jako knihovna schémat. Ve <xref:System.Xml?displayProperty=nameWithType> <xref:System.Xml.XmlValidatingReader> verzi 2,0 <xref:System.Xml.Schema.XmlSchemaCollection> třídy a jsou zastaralé a byly nahrazeny <xref:System.Xml.XmlReader.Create%2A> metodami a <xref:System.Xml.Schema.XmlSchemaSet> třídou v uvedeném pořadí.  
  
 <xref:System.Xml.Schema.XmlSchemaSet> Byla představena Oprava počtu problémů, včetně kompatibility standardů, výkonu a zastaralých formátů schématu Microsoft XML-data redukovaná (XDR).  
  
 Následuje porovnání mezi <xref:System.Xml.Schema.XmlSchemaCollection> třídou a <xref:System.Xml.Schema.XmlSchemaSet> třídou.  
  
|Kolekci XmlSchemaCollection neexistuje|XmlSchemaSet|  
|-------------------------|------------------|  
|Podporuje schémata Microsoft XDR a W3C XML.|Podporuje pouze schémata W3C XML.|  
|Schémata jsou kompilována při <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> volání metody.|Schémata nejsou kompilována při volání <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody. Tím je zajištěno zlepšení výkonu při vytváření knihovny schémat.|  
|Každé schéma generuje jednotlivé kompilované verze, které mohou mít za následek "ostrovy schemas". V důsledku toho jsou všechny zahrnutí a importy vymezeny pouze v rámci tohoto schématu.|Kompilovaná schémata generují jedno logické schéma, "sadu" schémat. Všechna importovaná schémata v rámci schématu, která jsou přidána do sady, jsou přímo přidána do samotné sady. To znamená, že všechny typy jsou k dispozici pro všechna schémata.|  
|V kolekci může existovat pouze jedno schéma pro určitý cílový obor názvů.|Více schémat stejného cílového oboru názvů lze přidat, pokud neexistují žádné konflikty typů.|  
  
## <a name="migrating-to-the-xmlschemaset"></a>Migrace do sady XmlSchemaSet  
 Následující příklad kódu poskytuje průvodce pro migraci na novou <xref:System.Xml.Schema.XmlSchemaSet> třídu z zastaralé <xref:System.Xml.Schema.XmlSchemaCollection> třídy. Příklad kódu ukazuje následující hlavní rozdíly mezi dvěma třídami.  
  
- Na rozdíl od <xref:System.Xml.Schema.XmlSchemaCollection.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaCollection> třídy nejsou schémata kompilována při volání <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody. <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Metoda <xref:System.Xml.Schema.XmlSchemaSet> je explicitně volána v příkladu kódu.  
  
- Chcete-li iterovat <xref:System.Xml.Schema.XmlSchemaSet>přes, je nutné použít <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Následuje příklad zastaralého <xref:System.Xml.Schema.XmlSchemaCollection> kódu.  
  
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
  
 V následujícím příkladu je podobný <xref:System.Xml.Schema.XmlSchemaSet> příklad kódu.  
  
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
 Schémata jsou přidána do objektu <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody <xref:System.Xml.Schema.XmlSchemaSet>. Když je schéma přidáno do <xref:System.Xml.Schema.XmlSchemaSet>, je přidruženo k identifikátoru URI cílového oboru názvů. Identifikátor URI cílového oboru názvů je možné zadat buď jako parametr <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody, nebo pokud není zadaný žádný cílový obor názvů, <xref:System.Xml.Schema.XmlSchemaSet> použije cílový obor názvů definovaný ve schématu.  
  
 Schémata jsou načítána z <xref:System.Xml.Schema.XmlSchemaSet> pomocí <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnosti <xref:System.Xml.Schema.XmlSchemaSet>. <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Vlastnost <xref:System.Xml.Schema.XmlSchemaSet> umožňuje iterovat <xref:System.Xml.Schema.XmlSchema> objekty, které jsou obsaženy v. <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> Vlastnost buď vrátí všechny <xref:System.Xml.Schema.XmlSchema> objekty obsažené v <xref:System.Xml.Schema.XmlSchemaSet>, nebo s daným parametrem cílového oboru názvů, vrátí všechny <xref:System.Xml.Schema.XmlSchema> objekty, které patří do cílového oboru názvů. Pokud `null` je zadána jako parametr cílového oboru názvů, vrátí <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnost všechna schémata bez oboru názvů.  
  
 Následující příklad přidá `books.xsd` `http://www.contoso.com/books` schéma v oboru názvů do <xref:System.Xml.Schema.XmlSchemaSet>, načte všechna schémata, která patří do `http://www.contoso.com/books` oboru názvů z <xref:System.Xml.Schema.XmlSchemaSet>a následně zapíše tato schémata do. <xref:System.Console>  
  
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
  
 Další informace o přidání a načtení schémat z <xref:System.Xml.Schema.XmlSchemaSet> objektu naleznete v tématu <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metoda a referenční dokumentace k <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A> vlastnostem.  
  
## <a name="compiling-schemas"></a>Kompilace schémat  
 Schémata v <xref:System.Xml.Schema.XmlSchemaSet> jsou zkompilována do jednoho logického schématu <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodou. <xref:System.Xml.Schema.XmlSchemaSet>  
  
> [!NOTE]
> Na rozdíl od zastaralé <xref:System.Xml.Schema.XmlSchemaCollection> třídy nejsou schémata kompilována při volání <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody.  
  
 Pokud se <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metoda úspěšně spustí, <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost <xref:System.Xml.Schema.XmlSchemaSet> je nastavena na. `true`  
  
> [!NOTE]
> Tato <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost není ovlivněna, pokud jsou schémata upravována v <xref:System.Xml.Schema.XmlSchemaSet>. Aktualizace jednotlivých schémat v <xref:System.Xml.Schema.XmlSchemaSet> nástroji nejsou sledovány. V důsledku toho může být <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> `true` vlastnost i v případě, že jedno ze schémat obsažených v nástroji <xref:System.Xml.Schema.XmlSchemaSet> bylo upraveno, pokud nebyla přidána ani odebrána žádná schémata z <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Následující příklad přidá `books.xsd` soubor do <xref:System.Xml.Schema.XmlSchemaSet> a pak zavolá <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> metodu.  
  
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
  
 Další informace o kompilaci schémat v <xref:System.Xml.Schema.XmlSchemaSet>nástroji naleznete v referenční dokumentaci <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> k metodě.  
  
## <a name="reprocessing-schemas"></a>Zpracování schémat  
 Rezpracování schématu v <xref:System.Xml.Schema.XmlSchemaSet> provádí všechny kroky předzpracování provedené ve schématu při volání <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> metody. <xref:System.Xml.Schema.XmlSchemaSet> Pokud je <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> volání metody úspěšné <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> , vlastnost <xref:System.Xml.Schema.XmlSchemaSet> je nastavena na. `false`  
  
 Metoda <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> by měla být použita, pokud bylo po <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet> provedení kompilace změněno schéma v.  
  
 Následující příklad ukazuje, jak znovu zpracovat schéma přidané do <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metody pomocí metody. <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A> Po kompilaci pomocí metody a změně schématu přidaného do <xref:System.Xml.Schema.XmlSchemaSet> je <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost nastavena na `true` i v případě, že schéma v nástroji <xref:System.Xml.Schema.XmlSchemaSet> bylo upraveno. Volání <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metody provede <xref:System.Xml.Schema.XmlSchemaSet.Add%2A> všechny předzpracování prováděné metodou a nastaví <xref:System.Xml.Schema.XmlSchemaSet.IsCompiled%2A> vlastnost na `false`hodnotu.  
  
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
  
 Další informace o přepracování schématu v <xref:System.Xml.Schema.XmlSchemaSet>nástroji naleznete v referenční dokumentaci k <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A> metodě.  
  
## <a name="checking-for-a-schema"></a>Kontroluje se schéma.  
 Můžete použít <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metodu <xref:System.Xml.Schema.XmlSchemaSet> pro kontrolu, zda je schéma obsaženo v. <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> Metoda přijímá buď cílový obor názvů, nebo <xref:System.Xml.Schema.XmlSchema> objekt, který má být zkontrolován. V obou případech <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metoda vrátí `true` , pokud je schéma obsaženo v. <xref:System.Xml.Schema.XmlSchemaSet> v opačném případě `false`vrátí.  
  
 Další informace o kontrole schématu naleznete v referenční dokumentaci k <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A> metodě.  
  
## <a name="removing-schemas"></a>Odebírání schémat  
 Schémata jsou <xref:System.Xml.Schema.XmlSchemaSet> odebrána z pomocí metody <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> a. <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> Metoda odebere zadané schéma z rozhraní <xref:System.Xml.Schema.XmlSchemaSet>, zatímco <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metoda odebere zadané schéma a všechna schémata, která importuje z <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Následující příklad znázorňuje přidání více schémat do objektu <xref:System.Xml.Schema.XmlSchemaSet>a následné použití <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> metody pro odebrání jednoho ze schémat a všech schémat, která importuje.  
  
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
  
 Další informace o odebrání schémat z <xref:System.Xml.Schema.XmlSchemaSet>naleznete v referenční dokumentaci metod <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A> a <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A> .  
  
## <a name="schema-resolution-and-xsimport"></a>Rozlišení schématu a xs: Import  
 Následující příklady popisují <xref:System.Xml.Schema.XmlSchemaSet> chování při importu schémat, pokud v nástroji existuje více schémat pro daný obor názvů <xref:System.Xml.Schema.XmlSchemaSet>.  
  
 Zvažte například <xref:System.Xml.Schema.XmlSchemaSet> , že obsahuje více schémat pro `http://www.contoso.com` obor názvů. Do nástroje se přidá schéma `xs:import` s následující direktivou <xref:System.Xml.Schema.XmlSchemaSet>.  
  
```xml  
<xs:import namespace="http://www.contoso.com" schemaLocation="http://www.contoso.com/schema.xsd" />  
```  
  
 <xref:System.Xml.Schema.XmlSchemaSet> Pokusí se importovat schéma pro `http://www.contoso.com` obor názvů načtením z `http://www.contoso.com/schema.xsd` adresy URL. Pouze deklarace schématu a typy deklarované v dokumentu schématu jsou k dispozici v rámci importu schématu, i když existují další dokumenty schématu pro `http://www.contoso.com` obor názvů v. <xref:System.Xml.Schema.XmlSchemaSet> Pokud `schema.xsd` soubor nejde najít na `http://www.contoso.com/schema.xsd` adrese URL, do importovaného schématu se neimportuje žádné schéma pro `http://www.contoso.com` obor názvů.  
  
## <a name="validating-xml-documents"></a>Ověřování dokumentů XML  
 Dokumenty XML lze ověřit proti schématům v <xref:System.Xml.Schema.XmlSchemaSet>. Můžete ověřit dokument XML <xref:System.Xml.Schema.XmlSchemaSet> <xref:System.Xml.XmlReaderSettings.Schemas%2A> přidáním schématu <xref:System.Xml.XmlReaderSettings> do vlastnosti objektu nebo přidáním <xref:System.Xml.Schema.XmlSchemaSet> prvku do <xref:System.Xml.XmlReaderSettings.Schemas%2A> vlastnosti <xref:System.Xml.XmlReaderSettings> objektu. <xref:System.Xml.XmlReaderSettings> Objekt je pak použit <xref:System.Xml.XmlReader.Create%2A> metodou <xref:System.Xml.XmlReader> třídy pro vytvoření <xref:System.Xml.XmlReader> objektu a ověření dokumentu XML.  
  
 Další informace o ověřování dokumentů XML pomocí naleznete v <xref:System.Xml.Schema.XmlSchemaSet>tématu [ověření schématu XML (XSD) pomocí sady XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.Schema.XmlSchemaSet.Add%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Schemas%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Contains%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Compile%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Reprocess%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.Remove%2A>
- <xref:System.Xml.Schema.XmlSchemaSet.RemoveRecursive%2A>
- [Třída XmlSchemaSet jako mezipaměť schématu](../../../../docs/standard/data/xml/xmlschemaset-for-schema-compilation.md)
- [Ověření schématu XML (XSD) s třídou XmlSchemaSet](../../../../docs/standard/data/xml/xml-schema-xsd-validation-with-xmlschemaset.md)

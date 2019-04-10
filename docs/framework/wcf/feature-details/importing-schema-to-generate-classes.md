---
title: Import schématu pro generování tříd
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractImporter class
ms.assetid: b9170583-8c34-43bd-97bb-6c0c8dddeee0
ms.openlocfilehash: 68890a5d86d2781e3c8079c86e941144e3796ea6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228585"
---
# <a name="importing-schema-to-generate-classes"></a>Import schématu pro generování tříd
Chcete-li generovat třídy ze schémat, které lze použít s Windows Communication Foundation (WCF), použijte <xref:System.Runtime.Serialization.XsdDataContractImporter> třídy. Toto téma popisuje proces a odchylky.  
  
## <a name="the-import-process"></a>Proces importu
 Proces importu schématu začíná <xref:System.Xml.Schema.XmlSchemaSet> a vytváří <xref:System.CodeDom.CodeCompileUnit>.  
  
 `XmlSchemaSet` Je součástí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]od schématu objektu modelu (SOM), který představuje sadu dokumentů schématu XML definice jazyk (XSD) schématu. Vytvoření `XmlSchemaSet` objekt ze sady dokumentů XSD, každý dokument v deserializaci <xref:System.Xml.Schema.XmlSchema> objektu (pomocí <xref:System.Xml.Serialization.XmlSerializer>) a přidejte tyto objekty do nového `XmlSchemaSet`.  
  
 `CodeCompileUnit` Je součástí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]od Code Document Object Model (CodeDOM), který představuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kód abstraktní způsobem. K vygenerování skutečného kódu z `CodeCompileUnit`, použijte podtřídou třídy <xref:System.CodeDom.Compiler.CodeDomProvider> třídy, jako <xref:Microsoft.CSharp.CSharpCodeProvider> nebo <xref:Microsoft.VisualBasic.VBCodeProvider> třídy.  
  
### <a name="to-import-a-schema"></a>Chcete-li importovat schéma  
  
1. Vytvoření instance <xref:System.Runtime.Serialization.XsdDataContractImporter>.  
  
2. Volitelné. Předat `CodeCompileUnit` v konstruktoru. Typy generované při importu schématu jsou přidány do tohoto `CodeCompileUnit` instanci místo počínaje prázdnou hodnotu `CodeCompileUnit`.  
  
3. Volitelné. Volání jednoho z <xref:System.Runtime.Serialization.XsdDataContractImporter.CanImport%2A> metody. Metoda určuje, zda dané schéma je platný datový kontrakt schéma a mohou být naimportovány. `CanImport` Metoda má stejný přetížení jako `Import` (dál).  
  
4. Voláním přetížené `Import` metody, například <xref:System.Runtime.Serialization.XsdDataContractImporter.Import%28System.Xml.Schema.XmlSchemaSet%29> metody.  
  
     Nejjednodušší přetížená nepoužívá `XmlSchemaSet` a importuje všechny typy, včetně anonymních typů nalezena v dané sadě schémat. Další přetížení umožňují určit typ XSD nebo seznam typů pro import (ve formě <xref:System.Xml.XmlQualifiedName> nebo kolekci `XmlQualifiedName` objekty). V takovém případě budou importovány pouze na určené typy. Přijímá přetížení <xref:System.Xml.Schema.XmlSchemaElement> , který importuje konkrétní element z celkového počtu `XmlSchemaSet`, stejně jako jeho přidruženého typu (Určuje, zda je anonymní nebo ne). Vrátí toto přetížení `XmlQualifiedName`, která představuje název kontraktu dat typu vygenerovaného pro tento element.  
  
     Více volání z `Import` výsledek metody ve více položek, které se přidávají do stejné `CodeCompileUnit`. Typ negeneruje do `CodeCompileUnit` Pokud již existuje. Volání `Import` více než jednou ve stejném `XsdDataContractImporter` namísto použití více `XsdDataContractImporter` objekty. Toto je doporučený postup, aby se generuje duplicitní typy.  
  
    > [!NOTE]
    > Pokud dojde k chybě při importu, `CodeCompileUnit` bude v nepředvídatelném stavu. Použití `CodeCompileUnit` vyplývající z neúspěšných importu může zpřístupnit můžete k ohrožení bezpečnosti.  
  
5. Přístup `CodeCompileUnit` prostřednictvím <xref:System.Runtime.Serialization.XsdDataContractImporter.CodeCompileUnit%2A> vlastnost.  
  
### <a name="import-options-customizing-the-generated-types"></a>Možnosti importu: Přizpůsobení generované typy  
 Můžete nastavit <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> vlastnost <xref:System.Runtime.Serialization.XsdDataContractImporter> do instance <xref:System.Runtime.Serialization.ImportOptions> třídy pro řízení různých aspektů proces importu. Řadu možností mají přímý vliv na typy, které jsou generovány.  
  
#### <a name="controlling-the-access-level-generateinternal-or-the-internal-switch"></a>Řízení úrovně přístupu (GenerateInternal nebo / interní přepnutí)  
 To odpovídá **/ interní** zapnout [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Za normálních okolností jsou veřejné typy generované ze schématu, s privátní pole a odpovídající vlastnosti člena veřejná data. Chcete-li místo toho generovat vnitřní typy, nastavte <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> vlastnost `true`.  
  
 Následující příklad ukazuje schématu transformují do vnitřní třídu při <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> je nastavena na `true.`  
  
 [!code-csharp[c_SchemaImportExport#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#2)]
 [!code-vb[c_SchemaImportExport#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#2)]  
  
#### <a name="controlling-namespaces-namespaces-or-the-namespace-switch"></a>Řízení obory názvů (obory názvů nebo parametru/Namespace přepnutí)  
 To odpovídá **/Namespace** zapnout `Svcutil.exe` nástroj.  
  
 Za normálních okolností jsou generované typy generované ze schématu do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obory názvů, s každý obor názvů XSD odpovídající konkrétní [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] oboru názvů podle popisu v mapování [referenční dokumentace schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Toto mapování tak můžete přizpůsobit <xref:System.Runtime.Serialization.ImportOptions.Namespaces%2A> vlastnost <xref:System.Collections.Generic.Dictionary%602>. Pokud daný obor názvů XSD se nachází ve slovníku odpovídající [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obor názvů se také přebírá ze slovníku.  
  
 Zvažte například následující schéma.  
  
 [!code-xml[c_SchemaImportExport#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#10)]  
  
 V následujícím příkladu `Namespaces` vlastnost mapovat `http://schemas.contoso.com/carSchema` obor názvů pro "Contoso.Cars".  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
#### <a name="adding-the-serializableattribute-generateserializable-or-the-serializable-switch"></a>Přidat atribut SerializableAttribute (GenerateSerializable nebo / serializovatelný přepnutí)  
 To odpovídá **/ serializovatelný** zapnout `Svcutil.exe` nástroj.  
  
 Někdy je důležité pro typy generované ze schématu má být použitelná s [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] moduly runtime serializace (například <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> třídy). To je užitečné při použití typů pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] vzdálené komunikace. Chcete-li povolit, musíte použít <xref:System.SerializableAttribute> atribut generované typy kromě standardní <xref:System.Runtime.Serialization.DataContractAttribute> atribut. Atribut je generován automaticky, pokud `GenerateSerializable` možnost importu je nastavena na `true`.  
  
 Následující příklad ukazuje `Vehicle` generuje s použitím třídy `GenerateSerializable` nastavena na možnost importu `true`.  
  
 [!code-csharp[c_SchemaImportExport#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#4)]
 [!code-vb[c_SchemaImportExport#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#4)]  
  
#### <a name="adding-data-binding-support-enabledatabinding-or-the-enabledatabinding-switch"></a>Přidání podpory vazby dat (EnableDataBinding nebo přepínač /enableDataBinding)  
 To odpovídá **/enableDataBinding** zapnout nástroje Svcutil.exe.  
  
 V některých případech můžete chtít vytvořit vazbu typy generované ze schématu součásti grafického uživatelského rozhraní tak, aby se jakýmkoli aktualizacím instancí těchto typů budou automaticky aktualizovat uživatelské rozhraní. `XsdDataContractImporter` Můžete vygenerovat typy, které implementují <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní tak, že všechny změny vlastností aktivuje událost. Pokud jsou generování typů pro použití s programovací prostředí klienta uživatelského rozhraní, která podporuje toto rozhraní (jako je například Windows Presentation Foundation (WPF)), nastavte <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> vlastnost `true` tuto funkci povolil.  
  
 Následující příklad ukazuje `Vehicle` generuje s použitím třídy <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> nastavena na `true`.  
  
 [!code-csharp[C_SchemaImportExport#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#5)]
 [!code-vb[C_SchemaImportExport#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#5)]  
  
### <a name="import-options-choosing-collection-types"></a>Možnosti importu: Když zvolíte typy kolekcí  
 Kolekce položek představují dva speciální vzory v kódu XML: seznam položek a přidružení mezi jednu položku a další. Následuje příklad seznamu řetězců.  
  
 [!code-xml[C_SchemaImportExport#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#11)]  
  
 Následuje příklad asociace mezi řetězci a celé číslo (`city name` a `population`).  
  
 [!code-xml[C_SchemaImportExport#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#12)]  
  
> [!NOTE]
>  Žádné přidružení může také zvážit seznamu. Například můžete zobrazit předchozí asociace jako seznam komplexní `city` objekty, ke kterým dochází na dvou polí (pole řetězce a pole celé číslo). Oba vzorky mít reprezentaci ve schématu XSD. Neexistuje žádný způsob k rozlišení mezi seznamem a přidružení, tak tyto vzory jsou vždy považovány za seznamy, pokud je k dispozici ve schématu speciální poznámky specifické pro WCF. Anotace označuje, že zadaný vzor představuje přidružení. Další informace najdete v tématu [schéma kontraktů dat – referenční informace](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Za normálních okolností je importovat seznam jako, který je odvozen z obecného seznamu nebo jako kontraktu dat kolekce [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pole, v závislosti na tom, zda schéma dodržuje standardní pojmenování pro kolekce. To je popsáno podrobněji v [typy kolekcí v kontraktech dat](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). Přidružení se obvykle importují jako buď <xref:System.Collections.Generic.Dictionary%602> nebo kontraktu dat kolekce, která je odvozena z objektu slovník. Zvažte například následující schéma.  
  
 [!code-xml[c_SchemaImportExport#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#13)]  
  
 To by byl importován následujícím způsobem (pole se zobrazí místo vlastnosti pro lepší čitelnost).  
  
 [!code-csharp[c_SchemaImportExport#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#6)]
 [!code-vb[c_SchemaImportExport#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#6)]  
  
 Je možné přizpůsobit typy kolekcí, které jsou generovány pro tyto vzory schématu. Například můžete chtít generovat kolekce odvozené od <xref:System.ComponentModel.BindingList%601> místo <xref:System.Collections.Generic.List%601> třídy, aby bylo možné navázat na pole se seznamem a jeho automaticky aktualizovat při změně obsahu z kolekce. Chcete-li to provést, nastavte <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> vlastnost <xref:System.Runtime.Serialization.ImportOptions> třídy do seznamu typy kolekce, který se má použít (dále jen označované jako odkazované typy). Při importu jakoukoli kolekci, je možné tento seznam odkazovaných typů kolekce a nejlépe odpovídající kolekci se používá, pokud je takový nalezen. Přidružení jsou porovnány pouze s typy, které implementují obecné a neobecné <xref:System.Collections.IDictionary> rozhraní, zatímco seznamy jsou porovnány s jakýkoli typ podporovaných kolekce.  
  
 Například pokud <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> je nastavena na <xref:System.ComponentModel.BindingList%601>, `people` typ v předchozím příkladu je generován následujícím způsobem.  
  
 [!code-csharp[C_SchemaImportExport#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#7)]
 [!code-vb[C_SchemaImportExport#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#7)]  
  
 Uzavřený obecný se považuje za nejvhodnější. Například pokud typy `BindingList(Of Integer)` a <xref:System.Collections.ArrayList> jsou předány do kolekce odkazované typy, jsou importovány všechny seznamy celá čísla nalezena ve schématu jako `BindingList(Of Integer)`. Jakékoli další seznamy, například `List(Of String)`, jsou naimportované jako `ArrayList`.  
  
 Pokud typ, který implementuje obecné `IDictionary` rozhraní se přidá do kolekce odkazovaných typů, jeho parametry typu musí být zcela otevřená nebo plně uzavřené.  
  
 Duplicitní položky nejsou povoleny. Například nelze přidat i `List(Of Integer)` a `Collection(Of Integer)` pro odkazované typy. Který by ji činilo možné určit, který má být použit, pokud je seznam celá čísla nalezena ve schématu. Duplicitní položky se zjistil pouze v případě, že je typ ve schématu, která zveřejňuje problém duplicitní položky. Například pokud importované schéma neobsahuje seznam celých čísel, to může mít oba `List(Of Integer)` a `Collection(Of Integer)` v odkazovaných typů kolekce, ale ani jeden bude mít žádný efekt.  
  
 Odkazovaných typů kolekce, které mechanismus funguje stejně dobře pro kolekce komplexních typů (včetně kolekce jiných kolekcí) a ne jenom pro kolekce primitivních elementů.  
  
 `ReferencedCollectionTypes` Odpovídá vlastnosti **/collectionType** zapnout nástroje SvcUtil.exe. Všimněte si, že odkazují na více typy kolekcí **/collectionType** přepínač musí být zadán více než jednou. Pokud typ není v knihovnu MsCorLib.dll, jeho sestavení musí také být odkazovány **/reference** přepnout.  
  
#### <a name="import-options-referencing-existing-types"></a>Možnosti importu: Odkazování na existující typy  
 V některých případech odpovídají existující typy ve schématu [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typů, a není nutné ke generování těchto typů úplně od začátku. (Tato část platí pouze pro typy noncollection. Typy kolekcí najdete v předchozí části.)  
  
 Například může mít standardní pořádaného microsoftem "Osoba" typ kontraktu dat, který chcete vždy použít při vyjadřování osoby. Pokaždé, když některé služby díky použití tohoto typu a jeho schématu se zobrazí v metadata služby, můžete chtít znovu použít existující `Person` zadejte při importu tohoto schématu namísto generování nové pro každou službu.  
  
 Chcete-li to provést, předejte seznam [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, které chcete znovu použít do kolekce <xref:System.Runtime.Serialization.ImportOptions.ReferencedTypes%2A> vlastnost vrátí na <xref:System.Runtime.Serialization.ImportOptions> třídy. Pokud některý z těchto typů názvem kontraktu dat a obor názvů, který odpovídá názvu a oboru názvů typu schématu, strukturálního porovnání je provedeno. Pokud je zjištěno, že typy mají odpovídající názvy a odpovídající struktury existující [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ je znovu použít namísto generování nové. Pokud pouze název odpovídá ale není struktury, je vyvolána výjimka. Všimněte si, že neexistuje žádný příspěvek pro správu verzí při odkazování na typy (například přidávání nové volitelné datové členy). Struktury musí přesně odpovídat.  
  
 Žádné typy schémat se importují s daným názvem a obor názvů, je možné přidat více typů se stejným názvem kontraktu dat a obor názvů do odkazovaných typů kolekce. To umožňuje snadno přidat všechny typy v sestavení do kolekce bez starostí o duplicitní položky pro typy, které skutečně nedojde ve schématu.  
  
 `ReferencedTypes` Odpovídá vlastnosti **/reference** v určitých režimy fungování nástroje Svcutil.exe přepínač.  
  
> [!NOTE]
>  Při použití Svcutil.exe nebo (v sadě Visual Studio) **přidat odkaz na službu** jsou automaticky odkazována nástroje, všechny typy v knihovně MsCorLib.dll.  
  
#### <a name="import-options-importing-non-datacontract-schema-as-ixmlserializable-types"></a>Možnosti importu: Import schématu jiné než DataContract jako IXmlSerializable typy  
 <xref:System.Runtime.Serialization.XsdDataContractImporter> Podporuje omezenou podmnožinou schématu. Pokud je konstrukce nepodporované schéma (například atributy ve formátu XML), pokus o import selže s výjimku. Však nastavení <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> vlastnost `true` rozšiřuje škálu schématu nepodporuje. Pokud je nastavena na `true`, <xref:System.Runtime.Serialization.XsdDataContractImporter> generuje typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní. To umožňuje přímý přístup k reprezentaci XML pro tyto typy.  
  
##### <a name="design-considerations"></a>Aspekty návrhu  
  
-   Může být obtížné pracovat přímo s slabě typované reprezentaci XML. Zvažte použití alternativní Serializační stroj, jako <xref:System.Xml.Serialization.XmlSerializer>, pro práci se schématem není kompatibilní s daty smlouvy tak silného typu. Další informace najdete v tématu [horizontálních oddílů pomocí třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
-   Některé schémat nejde importovat podle <xref:System.Runtime.Serialization.XsdDataContractImporter> i v případě <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> je nastavena na `true`. Znovu, zvažte použití <xref:System.Xml.Serialization.XmlSerializer> pro tyto případy.  
  
-   Přesné schémat, které jsou podporované jak při <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> je `true` nebo `false` jsou popsány v [schéma kontraktů dat – referenční informace](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
-   Generované schéma pro <xref:System.Xml.Serialization.IXmlSerializable> typy nezachovávají si věrnost při importovat a exportovat. To znamená export schématu z generované typy a import jako třídy vracet původnímu schématu.  
  
 Je možné kombinovat <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> spolu s možností <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> možnost popsaných výše. Pro typy, které mají být generován jako <xref:System.Xml.Serialization.IXmlSerializable> implementace, zkontrolujte strukturální bude přeskočena při použití <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> funkce.  
  
 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> Možnost odpovídá nabídce **/importXmlTypes** zapnout nástroje Svcutil.exe.  
  
##### <a name="working-with-generated-ixmlserializable-types"></a>Práce s typy generované IXmlSerializable  
 Vygenerovaný `IXmlSerializable` soukromé pole s názvem "nodesField," obsahují typy, které vrátí pole <xref:System.Xml.XmlNode> objekty. Při deserializaci instance takový typ, můžete přístup k datům XML přímo přes toto pole s použitím modelu objektu dokumentu XML. Při serializaci instance tohoto typu, toto pole můžete nastavit na požadovaná data XML a bude serializována.  
  
 To lze provést prostřednictvím `IXmlSerializable` implementace. V generované `IXmlSerializable` typ, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> implementace volá <xref:System.Runtime.Serialization.XmlSerializableServices.ReadNodes%2A> metodu <xref:System.Runtime.Serialization.XmlSerializableServices> třídy. Metoda je metoda helper, který převádí kód XML poskytnutý prostřednictvím <xref:System.Xml.XmlReader> pole <xref:System.Xml.XmlNode> objekty. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Implementace provádí opak a převede pole `XmlNode` objekty na řadu <xref:System.Xml.XmlWriter> volání. Využívá se při něm <xref:System.Runtime.Serialization.XmlSerializableServices.WriteNodes%2A> metody.  
  
 Je možné spustit proces exportu schématu generované `IXmlSerializable` třídy. Jak je uvedeno výše nebude původní schématu vrátit zpět. Místo toho se zobrazí "anyType" standardní XSD typu, což je zástupný znak pro jakýkoli typ XSD.  
  
 To lze provést použitím <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atribut generované `IXmlSerializable` třídy a zadávání metody, která volá <xref:System.Runtime.Serialization.XmlSerializableServices.AddDefaultSchema%2A> metoda ke generování typu "anyType".  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.XmlSerializableServices> Typ existuje výhradně na podporu této konkrétní funkce. To se nedoporučuje používat za žádným jiným účelem.  
  
#### <a name="import-options-advanced-options"></a>Možnosti importu: Rozšířené možnosti  
 Následující jsou rozšířené možnosti importu:  
  
-   <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> Vlastnost. Zadejte <xref:System.CodeDom.Compiler.CodeDomProvider> pro generování kódu pro vygenerované třídy. Pokusy o mechanismu import, aby funkce, které <xref:System.CodeDom.Compiler.CodeDomProvider> nepodporuje. Pokud <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> není nastavena, kompletní [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] funkce se používá bez omezení.  
  
-   <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> Vlastnost. <xref:System.Runtime.Serialization.IDataContractSurrogate> Implementace se dá nastavit pomocí této vlastnosti. <xref:System.Runtime.Serialization.IDataContractSurrogate> Přizpůsobí proces importu. Další informace najdete v tématu [náhrady kontraktů dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Ve výchozím nastavení je použít žádné náhrady.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.XsdDataContractImporter>
- <xref:System.Runtime.Serialization.XsdDataContractExporter>
- <xref:System.Runtime.Serialization.ImportOptions>
- [Schéma kontraktů dat – referenční informace](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)
- [Náhrady kontraktů dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)
- [Import a export schémat](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)
- [Export schémat ze tříd](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)
- [Schéma kontraktů dat – referenční informace](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)

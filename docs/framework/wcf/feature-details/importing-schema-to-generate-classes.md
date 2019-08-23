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
ms.openlocfilehash: dc33088c3519bfd088ed64a4de087c5086890804
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69918478"
---
# <a name="importing-schema-to-generate-classes"></a>Import schématu pro generování tříd
Chcete-li generovat třídy ze schémat, která jsou použitelná pomocí Windows Communication Foundation (WCF) <xref:System.Runtime.Serialization.XsdDataContractImporter> , použijte třídu. Toto téma popisuje proces a variace.  
  
## <a name="the-import-process"></a>Proces importu
 Proces importu schématu začíná <xref:System.Xml.Schema.XmlSchemaSet> na a a <xref:System.CodeDom.CodeCompileUnit>vytvoří.  
  
 `XmlSchemaSet` Je součástí modelu objektu schématu .NET Framework (SOM), který představuje sadu dokumentů schémat XML Schema Definition Language (XSD). Chcete-li `XmlSchemaSet` vytvořit objekt ze sady dokumentů XSD, proveďte deserializaci každého dokumentu <xref:System.Xml.Schema.XmlSchema> do objektu (pomocí <xref:System.Xml.Serialization.XmlSerializer>) a přidejte tyto objekty do nového `XmlSchemaSet`.  
  
 `CodeCompileUnit` Je součástí Code Document Object Model .NET Framework (CodeDOM), která představuje kód .NET Framework abstraktním způsobem. Chcete-li vygenerovat skutečný kód `CodeCompileUnit`z a, použijte podtřídu <xref:System.CodeDom.Compiler.CodeDomProvider> třídy, jako je <xref:Microsoft.CSharp.CSharpCodeProvider> například třída <xref:Microsoft.VisualBasic.VBCodeProvider> nebo.  
  
### <a name="to-import-a-schema"></a>Import schématu  
  
1. Vytvořte instanci <xref:System.Runtime.Serialization.XsdDataContractImporter>.  
  
2. Volitelný parametr. `CodeCompileUnit` Předat v konstruktoru. Typy generované během importu schématu jsou přidány do této `CodeCompileUnit` instance namísto začátku s prázdným. `CodeCompileUnit`  
  
3. Volitelný parametr. Zavolejte jednu z <xref:System.Runtime.Serialization.XsdDataContractImporter.CanImport%2A> metod. Metoda určuje, zda je dané schéma platné schéma kontraktu dat a lze jej importovat. Metoda má stejná přetížení jako `Import` (další krok). `CanImport`  
  
4. Zavolejte jednu z přetížených `Import` metod, <xref:System.Runtime.Serialization.XsdDataContractImporter.Import%28System.Xml.Schema.XmlSchemaSet%29> například metoda.  
  
     Nejjednodušší přetížení přebírá `XmlSchemaSet` a importuje všechny typy, včetně anonymních typů, které jsou v této sadě schémat nalezeny. Další přetížení umožňují zadat typ XSD nebo seznam typů pro import (ve formě <xref:System.Xml.XmlQualifiedName> nebo `XmlQualifiedName` kolekce objektů). V takovém případě se importují pouze zadané typy. Přetížení přebírá <xref:System.Xml.Schema.XmlSchemaElement> , které importuje konkrétní element mimo `XmlSchemaSet`, a také přidružený typ (bez ohledu na to, jestli je anonymní nebo ne). Toto přetížení vrátí hodnotu `XmlQualifiedName`, která představuje název kontraktu dat typu generovaného pro tento element.  
  
     Více volání `Import` metody má za následek přidání více položek do stejného `CodeCompileUnit`. Typ se negeneruje do, `CodeCompileUnit` Pokud již existuje. Volejte `Import` `XsdDataContractImporter` víckrát `XsdDataContractImporter` namísto použití více objektů. Toto je doporučený způsob, jak se vyhnout vygenerování duplicitních typů.  
  
    > [!NOTE]
    > Pokud během importu dojde k chybě, `CodeCompileUnit` bude v nepředvídatelném stavu. `CodeCompileUnit` Použití výsledku importu z neúspěšného importu vám může vystavit ohrožení zabezpečení.  
  
5. Přístup k `CodeCompileUnit` <xref:System.Runtime.Serialization.XsdDataContractImporter.CodeCompileUnit%2A> vlastnostem.  
  
### <a name="import-options-customizing-the-generated-types"></a>Možnosti importu: Přizpůsobení generovaných typů  
 Můžete nastavit <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> vlastnost <xref:System.Runtime.Serialization.XsdDataContractImporter> na instanci <xref:System.Runtime.Serialization.ImportOptions> třídy pro řízení různých aspektů procesu importu. Mnoho možností má přímý vliv na typy, které jsou generovány.  
  
#### <a name="controlling-the-access-level-generateinternal-or-the-internal-switch"></a>Řízení úrovně přístupu (GenerateInternal nebo přepínač/Internal)  
 To odpovídá přepínači **/internal** v nástroji pro nástroj pro [metadata ServiceModel (Svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 V normálním případě veřejné typy jsou generovány ze schématu s privátními poli a se shodnými vlastnostmi členů veřejných dat. Chcete-li místo toho vytvořit interní typy <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> , nastavte `true`vlastnost na hodnotu.  
  
 Následující příklad ukazuje schéma transformované na interní třídu, <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> Pokud je vlastnost nastavena na`true.`  
  
 [!code-csharp[c_SchemaImportExport#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#2)]
 [!code-vb[c_SchemaImportExport#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#2)]  
  
#### <a name="controlling-namespaces-namespaces-or-the-namespace-switch"></a>Řízení oborů názvů (obory názvů nebo přepínač/namespace)  
 To odpovídá přepínači **/Namespace** na `Svcutil.exe` nástroji.  
  
 Obvykle se typy generované ze schématu generují do .NET Framework obory názvů s každým oborem názvů XSD odpovídajícím konkrétnímu .NET Framework oboru názvů podle mapování popsaného v tématu [referenční informace schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Toto mapování <xref:System.Runtime.Serialization.ImportOptions.Namespaces%2A> můžete přizpůsobit vlastností <xref:System.Collections.Generic.Dictionary%602>na. Pokud je daný obor názvů XSD nalezen ve slovníku, povedený .NET Framework obor názvů je také z vašeho slovníku.  
  
 Zvažte například následující schéma.  
  
 [!code-xml[c_SchemaImportExport#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#10)]  
  
 Následující příklad používá `Namespaces` vlastnost k `http://schemas.contoso.com/carSchema` mapování oboru názvů na "contoso. auta".  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
#### <a name="adding-the-serializableattribute-generateserializable-or-the-serializable-switch"></a>Přidání parametru SerializableAttribute (GenerateSerializable nebo/Serializable)  
 To odpovídá přepínači **/Serializable** na `Svcutil.exe` nástroji.  
  
 Někdy je důležité, aby typy generované ve schématu byly použitelné s .NET Framework modulem runtime serializace (například <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> třídy a třídy). To je užitečné, když používáte typy pro vzdálenou komunikaci .NET Framework. Chcete-li tuto možnost povolit, je <xref:System.SerializableAttribute> nutné použít atribut pro vygenerované typy kromě regulárního <xref:System.Runtime.Serialization.DataContractAttribute> atributu. Atribut je generován automaticky, pokud `GenerateSerializable` je možnost importu nastavena na. `true`  
  
 Následující příklad ukazuje `Vehicle` třídu generovanou `GenerateSerializable` s možností import nastavenou na `true`.  
  
 [!code-csharp[c_SchemaImportExport#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#4)]
 [!code-vb[c_SchemaImportExport#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#4)]  
  
#### <a name="adding-data-binding-support-enabledatabinding-or-the-enabledatabinding-switch"></a>Přidání podpory datových vazeb (EnableDataBinding nebo přepínač/enableDataBinding)  
 To odpovídá přepínači **/EnableDataBinding** pro nástroj Svcutil. exe.  
  
 V některých případech můžete chtít navazovat typy generované ze schématu na komponenty grafického uživatelského rozhraní, aby každá aktualizace instancí těchto typů automaticky aktualizovala uživatelské rozhraní. Může generovat typy, které <xref:System.ComponentModel.INotifyPropertyChanged> implementují rozhraní takovým způsobem, že jakákoli změna vlastnosti aktivuje událost. `XsdDataContractImporter` Pokud generujete typy pro použití s prostředím programování klientského uživatelského rozhraní, které podporuje toto rozhraní (například Windows Presentation Foundation (WPF)), nastavte <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> vlastnost na `true` hodnotu Povolit tuto funkci.  
  
 Následující příklad ukazuje `Vehicle` třídu generovanou <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> s nastavením na `true`.  
  
 [!code-csharp[C_SchemaImportExport#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#5)]
 [!code-vb[C_SchemaImportExport#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#5)]  
  
### <a name="import-options-choosing-collection-types"></a>Možnosti importu: Výběr typů kolekce  
 Dva speciální vzory v XML reprezentují kolekce položek: seznam položek a přidružení mezi jednou a druhou položkou. Následuje příklad seznamu řetězců.  
  
 [!code-xml[C_SchemaImportExport#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#11)]  
  
 Následuje příklad přidružení mezi řetězcem a celým číslem (`city name` a `population`).  
  
 [!code-xml[C_SchemaImportExport#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#12)]  
  
> [!NOTE]
> Jakékoli přidružení může být také považováno za seznam. Můžete například zobrazit předchozí přidružení jako seznam komplexních `city` objektů, které se stávají mít dvě pole (pole řetězce a pole typu Integer). Oba vzory mají reprezentaci ve schématu XSD. Neexistuje žádný způsob, jak rozlišovat mezi seznamem a přidruženími, takže takové vzory jsou vždy považovány za seznamy, pokud není ve schématu k dispozici speciální Poznámka specifická pro WCF. Poznámka označuje, že daný vzor představuje přidružení. Další informace najdete v tématu [referenční informace o schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 V normálním případě je seznam importován jako kontrakt dat kolekce, který je odvozen z obecného seznamu nebo jako .NET Framework pole, podle toho, zda schéma řídí standardní vzor názvů pro kolekce. Tato informace je podrobněji popsána v tématu [typy kolekcí v kontraktech dat](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). Přidružení jsou obvykle importována jako <xref:System.Collections.Generic.Dictionary%602> kontrakt dat kolekce nebo, který je odvozen z objektu Dictionary. Zvažte například následující schéma.  
  
 [!code-xml[c_SchemaImportExport#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#13)]  
  
 To by se importovalo takto (pole se zobrazují místo vlastností pro čitelnost).  
  
 [!code-csharp[c_SchemaImportExport#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#6)]
 [!code-vb[c_SchemaImportExport#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#6)]  
  
 Je možné přizpůsobit typy kolekce, které jsou generovány pro tyto vzory schématu. Například můžete chtít generovat kolekce, které jsou odvozeny od <xref:System.ComponentModel.BindingList%601> <xref:System.Collections.Generic.List%601> třídy namísto třídy, aby bylo možné vytvořit vazby typu k poli seznamu a automaticky aktualizovat při změně obsahu kolekce. Chcete-li to provést, <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> nastavte vlastnost <xref:System.Runtime.Serialization.ImportOptions> třídy na seznam typů kolekce, které mají být použity (dále označované jako odkazované typy). Při importu libovolné kolekce se prohledají tento seznam odkazovaných typů kolekce a když se najde ten, použije se nejlepší vyhovující kolekce. Přidružení jsou shodná pouze s typy, které implementují obecné nebo neobecné <xref:System.Collections.IDictionary> rozhraní, zatímco seznamy jsou porovnány s libovolným podporovaným typem kolekce.  
  
 Například pokud <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> je vlastnost nastavena <xref:System.ComponentModel.BindingList%601>na, `people` typ v předchozím příkladu je generován následujícím způsobem.  
  
 [!code-csharp[C_SchemaImportExport#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#7)]
 [!code-vb[C_SchemaImportExport#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#7)]  
  
 Uzavřená obecná je považována za nejlepší shodu. Například pokud jsou typy `BindingList(Of Integer)` a <xref:System.Collections.ArrayList> předány do kolekce odkazovaných typů, všechny seznamy celých čísel nalezených ve `BindingList(Of Integer)`schématu jsou importovány jako. Všechny ostatní seznamy, například a `List(Of String)`, jsou importovány `ArrayList`jako.  
  
 Pokud je typ, který implementuje obecné `IDictionary` rozhraní, přidán do kolekce odkazovaných typů, jeho parametry typu musí být buď plně otevřené, nebo zcela uzavřeny.  
  
 Duplicity nejsou povoleny. Například nelze přidat jak `List(Of Integer)` `Collection(Of Integer)` a, do odkazovaných typů. Takže by nebylo možné určit, která by se měla použít, když se ve schématu najde seznam celých čísel. Duplicity budou zjištěny pouze v případě, že existuje typ ve schématu, který zveřejňuje problém s duplicitami. Například pokud importované schéma neobsahuje seznam celých čísel, může mít `List(Of Integer)` `Collection(Of Integer)` i v kolekci odkazovaných typů, ale ani to nebude mít žádný vliv.  
  
 Seznam odkazovaných typů kolekce funguje stejně dobře pro kolekce komplexních typů (včetně kolekcí jiných kolekcí), a ne pouze pro kolekce primitivních elementů.  
  
 Vlastnost odpovídá přepínači/CollectionType pro nástroj Svcutil. exe. `ReferencedCollectionTypes` Všimněte si, že pro odkazování na více typů kolekce je třeba zadat přepínač **/CollectionType** několikrát. Pokud typ není v knihovně MsCorLib. dll, jeho sestavení musí být také odkazováno pomocí přepínače **/reference** .  
  
#### <a name="import-options-referencing-existing-types"></a>Možnosti importu: Odkazování na existující typy  
 V některých případech typy ve schématu odpovídají existujícím typům .NET Framework a není nutné generovat tyto typy od začátku. (Tato část se vztahuje pouze na typy nekolekce. Typy kolekcí najdete v předchozí části.)  
  
 Můžete mít například standardní typ kontraktu dat "osoba", který je možné vždy použít při reprezentaci osoby. Když některá služba využívá tento typ a jeho schéma se zobrazí v metadatech služby, můžete chtít znovu použít existující `Person` typ při importu tohoto schématu místo generování nového pro každou službu.  
  
 Provedete to tak, že předáte seznam typů .NET Framework, které chcete znovu použít do kolekce <xref:System.Runtime.Serialization.ImportOptions.ReferencedTypes%2A> , kterou vlastnost vrátí <xref:System.Runtime.Serialization.ImportOptions> u třídy. Pokud některý z těchto typů má název kontraktu dat a obor názvů, který se shoduje s názvem a oborem názvů typu schématu, provede se strukturální porovnání. Je-li zjištěno, že typy mají jak stejné názvy, tak i odpovídající struktury, je místo generování nového typu .NET Framework znovu použit existující typ. Pokud pouze název odpovídá pouze názvu, ale nikoli struktuře, je vyvolána výjimka. Všimněte si, že při odkazování na typy (například přidávání nových volitelných datových členů) neplatí žádná náhrada při vytváření verzí. Struktury se musí přesně shodovat.  
  
 Je možné přidat více typů se stejným názvem kontraktu dat a oborem názvů do odkazované kolekce typů, pokud nejsou importovány žádné typy schémat s tímto názvem a oborem názvů. To umožňuje snadno přidat všechny typy v sestavení do kolekce, aniž byste se museli starat o duplicity pro typy, které ve schématu skutečně nevzniknou.  
  
 Vlastnost odpovídá přepínači/reference v určitých režimech provozu nástroje Svcutil. exe. `ReferencedTypes`  
  
> [!NOTE]
> Při použití nástroje Svcutil. exe nebo (v aplikaci Visual Studio) **Přidat odkaz na službu** nástrojů jsou automaticky odkazovány všechny typy v knihovně Mscorlib. dll.  
  
#### <a name="import-options-importing-non-datacontract-schema-as-ixmlserializable-types"></a>Možnosti importu: Import schématu nesouvisejících kontraktů dat jako typů IXmlSerializable  
 <xref:System.Runtime.Serialization.XsdDataContractImporter> Podporuje omezené podmnožinu schématu. Pokud jsou k dispozici nepodporované konstrukce schématu (například atributy XML), pokus o import se nezdaří s výjimkou. Nicméně nastavení <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> vlastnosti na `true` prodlouží rozsah podporovaných schémat. Když je `true` <xref:System.Runtime.Serialization.XsdDataContractImporter> nastavena na, <xref:System.Xml.Serialization.IXmlSerializable> vygeneruje typy, které implementují rozhraní. To umožňuje přímý přístup k reprezentace XML těchto typů.  
  
##### <a name="design-considerations"></a>Faktory návrhu  
  
- Může být obtížné pracovat se slabě typovou reprezentací XML přímo. Zvažte použití alternativního modulu serializace, jako je <xref:System.Xml.Serialization.XmlSerializer>, pro práci se schématem, který není kompatibilní s kontrakty dat se silným typem. Další informace naleznete v tématu [použití třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
- Některé konstrukce schématu nelze importovat <xref:System.Runtime.Serialization.XsdDataContractImporter> ani v případě, <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> že je vlastnost nastavena na `true`hodnotu. Znovu zvažte použití <xref:System.Xml.Serialization.XmlSerializer> pro tyto případy.  
  
- Přesné konstrukce schématu, které jsou podporovány v případě, <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> kdy `true` je `false` , nebo jsou popsány v tématu [referenční informace schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
- Schéma pro vygenerované <xref:System.Xml.Serialization.IXmlSerializable> typy nezachovává věrnost při importu a exportu. To znamená, že exportování schématu z generovaných typů a import jako třídy nevrátí původní schéma.  
  
 Je možné zkombinovat <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> možnost <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> s výše popsanou možností. Pro typy, které musí být vygenerovány jako <xref:System.Xml.Serialization.IXmlSerializable> implementace, je při <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> používání funkce při použití této funkce vynechána strukturální kontroly.  
  
 Možnost odpovídá přepínači/importXmlTypes v nástroji Svcutil. exe. <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A>  
  
##### <a name="working-with-generated-ixmlserializable-types"></a>Práce s generovanými typy IXmlSerializable  
 Generované `IXmlSerializable` typy obsahují soukromé pole s názvem "nodesField", které vrací <xref:System.Xml.XmlNode> pole objektů. Při deserializaci instance takového typu můžete k datům XML přistupovat přímo prostřednictvím tohoto pole pomocí model DOM (Document Object Model) XML. Při serializaci instance tohoto typu můžete nastavit toto pole na požadovaná data XML a bude serializován.  
  
 To je provedeno `IXmlSerializable` implementací. Ve vygenerovaném `IXmlSerializable` typu <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> implementuje implementace <xref:System.Runtime.Serialization.XmlSerializableServices> volání <xref:System.Runtime.Serialization.XmlSerializableServices.ReadNodes%2A> metody třídy. Metoda je pomocná metoda, která převádí XML poskytnuté přes <xref:System.Xml.XmlReader> <xref:System.Xml.XmlNode> pole objektů. Implementace provede opak a převede `XmlNode` pole <xref:System.Xml.XmlWriter> objektů na posloupnost volání. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> To je provedeno pomocí <xref:System.Runtime.Serialization.XmlSerializableServices.WriteNodes%2A> metody.  
  
 Pro vygenerované `IXmlSerializable` třídy je možné spustit proces exportu schématu. Jak bylo uvedeno výše, původní schéma se zpátky nevrátí. Místo toho se zobrazí standardní typ XSD "anyType", což je zástupný znak pro libovolný typ XSD.  
  
 To lze provést použitím <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atributu na generované `IXmlSerializable` třídy a zadáním metody, která volá <xref:System.Runtime.Serialization.XmlSerializableServices.AddDefaultSchema%2A> metodu pro vygenerování typu "anyType".  
  
> [!NOTE]
> <xref:System.Runtime.Serialization.XmlSerializableServices> Typ existuje výhradně pro podporu této konkrétní funkce. Nedoporučuje se používat pro žádné jiné účely.  
  
#### <a name="import-options-advanced-options"></a>Možnosti importu: Rozšířené možnosti  
 Níže jsou uvedené rozšířené možnosti importu:  
  
- <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A>majetek. Určete, <xref:System.CodeDom.Compiler.CodeDomProvider> který má být použit k vygenerování kódu pro vygenerované třídy. Mechanismus importu se pokusí vyhnout funkcím, které <xref:System.CodeDom.Compiler.CodeDomProvider> nepodporuje. <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> Pokud není nastavená, použije se úplná sada funkcí .NET Framework bez omezení.  
  
- <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A>majetek. Pomocí této vlastnosti lze určit implementaci.<xref:System.Runtime.Serialization.IDataContractSurrogate> <xref:System.Runtime.Serialization.IDataContractSurrogate> Přizpůsobuje proces importu. Další informace najdete v tématu [náhrada za kontrakty dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Ve výchozím nastavení se nepoužívá žádná náhrada.  
  
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

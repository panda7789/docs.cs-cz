---
title: Import schématu pro generování tříd
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, schema import and export
- XsdDataContractImporter class
ms.assetid: b9170583-8c34-43bd-97bb-6c0c8dddeee0
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7fc755ff7f1b6c583a1e9aa1bc209495563812f0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="importing-schema-to-generate-classes"></a>Import schématu pro generování tříd
Generovat třídy z schémat, které lze použít s [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], použijte <xref:System.Runtime.Serialization.XsdDataContractImporter> třídy. Toto téma popisuje proces a variace.  
  
## <a name="the-import-process"></a>Proces importu  
 Proces importu schématu začíná <xref:System.Xml.Schema.XmlSchemaSet> a vytvoří <xref:System.CodeDom.CodeCompileUnit>.  
  
 `XmlSchemaSet` Je součástí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]na schéma objektu modelu (SOM) představující sadu schématu XML definition language (XSD) schéma dokumentů. K vytvoření `XmlSchemaSet` objektu ze sady XSD dokumentů, deserializovat každý dokument do <xref:System.Xml.Schema.XmlSchema> objektu (pomocí <xref:System.Xml.Serialization.XmlSerializer>) a přidejte tyto objekty na nový `XmlSchemaSet`.  
  
 `CodeCompileUnit` Je součástí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]na Code Document Object Model (CodeDOM), který představuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] kód abstraktní způsobem. Ke generování skutečné kódu z `CodeCompileUnit`, použijte podtřídou třídy <xref:System.CodeDom.Compiler.CodeDomProvider> třídy, jako <xref:Microsoft.CSharp.CSharpCodeProvider> nebo <xref:Microsoft.VisualBasic.VBCodeProvider> – třída.  
  
#### <a name="to-import-a-schema"></a>Chcete-li importovat schéma.  
  
1.  Vytvoření instance <xref:System.Runtime.Serialization.XsdDataContractImporter>.  
  
2.  Volitelné. Předat `CodeCompileUnit` v konstruktoru. Typy vygenerovaných během importu schématu jsou přidány do tohoto `CodeCompileUnit` instanci místo počínaje prázdné `CodeCompileUnit`.  
  
3.  Volitelné. Volání jednoho z <xref:System.Runtime.Serialization.XsdDataContractImporter.CanImport%2A> metody. Metoda určuje, zda daný schématu je schéma kontrakt platná data a lze importovat. `CanImport` Metoda má stejné přetížení jako `Import` (Další krok).  
  
4.  Volání jednoho z přetížené `Import` metody, například <xref:System.Runtime.Serialization.XsdDataContractImporter.Import%28System.Xml.Schema.XmlSchemaSet%29> metoda.  
  
     Nejjednodušší přetížení trvá `XmlSchemaSet` a importuje všechny typy, včetně anonymní typy, nalezeno v dané sadě schématu. Další přetížení umožňují určit typ XSD nebo seznam typů import (ve formě <xref:System.Xml.XmlQualifiedName> nebo kolekci `XmlQualifiedName` objektů). V takovém případě jsou importována pouze zadaného typu. Přetížení trvá <xref:System.Xml.Schema.XmlSchemaElement> který naimportuje určitý element mimo `XmlSchemaSet`, a jeho přidružený typ (jestli je anonymní nebo ne). Toto přetížení vrátí `XmlQualifiedName`, která představuje název kontraktu dat typu generované pro tento element.  
  
     Více volá z `Import` výsledek metody v více položek, který se přidává do stejné `CodeCompileUnit`. Typ nevygenerovala do `CodeCompileUnit` Pokud zde již existuje. Volání `Import` víckrát na stejný `XsdDataContractImporter` místo použití více `XsdDataContractImporter` objekty. To je doporučeným způsobem, aby se zabránilo duplicitním typy generován.  
  
    > [!NOTE]
    >  Pokud dojde k selhání při importu, `CodeCompileUnit` bude v nepředvídatelném stavu. Použití `CodeCompileUnit` vyplývající z neúspěšných import mohla vystavit můžete k ohrožení zabezpečení.  
  
5.  Přístup `CodeCompileUnit` prostřednictvím <xref:System.Runtime.Serialization.XsdDataContractImporter.CodeCompileUnit%2A> vlastnost.  
  
### <a name="import-options-customizing-the-generated-types"></a>Možnosti importu: Přizpůsobení generovaného typy  
 Můžete nastavit <xref:System.Runtime.Serialization.XsdDataContractImporter.Options%2A> vlastnost <xref:System.Runtime.Serialization.XsdDataContractImporter> na instanci systému <xref:System.Runtime.Serialization.ImportOptions> třídy ovládat různé aspekty procesu importu. Počet možností přímo ovlivňují typy, které se generují.  
  
#### <a name="controlling-the-access-level-generateinternal-or-the-internal-switch"></a>Řízení úrovně přístupu (GenerateInternal nebo / vnitřní přepínače)  
 To odpovídá **/ vnitřní** přepínač na [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).  
  
 Za normálních okolností veřejné typy jsou generovány ze schématu s privátním polím a odpovídající vlastnosti člena veřejná data. Chcete-li vygenerovat interní typy místo, nastavte <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> vlastnost `true`.  
  
 Následující příklad ukazuje schéma převede na interní třídy, kdy <xref:System.Runtime.Serialization.ImportOptions.GenerateInternal%2A> je nastavena na `true.`  
  
 [!code-csharp[c_SchemaImportExport#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#2)]
 [!code-vb[c_SchemaImportExport#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#2)]  
  
#### <a name="controlling-namespaces-namespaces-or-the-namespace-switch"></a>Řízení obory názvů (obory názvů nebo/Namespace přepínače)  
 To odpovídá **/Namespace** přepínač na `Svcutil.exe` nástroj.  
  
 Za normálních okolností jsou generovány typy generované ze schématu do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obory názvů, s každý obor názvů XSD odpovídající konkrétní [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] oboru názvů podle mapování popsané v [Přehled schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md). Můžete upravit toto mapování pomocí <xref:System.Runtime.Serialization.ImportOptions.Namespaces%2A> vlastnosti <xref:System.Collections.Generic.Dictionary%602>. Pokud se najde daném oboru názvů XSD ve slovníku shody [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] obor názvů je také převzat ze slovníku.  
  
 Zvažte například následující schéma.  
  
 [!code-xml[c_SchemaImportExport#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#10)]  
  
 Následující příklad používá `Namespaces` vlastnost mapovat "http://schemas.contoso.com/carSchema" názvů "Contoso.Cars".  
  
 [!code-csharp[c_SchemaImportExport#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#8)]
 [!code-vb[c_SchemaImportExport#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#8)]  
  
#### <a name="adding-the-serializableattribute-generateserializable-or-the-serializable-switch"></a>Přidávání SerializableAttribute (GenerateSerializable nebo / serializovatelný přepínače)  
 To odpovídá **/ serializovatelný** přepínač na `Svcutil.exe` nástroj.  
  
 Někdy je důležité pro typy generované ze schématu možné používat s [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] moduly runtime serializace (například <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter?displayProperty=nameWithType> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> třídy). To je užitečné při použití typy pro [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] vzdálenou komunikaci. Chcete-li povolit, je nutné použít <xref:System.SerializableAttribute> atribut generovaný typy kromě běžné <xref:System.Runtime.Serialization.DataContractAttribute> atribut. Atribut je vytvořen automaticky, pokud `GenerateSerializable` import možnost nastavená na `true`.  
  
 Následující příklad ukazuje `Vehicle` třída vygenerovat pomocí `GenerateSerializable` importovat možnost nastavena na hodnotu `true`.  
  
 [!code-csharp[c_SchemaImportExport#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#4)]
 [!code-vb[c_SchemaImportExport#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#4)]  
  
#### <a name="adding-data-binding-support-enabledatabinding-or-the-enabledatabinding-switch"></a>Přidání podpory vazby dat (EnableDataBinding nebo přepínač /enableDataBinding)  
 To odpovídá **/enableDataBinding** přepínač na nástroje Svcutil.exe.  
  
 V některých případech můžete vytvořit vazbu typy generované ze schématu součásti grafické uživatelské rozhraní tak, aby všechny výskyty tyto typy automaticky aktualizuje uživatelské rozhraní. `XsdDataContractImporter` Může generovat typy, které implementují <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní tak, že všechny změny vlastností aktivuje událost. Pokud jsou generování typů pro použití s programovací prostředí klienta uživatelského rozhraní, která podporuje toto rozhraní (například Windows Presentation Foundation (WPF)), nastavte <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> vlastnost `true` tuto funkci povolíte.  
  
 Následující příklad ukazuje `Vehicle` třída vygenerovat pomocí <xref:System.Runtime.Serialization.ImportOptions.EnableDataBinding%2A> nastavena na `true`.  
  
 [!code-csharp[C_SchemaImportExport#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#5)]
 [!code-vb[C_SchemaImportExport#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#5)]  
  
### <a name="import-options-choosing-collection-types"></a>Možnosti importu: Výběr typy kolekcí  
 Kolekce položek, představují dva speciální vzory v kódu XML: seznam položek a přidružení mezi jednu položku. Následuje příklad seznamu řetězců.  
  
 [!code-xml[C_SchemaImportExport#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#11)]  
  
 Tady je příklad přidružení mezi řetězce a celé číslo (`city name` a `population`).  
  
 [!code-xml[C_SchemaImportExport#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#12)]  
  
> [!NOTE]
>  Přidružení, může také zvážit seznamu. Například můžete zobrazit předchozí přidružení jako seznam komplexní `city` objekty, které mají náhodou dvě pole (pole řetězce a pole celé číslo). Obě vzory mít znázornění ve schématu XSD. Neexistuje žádný způsob k rozlišení mezi seznam a přidružení, takže pokud jsou tyto vzory vždy považovány za seznamy speciální poznámky, které jsou specifické pro [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je k dispozici ve schématu. Anotace označuje, že se zadaným vzorem představuje přidružení. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Referenční schéma kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Za normálních okolností se importuje seznam jako kontrakt dat kolekce, která je odvozena ze seznamu obecný nebo jako [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pole, v závislosti na tom, zda schéma se následující standardní pojmenování pro kolekce. To je popsáno v podrobněji [typy kolekcí v kontraktech dat](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md). Přidružení jsou obvykle importovat, protože buď <xref:System.Collections.Generic.Dictionary%602> nebo kontrakt dat kolekce, která je odvozena z objekt slovníku. Zvažte například následující schéma.  
  
 [!code-xml[c_SchemaImportExport#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/common/source.config#13)]  
  
 To by byl importován následujícím způsobem (pole jsou uvedené místo vlastnosti čitelnější).  
  
 [!code-csharp[c_SchemaImportExport#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#6)]
 [!code-vb[c_SchemaImportExport#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#6)]  
  
 Je možné přizpůsobit typy kolekcí, které jsou generovány pro tyto vzory schématu. Můžete například vygenerovat odvozování z kolekce <xref:System.ComponentModel.BindingList%601> místo <xref:System.Collections.Generic.List%601> třídy, aby bylo možné vytvořit vazbu typ pole se seznamem a mějte ho automaticky aktualizuje při změně obsahu kolekce. Chcete-li to provést, nastavte <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> vlastnost <xref:System.Runtime.Serialization.ImportOptions> třídy do seznamu typy kolekcí, který se má použít (dále jen známé jako odkazované typy). Při importu jakoukoli kolekci, je tento seznam typů odkazovaná kolekce kontroloval a nejlépe odpovídající kolekce se používá, pokud je takový nalezen. Přidružení se porovnání pouze typy, které implementují obecné nebo neobecné <xref:System.Collections.IDictionary> rozhraní, zatímco seznamy jsou porovnání jakýkoli typ podporované kolekce.  
  
 Například pokud <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> je nastavena na <xref:System.ComponentModel.BindingList%601>, `people` typ v předchozím příkladu je generován následujícím způsobem.  
  
 [!code-csharp[C_SchemaImportExport#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_schemaimportexport/cs/source.cs#7)]
 [!code-vb[C_SchemaImportExport#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_schemaimportexport/vb/source.vb#7)]  
  
 Uzavřené obecného považuje za nejlepší shodu. Například pokud typy `BindingList(Of Integer)` a <xref:System.Collections.ArrayList> se předávají do kolekce z odkazovaných typů, všechny seznamy celých čísel v schématu nalezeno importují jako `BindingList(Of Integer)`. Jakékoli další seznamy, například `List(Of String)`, se importují jako `ArrayList`.  
  
 Pokud typ, který implementuje obecné `IDictionary` rozhraní je přidat do kolekce z odkazovaných typů, jeho parametry typu musí být buď plně otevřené nebo plně uzavřené.  
  
 Duplicitní položky nejsou povoleny. Například nelze přidat, i `List(Of Integer)` a `Collection(Of Integer)` na odkazované typy. Který by ji činilo možné určit, který má být použit, když se najde seznam celých čísel ve schématu. Duplicity se vyhledat pouze v případě, že je typu ve schématu, která zveřejňuje problém duplicitní položky. Například pokud schéma importované neobsahuje seznam celých čísel, je povoleno oba `List(Of Integer)` a `Collection(Of Integer)` v odkazovaných typů kolekce, ale ani jeden z nich bude mít žádný vliv.  
  
 Typy odkazovaná kolekce, které mechanismus funguje stejně dobře pro kolekce komplexních typů (včetně kolekce jiné kolekce) a nejen pro kolekce primitivních elementů.  
  
 `ReferencedCollectionTypes` Vlastnost odpovídá **/collectionType** přepínač na nástroje SvcUtil.exe. Všimněte si, že chcete-li více typy kolekcí **/collectionType** přepínače musí být zadána vícekrát. Pokud typ není v MsCorLib.dll, jeho sestavení musí také odkazovat pomocí **/reference** přepínače.  
  
#### <a name="import-options-referencing-existing-types"></a>Možnosti importu: Odkazující na existující typy  
 V některých případech typy ve schématu odpovídají existující [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, a není nutné ke generování tyto typy od začátku. (V této části platí pouze pro typy noncollection. Typy kolekcí najdete v předchozí části.)  
  
 Například může mít standardní společnosti "Osoba" datový kontrakt typ, který chcete vždy použít při představující osoby. Vždy, když některé služby umožňuje použití tohoto typu a jeho schématu se zobrazí v metadatech služby, možná budete chtít použít existující `Person` zadejte při importu toto schéma, místo aby generovala novou pro každou službu.  
  
 K tomuto účelu předat seznam [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typy, které chcete znovu použít do kolekce <xref:System.Runtime.Serialization.ImportOptions.ReferencedTypes%2A> vlastnost vrací na <xref:System.Runtime.Serialization.ImportOptions> třídy. Pokud některý z těchto typů název kontraktu dat a obor názvů, který odpovídá názvu a obor názvů typu schématu, se provádí strukturální porovnání. Pokud je zjištěno, že typy mají odpovídající názvy a odpovídající struktury, existující [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typu se znovu použije, místo aby generovala novou. Pokud jenom název odpovídá ale není strukturu, je vyvolána výjimka. Všimněte si, že žádné povoleného užívání pro správu verzí při odkazování na typy (například přidání nové volitelné datových členů). Struktury se musí přesně shodovat.  
  
 Žádné schéma jsou importována s tímto názvem a obor názvů, je právní přidat více typů se stejným názvem kontraktu dat. a obor názvů ke kolekci odkazované typy. To umožňuje snadno přidat všechny typy v sestavení do kolekce bez obav, duplicitní položky pro typy, které se ve skutečnosti nevyskytují ve schématu.  
  
 `ReferencedTypes` Vlastnost odpovídá **/reference** přepínače v určité režimy činnosti nástroje Svcutil.exe.  
  
> [!NOTE]
>  Při použití Svcutil.exe nebo (v [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)]) **přidat odkaz na službu** nástroje pro všechny typy v MsCorLib.dll se automaticky odkazuje.  
  
#### <a name="import-options-importing-non-datacontract-schema-as-ixmlserializable-types"></a>Možnosti importu: Import schématu Non-kontraktu jako IXmlSerializable typy  
 <xref:System.Runtime.Serialization.XsdDataContractImporter> Podporuje omezenou podmnožinou schématu. Nepodporované schéma konstrukce jsou v něm (například atributy XML), import pokus selže, s výjimkou. Nastavení však <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> vlastnost `true` rozšiřuje rozsah schématu podporována. Pokud nastavíte hodnotu `true`, <xref:System.Runtime.Serialization.XsdDataContractImporter> generuje typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní. To umožňuje přímý přístup k reprezentaci XML z těchto typů.  
  
##### <a name="design-considerations"></a>Aspekty návrhu  
  
-   Může být obtížné pracovat přímo s slabě typovaná reprezentaci XML. Zvažte použití modul alternativní serializace, jako <xref:System.Xml.Serialization.XmlSerializer>, pracovat s schématu není kompatibilní s daty kontrakty způsobem silného typu. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Používání třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md).  
  
-   Některé konstrukce schématu nelze importovat pomocí <xref:System.Runtime.Serialization.XsdDataContractImporter> i v případě <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> je nastavena na `true`. Znovu, zvažte použití <xref:System.Xml.Serialization.XmlSerializer> takových případech.  
  
-   Konstrukce přesný schéma, které jsou podporované, jak při <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> je `true` nebo `false` jsou popsané v [Přehled schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
-   Schéma pro generované <xref:System.Xml.Serialization.IXmlSerializable> typy není zachována věrnosti import a export. Schéma původní tedy nevrací export schématu generovaného typy a import jako třídy.  
  
 Je možné kombinovat <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> možnost s <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> možnost popsaných výše. Pro typy, které mají být generován jako <xref:System.Xml.Serialization.IXmlSerializable> implementacích strukturální kontrola bude přeskočena při použití <xref:System.ServiceModel.Description.ServiceContractGenerator.ReferencedTypes%2A> funkce.  
  
 <xref:System.Runtime.Serialization.ImportOptions.ImportXmlType%2A> Možnost odpovídá nabídce **/importXmlTypes** přepínač na nástroje Svcutil.exe.  
  
##### <a name="working-with-generated-ixmlserializable-types"></a>Práce s generovaného IXmlSerializable typy  
 Generovaný objekt `IXmlSerializable` typy obsahovat privátní pole, s názvem "nodesField", který vrátí pole <xref:System.Xml.XmlNode> objekty. Při deserializaci instanci takového typu, můžete přístup k datům XML přímo přes toto pole pomocí objektového modelu dokumentu XML. Při serializaci instance tohoto typu, můžete nastavit v tomto poli k požadovaným datům XML a budou serializována.  
  
 To lze provést pomocí `IXmlSerializable` implementace. V vygenerovaného `IXmlSerializable` typu, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> implementace volá <xref:System.Runtime.Serialization.XmlSerializableServices.ReadNodes%2A> metodu <xref:System.Runtime.Serialization.XmlSerializableServices> třídy. Metoda je pomocná metoda, která převede XML zajišťováno prostřednictvím <xref:System.Xml.XmlReader> na pole <xref:System.Xml.XmlNode> objekty. <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> Implementace je tomu naopak a převede pole `XmlNode` objekty, které se posloupnost <xref:System.Xml.XmlWriter> volání. Toho dosahuje pomocí <xref:System.Runtime.Serialization.XmlSerializableServices.WriteNodes%2A> metoda.  
  
 Je možné spustit proces exportu schématu na vygenerovaného `IXmlSerializable` třídy. Jak je uvedeno nebude původní schéma vrátit zpět. Místo toho obdržíte "anyType" standardní typ XSD, což je zástupný znak pro jakýkoli typ XSD.  
  
 Toho dosáhnete použitím <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atribut vygenerovaného `IXmlSerializable` třídy a metody určení, který volá <xref:System.Runtime.Serialization.XmlSerializableServices.AddDefaultSchema%2A> metoda ke generování typu "anyType".  
  
> [!NOTE]
>  <xref:System.Runtime.Serialization.XmlSerializableServices> Typ existuje výhradně pro podporu tato konkrétní funkce. Není doporučeno používat za žádným jiným účelem.  
  
#### <a name="import-options-advanced-options"></a>Možnosti importu: Rozšířené možnosti  
 Následující pokročilé možnosti importu:  
  
-   <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> Vlastnost. Zadejte <xref:System.CodeDom.Compiler.CodeDomProvider> sloužící ke generování kódu pro vygenerovaný třídy. Pokusy o mechanismus import, aby se zabránilo funkce, které <xref:System.CodeDom.Compiler.CodeDomProvider> nepodporuje. Pokud <xref:System.Runtime.Serialization.ImportOptions.CodeProvider%2A> není nastavena, kompletní [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] funkce se používá bez omezení.  
  
-   <xref:System.Runtime.Serialization.ImportOptions.DataContractSurrogate%2A> Vlastnost. <xref:System.Runtime.Serialization.IDataContractSurrogate> Implementace lze zadat s touto vlastností. <xref:System.Runtime.Serialization.IDataContractSurrogate> Přizpůsobí procesu importu. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Náhrady kontraktů dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md). Ve výchozím nastavení se používá žádné náhradní.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.XsdDataContractImporter>  
 <xref:System.Runtime.Serialization.XsdDataContractExporter>  
 <xref:System.Runtime.Serialization.ImportOptions>  
 [Schéma kontraktů dat – referenční informace](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 [Náhrady kontraktů dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md)  
 [Import a export schémat](../../../../docs/framework/wcf/feature-details/schema-import-and-export.md)  
 [Export schémat ze tříd](../../../../docs/framework/wcf/feature-details/exporting-schemas-from-classes.md)  
 [Schéma kontraktů dat – referenční informace](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)

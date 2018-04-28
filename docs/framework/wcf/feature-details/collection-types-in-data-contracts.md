---
title: Typy kolekcí v kontraktech dat
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
- collection types [WCF], data contracts
- data contracts [WCF], collection types
- collection types [WCF]
ms.assetid: 9b45b28e-0a82-4ea3-8c33-ec0094aff9d5
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 528c1661b99ff5f50d42bb7a42371c302e335c90
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="collection-types-in-data-contracts"></a>Typy kolekcí v kontraktech dat
A *kolekce* je seznam položek určitého typu. V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], jsou seznamy může být reprezentován pomocí pole nebo celou řadu dalších typů (obecný seznam, obecného <xref:System.ComponentModel.BindingList%601>, <xref:System.Collections.Specialized.StringCollection>, nebo <xref:System.Collections.ArrayList>). Například kolekce může obsahovat seznam adres pro danou zákazníka. Tato kolekce se nazývají *seznam kolekcí*, bez ohledu na to jejich skutečným typem.  
  
 Speciální formulář kolekce existuje, který představuje přidružení mezi jednu položku ("klíč") a jiné ("hodnota"). V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], ty jsou reprezentované pomocí typy, jako <xref:System.Collections.Hashtable> a obecné slovníku. Například může kolekci přidružení mapování města ("klíč") na jeho naplnění ("value"). Tato kolekce se nazývají *kolekce slovníku*, bez ohledu na to jejich skutečným typem.  
  
 Kolekce přijímat zvláštní zacházení v datovém modelu kontrakt.  
  
 Typy, které implementují <xref:System.Collections.IEnumerable> rozhraní, včetně polí a obecné kolekce, jsou rozpoznány jako kolekce. Z nich, typy, které implementují <xref:System.Collections.IDictionary> nebo obecný <xref:System.Collections.Generic.IDictionary%602> rozhraní jsou kolekce slovníku; všechny ostatní jsou kolekce seznamu.  
  
 Další požadavky na typy kolekcí, jako je například s metodu s názvem `Add` a výchozí konstruktor, jsou podrobněji v následujících částech. To zajistí, že typy kolekcí může být současně serializaci a deserializaci. To znamená, že některé kolekce nepodporuje přímo, jako je například obecná <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> (protože nemá žádné výchozí konstruktor). Ale informace o obcházení tato omezení, najdete v části "Použití kolekce rozhraní typy a jen pro čtení kolekce" dál v tomto tématu.  
  
 Typy obsažené v kolekcích musí být typy kontraktů dat nebo jinak být serializovatelný. Další informace najdete v tématu [typy nepodporuje serializátor kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Co je a co se nepovažuje za platnou kolekci, stejně jako o tom, jak se serializují kolekcí, přečtěte si informace o serializaci kolekce v části "pravidla shromažďování Advanced" v tomto tématu.  
  
## <a name="interchangeable-collections"></a>Zaměňovat kolekce  
 Všechny kolekce seznamu stejného typu jsou považovány za stejná data kontrakt (Pokud se jsou přizpůsobit pomocí <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributu, jak je popsáno dále v tomto tématu). Proto například následující kontrakty dat jsou ekvivalentní.  
  
 [!code-csharp[c_collection_types_in_data_contracts#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#0)]
 [!code-vb[c_collection_types_in_data_contracts#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#0)]  
  
 Obě kontrakty dat za následek podobná následující kód XML.  
  
```xml  
<PurchaseOrder>  
    <customerName>...</customerName>  
    <items>  
        <Item>...</Item>  
        <Item>...</Item>  
        <Item>...</Item>  
        ...  
    </items>  
    <comments>  
        <string>...</string>  
        <string>...</string>  
        <string>...</string>  
        ...  
    </comments>  
</PurchaseOrder>  
```  
  
 Kolekce zaměnitelnost umožňuje vám použít, například, typu kolekce, která je optimalizovaná pro výkon na serveru a typu kolekce, která je navržená tak, aby být vázána na součásti uživatelského rozhraní na straně klienta.  
  
 Podobně jako seznam kolekcí, všechny kolekce slovníku, které mají stejný klíč a hodnotu typy jsou považovány za obsahovaly stejná data kontrakt (není-li přizpůsobit pomocí <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut).  
  
 Pouze data kontrakt typ záleží daleko collection ekvivalenční problémem, není typy .NET. To znamená kolekce Type1 je považovány za ekvivalentní na kolekci Type2 Pokud Type1 a Type2 ekvivalentní datové kontrakty.  
  
 Non obecné kolekce jsou považovány za stejná data jako obecné kolekce typu kontraktu `Object`. (Například na smlouvách data <xref:System.Collections.ArrayList> a obecná <xref:System.Collections.Generic.List%601> z `Object` jsou stejné.)  
  
## <a name="using-collection-interface-types-and-read-only-collections"></a>Pomocí rozhraní typy kolekcí a kolekce jen pro čtení  
 Typy kolekcí rozhraní (<xref:System.Collections.IEnumerable>, <xref:System.Collections.IDictionary>obecný <xref:System.Collections.Generic.IDictionary%602>, nebo rozhraní odvozené od těchto rozhraní) jsou také považovány za tak, že má kolekce datové kontrakty, ekvivalentní kontrakty kolekce dat pro typy skutečné kolekcí. Proto je možné deklarovat serializovaný jako typ rozhraní kolekce typ a výsledky jsou stejné, jako kdyby byly použity typ shromažďování. Například následující kontrakty dat jsou ekvivalentní.  
  
 [!code-csharp[c_collection_types_in_data_contracts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#1)]
 [!code-vb[c_collection_types_in_data_contracts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#1)]  
  
 Během serializace Pokud je deklarovaný typ rozhraní, lze skutečné instance typu použitého žádný typ, který implementuje rozhraní. Omezení jak jsme vysvětlili výše (s výchozí konstruktor a `Add` metoda) se nevztahují. Například můžete nastavit adresy v Customer2 na instanci Obecné <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> adresy, i když nelze deklarovat přímo data členem zadejte obecného <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
 Během deserializace, pokud deklarovaný typ je rozhraní, pro Serializační stroj vybere typ, který implementuje rozhraní deklarované a vytvoření instance typu. Známé typy mechanismus (popsané v [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)) nemá žádný vliv zde; je součástí volba typu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="customizing-collection-types"></a>Přizpůsobení typy kolekcí  
 Typy kolekcí lze přizpůsobit pomocí <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut, který se dá použít několika způsoby.  
  
 Poznámka: Tento přizpůsobení kolekci typů ohrožení kolekce zaměnitelnost, tak obecně se doporučuje Vyhněte se použití tohoto atributu, kdykoli je to možné. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Tento problém, naleznete v části "pravidla shromažďování Advanced" dál v tomto tématu.  
  
### <a name="collection-data-contract-naming"></a>Kontrakt dat kolekce pojmenování  
 Pravidla pro pojmenovávání typy kolekcí jsou podobná těm pro pojmenování regulární datové typy kontrakt, jak je popsáno v [názvy datových kontraktů](../../../../docs/framework/wcf/feature-details/data-contract-names.md), i když existuje několik důležitých rozdílů:  
  
-   <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Atribut slouží k přizpůsobení názvu, místo <xref:System.Runtime.Serialization.DataContractAttribute> atribut. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Atribut má také `Name` a `Namespace` vlastnosti.  
  
-   Když <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut není použit, výchozí název a obor názvů pro typy kolekcí závisí na názvy a obory názvů obsažené v kolekci typů. Ovlivněné nejsou podle názvu a obor názvů samotného typu kolekce. Příklad najdete v tématu následující typy.  
  
    ```  
    public CustomerList1 : Collection<string> {}  
    public StringList1 : Collection<string> {}  
    ```  
  
 Název kontraktu oba typy dat je "ArrayOfstring" a není "CustomerList1" nebo "StringList1". To znamená, že serializaci kterékoli z těchto typů na kořenové úrovni vypočítá podobná následující kód XML.  
  
```xml  
<ArrayOfstring>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</ArrayOfstring>  
```  
  
 Toto pravidlo pojmenování jste vybrali zajistit, že žádný neupravené typ, který představuje seznam řetězců, má stejné kontrakt dat a reprezentaci XML. Díky zaměnitelnost kolekce. V tomto příkladu se úplně zaměňovat CustomerList1 a StringList1.  
  
 Ale pokud <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut se používá, kolekce stane kontraktu uzpůsobenou kolekci dat i v případě, že jsou na atribut nastavené žádné vlastnosti. Název a obor názvů dat kolekce smlouvy a závisí na typu kolekce sám sebe. Příklad najdete v tématu následujícího typu.  
  
 [!code-csharp[c_collection_types_in_data_contracts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#2)]
 [!code-vb[c_collection_types_in_data_contracts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#2)]  
  
 Když serializovat, výsledná XML je podobný následujícímu.  
  
```xml  
<CustomerList2>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</CustomerList2>  
```  
  
 Všimněte si, že není již ekvivalentní k reprezentaci XML neupravené typů.  
  
-   Můžete použít `Name` a `Namespace` vlastnosti k dalšímu přizpůsobení u názvu. Viz následující třídy.  
  
     [!code-csharp[c_collection_types_in_data_contracts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#3)]
     [!code-vb[c_collection_types_in_data_contracts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#3)]  
  
 Výsledný XML je podobný následujícímu.  
  
```xml  
<cust_list>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</cust_list>  
```  
  
 Další informace najdete v části "pravidla shromažďování Advanced" dál v tomto tématu.  
  
### <a name="customizing-the-repeating-element-name-in-list-collections"></a>Přizpůsobení opakovaný název elementu v seznamu kolekce  
 Seznam kolekcí obsahovat opakující se položky. Každý záznam opakující se za normálních okolností je reprezentována jako element s názvem podle název kontraktu dat typu obsažené v kolekci.  
  
 V `CustomerList` příklady, kolekce obsažené řetězce. Název kontraktu dat pro primitivní typ řetězec je "řetězec", takže opakovaných element "\<řetězec >".  
  
 Však pomocí <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> vlastnost na <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut opakující se tento název elementu, který lze přizpůsobit. Příklad najdete v tématu následujícího typu.  
  
 [!code-csharp[c_collection_types_in_data_contracts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#4)]
 [!code-vb[c_collection_types_in_data_contracts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#4)]  
  
 Výsledný XML je podobný následujícímu.  
  
```xml  
<CustomerList4>  
    <customer>...</customer>  
    <customer>...</customer>  
    <customer>...</customer>  
    ...  
</CustomerList4>  
```  
  
 Obor názvů opakující se prvek je vždy stejný jako obor názvů kontraktu dat kolekce, které lze přizpůsobit pomocí `Namespace` vlastnost, jak je popsáno výše.  
  
### <a name="customizing-dictionary-collections"></a>Přizpůsobení kolekce slovníku  
 Kolekce slovníku jsou v podstatě seznam položek, kde každá položka má klíč a hodnotu. Stejně jako s regulární seznamy, můžete změnit název elementu, který odpovídá opakovaných element pomocí <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> vlastnost.  
  
 Kromě toho můžete změnit názvy elementů, které představují klíč a hodnotu pomocí <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> a <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> vlastnosti. Obory názvů pro tyto prvky jsou stejné jako obor názvů kontraktu dat kolekce.  
  
 Příklad najdete v tématu následujícího typu.  
  
 [!code-csharp[c_collection_types_in_data_contracts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#5)]
 [!code-vb[c_collection_types_in_data_contracts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#5)]  
  
 Když serializovat, výsledná XML je podobný následujícímu.  
  
```xml  
<CountriesOrRegionsWithCapitals>  
    <entry>  
        <countryorregion>USA</countryorregion>  
        <capital>Washington</capital>  
    </entry>  
    <entry>  
        <countryorregion>France</countryorregion>  
        <capital>Paris</capital>  
    </entry>  
    ...  
</CountriesOrRegionsWithCapitals>  
```  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] kolekce slovníku, najdete v části "pravidla shromažďování Advanced" dál v tomto tématu.  
  
## <a name="collections-and-known-types"></a>Kolekce a známé typy  
 Není nutné přidat typy kolekcí do známé typy při použití polymorphically místo ostatní kolekce nebo rozhraní pro kolekce. Například, pokud je deklarovat členem datového typu <xref:System.Collections.IEnumerable> a použít ho k odeslání instanci <xref:System.Collections.ArrayList>, není potřeba přidat <xref:System.Collections.ArrayList> na známé typy.  
  
 Použijete-li kolekce polymorphically místo typy jiných kolekcí, je nutné přidat do známé typy. Například, pokud je deklarovat členem datového typu `Object` a použít ho k odeslání instanci <xref:System.Collections.ArrayList>, přidejte <xref:System.Collections.ArrayList> na známé typy.  
  
 To je určená k serializaci jakékoli ekvivalentní kolekce polymorphically nepovolíte. Například když přidáte <xref:System.Collections.ArrayList> do seznamu ze známých typů v předchozím příkladu to neumožňuje přiřadit `Array of Object` třídy, i když má ekvivalentní datové kontrakt. Nijak se to neliší od chování regulárních známé typy v serializace pro typy jiných kolekcí, ale je velmi důležité pochopit v případě kolekcí, protože je velmi běžné pro kolekce jako ekvivalentní.  
  
 Během serializace může být známé pouze jeden typ v jakékoli dané oboru pro kontraktu dat a ekvivalentní kolekce všechny mají stejné kontrakty dat. To znamená, že v předchozím příkladu, nemůžete přidat i <xref:System.Collections.ArrayList> a `Array of Object` na známé typy ve stejném oboru. Znovu jde o ekvivalent známé typy chování pro jiné kolekce typy, ale je velmi důležité porozumět pro kolekce.  
  
 Známé typy může být potřeba taky pro obsah kolekcí. Například pokud <xref:System.Collections.ArrayList> ve skutečnosti obsahuje instance `Type1` a `Type2`, oba tyto typy musí být přidaní do známé typy.  
  
 Následující příklad ukazuje správně strukturovaný objekt graf pomocí kolekcí a známé typy. V příkladu je poněkud contrived, protože v aplikaci skutečné nejsou obvykle definujete následující členy data jako `Object`a proto nemají žádné známé typu nebo polymorfismus problémy.  
  
 [!code-csharp[c_collection_types_in_data_contracts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#6)]
 [!code-vb[c_collection_types_in_data_contracts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#6)]  
  
 U deserializace Pokud deklarovaný typ je typu kolekce je deklarovaný typ instanci bez ohledu na typ, který vám byl zaslán ve skutečnosti. Pokud deklarovaný typ rozhraní kolekci, vybere deserializátor typu, který chcete vytvořit instanci, bez ohledu na na známé typy.  
  
 Také u deserializace, pokud deklarovaný typ není typu kolekce, ale typ kolekce je odesílány, odpovídající typ kolekce vydán mimo seznamu známé typy. Je možné přidat do seznamu ze známých typů pro deserializaci rozhraní typy kolekcí. V takovém případě modul deserializace znovu vybere typ má být vytvořena instance.  
  
## <a name="collections-and-the-netdatacontractserializer-class"></a>Kolekce a NetDataContractSerializer – třída  
 Když <xref:System.Runtime.Serialization.NetDataContractSerializer> třída se používá, typy kolekcí neupravené (bez <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut), není pole ztrácejí zvláštní význam.  
  
 Typy kolekcí přizpůsobené bez označené jako <xref:System.SerializableAttribute> atribut může serializovat stále <xref:System.Runtime.Serialization.NetDataContractSerializer> třídy podle <xref:System.SerializableAttribute> atribut nebo <xref:System.Runtime.Serialization.ISerializable> rozhraní pravidla.  
  
 Typy vlastní kolekce, rozhraní pro kolekce a pole jsou stále považovány za kolekcí, i v případě <xref:System.Runtime.Serialization.NetDataContractSerializer> třída se používá.  
  
## <a name="collections-and-schema"></a>Kolekce a schématu  
 Všechny kolekce ekvivalentní mají stejnou reprezentaci ve schématu XML definition language (XSD) schématu. Z toho důvodu se obvykle nezobrazí stejného typu kolekce v kód klienta vygenerovaný jako ten, na serveru. Například může server použít kontraktu dat s obecný <xref:System.Collections.Generic.List%601> datového členu celé číslo, ale kód klienta vygenerovaný stejného člena dat se může stát pole celých čísel.  
  
 Kolekce slovníku jsou označené [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-poznámky určité schéma, které označují, že jsou slovník; jinak, jsou lišit od jednoduchých seznamů, které obsahují položky se klíč a hodnotu. Přesný popis zastoupení kolekce ve schématu kontraktu dat, najdete v části [Přehled schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Ve výchozím nastavení nejsou typy generované neupravené kolekcí v importovaných kódu. Datové členy kolekce typů seznamu se importují jako pole a datové členy typy kolekcí slovník importují jako obecný slovníku.  
  
 Ale pro vlastní kolekce, samostatné typy jsou generovány, označené jako <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut. (Uzpůsobenou kolekci typu ve schématu je ten, který nepoužívá výchozí obor názvů, název, opakovaný název elementu nebo klíč/hodnota názvy elementu.) Tyto typy jsou prázdné typy, které jsou odvozeny od obecného <xref:System.Collections.Generic.List%601> typů seznamů a obecné slovník pro typy slovníku.  
  
 Například může mít následující typy na serveru.  
  
 [!code-csharp[c_collection_types_in_data_contracts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#7)]
 [!code-vb[c_collection_types_in_data_contracts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#7)]  
  
 Při exportu schéma a importované zpět znovu, kód klienta vygenerovaný je podobný následujícímu (pole jsou uvedené místo vlastnosti pro snadnější čtení).  
  
 [!code-csharp[c_collection_types_in_data_contracts#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#8)]
 [!code-vb[c_collection_types_in_data_contracts#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#8)]  
  
 Můžete používat různé typy generovaného kódu než výchozí hodnoty. Například můžete chtít použít Obecné <xref:System.ComponentModel.BindingList%601> místo regulární pole členům dat se usnadňují navázat je součástí uživatelského rozhraní.  
  
 Chcete-li zvolit typy kolekcí ke generování, předat seznam typů kolekce, kterou chcete použít do <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> vlastnost <xref:System.Runtime.Serialization.ImportOptions> objektu při importu schématu. Tyto typy jsou označovány jako *odkazuje typy kolekcí*.  
  
 Při obecné typy se odkazuje, se musí být buď plně open obecné nebo plně uzavřený obecné typy.  
  
> [!NOTE]
>  Při použití nástroje Svcutil.exe, tento odkaz můžete provést pomocí **/collectionType** přepínač příkazového řádku (krátký tvar: **/ct**). Mějte na paměti, která je nutné také zadat sestavení pro typy odkazovaná kolekce pomocí **/reference** přepínače (krátký tvar: **/r**). Pokud je obecný typ, se musí následovat zpětné uvozovky a počet obecné parametry. Zpětné uvozovky (') je termín nelze zaměňovat s znak jednoduché uvozovky ('). Můžete určit více typy odkazovaná kolekce pomocí **/collectionType** přepínač více než jednou.  
  
 Chcete-li například způsobit, že všechny seznamy, které má být importován jako obecný <xref:System.Collections.Generic.List%601>.  
  
```  
svcutil.exe MyService.wsdl MyServiceSchema.xsd /r:C:\full_path_to_system_dll\System.dll /ct:System.Collections.Generic.List`1  
```  
  
 Při importu jakoukoli kolekci, je tento seznam typů odkazovaná kolekce zkontrolovat a nejlépe odpovídající kolekce se používá, pokud ho najde, jako datový typ člena (pro neupravené kolekce) nebo jako základní typ k odvozování z (pro vlastní kolekce). Slovník jsou pouze porovnání slovníky, zatímco seznamy jsou porovnání seznamy.  
  
 Například, pokud přidáte obecná <xref:System.ComponentModel.BindingList%601> a <xref:System.Collections.Hashtable> seznam odkazovaných typů, kód klienta vygenerovaný pro v předchozím příkladu je podobný následujícímu.  
  
 [!code-csharp[c_collection_types_in_data_contracts#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#9)]
 [!code-vb[c_collection_types_in_data_contracts#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#9)]  
  
 Můžete určit typy rozhraní kolekce jako součást vaší typy odkazovaná kolekce, nemůžete ale zadat neplatný kolekci typů (jako jsou ty, které bez `Add` metoda nebo konstruktor public).  
  
 Uzavřené obecného se považuje za nejlepší shodu. (Non obecné typy jsou považovány za ekvivalentní do uzavřených obecných typů z `Object`). Například pokud typy obecného <xref:System.Collections.Generic.List%601> z <xref:System.DateTime>obecný <xref:System.ComponentModel.BindingList%601> (otevřete obecné), a <xref:System.Collections.ArrayList> jsou typy odkazovaná kolekce následující se vygeneruje.  
  
 [!code-csharp[c_collection_types_in_data_contracts#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#10)]
 [!code-vb[c_collection_types_in_data_contracts#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#10)]  
  
 Seznam kolekcí jsou podporovány pouze v případech v následující tabulce.  
  
|Odkazovaného typu|Rozhraní implementované odkazovaného typu|Příklad|Typ považován za:|  
|---------------------|----------------------------------------------|-------------|----------------------|  
|Obecná jiného typu nebo uzavřených obecného (libovolný počet parametrů)|Non obecné|`MyType : IList`<br /><br /> or<br /><br /> `MyType<T> : IList`<br /><br /> kde T = `int`|Uzavřený obecné z `Object` (například `IList<object>`)|  
|Obecná jiného typu nebo uzavřených obecného (libovolný počet parametrů, které neodpovídají nutně typ kolekce)|Uzavřený obecné|`MyType : IList<string>`<br /><br /> or<br /><br /> `MyType<T> : IList<string>` kde T =`int`|Uzavřené obecného (například `IList<string>`)|  
|Uzavřený obecné s libovolným počtem parametrů|Otevřete obecného pomocí některého z parametrů typu.|`MyType<T,U,V> : IList<U>`<br /><br /> kde T =`int`, U =`string`, V =`bool`|Uzavřené obecného (například `IList<string>`)|  
|Otevřete obecného s jeden parametr|Otevřete obecného pomocí parametru typu.|`MyType<T> : IList<T>`, T je otevřený|Otevřete obecného (například `IList<T>`)|  
  
 Pokud typ implementuje více než jedno rozhraní kolekce seznamu, se vztahují následující omezení:  
  
-   Pokud typ implementuje obecného <xref:System.Collections.Generic.IEnumerable%601> (nebo její odvozené rozhraní) více než jednou pro různé typy typ typu platný odkazovaná kolekce, nepovažuje se ignoruje. To platí i v případě, že některé implementace jsou neplatné nebo používají otevřete obecné typy. Například typ, který implementuje obecného <xref:System.Collections.Generic.IEnumerable%601> z `int` a obecná <xref:System.Collections.Generic.IEnumerable%601> t, které by se nikdy nepoužívá jako odkazované kolekce `int` nebo jakýkoli jiný typ, bez ohledu na to, zda má tento typ `Add` přijetí – metoda `int` nebo `Add` metoda přijímá parametr typ T, nebo obojí.  
  
-   Pokud typ implementuje rozhraní obecnou kolekci a také <xref:System.Collections.IList>, typ se nikdy nepoužívá jako typ odkazované kolekce, pokud rozhraní obecnou kolekci je uzavřené obecného typu <xref:System.Object>.  
  
 Pro kolekce slovníku jsou podporovány pouze v případech v následující tabulce.  
  
|Odkazovaného typu|Rozhraní implementované odkazovaného typu|Příklad|Typ považován za|  
|---------------------|----------------------------------------------|-------------|---------------------|  
|Obecná jiného typu nebo uzavřených obecného (libovolný počet parametrů)|<xref:System.Collections.IDictionary>|`MyType : IDictionary`<br /><br /> or<br /><br /> `MyType<T> : IDictionary` kde T =`int`|Uzavřený obecné `IDictionary<object,object>`|  
|Uzavřené obecného (libovolný počet parametrů)|<xref:System.Collections.Generic.IDictionary%602>, uzavřený|`MyType<T> : IDictionary<string, bool>` kde T =`int`|Uzavřené obecného (například `IDIctionary<string,bool>`)|  
|Uzavřené obecného (libovolný počet parametrů)|Obecné <xref:System.Collections.Generic.IDictionary%602>, jeden klíč nebo hodnota je uzavřen, druhý je otevřený a používá jeden z parametrů typu.|`MyType<T,U,V> : IDictionary<string,V>` kde T =`int`, U =`float`, V =`bool`<br /><br /> or<br /><br /> `MyType<Z> : IDictionary<Z,bool>` kde Z =`string`|Uzavřené obecného (například `IDictionary<string,bool>`)|  
|Uzavřené obecného (libovolný počet parametrů)|Obecné <xref:System.Collections.Generic.IDictionary%602>, klíče a hodnoty jsou otevřené a každá používá jeden z parametrů typu.|`MyType<T,U,V> : IDictionary<V,U>` kde T =`int`, U =`bool`, V =`string`|Uzavřené obecného (například `IDictionary<string,bool>`)|  
|Otevřete obecného (dva parametry)|Obecné <xref:System.Collections.Generic.IDictionary%602>, otevření, oba parametry obecného typu používá v pořadí, jsou zobrazeny|`MyType<K,V> : IDictionary<K,V>`, Tisíc a V obou otevřete|Otevřete obecného (například `IDictionary<K,V>`)|  
  
 Pokud typ implementuje obě <xref:System.Collections.IDictionary> a obecná <xref:System.Collections.Generic.IDictionary%602>pouze obecný <xref:System.Collections.Generic.IDictionary%602> se považuje za.  
  
 Odkazování na částečné obecné typy není podporována.  
  
 Duplicitní položky nejsou povoleny, například nelze přidat obě obecná <xref:System.Collections.Generic.List%601> z `Integer` a obecné kolekce `Integer` k <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, protože díky tomu je možné určit, který se má použít při seznam celých čísel nenajde ve schématu. Duplicity se jenom v případě, že je typu ve schématu, která zveřejňuje problém duplicitní položky. Například pokud schéma importovaných neobsahuje seznam celých čísel, je povoleno mít obě obecná <xref:System.Collections.Generic.List%601> z `Integer` a obecné kolekce `Integer` v <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, ale ani nemá žádný vliv.  
  
## <a name="advanced-collection-rules"></a>Pokročilé kolekce pravidel  
  
### <a name="serializing-collections"></a>Serializace kolekcí  
 Následuje seznam kolekci pravidel pro serializaci:  
  
-   Kombinování typy kolekcí (s kolekcí kolekcí) je povolen. Vícenásobná pole jsou považovány za kolekce kolekcí. Multidimenzionální pole nejsou podporována.  
  
-   Pole bajtů a pole <xref:System.Xml.XmlNode> jsou pole speciální typy, které jsou zpracovány jako primitiva, není kolekcí. Serializace pole bajtů výsledky v jednom elementu XML, který obsahuje bloku dat kódováním Base64, místo samostatných element pro každou bajtů. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] jak pole <xref:System.Xml.XmlNode> je zpracováván, najdete v části [typy XML a ADO.NET v kontraktech dat](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md). Samozřejmě, tyto speciální typy můžete sami účastnit kolekcí: pole pole bajtů za následek více elementů XML, pomocí každý obsahující bloků dat s kódováním Base64.  
  
-   Pokud <xref:System.Runtime.Serialization.DataContractAttribute> je použit atribut typu kolekce, typ je považován za regulární datového typu kontraktu, ne jako kolekce.  
  
-   Pokud typ kolekce implementuje <xref:System.Xml.Serialization.IXmlSerializable> platí následující pravidla rozhraní, zadaný typ `myType:IList<string>, IXmlSerializable`:  
  
    -   Pokud je deklarovaný typ `IList<string>`, je typ serializován jako seznam.  
  
    -   Pokud je deklarovaný typ `myType`, je serializován jako `IXmlSerializable`.  
  
    -   Pokud je deklarovaný typ `IXmlSerializable`, je serializován jako `IXmlSerializable`, ale jenom v případě, že přidáte `myType` do seznamu ze známých typů.  
  
-   Kolekce lze serializovat a deserializovat pomocí metody uvedené v následující tabulce.  
  
|Implementuje – typ kolekce|Volání metody pro serializaci|Volá metodu nebo metody k deserializaci|  
|--------------------------------|-----------------------------------------|-------------------------------------------|  
|Obecné <xref:System.Collections.Generic.IDictionary%602>|`get_Keys`, `get_Values`|Přidat obecné|  
|<xref:System.Collections.IDictionary>|`get_Keys`, `get_Values`|`Add`|  
|Obecné <xref:System.Collections.Generic.IList%601>|Obecné <xref:System.Collections.Generic.IList%601> indexeru|Přidat obecné|  
|Obecné <xref:System.Collections.Generic.ICollection%601>|Enumerátor|Přidat obecné|  
|<xref:System.Collections.IList>|<xref:System.Collections.IList> indexer|`Add`|  
|Obecné <xref:System.Collections.Generic.IEnumerable%601>|`GetEnumerator`|Volána metoda nestatické `Add` které přijímá jeden parametr příslušného typu (typ obecný parametr) nebo jednoho z jeho základních typů. Tato metoda musí existovat serializátoru považovat za kolekci během serializace a deserializace typu kolekce.|  
|<xref:System.Collections.IEnumerable> (a tedy <xref:System.Collections.ICollection>, která je odvozena z něj)|`GetEnumerator`|Volána metoda nestatické `Add` které přijímá jeden parametr typu `Object`. Tato metoda musí existovat serializátoru považovat za kolekci během serializace a deserializace typu kolekce.|  
  
 V předchozí tabulce jsou uvedeny rozhraní pro kolekce v sestupném pořadí podle priority. To znamená, například, pokud typ implementuje obě <xref:System.Collections.IList> a obecná <xref:System.Collections.Generic.IEnumerable%601>, kolekce se serializovat a deserializovat podle <xref:System.Collections.IList> pravidla:  
  
-   Při deserializaci jsou všechny kolekce deserializovat vytvořením první instance typu voláním výchozí konstruktor, který musí být k dispozici pro serializátor zacházet s typem kolekce jako kolekce během serializace a deserializace.  
  
-   Pokud je více než jednou implementovat stejné rozhraní obecnou kolekci (např. Pokud typ implementuje obou obecného <xref:System.Collections.Generic.ICollection%601> z `Integer` a obecná <xref:System.Collections.Generic.ICollection%601> z <xref:System.String>) a nenajde žádné rozhraní s vyšší prioritou, je kolekce nejsou považovány za platnou kolekci.  
  
-   Typy kolekcí může mít <xref:System.SerializableAttribute> atribut na ně použity a můžete implementovat <xref:System.Runtime.Serialization.ISerializable> rozhraní. Obě tyto se ignorují. Ale pokud typ plně nesplňuje požadavky na typ kolekce (například `Add` metoda nebyla nalezena), typ se nepovažuje za typu kolekce proto <xref:System.SerializableAttribute> atribut a <xref:System.Runtime.Serialization.ISerializable> rozhraní se používají k určení jestli může být typ serializovat.  
  
-   Použití <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut kolekce a přizpůsobit odebere <xref:System.SerializableAttribute> předcházející nouzový mechanismus. Místo toho, pokud vlastní kolekce nemá plnění kolekce zadejte požadavky, <xref:System.Runtime.Serialization.InvalidDataContractException> je vyvolána výjimka. Řetězec výjimky často obsahuje informace popisující, proč se daný typ nepovažuje za platnou kolekci (žádné `Add` metoda, neexistoval výchozí konstruktor a tak dále), takže je často užitečné použít <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut pro účely ladění.  
  
### <a name="collection-naming"></a>Pojmenování kolekce  
 Následuje seznam pravidla pojmenování kolekce:  
  
-   Výchozí obor názvů pro všechny smlouvy dat kolekce slovníku i pro kontrakty seznamu kolekce dat, které obsahují primitivní typy, je http://schemas.microsoft.com/2003/10/Serialization/Arrays Pokud přepsat pomocí Namespace. Typy, které jsou mapovány na vestavěné typy XSD, a také `char`, `Timespan`, a `Guid` typy, jsou považovány za primitiv pro tento účel.  
  
-   Výchozí obor názvů pro typy kolekcí, které obsahují není primitivní typy, pokud je přepsat, pomocí Namespace, je stejný jako obor názvů kontraktu dat typu obsažené v kolekci.  
  
-   Výchozí název pro seznam kolekce datové kontrakty, není-li přepsat pomocí názvu, je řetězec, který kombinaci "ArrayOf" s název kontraktu dat typu obsažené v kolekci. Například název kontraktu dat obecné seznamu celá je "ArrayOfint". Mějte na paměti, že název kontraktu dat `Object` je "anyType", aby jako název kontraktu dat neobecnou seznamů <xref:System.Collections.ArrayList> je "ArrayOfanyType".  
  
 Výchozí název pro slovník dat kolekce měnící, není-li přepsat pomocí `Name`, je "ArrayOfKeyValueOf" v kombinaci s názvem kontraktu dat typ klíče, za nímž následuje název kontraktu dat hodnota typu řetězec. Například data "ArrayOfKeyValueOfstringint" je název kontraktu pro obecné slovník řetězec a celé číslo. Navíc pokud klíč nebo typy hodnot nejsou primitivní typy, připojí se k názvu hash obor názvů oborů názvů kontraktu dat typů klíč a hodnotu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] obor názvů hodnoty hash, najdete v části [názvy datových kontraktů](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Každý kontrakt dat kolekce slovníku má doprovodné kontraktu dat, která představuje jednu položku ve slovníku. Jeho název je stejné jako slovník dat kontrakt, s výjimkou předponu "ArrayOf" a její obor názvů je stejné jako pro kontrakt dat slovníku. Například pro kontrakt dat slovník "ArrayOfKeyValueOfstringint", kontrakt dat "KeyValueofstringint" představuje jednu položku ve slovníku. Název tohoto kontraktu dat lze přizpůsobit pomocí `ItemName` vlastnost, jak je popsáno v následující části.  
  
 Obecná pravidla pojmenování, zadejte, jak je popsáno v [názvy datových kontraktů](../../../../docs/framework/wcf/feature-details/data-contract-names.md), plně použít typy kolekcí; tzn., můžete použít složené závorky v název označující parametry obecného typu. Čísla do závorek však naleznete obecné parametry a není typy obsažené v kolekci.  
  
## <a name="collection-customization"></a>Přizpůsobení kolekce  
 Následující používání <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut jsou zakázané a vést <xref:System.Runtime.Serialization.InvalidDataContractException> výjimka:  
  
-   Použití <xref:System.Runtime.Serialization.DataContractAttribute> atribut na typ, do kterého <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut byl použité, nebo do jednoho z jeho odvozených typů.  
  
-   Použití <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut na typ, který implementuje <xref:System.Xml.Serialization.IXmlSerializable> rozhraní.  
  
-   Použití <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut typu jiné kolekce.  
  
-   Probíhá pokus o nastavení <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> nebo <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> na <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut použitý typ jiný adresář.  
  
### <a name="polymorphism-rules"></a>Polymorfismus pravidla  
 Jak už jsme zmínili, přizpůsobení kolekce pomocí <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut mohou ovlivňovat zaměnitelnost kolekce. Dva typy uzpůsobenou kolekci lze pouze považovat za ekvivalentní, pokud se jejich název, obor názvů, název položky, jakož i názvy klíčů a hodnot (pokud jsou kolekce slovníku) shodují.  
  
 Z důvodu úprav je možné nechtěně použít kontrakt dat jednu kolekci jiné, kde je očekávána. To je nutno. Zobrazíte následující typy.  
  
 [!code-csharp[c_collection_types_in_data_contracts#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#11)]
 [!code-vb[c_collection_types_in_data_contracts#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#11)]  
  
 V tomto případě instance `Marks1` lze přiřadit k `testMarks`. Ale `Marks2` by se neměla používat, protože jeho kontrakt dat není považovány za ekvivalentní k `IList<int>` kontrakt dat. Název kontraktu dat je "Marks2" a není "ArrayOfint" a je opakovaný název elementu "\<označit >" a zda není "\<int >".  
  
 Pravidla v následující tabulce platí pro polymorfní přiřazení kolekcí.  
  
|Deklarovaný typ|Přiřazení neupravené kolekce|Přiřazení uzpůsobenou kolekci|  
|-------------------|--------------------------------------------|---------------------------------------|  
|Objekt|Název smlouvy je serializováno.|Název smlouvy je serializováno.<br /><br /> Slouží k přizpůsobení.|  
|Rozhraní kolekce|Název kontraktu není serializovat.|Název kontraktu není serializovat.<br /><br /> Přizpůsobení není used.*|  
|Přizpůsobené bez kolekce|Název kontraktu není serializovat.|Název smlouvy je serializováno.<br /><br /> Přizpůsobení je used.* *|  
|Vlastní kolekce|Název smlouvy je serializováno. Přizpůsobení není used.* *|Název smlouvy je serializováno.<br /><br /> Přizpůsobení přiřazené typu je used.* *|  
  
 * Se <xref:System.Runtime.Serialization.NetDataContractSerializer> třídy, přizpůsobení se používá v tomto případě. <xref:System.Runtime.Serialization.NetDataContractSerializer> Třídy v tomto případě také serializuje název skutečný typ, takže deserializace funguje podle očekávání.  
  
 ** Těchto případech vést k neplatné schéma instancí a proto by měly být vyloučeny.  
  
 V případech, kde je serializováno název kontraktu musí být typu přiřazené kolekce v seznamu známých typů. Jako opak platí to i naopak: v případech, kde se název neserializuje, přidáte do seznamu známé typy typ se nevyžaduje.  
  
 Do pole Základní typ lze přiřadit pole odvozeného typu. V takovém případě je název kontraktu pro odvozený typ serializovat pro každý opakovaných prvek. Například, pokud typ `Book` je odvozen od typu `LibraryItem`, můžete přiřadit pole `Book` na pole `LibraryItem`. To se nevztahuje na jiné typy kolekcí. Nelze přiřadit například `Generic List of Book` k `Generic List of LibraryItem`. Můžete ale přiřadit `Generic List of LibraryItem` obsahující `Book` instance. V poli i případě mimo pole `Book` by měla být v seznamu známých typů.  
  
## <a name="collections-and-object-reference-preservation"></a>Kolekce a zachovávání odkaz na objekt  
 Při serializátor funkce v režimu, kde uchovává odkazy na objekty, objekt odkaz zachovávání platí také pro kolekce. Identity – objekt je konkrétně zachovají pro celý kolekce a jednotlivé položky, které jsou obsažené v kolekcích. Pro slovník je zachovaná objekt identity pro objekty dvojice klíč/hodnota i jednotlivé objekty klíč a hodnotu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>

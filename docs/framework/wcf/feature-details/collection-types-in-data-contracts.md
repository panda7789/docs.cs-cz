---
title: Typy kolekcí v kontraktech dat
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- collection types [WCF], data contracts
- data contracts [WCF], collection types
- collection types [WCF]
ms.assetid: 9b45b28e-0a82-4ea3-8c33-ec0094aff9d5
ms.openlocfilehash: a2528699387a86ca276cb3ba63eab39544552a4f
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850873"
---
# <a name="collection-types-in-data-contracts"></a>Typy kolekcí v kontraktech dat
A *kolekce* je seznam položek určitého typu. V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], tyto seznamy můžou být vyjádřeny pomocí pole nebo celou řadu dalších typů (obecný seznam, obecný <xref:System.ComponentModel.BindingList%601>, <xref:System.Collections.Specialized.StringCollection>, nebo <xref:System.Collections.ArrayList>). Například kolekce může obsahovat seznam adres pro daného zákazníka. Těchto kolekcí se nazývají *seznamu kolekcí*, bez ohledu na jejich skutečné typu.  
  
 Zvláštní forma kolekce existuje, který reprezentuje asociace mezi jednu položku ("klíče") a jiné ("hodnota"). V [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)], jsou představovány typy, jako <xref:System.Collections.Hashtable> a generický slovník. Kolekci přidružení může například mapování města ("klíče") na obyvatel ("value"). Těchto kolekcí se nazývají *kolekce slovníku*, bez ohledu na jejich skutečné typu.  
  
 Kolekce zobrazí zvláštní zacházení v datovém modelu kontraktu.  
  
 Typy, které implementují <xref:System.Collections.IEnumerable> rozhraní, včetně polí a obecných kolekcí, jsou rozpoznány jako kolekce. Z nich, typy, které implementují <xref:System.Collections.IDictionary> nebo obecná <xref:System.Collections.Generic.IDictionary%602> rozhraní jsou kolekce slovníku, všechny ostatní se seznam kolekcí.  
  
 Další požadavky na typy kolekcí, jako je například s metodu nazvanou `Add` a výchozí konstruktor, jsou podrobně popsány v následujících částech. Tím se zajistí, že typy kolekcí může být současně serializaci a deserializaci. To znamená, že některé kolekce se nepodporují přímo, jako je obecný <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> (protože nemá žádný výchozí konstruktor.). Ale informace o obcházení tato omezení, naleznete v části "Použití kolekce rozhraní typy a jen pro čtení kolekce" dále v tomto tématu.  
  
 Typy obsažené v kolekci musí být typy kontraktů dat nebo bude jinak serializovatelný. Další informace najdete v tématu [typy podporované serializátorem kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).  
  
 Další informace o novinkách a co není považována za platnou kolekci, stejně jako o způsob, jakým serializují kolekce zobrazit informace o serializaci kolekce v části "pravidla shromažďování pokročilé" v tomto tématu.  
  
## <a name="interchangeable-collections"></a>Zaměňovat kolekce  
 Všechny kolekce seznamu stejného typu, jsou považovány za obsahovaly stejná data smlouvy (Pokud je přizpůsobíte pomocí <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributu, jak je popsáno dále v tomto tématu). Proto například následujícími kontrakty dat jsou ekvivalentní.  
  
 [!code-csharp[c_collection_types_in_data_contracts#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#0)]
 [!code-vb[c_collection_types_in_data_contracts#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#0)]  
  
 Kontrakty obou data za následek podobně jako následující kód XML.  
  
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
  
 Kolekce zaměnitelnost umožňuje použít, například, typ kolekce optimalizované pro výkon serveru a typ kolekce navržená tak, aby být vázaný na součásti uživatelského rozhraní na straně klienta.  
  
 Podobně jako seznam kolekcí, všechny kolekce slovníku, které mají stejné typy klíče a hodnoty jsou považovány za obsahovaly stejná data smlouvy (není-li přizpůsobit <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributu).  
  
 Pouze data smlouvy typ věcech pokud jde o kolekci ekvivalence, ne typy .NET. To znamená kolekce Type1 je považován za rovnocenný kolekce Type2 případě Type1 a Type2 mají ekvivalentní datové kontrakty.  
  
 Neobecnou kolekce jsou považovány za stejný datový kontrakt jako obecné kolekce typu `Object`. (Například data smlouvy o <xref:System.Collections.ArrayList> a obecná <xref:System.Collections.Generic.List%601> z `Object` jsou stejné.)  
  
## <a name="using-collection-interface-types-and-read-only-collections"></a>Použití typů rozhraní kolekce a kolekce jen pro čtení  
 Typy rozhraní kolekce (<xref:System.Collections.IEnumerable>, <xref:System.Collections.IDictionary>obecný <xref:System.Collections.Generic.IDictionary%602>, nebo rozhraní je odvozena z těchto rozhraní) jsou také považovány za tak, že má kolekce datové kontrakty, odpovídá kontraktů dat kolekce pro kolekci skutečné typy. Proto je možné deklarovat typ serializovaný jako typ rozhraní kolekce a výsledky jsou stejné, jako kdyby bylo použito typ skutečný kolekce. Například následující kontraktů dat jsou ekvivalentní.  
  
 [!code-csharp[c_collection_types_in_data_contracts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#1)]
 [!code-vb[c_collection_types_in_data_contracts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#1)]  
  
 Během serializace, pokud deklarovaný typ je rozhraní, skutečné instance typ používá může být libovolný typ, který implementuje rozhraní. Omezení jak jsme vysvětlili výše (s výchozí konstruktor a `Add` metoda) se nevztahují. Například můžete nastavit adresy v Customer2 do instance obecného <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> adresy, i když nelze deklarovat přímo datový člen třídy typu obecného <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>.  
  
 Během deserializace, pokud deklarovaný typ je rozhraní, Serializační stroj vybere typ, který implementuje rozhraní deklarované a která je vytvořena instance typu. Známých typů mechanismus (popsané v [známé typy kontraktů dat.](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)) nemá žádný vliv; zde volba typu je integrovaná do WCF.  
  
## <a name="customizing-collection-types"></a>Přizpůsobení typy kolekcí  
 Typy kolekce můžete upravit pomocí <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut, který má několik využití.  
  
 Poznámka: Tento přizpůsobení kolekci typů ohrožení kolekce zaměnitelnost, obecně se doporučuje použití tohoto atributu, kdykoli je to možné, aby. Další informace o tomto problému naleznete v části "pravidla shromažďování pokročilé" dále v tomto tématu.  
  
### <a name="collection-data-contract-naming"></a>Kontraktu dat kolekce pojmenování  
 Pravidla pro pojmenovávání typy kolekcí jsou podobné jako u názvů běžných dat typy kontraktů, jak je popsáno v [názvy datových kontraktů](../../../../docs/framework/wcf/feature-details/data-contract-names.md), i když existuje několik důležitých rozdílů:  
  
-   <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Atribut se používá k přizpůsobení názvu, namísto <xref:System.Runtime.Serialization.DataContractAttribute> atribut. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Atribut má také `Name` a `Namespace` vlastnosti.  
  
-   Když <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut není použit, výchozí název a obor názvů pro typy kolekcí, závisí na názvy a obory názvů typů, které jsou obsaženy v rámci kolekce. Nejsou ovlivněny podle názvu a oboru názvů samotného typu kolekce. Příklad najdete v následujících typů.  
  
    ```  
    public CustomerList1 : Collection<string> {}  
    public StringList1 : Collection<string> {}  
    ```  
  
 Oba typy názvem kontraktu dat je "ArrayOfstring" a nikoli "CustomerList1" nebo "StringList1". To znamená, že serializaci jednoho z těchto typů na kořenové úrovni vrací podobně jako následující kód XML.  
  
```xml  
<ArrayOfstring>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</ArrayOfstring>  
```  
  
 Toto pravidlo pro pojmenování byla zvolena zajistit, že jakýkoli neupravené typ, který představuje seznam řetězců stejný kontrakt dat a reprezentaci XML. Díky zaměnitelnost kolekce. V tomto příkladu jsou CustomerList1 a StringList1 zcela zaměnitelné.  
  
 Nicméně, když <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut se používá, i v případě, že jsou nastaveny žádné vlastnosti v atributu se stane kontraktu dat vlastní kolekce, kolekce. Název a obor názvů kolekce dat smlouvy a závisí na samotný datový typ kolekce. Příklad najdete v tématu následujícího typu.  
  
 [!code-csharp[c_collection_types_in_data_contracts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#2)]
 [!code-vb[c_collection_types_in_data_contracts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#2)]  
  
 Při serializován, výsledný XML je podobný následujícímu.  
  
```xml  
<CustomerList2>  
    <string>...</string>  
    <string>...</string>  
    <string>...</string>  
    ...  
</CustomerList2>  
```  
  
 Všimněte si, že to již není ekvivalentní k reprezentaci XML pro typy bez přizpůsobit.  
  
-   Můžete použít `Name` a `Namespace` vlastnosti k dalšímu přizpůsobení názvů. Podívejte se následující třídy.  
  
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
  
 Další informace najdete v části "pravidla shromažďování pokročilé" dále v tomto tématu.  
  
### <a name="customizing-the-repeating-element-name-in-list-collections"></a>Přizpůsobení názvu elementu opakující se seznam kolekcí  
 Seznam kolekcí obsahovat položky s opakováním. Každá položka opakující se za normálních okolností je vyjádřena jako element pojmenována v souladu s názvem kontraktu dat typu obsažené v kolekci.  
  
 V `CustomerList` příklady, kolekcí řetězců. Názvem kontraktu dat pro primitivní typ řetězec je "string", proto byla opakující se prvek "\<řetězec >".  
  
 Avšak použití <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> vlastnost na <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut opakující se tento název elementu je možné přizpůsobit. Příklad najdete v tématu následujícího typu.  
  
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
  
 Obor názvů s opakováním elementu je vždy stejný jako obor názvů kontraktu dat kolekce, která se dá přizpůsobit pomocí `Namespace` vlastnost, jak je popsáno výše.  
  
### <a name="customizing-dictionary-collections"></a>Přizpůsobení slovníku kolekcí  
 Kolekce slovníku jsou v podstatě seznam položek, kde každý záznam obsahuje klíč a hodnotu. Stejně jako se pravidelně seznamy, můžete změnit název elementu, který odpovídá opakující se element s použitím <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> vlastnost.  
  
 Kromě toho můžete změnit názvy elementů, které představují klíč a hodnotu s použitím <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> a <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> vlastnosti. Obory názvů pro tyto prvky jsou stejné jako obor názvů kontraktu dat kolekce.  
  
 Příklad najdete v tématu následujícího typu.  
  
 [!code-csharp[c_collection_types_in_data_contracts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#5)]
 [!code-vb[c_collection_types_in_data_contracts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#5)]  
  
 Při serializován, výsledný XML je podobný následujícímu.  
  
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
  
 Další informace o kolekce slovníku naleznete v části "pravidla shromažďování pokročilé" dále v tomto tématu.  
  
## <a name="collections-and-known-types"></a>Kolekce a známé typy  
 Nepotřebujete přidat typy kolekce známých typů, když polymorphically použít namísto jiných kolekcí nebo rozhraní pro kolekce. Například, pokud deklarujete datový člen typu <xref:System.Collections.IEnumerable> a používat k odesílání instance <xref:System.Collections.ArrayList>, není nutné přidávat <xref:System.Collections.ArrayList> pro známé typy.  
  
 Při použití kolekce polymorphically místo typů bez kolekce je nutné přidat do známých typů. Například, pokud deklarujete datový člen typu `Object` a používat k odesílání instance <xref:System.Collections.ArrayList>, přidejte <xref:System.Collections.ArrayList> pro známé typy.  
  
 To neumožňuje polymorphically serializovat jakékoli ekvivalentní kolekce. Například když přidáte <xref:System.Collections.ArrayList> do seznamu známých typů v předchozím příkladu to neumožňuje přiřadit `Array of Object` třídy, i když má kontrakt ekvivalentní data. To se nijak neliší od pravidelných známé typy chování serializace pro typy jiné kolekce, ale je velmi důležité pochopit v případě kolekcí, protože je velmi běžné, že kolekce jako ekvivalentní.  
  
 Během serializace můžete být známé pouze jeden typ v jakékoli dané oboru pro daný datový kontrakt a ekvivalentní kolekce všechny mají stejnou kontraktů dat. To znamená, že v předchozím příkladu, nelze přidat obě <xref:System.Collections.ArrayList> a `Array of Object` známých typů ve stejném oboru. Znovu jedná se o ekvivalent pro známé typy chování pro typy jiné kolekce, ale je zvláště důležité, abyste pochopili pro kolekce.  
  
 Známé typy mohou být také požadované obsah kolekce. Například pokud <xref:System.Collections.ArrayList> ve skutečnosti obsahuje instance `Type1` a `Type2`, oba tyto typy by měla být přidána do známých typů.  
  
 Následující příklad ukazuje správně vytvořený objekt grafu pomocí kolekce a známých typů. V příkladu je poměrně contrived, protože aplikace skutečný nejsou obvykle definujete následující datové členy jako `Object`a proto nemají nějaké problémy známý typ/polymorfismu.  
  
 [!code-csharp[c_collection_types_in_data_contracts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#6)]
 [!code-vb[c_collection_types_in_data_contracts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#6)]  
  
 K deserializaci je-li deklarovaný typ je typ kolekce, deklarovaného typu je vytvořena instance bez ohledu na typ, který ve skutečnosti byl odeslán. Je-li deklarovaný typ rozhraní kolekce, vybere deserializátor typu má být vytvořena, bez ohledu na známých typů.  
  
 Také na deserializace, pokud deklarovaný typ není typ kolekce, ale typ kolekce je odesíláno, odpovídající typ kolekce se vybere ze seznamu známých typů. Je možné přidat do seznamu známých typů pro deserializaci typy rozhraní kolekcí. V takovém případě modul deserializace znovu vybere typ má být vytvořena.  
  
## <a name="collections-and-the-netdatacontractserializer-class"></a>Kolekce a třídou NetDataContractSerializer  
 Když <xref:System.Runtime.Serialization.NetDataContractSerializer> třída se používá, typy kolekcí neupravené (bez <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut), že se pole není ztratit jejich zvláštní význam.  
  
 Typy kolekcí přizpůsobit bez označené <xref:System.SerializableAttribute> atribut může stále bylo serializováno modulem <xref:System.Runtime.Serialization.NetDataContractSerializer> třídy podle <xref:System.SerializableAttribute> atribut nebo <xref:System.Runtime.Serialization.ISerializable> rozhraní pravidla.  
  
 Typy vlastní kolekce, rozhraní pro kolekce a pole jsou stále považovány za kolekcí, i když <xref:System.Runtime.Serialization.NetDataContractSerializer> třída se používá.  
  
## <a name="collections-and-schema"></a>Kolekce a schématu  
 Všechny kolekce ekvivalentní mají stejnou reprezentaci ve schématu XML definice jazyk (XSD) schématu. Z toho důvodu se obvykle nezobrazí stejný typ kolekce v kódu generovaného klienta jako ta, na serveru. Například server může použít kontrakt dat s obecnou <xref:System.Collections.Generic.List%601> datový člen celé číslo, ale v kódu generovaného klienta může být stejný datový člen pole celých čísel.  
  
 Kolekce slovníku jsou označené poznámky ke schématu konkrétní WCF, která označuje, že jsou slovníky; v opačném případě je nerozeznatelná od jednoduché seznamy, které obsahují položky se klíč a hodnotu. Pro přesné určení jak kolekce jsou reprezentovány ve schématu kontraktu dat, naleznete v tématu [schéma kontraktů dat – referenční informace](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Ve výchozím nastavení nejsou pro neupravené kolekce v importované kódu generované typy. Datové členy list – typy kolekcí jsou naimportované jako pole a datové členy typů kolekce slovníku jsou naimportované jako generický slovník.  
  
 Ale pro vlastní kolekce, samostatné typy jsou generovány, označené <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut. (Vlastní kolekce typu ve schématu je ten, který nepoužívá výchozí obor názvů, název, opakující se název elementu nebo klíč/hodnota názvy elementů.) Tyto typy jsou prázdných typů, které jsou odvozeny z obecných <xref:System.Collections.Generic.List%601> pro typy seznamu a generický slovník u typů slovníku.  
  
 Například může mít následující typy na serveru.  
  
 [!code-csharp[c_collection_types_in_data_contracts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#7)]
 [!code-vb[c_collection_types_in_data_contracts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#7)]  
  
 Při exportu schématu a importované zpět znovu, kód klienta vygenerovaný je podobný následujícímu (pole se zobrazí místo vlastnosti pro snadnější čtení).  
  
 [!code-csharp[c_collection_types_in_data_contracts#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#8)]
 [!code-vb[c_collection_types_in_data_contracts#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#8)]  
  
 Můžete chtít použít různé typy v generovaném kódu než výchozí hodnoty. Například můžete chtít použít obecný <xref:System.ComponentModel.BindingList%601> místo pravidelných polí pro vaše datové členy, aby bylo snazší pro vazbu k součásti uživatelského rozhraní.  
  
 Vybrat typy kolekcí ke generování, předejte seznam typy kolekce, kterou chcete použít do <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> vlastnost <xref:System.Runtime.Serialization.ImportOptions> objektu při importu schématu. Tyto typy jsou označovány jako *odkazované typy kolekcí*.  
  
 Při obecné typy se odkazuje, se musí být plně open obecných typů nebo plně uzavřeno obecných typů.  
  
> [!NOTE]
>  Při použití nástroje Svcutil.exe, tento odkaz můžete provést pomocí **/collectionType** přepínač příkazového řádku (krátký tvar: **/ct**). Pamatujte, že musíte zadat také sestavení pro odkazované kolekce typů pomocí **/reference** přepnout (krátký tvar: **/r**). Pokud je typ obecný, se musí být následován znakem závěrečnou uvozovkou a počet obecných parametrů. Závěrečnou uvozovkou (\`) by se zaměňovat s znak jednoduché uvozovky ('). Můžete určit více odkazovaných typů kolekce pomocí **/collectionType** přepnout více než jednou.  
  
 Například způsobit, že všechny seznamy, které se mají importovat jako obecný <xref:System.Collections.Generic.List%601>.  
  
```  
svcutil.exe MyService.wsdl MyServiceSchema.xsd /r:C:\full_path_to_system_dll\System.dll /ct:System.Collections.Generic.List`1  
```  
  
 Při importu jakoukoli kolekci, je možné tento seznam odkazovaných typů kolekce a nejlépe odpovídající kolekci se používá, pokud ho najde, jako typ datového členu (pro neupravené kolekce) nebo jako základní typ pro odvození z (pro vlastní kolekce). Slovníky jsou porovnány pouze s slovníky, zatímco seznamy jsou porovnány s seznamy.  
  
 Například, pokud chcete přidat Obecné <xref:System.ComponentModel.BindingList%601> a <xref:System.Collections.Hashtable> seznam odkazovaných typů, kód klienta vygenerovaný pro předchozí příklad je podobný následujícímu.  
  
 [!code-csharp[c_collection_types_in_data_contracts#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#9)]
 [!code-vb[c_collection_types_in_data_contracts#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#9)]  
  
 Typy rozhraní kolekce můžete zadat jako součást vašich odkazovaných typů kolekce, ale není možné určit typy kolekcí neplatná (například těch, které jsou bez `Add` metoda nebo konstruktor public).  
  
 Uzavřený obecný se považuje za nejvhodnější. (Neobecné typy se považují za ekvivalentní uzavřených obecných typů z `Object`). Například pokud typy Obecné <xref:System.Collections.Generic.List%601> z <xref:System.DateTime>obecný <xref:System.ComponentModel.BindingList%601> (otevřený obecný), a <xref:System.Collections.ArrayList> jsou generovány odkazovaných typů kolekce, následující.  
  
 [!code-csharp[c_collection_types_in_data_contracts#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#10)]
 [!code-vb[c_collection_types_in_data_contracts#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#10)]  
  
 Seznam kolekcí jsou podporovány pouze případy v následující tabulce.  
  
|Odkazovaný typ|Rozhraní implementované odkazovaného typu|Příklad|Typ považován za:|  
|---------------------|----------------------------------------------|-------------|----------------------|  
|Neobecné "nebo" Uzavřeno obecného (libovolný počet parametrů)|Neobecné|`MyType : IList`<br /><br /> or<br /><br /> `MyType<T> : IList`<br /><br /> kde T = `int`|Uzavřený obecný z `Object` (například `IList<object>`)|  
|Neobecné "nebo" Uzavřeno obecného (libovolný počet parametrů, které nemusí nutně odpovídat typ kolekce)|Uzavřený obecný|`MyType : IList<string>`<br /><br /> or<br /><br /> `MyType<T> : IList<string>` kde T =`int`|Uzavřený obecný (například `IList<string>`)|  
|Uzavřený obecný s libovolným počtem parametrů|Otevřený obecný pomocí některé z parametrů typu|`MyType<T,U,V> : IList<U>`<br /><br /> kde T =`int`, U =`string`, V =`bool`|Uzavřený obecný (například `IList<string>`)|  
|Otevřený obecný s jedním parametrem|Otevřený obecný parametr typu|`MyType<T> : IList<T>`, T je otevřený|Otevřený obecný (například `IList<T>`)|  
  
 Pokud typ implementuje víc než jedno rozhraní kolekce seznamu, platí následující omezení:  
  
-   Pokud tento typ implementuje obecné <xref:System.Collections.Generic.IEnumerable%601> (nebo jeho odvozená rozhraní) více než jednou pro různé typy, typ není považován za typ platný odkazované kolekce a je ignorován. To platí i v případě některých implementacích jsou neplatné nebo používají otevřených obecných typů. Například typ, který implementuje obecné <xref:System.Collections.Generic.IEnumerable%601> z `int` a obecná <xref:System.Collections.Generic.IEnumerable%601> t by se nikdy nepoužívá jako odkazovaná kolekce `int` nebo jakýkoli jiný typ, bez ohledu na to, zda má typ `Add` přijímá – metoda `int` nebo `Add` metoda přijímá parametr typu T nebo obojí.  
  
-   Pokud tento typ implementuje rozhraní obecné kolekce stejně jako <xref:System.Collections.IList>, typu se nikdy nepoužívá jako typ odkazované kolekce, pokud rozhraní obecné kolekce není uzavřený obecný typ <xref:System.Object>.  
  
 Pro kolekce slovníku jsou podporovány pouze případy v následující tabulce.  
  
|Odkazovaný typ|Rozhraní implementované odkazovaného typu|Příklad|Typ považován za|  
|---------------------|----------------------------------------------|-------------|---------------------|  
|Neobecné "nebo" Uzavřeno obecného (libovolný počet parametrů)|<xref:System.Collections.IDictionary>|`MyType : IDictionary`<br /><br /> or<br /><br /> `MyType<T> : IDictionary` kde T =`int`|Uzavřený obecný `IDictionary<object,object>`|  
|Uzavřený obecný (libovolný počet parametrů)|<xref:System.Collections.Generic.IDictionary%602>, Uzavřeno|`MyType<T> : IDictionary<string, bool>` kde T =`int`|Uzavřený obecný (například `IDIctionary<string,bool>`)|  
|Uzavřený obecný (libovolný počet parametrů)|Obecný <xref:System.Collections.Generic.IDictionary%602>, klíč nebo hodnota je uzavřen, druhá je otevřený a používá jeden z parametrů typu|`MyType<T,U,V> : IDictionary<string,V>` kde T =`int`, U =`float`, V =`bool`<br /><br /> or<br /><br /> `MyType<Z> : IDictionary<Z,bool>` Pokud Z =`string`|Uzavřený obecný (například `IDictionary<string,bool>`)|  
|Uzavřený obecný (libovolný počet parametrů)|Obecný <xref:System.Collections.Generic.IDictionary%602>, klíče a hodnoty jsou otevřené a každá používá jeden z parametrů typu|`MyType<T,U,V> : IDictionary<V,U>` kde T =`int`, U =`bool`, V =`string`|Uzavřený obecný (například `IDictionary<string,bool>`)|  
|Otevřený obecný (dva parametry)|Obecný <xref:System.Collections.Generic.IDictionary%602>, otevřít, používá oba parametry obecného typu v pořadí, jsou uvedeny|`MyType<K,V> : IDictionary<K,V>`, K a V obou otevřít|Otevřený obecný (například `IDictionary<K,V>`)|  
  
 Pokud tento typ implementuje oba <xref:System.Collections.IDictionary> a obecná <xref:System.Collections.Generic.IDictionary%602>, jenom obecná <xref:System.Collections.Generic.IDictionary%602> se považuje za.  
  
 Odkazování na částečné obecné typy se nepodporuje.  
  
 Duplicitní položky nejsou povoleny, například nelze přidat obě Obecné <xref:System.Collections.Generic.List%601> z `Integer` a obecné kolekce `Integer` k <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, protože díky tomu je možné určit, který se má použít při seznamu celých čísel se nenašel ve schématu. Duplicity se pouze v případě, že je typ ve schématu, která zveřejňuje problém duplicitní položky. Například pokud schéma importu neobsahuje seznam celých čísel, to může mít obě Obecné <xref:System.Collections.Generic.List%601> z `Integer` a obecné kolekce `Integer` v <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, ale ani nemá žádný vliv.  
  
## <a name="advanced-collection-rules"></a>Pokročilé kolekce pravidel  
  
### <a name="serializing-collections"></a>Serializace kolekcí  
 Následuje seznam kolekci pravidel pro serializaci:  
  
-   Kombinování typů kolekce (s kolekcí kolekcí) je povolený. Vícenásobná pole jsou považovány za kolekce kolekcí. Vícerozměrná pole nejsou podporována.  
  
-   Pole bajtů a pole <xref:System.Xml.XmlNode> jsou typy zvláštní pole, které jsou považovány za primitiv, nikoli kolekce. Serializace pole bajtů výsledků v jednom elementu XML, který obsahuje blok dat s kódováním Base64, místo samostatných element pro každý bajt. Další informace o tom, pole <xref:System.Xml.XmlNode> je zacházeno, naleznete v tématu [typy XML a ADO.NET v kontraktech dat](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md). Samozřejmě, tyto speciální typy můžete sami účastnit kolekcí: pole pole bajtů za následek více elementů XML s každou obsahující blok dat s kódováním Base64.  
  
-   Pokud <xref:System.Runtime.Serialization.DataContractAttribute> atributu je použité u typu kolekce, typ je považován za typ kontraktu běžných dat, nikoli jako kolekce.  
  
-   Pokud typ kolekce implementuje <xref:System.Xml.Serialization.IXmlSerializable> platí následující pravidla rozhraní, přidělí typ. `myType:IList<string>, IXmlSerializable`:  
  
    -   Pokud je typ deklarovaný `IList<string>`, je typ serializován jako seznam.  
  
    -   Pokud je typ deklarovaný `myType`, je serializován jako `IXmlSerializable`.  
  
    -   Pokud je typ deklarovaný `IXmlSerializable`, je serializován jako `IXmlSerializable`, ale pouze v případě, že přidáte `myType` do seznamu známých typů.  
  
-   Kolekce jsou serializaci a deserializaci pomocí metody uvedené v následující tabulce.  
  
|Implementuje typ kolekce|Volat metody pro serializaci|Volá metody k deserializaci|  
|--------------------------------|-----------------------------------------|-------------------------------------------|  
|Obecné <xref:System.Collections.Generic.IDictionary%602>|`get_Keys`, `get_Values`|Přidání obecného|  
|<xref:System.Collections.IDictionary>|`get_Keys`, `get_Values`|`Add`|  
|Obecné <xref:System.Collections.Generic.IList%601>|Obecný <xref:System.Collections.Generic.IList%601> indexeru|Přidání obecného|  
|Obecné <xref:System.Collections.Generic.ICollection%601>|Enumerátor|Přidání obecného|  
|<xref:System.Collections.IList>|<xref:System.Collections.IList> Indexer|`Add`|  
|Obecné <xref:System.Collections.Generic.IEnumerable%601>|`GetEnumerator`|Nestatická metoda volána `Add` , která přijímá jeden parametr příslušného typu (typ obecného parametru) nebo jedna z jeho základních typů. Tato metoda musí existovat serializátor považovat za typ kolekce kolekce během serializace a deserializace.|  
|<xref:System.Collections.IEnumerable> (a tedy <xref:System.Collections.ICollection>, která je odvozena z něj)|`GetEnumerator`|Nestatická metoda volána `Add` , která přijímá jeden parametr typu `Object`. Tato metoda musí existovat serializátor považovat za typ kolekce kolekce během serializace a deserializace.|  
  
 V předchozí tabulce jsou uvedeny rozhraní pro kolekce v sestupném pořadí podle priority. To znamená, například, že pokud typ implementuje oba <xref:System.Collections.IList> a obecná <xref:System.Collections.Generic.IEnumerable%601>, kolekce je serializaci a deserializaci podle <xref:System.Collections.IList> pravidla:  
  
-   Při deserializaci jsou všechny kolekce deserializovat vytvořením první instance typu při volání výchozí konstruktor, který musí být k dispozici pro serializátor považovat za typ kolekce kolekce během serializace a deserializace.  
  
-   Pokud stejné obecné kolekce rozhraní je implementováno více než jednou (např. Pokud typ implementuje oba obecného <xref:System.Collections.Generic.ICollection%601> z `Integer` a obecná <xref:System.Collections.Generic.ICollection%601> z <xref:System.String>) a nenajde žádné rozhraní vyšší prioritu, je kolekce nejsou považovány za platné kolekce.  
  
-   Typy kolekcí může mít <xref:System.SerializableAttribute> atributu na ně použity a můžete implementovat <xref:System.Runtime.Serialization.ISerializable> rozhraní. Obě tyto jsou ignorovány. Ale pokud typ plně nesplňuje požadavky na typ kolekce (například `Add` chybí metoda), typ není považován za typ kolekce a proto <xref:System.SerializableAttribute> atribut a <xref:System.Runtime.Serialization.ISerializable> rozhraní se používají k určení Určuje, zda typ lze serializovat.  
  
-   Použití <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut do kolekce a přizpůsobit odebere <xref:System.SerializableAttribute> předchozí záložní mechanismus. Místo toho, pokud přizpůsobenou sadu kolekce nelze setkat typu požadavky, <xref:System.Runtime.Serialization.InvalidDataContractException> je vyvolána výjimka. Řetězec výjimky často obsahují informace, které vysvětlují, proč se daný typ není považován za platný kolekce (žádné `Add` metoda, žádný výchozí konstruktor a tak dále), takže je často užitečné použít <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut pro účely ladění.  
  
### <a name="collection-naming"></a>Kolekce názvů  
 Následuje seznam pravidel pojmenování kolekce:  
  
-   Výchozí obor názvů pro všechny kontrakty dat kolekce slovníku, stejně jako u seznamu kolekce dat smluv, které obsahují primitivní typy, `http://schemas.microsoft.com/2003/10/Serialization/Arrays` nepřepíšete pomocí Namespace. Typy, které mapují na vestavěné typy XSD, stejně jako `char`, `Timespan`, a `Guid` typy, jsou považovány za primitivy pro tento účel.  
  
-   Výchozí obor názvů pro typy kolekcí, které obsahují neprimitivní typy nepřepíšete pomocí Namespace, je stejný jako obor názvů kontraktu dat typu obsažené v kolekci.  
  
-   Výchozí název pro seznam kolekce datové kontrakty, pokud nejsou přepsány, pomocí názvu, je řetězec, který "ArrayOf" v kombinaci s názvem kontraktu dat typu obsažené v kolekci. Název kontraktu dat pro obecný seznam celá je například "ArrayOfint". Pamatujte, že název kontraktu dat `Object` je "anyType", takže názvem kontraktu dat neobecnou seznamů, jako jsou <xref:System.Collections.ArrayList> je "ArrayOfanyType".  
  
 Výchozí název data kolekce slovníku smlouvy, není-li přepsat pomocí `Name`, je řetězec "ArrayOfKeyValueOf" v kombinaci s názvem kontraktu dat typu klíče spolu s názvem kontraktu dat typu hodnoty. Například data název smlouvy pro obecný řetězci slovníku a celého čísla je "ArrayOfKeyValueOfstringint". Kromě toho pokud klíče nebo hodnoty typů nejsou primitivní typy, obor názvů hash obor názvů kontraktu dat typů klíč a hodnotu připojeným k názvu. Další informace o oboru názvů hodnoty hash, naleznete v tématu [názvy datových kontraktů](../../../../docs/framework/wcf/feature-details/data-contract-names.md).  
  
 Každý kontraktu dat kolekce slovníku má doprovodná kontraktu dat, který představuje jednu položku ve slovníku. Její název je stejná jako slovník dat smlouvy, s výjimkou předponu "ArrayOf" a její obor názvů je stejné jako u kontraktu dat slovníku. Kontrakt dat "KeyValueofstringint" představuje "ArrayOfKeyValueOfstringint" slovník dat smlouvy, jednu položku ve slovníku. Můžete přizpůsobit název tohoto kontraktu dat s použitím `ItemName` vlastnost, jak je popsáno v další části.  
  
 Obecný typ pravidla pojmenování, jak je popsáno v [názvy datových kontraktů](../../../../docs/framework/wcf/feature-details/data-contract-names.md), plně na typy kolekcí; které se vztahují, složené závorky v názvu můžete použít k označení parametry obecného typu. Čísla v rámci složené závorky však naleznete obecné parametry a nejsou typy obsažené v rámci kolekce.  
  
## <a name="collection-customization"></a>Vlastní nastavení kolekce  
 Použití následujících <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut jsou zakázané a vést <xref:System.Runtime.Serialization.InvalidDataContractException> výjimka:  
  
-   Použití <xref:System.Runtime.Serialization.DataContractAttribute> atribut typu, na který <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut byl použitý, nebo na jednu z jeho odvozených typů.  
  
-   Použití <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut na typ, který implementuje <xref:System.Xml.Serialization.IXmlSerializable> rozhraní.  
  
-   Použití <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut typu není kolekce.  
  
-   Pokus o nastavení <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> nebo <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> na <xref:System.Runtime.Serialization.CollectionDataContractAttribute> použité u typu není ve slovníku atributů.  
  
### <a name="polymorphism-rules"></a>Polymorfismus pravidla  
 Jak už jsme zmínili, přizpůsobení kolekcí s použitím <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atribut může kolidovat s zaměnitelnost kolekce. Dva typy přizpůsobené kolekce lze pouze považovat za rovnocenné, pokud odpovídají jejich názvem, obor názvů, název položky, jakož i názvy klíčů a hodnot (pokud jsou kolekce slovníku).  
  
 Z důvodu úprav je možné neúmyslně použití kontraktu dat kolekce jednoho jiného, kde se očekává. To by se jim vyhnout. Zobrazíte následující typy.  
  
 [!code-csharp[c_collection_types_in_data_contracts#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#11)]
 [!code-vb[c_collection_types_in_data_contracts#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#11)]  
  
 V tomto případě instance `Marks1` lze přiřadit k `testMarks`. Ale `Marks2` neměli použít, protože jeho kontraktu dat. není považován za rovnocenný `IList<int>` kontraktu dat. Název kontraktu dat je "Marks2" a nikoli "ArrayOfint" a opakovaný název elementu je "\<označit >", ne "\<int >".  
  
 Pravidla v následující tabulce platí pro polymorfní přiřazení kolekce.  
  
|Deklarovaný typ|Přiřazení bez přizpůsobené kolekce|Přiřazení vlastní kolekce|  
|-------------------|--------------------------------------------|---------------------------------------|  
|Objekt|Název smlouvy je serializována.|Název smlouvy je serializována.<br /><br /> Vlastní nastavení se používá.|  
|Rozhraní kolekce|Název kontraktu není provedena.|Název kontraktu není provedena.<br /><br /> Přizpůsobení není used.*|  
|Bez přizpůsobené kolekce|Název kontraktu není provedena.|Název smlouvy je serializována.<br /><br /> Přizpůsobení je used.* *|  
|Přizpůsobené kolekce|Název smlouvy je serializována. Přizpůsobení není used.* *|Název smlouvy je serializována.<br /><br /> Přizpůsobení přiřazené typu je used.* *|  
  
 * S <xref:System.Runtime.Serialization.NetDataContractSerializer> třídy, přizpůsobení se používá v tomto případě. <xref:System.Runtime.Serialization.NetDataContractSerializer> Třídy v tomto případě také serializuje skutečný typ název, takže deserializace funguje podle očekávání.  
  
 ** V těchto případech způsobit schématu neplatná instance a tedy třeba se jim vyhnout.  
  
 V případech, kde je serializována název kontraktu musí být typ přiřazené kolekce v seznamu známých typů. Opak platí to i naopak: v případech, kdy se neserializuje název, přidat typ do seznamu známých typů není povinné.  
  
 Do pole musí mít základní typ je možné přiřadit pole odvozeného typu. V tomto případě název smlouvy pro odvozený typ serializován pro každý opakovaný prvek. Například, pokud typ `Book` je odvozen od typu `LibraryItem`, můžete přiřadit pole `Book` pole `LibraryItem`. To se nevztahuje na jiné typy kolekcí. Například nelze přiřadit `Generic List of Book` k `Generic List of LibraryItem`. Ale můžete přiřadit `Generic List of LibraryItem` obsahující `Book` instancí. V poli a případ mimo pole `Book` by měla být v seznamu známých typů.  
  
## <a name="collections-and-object-reference-preservation"></a>Kolekce a zachovávání s rozlišením odkaz na objekt  
 Serializátor functions v režimu, ve kterém zachová odkazy na objekty, při zachování odkaz na objekt platí také pro kolekce. Konkrétně identity objektu je zachována kvůli celé kolekce a jednotlivé položky obsažené v kolekcích. Pro slovníky se zachovají identity objektu pro objekty dvojice klíč/hodnota a jednotlivé objekty, klíč a hodnotu.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.CollectionDataContractAttribute>

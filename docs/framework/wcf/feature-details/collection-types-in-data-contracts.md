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
ms.openlocfilehash: 810238ee631808dac472456f910eb52f8bbf550c
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363809"
---
# <a name="collection-types-in-data-contracts"></a>Typy kolekcí v kontraktech dat

*Kolekce* je seznam položek určitého typu. V .NET Framework mohou být takové seznamy vyjádřeny pomocí polí nebo různých typů (obecný seznam, obecné <xref:System.ComponentModel.BindingList%601>, <xref:System.Collections.Specialized.StringCollection>nebo <xref:System.Collections.ArrayList>). Kolekce může například obsahovat seznam adres pro daného zákazníka. Tyto kolekce se nazývají *kolekce seznamů*bez ohledu na jejich skutečný typ.

Existuje speciální forma kolekce, která představuje přidružení mezi jednou položkou (klíč) a jinou hodnotou ("value"). V .NET Framework představují tyto typy jako <xref:System.Collections.Hashtable> a obecný slovník. Například kolekce přidružení může mapovat město ("klíč") na jeho naplnění ("value"). Tyto kolekce se nazývají *kolekce slovníku*bez ohledu na jejich skutečný typ.

Kolekce získají zvláštní zacházení v modelu kontraktu dat.

Typy, které implementují <xref:System.Collections.IEnumerable> rozhraní, včetně polí a obecných kolekcí, se rozpoznávají jako kolekce. Typy, které implementují <xref:System.Collections.IDictionary> obecná <xref:System.Collections.Generic.IDictionary%602> rozhraní nebo, jsou kolekce slovníku; všichni ostatní jsou kolekce seznamů.

Další požadavky na typy kolekce, jako je například volání `Add` metody a konstruktor bez parametrů, jsou podrobněji popsány v následujících částech. Tím zajistíte, že typy kolekcí mohou být serializovány i deserializovány. To znamená, že některé kolekce nejsou přímo podporovány, například obecné <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> (protože nemá žádný konstruktor bez parametrů). Informace o obcházení těchto omezení naleznete v části "použití typů rozhraní kolekce a kolekcí jen pro čtení" dále v tomto tématu.

Typy obsažené v kolekcích musí být typy kontraktů dat, nebo by měly být jinak serializovatelný. Další informace najdete v tématu [typy podporované serializátorem kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md).

Další informace o tom, co je a co se nepovažuje za platnou kolekci, a také o tom, jak jsou kolekce serializovány, najdete v části informace o serializaci kolekcí v tématu "Rozšířená pravidla shromažďování" v tomto tématu.

## <a name="interchangeable-collections"></a>Zaměnitelné kolekce

Všechny kolekce seznamů stejného typu se považují za stejné kontrakty dat (pokud nejsou přizpůsobené pomocí <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributu, jak je popsáno dále v tomto tématu). Například následující kontrakty dat jsou ekvivalentní.

[!code-csharp[c_collection_types_in_data_contracts#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#0)]
[!code-vb[c_collection_types_in_data_contracts#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#0)]

Obě kontrakty dat vedou jako výsledek XML podobně jako následující kód.

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

V rámci kolekce můžete použít například typ kolekce optimalizovaný pro výkon serveru a typ kolekce, který je zaměřený na vázání na součásti uživatelského rozhraní na klientovi.

Podobně jako u kolekcí seznamů jsou všechny kolekce slovníku, které mají stejné typy klíčů a hodnot, považovány za stejné kontrakty dat (Pokud se <xref:System.Runtime.Serialization.CollectionDataContractAttribute> nejedná o vlastní atribut).

Pouze takové typy kontraktů dat se týkají rovnocennosti kolekcí, nikoli typů .NET. To znamená, že kolekce typ1 je považována za rovnocennou pro kolekci typ2, pokud mají typ1 a typ2 stejné kontrakty dat.

Neobecné kolekce se považují za stejné kontrakty dat jako obecné kolekce typu `Object`. (Například kontrakty dat pro <xref:System.Collections.ArrayList> a `Object` obecné <xref:System.Collections.Generic.List%601> jsou stejné.)

## <a name="using-collection-interface-types-and-read-only-collections"></a>Použití typů rozhraní kolekce a kolekcí jen pro čtení

Typy rozhraní kolekce (<xref:System.Collections.IEnumerable>, <xref:System.Collections.IDictionary>, obecná <xref:System.Collections.Generic.IDictionary%602>nebo rozhraní odvozená z těchto rozhraní) se také považují za kontrakty dat kolekce, které jsou ekvivalentní kontraktům dat kolekce pro skutečné typy kolekcí. Proto je možné deklarovat typ serializovaný jako typ rozhraní kolekce a výsledky jsou stejné, jako kdyby byl použit skutečný typ kolekce. Například následující kontrakty dat jsou ekvivalentní.

[!code-csharp[c_collection_types_in_data_contracts#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#1)]
[!code-vb[c_collection_types_in_data_contracts#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#1)]

Při serializaci, když je deklarovaný typ rozhraní, může být samotný typ používané instance libovolný typ, který implementuje toto rozhraní. Výše popsaná omezení (s konstruktorem bez parametrů a `Add` metodou) se nevztahují. Můžete například nastavit adresy v Customer2 na instanci obecné <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> adresy, i když nemůžete přímo deklarovat datový člen typu Generic. <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>

Při deserializaci, když deklarovaný typ je rozhraní, modul serializace zvolí typ, který implementuje deklarované rozhraní a vytvoří instanci typu. Mechanismus známých typů (popsaný v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)) nemá žádný vliv. Volba typu je integrována do WCF.

## <a name="customizing-collection-types"></a>Přizpůsobení typů kolekcí

Typy kolekce lze přizpůsobit pomocí <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributu, který má několik použití.

Všimněte si, že přizpůsobení typů kolekce ohrožuje zarovnávání kolekce, takže je obecně doporučeno vyhnout se použití tohoto atributu, kdykoli je to možné. Další informace o tomto problému najdete v části Rozšířená pravidla shromažďování informací dále v tomto tématu.

### <a name="collection-data-contract-naming"></a>Vyjmenovávání kontraktů dat kolekce

Pravidla pro pojmenování typů kolekcí jsou podobná těm pro pojmenování běžných typů kontraktů dat, jak je popsáno v tématu [názvy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-names.md), i když některé důležité rozdíly existují:

- Atribut slouží k přizpůsobení názvu namísto <xref:System.Runtime.Serialization.DataContractAttribute> atributu. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Atribut má `Name` také vlastnosti a `Namespace`. <xref:System.Runtime.Serialization.CollectionDataContractAttribute>

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Pokud atribut použit není, výchozí název a obor názvů pro typy kolekcí závisí na názvech a oborech názvů typů obsažených v kolekci. Nejsou ovlivněny názvem a oborem názvů samotného typu kolekce. Příklad naleznete v následujících typech.

  ```csharp
  public CustomerList1 : Collection<string> {}
  public StringList1 : Collection<string> {}
  ```

Oba typy název kontraktu dat jsou "ArrayOfstring", nikoli "CustomerList1" nebo "StringList1". To znamená, že serializace některého z těchto typů na kořenové úrovni vrátí XML podobně jako následující kód.

```xml
<ArrayOfstring>
    <string>...</string>
    <string>...</string>
    <string>...</string>
    ...
</ArrayOfstring>
```

Toto pravidlo pojmenování bylo zvoleno, aby se zajistilo, že jakýkoli nepřizpůsobený typ, který představuje seznam řetězců, má stejný kontrakt dat a reprezentace XML. Díky tomu je možné proměnit kolekci. V tomto příkladu jsou CustomerList1 a StringList1 úplně zaměnitelné.

Nicméně při <xref:System.Runtime.Serialization.CollectionDataContractAttribute> použití atributu se kolekce stala přizpůsobenou kontraktem dat kolekce, a to i v případě, že u atributu nejsou nastaveny žádné vlastnosti. Název a obor názvů kontraktu dat kolekce závisí na samotném typu kolekce. Příklad naleznete v následujícím typu.

[!code-csharp[c_collection_types_in_data_contracts#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#2)]
[!code-vb[c_collection_types_in_data_contracts#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#2)]

Při serializaci je výsledný kód XML podobný následujícímu.

```xml
<CustomerList2>
    <string>...</string>
    <string>...</string>
    <string>...</string>
    ...
</CustomerList2>
```

Všimněte si, že to již není ekvivalentem reprezentace XML nepřizpůsobených typů.

- Můžete použít `Name` vlastnosti a `Namespace` k dalšímu přizpůsobení názvů. Podívejte se na následující třídu.

  [!code-csharp[c_collection_types_in_data_contracts#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#3)]
  [!code-vb[c_collection_types_in_data_contracts#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#3)]

Výsledný kód XML je podobný následujícímu.

```xml
<cust_list>
    <string>...</string>
    <string>...</string>
    <string>...</string>
    ...
</cust_list>
```

Další informace najdete v části Rozšířená pravidla shromažďování informací dále v tomto tématu.

### <a name="customizing-the-repeating-element-name-in-list-collections"></a>Přizpůsobení opakujícího se názvu elementu v kolekcích seznamu

Kolekce seznamů obsahují opakující se položky. Obvykle je každá opakující se položka reprezentovaná jako element s názvem podle názvu kontraktu dat typu obsaženého v kolekci.

`CustomerList` V příkladech kolekce obsahovaly řetězce. Název kontraktu dat pro primitivní typ řetězce je "String", takže opakující se element byl "\<String >".

Nicméně pomocí <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> vlastnosti <xref:System.Runtime.Serialization.CollectionDataContractAttribute> u atributu lze tento opakující se název elementu přizpůsobit. Příklad naleznete v následujícím typu.

[!code-csharp[c_collection_types_in_data_contracts#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#4)]
[!code-vb[c_collection_types_in_data_contracts#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#4)]

Výsledný kód XML je podobný následujícímu.

```xml
<CustomerList4>
    <customer>...</customer>
    <customer>...</customer>
    <customer>...</customer>
    ...
</CustomerList4>
```

Obor názvů opakujícího se elementu je vždy stejný jako obor názvů kontraktu dat kolekce, který lze přizpůsobit pomocí `Namespace` vlastnosti, jak je popsáno výše.

### <a name="customizing-dictionary-collections"></a>Přizpůsobení kolekcí slovníku

Kolekce slovníku jsou v podstatě seznamy položek, kde každá položka má klíč následovaný hodnotou. Stejně jako u běžných seznamů můžete změnit název prvku, který odpovídá opakujícímu se elementu pomocí <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ItemName%2A> vlastnosti.

Kromě toho můžete změnit názvy elementů, které reprezentují klíč a hodnotu pomocí <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> vlastností a. <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> Obory názvů pro tyto prvky jsou stejné jako obor názvů kontraktu dat kolekce.

Příklad naleznete v následujícím typu.

[!code-csharp[c_collection_types_in_data_contracts#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#5)]
[!code-vb[c_collection_types_in_data_contracts#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#5)]

Při serializaci je výsledný kód XML podobný následujícímu.

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

Další informace o kolekcích slovníků najdete v části Rozšířená pravidla shromažďování informací dále v tomto tématu.

## <a name="collections-and-known-types"></a>Kolekce a známé typy

Nemusíte přidávat typy kolekcí ke známým typům, pokud se používají polymorfní místo jiných kolekcí nebo rozhraní kolekcí. Například pokud deklarujete datový člen typu <xref:System.Collections.IEnumerable> a použijete jej k odeslání <xref:System.Collections.ArrayList>instance, není nutné přidávat <xref:System.Collections.ArrayList> do známých typů.

Při použití kolekcí, které jsou polymorfní místo typů kolekce, je nutné je přidat ke známým typům. Například pokud deklarujete datový člen typu `Object` a použijete jej k odeslání <xref:System.Collections.ArrayList>instance, přidejte <xref:System.Collections.ArrayList> do známých typů.

To vám neumožňuje serializovat žádnou ekvivalentní kolekci polymorfní. Například při přidání <xref:System.Collections.ArrayList> do seznamu známých typů v předchozím příkladu vám to neumožňuje `Array of Object` přiřadit třídu, i když má ekvivalentní kontrakt dat. To se neliší od chování běžných známých typů při serializaci pro typy, které nejsou kolekcemi, ale je obzvláště důležité pochopit v případě kolekcí, protože je velmi běžné, aby kolekce byly ekvivalentní.

Během serializace může být v daném oboru pro daný kontrakt dat znám pouze jeden typ a stejné kolekce mají stejné kontrakty dat. To znamená, že v předchozím příkladu nelze přidat obojí <xref:System.Collections.ArrayList> a `Array of Object` ke známým typům ve stejném oboru. Tento postup je stejný jako chování známých typů pro typy bez kolekce, ale je obzvláště důležité pochopit pro kolekce.

Pro obsah kolekcí můžou být také požadovány známé typy. Například pokud <xref:System.Collections.ArrayList> ve skutečnosti obsahuje `Type1` instance a `Type2`, oba tyto typy by měly být přidány do známých typů.

Následující příklad ukazuje správně vytvořený graf objektů pomocí kolekcí a známých typů. Příklad je trochu contrived, protože ve skutečné aplikaci byste normálně nedefinovali následující datové členy jako `Object`, a proto nemají žádné známé problémy typu a polymorfismus.

[!code-csharp[c_collection_types_in_data_contracts#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#6)]
[!code-vb[c_collection_types_in_data_contracts#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#6)]

Pokud je deklarovaný typ typem kolekce, je při deserializaci vytvořena instance deklarovaného typu bez ohledu na typ, který byl skutečně odeslán. Pokud je deklarovaný typ rozhraní kolekce, pak deserializátor vybere typ, který má být vytvořen bez ohledu na známé typy.

V případě deserializace, pokud deklarovaný typ není typem kolekce, ale je odesílán typ kolekce, je typ odpovídajícího typu kolekce vyzvednut ze seznamu známých typů. Je možné přidat typy rozhraní kolekce do seznamu známých typů při deserializaci. V tomto případě modul deserializace znovu vybere typ, který má být vytvořen.

## <a name="collections-and-the-netdatacontractserializer-class"></a>Kolekce a třída NetDataContractSerializer

Pokud je <xref:System.Runtime.Serialization.CollectionDataContractAttribute> třída používána, nevlastní typy kolekce (bez atributu), které nejsou pole, ztratí jejich zvláštní význam. <xref:System.Runtime.Serialization.NetDataContractSerializer>

Nepřizpůsobené <xref:System.SerializableAttribute> typy kolekce označené atributem mohou být nadále serializovány <xref:System.Runtime.Serialization.NetDataContractSerializer> třídou podle <xref:System.SerializableAttribute> atributu nebo <xref:System.Runtime.Serialization.ISerializable> pravidel rozhraní.

Přizpůsobené typy kolekce, rozhraní kolekce a pole jsou stále považovány za kolekce, i když <xref:System.Runtime.Serialization.NetDataContractSerializer> je třída používána.

## <a name="collections-and-schema"></a>Kolekce a schéma

Všechny ekvivalentní kolekce mají stejnou reprezentaci ve schématu XSD (XML Schema Definition Language). Z tohoto důvodu obvykle nezískáte stejný typ kolekce ve vygenerovaném klientském kódu jako ten na serveru. Například server může používat kontrakt dat s obecným <xref:System.Collections.Generic.List%601> datovým členem typu Integer, ale v generovaném kódu klienta se stejný datový člen může stát polem celých čísel.

Kolekce slovníku jsou označeny pomocí anotace schématu specifické pro WCF, která značí, že se jedná o slovníky. v opačném případě jsou nerozlišovatelné z jednoduchých seznamů, které obsahují položky s klíčem a hodnotou. Přesný popis toho, jak se kolekce reprezentují ve schématu kontraktu dat, najdete v tématu [referenční informace schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).

Ve výchozím nastavení nejsou typy pro nepřizpůsobené kolekce v importovaném kódu generovány. Datové členy typů kolekcí seznamu jsou importovány jako pole a datové členy typů kolekce slovníku jsou importovány jako obecný slovník.

Pro vlastní kolekce jsou však vygenerovány samostatné typy označené <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributem. (Přizpůsobený typ kolekce ve schématu je jeden, který nepoužívá výchozí obor názvů, název, název opakující se elementu nebo názvy elementů a hodnot.) Tyto typy jsou prázdné typy, které jsou odvozeny z obecného <xref:System.Collections.Generic.List%601> pro typy seznamu a obecný slovník pro typy slovníku.

Na serveru můžete například mít následující typy.

[!code-csharp[c_collection_types_in_data_contracts#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#7)]
[!code-vb[c_collection_types_in_data_contracts#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#7)]

Když se schéma exportuje a znovu naimportuje zpátky, vygenerovaný kód klienta je podobný následujícímu (pole se zobrazují místo vlastností pro usnadnění čtení).

[!code-csharp[c_collection_types_in_data_contracts#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#8)]
[!code-vb[c_collection_types_in_data_contracts#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#8)]

Můžete chtít použít různé typy v generovaném kódu, než je výchozí. Například můžete chtít použít obecný <xref:System.ComponentModel.BindingList%601> místo regulárních polí pro datové členy, aby bylo snazší je navazovat na součásti uživatelského rozhraní.

Chcete-li zvolit typy kolekce, které mají být vygenerovány, předejte seznam typů kolekcí <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A> , které chcete <xref:System.Runtime.Serialization.ImportOptions> použít, do vlastnosti objektu při importu schématu. Tyto typy se nazývají *odkazované typy kolekcí*.

Při odkazování na obecné typy musí být buď plně otevřené obecné nebo plně uzavřené obecné typy.

> [!NOTE]
> Při použití nástroje Svcutil. exe lze tento odkaz provést pomocí přepínače příkazového řádku **/CollectionType** (krátký tvar: **/CT**). Mějte na paměti, že musíte také zadat sestavení pro odkazované typy kolekcí pomocí přepínače **/reference** (krátký tvar: **/r**). Pokud je typ obecný, musí následovat zadní uvozovka a počet obecných parametrů. Zpětná uvozovka\`() se Nepleťe s znakem jednoduché uvozovky ('). Můžete zadat více odkazovaných typů kolekce pomocí přepínače **/CollectionType** více než jednou.

Například pokud chcete, aby všechny seznamy byly importovány jako obecné <xref:System.Collections.Generic.List%601>.

```console
svcutil.exe MyService.wsdl MyServiceSchema.xsd /r:C:\full_path_to_system_dll\System.dll /ct:System.Collections.Generic.List`1
```

Při importu libovolné kolekce se prohledají tento seznam odkazovaných typů kolekce a v případě, že se najde, použije se nejlepší kolekce, a to buď jako typ datového členu (pro nepřizpůsobené kolekce), nebo jako základní typ, který se má odvodit (pro přizpůsobené kolekce). Slovníky se shodují jenom se slovníky, zatímco seznamy se shodují se seznamy.

Například pokud přidáte obecné <xref:System.ComponentModel.BindingList%601> a <xref:System.Collections.Hashtable> do seznamu odkazovaných typů, vygenerovaný kód klienta pro předchozí příklad je podobný následujícímu.

[!code-csharp[c_collection_types_in_data_contracts#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#9)]
[!code-vb[c_collection_types_in_data_contracts#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#9)]

Typy rozhraní kolekce lze zadat jako součást vašich odkazovaných typů kolekce, ale nelze zadat neplatné typy kolekcí (například ty, které neobsahují `Add` metodu ani veřejný konstruktor).

Uzavřený obecný objekt je považován za nejlepší shodu. (Neobecné typy jsou považovány za ekvivalent k uzavřeným obecným `Object`typům). Pokud <xref:System.Collections.Generic.List%601> například obecné <xref:System.DateTime>typy, obecné <xref:System.ComponentModel.BindingList%601> (otevřené Obecné) a <xref:System.Collections.ArrayList> jsou odkazované typy kolekce, je vygenerováno následující.

[!code-csharp[c_collection_types_in_data_contracts#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#10)]
[!code-vb[c_collection_types_in_data_contracts#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#10)]

V případě kolekcí seznamů jsou podporovány pouze případy v následující tabulce.

|Odkazovaný typ|Rozhraní implementované odkazovaným typem|Příklad|Typ se považuje za:|
|---------------------|----------------------------------------------|-------------|----------------------|
|Neobecný nebo uzavřený obecný (libovolný počet parametrů)|Neobecné|`MyType : IList`<br /><br /> or<br /><br /> `MyType<T> : IList`<br /><br /> kde T =`int`|Uzavřený obecný `Object` příklad ( `IList<object>`například)|
|Neobecný nebo uzavřený obecný (libovolný počet parametrů, které se nutně neshodují s typem kolekce)|Uzavřený obecný|`MyType : IList<string>`<br /><br /> or<br /><br /> `MyType<T> : IList<string>`kde T =`int`|Uzavřený obecný (například `IList<string>`)|
|Uzavřený obecný s libovolným počtem parametrů|Otevřete obecné pomocí některého z parametrů typu.|`MyType<T,U,V> : IList<U>`<br /><br /> kde T =`int`, U =`string`, V =`bool`|Uzavřený obecný (například `IList<string>`)|
|Otevřít obecný s jedním parametrem|Otevření obecného pomocí parametru typu|`MyType<T> : IList<T>`, T je otevřený|Otevřený obecný (například `IList<T>`)|

Pokud typ implementuje více než jedno rozhraní kolekce seznamů, platí následující omezení:

- Pokud typ implementuje obecné <xref:System.Collections.Generic.IEnumerable%601> (nebo jeho odvozená rozhraní) několikrát pro různé typy, typ není považován za platný odkazový typ kolekce a je ignorován. To platí i v případě, že některé implementace jsou neplatné nebo používají otevřené obecné typy. Například typ, který implementuje <xref:System.Collections.Generic.IEnumerable%601> generické `int` a obecné <xref:System.Collections.Generic.IEnumerable%601> rozhraní T, se `int` nikdy nepoužije jako odkazovaná kolekce typu nebo jakéhokoliv `Add` jiného typu, bez ohledu na to, jestli typ obsahuje metodu přijímání. `int` nebo Metodapřijímáparametrtypu`Add` T nebo obojí.

- Pokud typ implementuje rozhraní pro obecné kolekce a také <xref:System.Collections.IList>, typ se nikdy nepoužívá jako odkazový typ kolekce, pokud obecné rozhraní kolekce není uzavřeným obecným typem. <xref:System.Object>

V případě kolekcí slovníků jsou podporovány pouze případy v následující tabulce.

|Odkazovaný typ|Rozhraní implementované odkazovaným typem|Příklad|Typ se považuje za|
|---------------------|----------------------------------------------|-------------|---------------------|
|Neobecný nebo uzavřený obecný (libovolný počet parametrů)|<xref:System.Collections.IDictionary>|`MyType : IDictionary`<br /><br /> or<br /><br /> `MyType<T> : IDictionary`kde T =`int`|Uzavřený obecný`IDictionary<object,object>`|
|Uzavřený obecný (libovolný počet parametrů)|<xref:System.Collections.Generic.IDictionary%602>, uzavřeno|`MyType<T> : IDictionary<string, bool>`kde T =`int`|Uzavřený obecný (například `IDIctionary<string,bool>`)|
|Uzavřený obecný (libovolný počet parametrů)|Generic <xref:System.Collections.Generic.IDictionary%602>, jedna z hodnot klíč nebo value je uzavřená, druhá je otevřená a používá jeden z parametrů typu.|`MyType<T,U,V> : IDictionary<string,V>`kde T =`int`, U =`float`, V =`bool`<br /><br /> or<br /><br /> `MyType<Z> : IDictionary<Z,bool>`kde Z =`string`|Uzavřený obecný (například `IDictionary<string,bool>`)|
|Uzavřený obecný (libovolný počet parametrů)|Generic <xref:System.Collections.Generic.IDictionary%602>, klíč i hodnota jsou otevřené a každá používá jeden z parametrů typu.|`MyType<T,U,V> : IDictionary<V,U>`kde T =`int`, U =`bool`, V =`string`|Uzavřený obecný (například `IDictionary<string,bool>`)|
|Otevřít obecný (dva parametry)|Obecné <xref:System.Collections.Generic.IDictionary%602>, otevřít, používá obecné parametry typu v pořadí, ve kterém se zobrazují.|`MyType<K,V> : IDictionary<K,V>`, K a V otevřené|Otevřený obecný (například `IDictionary<K,V>`)|

Pokud typ implementuje jak <xref:System.Collections.IDictionary> i obecné <xref:System.Collections.Generic.IDictionary%602>, je považována <xref:System.Collections.Generic.IDictionary%602> pouze obecná.

Odkazy na částečné obecné typy se nepodporují.

Duplicity nejsou <xref:System.Collections.Generic.List%601> povoleny, například nemůžete přidat obecnou `Integer` `Integer` i obecnou kolekci do <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>, protože díky tomu není možné určit, která z nich se má použít, když se najde seznam celých čísel. ve schématu. Duplicity jsou zjištěny pouze v případě, že ve schématu existuje typ, který zpřístupňuje problém s duplicitami. Například pokud importované schéma neobsahuje <xref:System.Collections.Generic.List%601> seznam celých čísel, může mít jak obecné `Integer` , tak i <xref:System.Runtime.Serialization.ImportOptions.ReferencedCollectionTypes%2A>obecnou kolekci `Integer` v, ale ani to nemá žádný vliv.

## <a name="advanced-collection-rules"></a>Rozšířená pravidla shromažďování

### <a name="serializing-collections"></a>Serializace kolekcí

Následuje seznam pravidel shromažďování pro serializaci:

- Kombinování typů kolekcí (mají kolekce kolekcí) je povoleno. Vícenásobná pole jsou považována za kolekce kolekcí. Multidimenzionální pole nejsou podporována.

- Pole bajtů a polí pro <xref:System.Xml.XmlNode> jsou speciální typy pole, které jsou považovány za primitivní, nikoli pro kolekce. Serializace pole bajtů v jednom elementu XML, který obsahuje blok dat kódovaných ve formátu base64, namísto samostatného prvku pro každý bajt. Další informace o tom, jak se vychází z <xref:System.Xml.XmlNode> pole, najdete v tématu [typy XML a ADO.NET v kontraktech dat](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md). Tyto speciální typy se samozřejmě můžou zúčastnit v kolekcích: pole bajtů má za následek více elementů XML, přičemž každý z nich obsahuje blok dat kódovaných ve formátu base64.

- Pokud je <xref:System.Runtime.Serialization.DataContractAttribute> atribut použit pro typ kolekce, je typ považován za běžný typ kontraktu dat, nikoli jako kolekce.

- Pokud typ kolekce implementuje <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, platí následující pravidla pro daný typ: `myType:IList<string>, IXmlSerializable`

  - Pokud je `IList<string>`deklarovaný typ, typ je serializován jako seznam.

  - Je `myType`-li deklarovaný typ, je serializován jako `IXmlSerializable`.

  - Pokud je `IXmlSerializable`deklarovaný typ, je serializován jako `IXmlSerializable`, ale pouze v případě, že přidáte `myType` do seznamu známých typů.

- Kolekce jsou serializovány a deserializovány pomocí metod, které jsou uvedeny v následující tabulce.

|Implementace typu kolekce|Metody, které jsou volány při serializaci|Metody, které jsou volány při deserializaci|
|--------------------------------|-----------------------------------------|-------------------------------------------|
|Obecněji<xref:System.Collections.Generic.IDictionary%602>|`get_Keys`, `get_Values`|Obecné přidání|
|<xref:System.Collections.IDictionary>|`get_Keys`, `get_Values`|`Add`|
|Obecněji<xref:System.Collections.Generic.IList%601>|Obecný <xref:System.Collections.Generic.IList%601> indexer|Obecné přidání|
|Obecněji<xref:System.Collections.Generic.ICollection%601>|Čítače|Obecné přidání|
|<xref:System.Collections.IList>|<xref:System.Collections.IList>Indexer|`Add`|
|Obecněji<xref:System.Collections.Generic.IEnumerable%601>|`GetEnumerator`|Nestatická metoda s názvem `Add` , která přijímá jeden parametr příslušného typu (typ obecného parametru nebo jeden z jeho základních typů). Taková metoda musí existovat, aby serializátor považoval typ kolekce jako kolekci během serializace i deserializace.|
|<xref:System.Collections.IEnumerable>(a tedy <xref:System.Collections.ICollection>z něj odvozeno)|`GetEnumerator`|Nestatická metoda s názvem `Add` , která přijímá jeden parametr typu. `Object` Taková metoda musí existovat, aby serializátor považoval typ kolekce jako kolekci během serializace i deserializace.|

V předchozí tabulce jsou uvedena rozhraní kolekce v sestupném pořadí podle priority. To například znamená, že pokud typ implementuje jak <xref:System.Collections.IList> i obecné <xref:System.Collections.Generic.IEnumerable%601>, kolekce je serializována a <xref:System.Collections.IList> deserializována podle pravidel:

- Při deserializaci jsou všechny kolekce deserializovány tím, že nejprve vytvoří instanci typu voláním konstruktoru bez parametrů, který musí být přítomen, aby serializátor považoval typ kolekce jako kolekci během serializace a deserializace.

- Je-li stejné obecné rozhraní kolekce implementováno více než jednou <xref:System.Collections.Generic.ICollection%601> (například pokud typ implementuje jak obecné `Integer` , tak obecné <xref:System.Collections.Generic.ICollection%601> z <xref:System.String>) a není nalezeno žádné rozhraní s vyšší prioritou, kolekce je nezpracovává se jako platná kolekce.

- Typy kolekcí mohou mít <xref:System.SerializableAttribute> atribut použit a mohou <xref:System.Runtime.Serialization.ISerializable> implementovat rozhraní. Obě tyto parametry jsou ignorovány. Nicméně pokud typ zcela nesplňuje požadavky na `Add` typ kolekce (například metoda chybí), typ není považován za typ kolekce, a <xref:System.SerializableAttribute> proto atribut a <xref:System.Runtime.Serialization.ISerializable> rozhraní slouží k určení Určuje, zda lze typ serializovat.

- Použití atributu na kolekci pro přizpůsobení <xref:System.SerializableAttribute> odebere předchozí nouzový mechanismus. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Místo toho, pokud přizpůsobená kolekce nesplňuje požadavky typu kolekce, <xref:System.Runtime.Serialization.InvalidDataContractException> je vyvolána výjimka. Řetězec výjimky často obsahuje informace, které vysvětlují, proč daný typ není považován za platnou kolekci ( `Add` žádná metoda, žádný konstruktor bez parametrů atd.), takže je často vhodné <xref:System.Runtime.Serialization.CollectionDataContractAttribute> použít atribut pro ladění. cíle.

### <a name="collection-naming"></a>Pojmenovávání kolekcí

Následuje seznam pravidel pro pojmenovávání kolekcí:

- Výchozí obor názvů pro všechny kontrakty dat kolekce slovníku, stejně jako pro kontrakty dat kolekce, které obsahují primitivní typy, `http://schemas.microsoft.com/2003/10/Serialization/Arrays` je, pokud není přepsán pomocí oboru názvů. Typy, které jsou mapovány na předdefinované typy XSD a také `char`typy, `Timespan`a `Guid` , jsou považovány za primitivní prvky pro tento účel.

- Výchozí obor názvů pro typy kolekce, které obsahují neprimitivní typy, pokud není přepsán pomocí oboru názvů, je stejný jako obor názvů kontraktu dat typu obsaženého v kolekci.

- Výchozí název pro kontrakty dat kolekce list, pokud není přepsán pomocí názvu, je řetězec "ArrayOf" v kombinaci s názvem kontraktu dat typu obsaženým v kolekci. Například název kontraktu dat pro obecný seznam celých čísel je "ArrayOfint". Mějte na paměti, že název `Object` kontraktu dat je "anyType", takže název kontraktu dat neobecných seznamů, jako <xref:System.Collections.ArrayList> je "ArrayOfanyType".

Výchozí název kontraktů dat kolekce slovníku, pokud není přepsán `Name`pomocí, je řetězec "ArrayOfKeyValueOf" v kombinaci s názvem kontraktu dat typu klíče následovaným názvem kontraktu dat typu hodnoty. Například název kontraktu dat pro obecný slovník typu řetězec a celé číslo je "ArrayOfKeyValueOfstringint". Kromě toho, pokud klíč nebo typ hodnoty nejsou primitivní typy, připojí se k názvu hodnota hash oboru názvů kontraktů dat pro obory názvů kontraktů dat. Další informace o hodnotách hash oboru názvů najdete v tématu [názvy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-names.md).

Každý kontrakt dat kolekce slovníku má doprovodnou kontrakt dat, který reprezentuje jednu položku ve slovníku. Jeho název je stejný jako u kontraktu dat slovníku, s výjimkou předpony "ArrayOf" a jeho obor názvů je stejný jako u kontraktu dat slovníku. Například kontrakt dat "KeyValueofstringint" ve slovníku "ArrayOfKeyValueOfstringint" představuje jednu položku ve slovníku. Název této kontraktu dat můžete přizpůsobit pomocí `ItemName` vlastnosti, jak je popsáno v následující části.

Pravidla pojmenování obecných typů, jak je popsáno v tématu [názvy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-names.md), se plně vztahují na typy kolekcí; To znamená, že můžete použít složené závorky v názvu k označení parametrů obecného typu. Čísla v rámci složených závorek však odkazují na Obecné parametry a nikoli na typy obsažené v kolekci.

## <a name="collection-customization"></a>Přizpůsobení kolekce

Následující použití <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributu je zakázáno a výsledkem je <xref:System.Runtime.Serialization.InvalidDataContractException> výjimka:

- Použití atributu na typ, na <xref:System.Runtime.Serialization.CollectionDataContractAttribute> který byl atribut použit, nebo na jeden z jeho odvozených typů. <xref:System.Runtime.Serialization.DataContractAttribute>

- Použití atributu na typ, který <xref:System.Xml.Serialization.IXmlSerializable> implementuje rozhraní. <xref:System.Runtime.Serialization.CollectionDataContractAttribute>

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Použití atributu pro typ, který není kolekce.

- Pokus o nastavení <xref:System.Runtime.Serialization.CollectionDataContractAttribute.KeyName%2A> nebo <xref:System.Runtime.Serialization.CollectionDataContractAttribute.ValueName%2A> <xref:System.Runtime.Serialization.CollectionDataContractAttribute> použití atributu použitého pro jiný typ než slovník.

### <a name="polymorphism-rules"></a>Pravidla polymorfismu

Jak už jsme uvedli, přizpůsobení kolekcí pomocí <xref:System.Runtime.Serialization.CollectionDataContractAttribute> atributu může narušit zaměnitelné kolekce. Dva přizpůsobené typy kolekce lze považovat za ekvivalentní pouze v případě, že se shodují jejich název, obor názvů, název položky a také názvy klíčů a hodnot (Pokud se jedná o kolekce slovníku).

Z důvodu přizpůsobení je možné neúmyslně použít jeden kontrakt dat kolekce, kde je očekáván další. To by mělo být zabráněno. Podívejte se na následující typy.

[!code-csharp[c_collection_types_in_data_contracts#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_collection_types_in_data_contracts/cs/program.cs#11)]
[!code-vb[c_collection_types_in_data_contracts#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_collection_types_in_data_contracts/vb/program.vb#11)]

V takovém případě `Marks1` může být `testMarks`přiřazena instance. Nicméně by `Marks2` neměl být použit, protože jeho kontrakt dat není považován za ekvivalent `IList<int>` kontraktu dat. Název kontraktu dat je "Marks2", nikoli "ArrayOfint" a název opakujícího se elementu je "\<Mark >", nikoli "\<int >".

Pravidla v následující tabulce platí pro polymorfní přiřazení kolekcí.

|Deklarovaný typ|Přiřazení nepřizpůsobené kolekce|Přiřazení přizpůsobené kolekce|
|-------------------|--------------------------------------------|---------------------------------------|
|Objekt|Název kontraktu je serializován.|Název kontraktu je serializován.<br /><br /> Vlastní nastavení se používá.|
|Rozhraní kolekce|Název kontraktu není serializován.|Název kontraktu není serializován.<br /><br /> Vlastní nastavení se nepoužívá.\*|
|Přizpůsobená kolekce|Název kontraktu není serializován.|Název kontraktu je serializován.<br /><br /> Používá se přizpůsobení. * *|
|Přizpůsobená kolekce|Název kontraktu je serializován. Vlastní nastavení se nepoužívá.\*\*|Název kontraktu je serializován.<br /><br /> Používá se přizpůsobení přiřazeného typu.\*\*|

\*<xref:System.Runtime.Serialization.NetDataContractSerializer> U třídy se v tomto případě používá přizpůsobení. <xref:System.Runtime.Serialization.NetDataContractSerializer> Třída také v tomto případě serializace skutečný název typu, takže deserializace funguje podle očekávání.

\*\*Tyto případy mají za následek neplatné instance schématu, takže by se měly vyhnout.

V případech, kdy je název kontraktu serializován, by měl být přiřazený typ kolekce v seznamu známých typů. Opak je také true: v případech, kde není název serializován, není nutné přidat typ do seznamu známých typů.

Pole odvozeného typu lze přiřadit poli základního typu. V tomto případě je název kontraktu pro odvozený typ serializován pro každý opakující se element. Například pokud typ `Book` je odvozen z typu `LibraryItem`, `Book` můžete přiřadit pole k poli `LibraryItem`. To se nevztahuje na jiné typy kolekcí. Například nemůžete přiřadit `Generic List of Book` `Generic List of LibraryItem`k. Můžete však přiřadit `Generic List of LibraryItem` instance, které obsahují `Book` instance. V poli i v případě, že se jedná o případ `Book` bez pole, by měl být v seznamu známých typů.

## <a name="collections-and-object-reference-preservation"></a>Zachování kolekcí a objektů odkazů na objekty

Když serializátor funguje v režimu, kde zachovává odkazy na objekty, vztahuje se na kolekce i zachování odkazů na objekty. Konkrétně je zachována identita objektu pro celou kolekci i pro jednotlivé položky obsažené v kolekcích. U slovníků je identita objektu zachovaná pro objekty dvojice klíč/hodnota a jednotlivé objekty klíče a hodnoty.

## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.CollectionDataContractAttribute>

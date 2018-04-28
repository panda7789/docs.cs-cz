---
title: Serializace a deserializace
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
ms.assetid: 3d71814c-bda7-424b-85b7-15084ff9377a
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4d5caa913a49205c387c22a615b2b8da2dba0a77
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="serialization-and-deserialization"></a>Serializace a deserializace
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zahrnuje nové Serializační stroj <xref:System.Runtime.Serialization.DataContractSerializer>. <xref:System.Runtime.Serialization.DataContractSerializer> Překládá mezi [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objekty a XML v obou směrech. Toto téma vysvětluje, jak funguje serializátor.  
  
 Při serializaci [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objekty, serializátor rozumí celou řadu serializace programovací modely, včetně nové *kontrakt dat* modelu. Úplný seznam podporovaných typů najdete v tématu [typy nepodporuje serializátor kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Úvod do kontrakty dat, najdete v části [pomocí kontrakty dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Při deserializaci XML, používá serializátor <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> třídy. Podporuje také <xref:System.Xml.XmlDictionaryReader> a <xref:System.Xml.XmlDictionaryWriter> třídy k povolení ji k vytvoření optimalizované XML v některých případech, například při použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binární formát XML.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zahrnuje také doprovodné serializátor, <xref:System.Runtime.Serialization.NetDataContractSerializer>. <xref:System.Runtime.Serialization.NetDataContractSerializer> Je podobná <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> serializátorů protože také vysílá [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] zadejte názvy v rámci serializovaná data. Používá se při stejné typy jsou sdíleny serializaci a deserializaci elementy end. Jak <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer> odvozena z běžných základní třídy, <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
> [!WARNING]
>  <xref:System.Runtime.Serialization.DataContractSerializer> Serializuje řetězců obsahujících řídicí znaky s hexadecimální hodnotu nižší než 20 jako entity XML. Při odesílání těchto dat na službu WCF může dojít k potížím s klienta bez WCF.  
  
## <a name="creating-a-datacontractserializer-instance"></a>Vytvoření DataContractSerializer Instance  
 Vytváření instance <xref:System.Runtime.Serialization.DataContractSerializer> je důležitý krok. Po vytváření nelze změnit některé z nastavení.  
  
### <a name="specifying-the-root-type"></a>Určení kořenové typ  
 *Kořenový typ* se o typ, které jsou instancemi serializován nebo deserializován. <xref:System.Runtime.Serialization.DataContractSerializer> Má mnoho přetížení konstruktoru, ale minimálně, je nutné zadat typ kořenového pomocí `type` parametr.  
  
 Označuje, že serializátor vytvořené pro určitý typ kořenové nelze použít k serializaci (nebo deserializaci) jiného typu, pokud je typ odvozený od typu root. Následující příklad ukazuje dvě třídy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#1)]
 [!code-vb[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#1)]  
  
 Tento kód vytvoří instanci objektu `DataContractSerializer` který lze použít pouze k serializaci nebo deserializaci instance `Person` třídy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#2)]
 [!code-vb[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#2)]  
  
### <a name="specifying-known-types"></a>Zadání známé typy  
 Pokud Polymorfismus je součástí serializována typy, které již nejsou zpracovávány pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut nebo jinému kontrolnímu mechanismu, musí být seznam možných známé typy předaný konstruktoru serializátor pomocí `knownTypes` parametr. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] známé typy, najdete v části [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 Následující příklad ukazuje třídu, `LibraryPatron`, který obsahuje kolekci určitého typu, `LibraryItem`. Definuje třídu sekundu `LibraryItem` typu. Třetí a čtyřmi třídy (`Book` a `Newspaper`) dědí `LibraryItem` třídy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#3)]  
 [!code-vb[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#3)]  
  
 Následující kód vytvoří instanci objektu serializátor pomocí `knownTypes` parametr.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#4)]
 [!code-vb[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#4)]  
  
### <a name="specifying-the-default-root-name-and-namespace"></a>Výchozí název kořenové a Namespace  
 Za normálních okolností při objekt serializován, výchozí název a oboru názvů nejkrajnější elementu XML se určují podle názvu kontraktu dat a oboru názvů. Názvy všech vnitřní prvky jsou určit názvy členů dat a jejich obor názvů je obor názvů kontraktu dat. Následující příklad sady `Name` a `Namespace` hodnoty v konstruktorech systému <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> třídy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#5)]
 [!code-vb[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#5)]  
  
 Serializace instance `Person` třída vytváří XML podobný následujícímu.  
  
```xml  
<PersonContract xmlns="http://schemas.contoso.com">  
  <AddressMember>  
    <StreetMember>123 Main Street</StreetMember>  
   </AddressMember>  
</PersonContract>  
```  
  
 Ale můžete přizpůsobit výchozí název a obor názvů kořenového prvku předáním hodnoty `rootName` a `rootNamespace` parametry, které <xref:System.Runtime.Serialization.DataContractSerializer> konstruktor. Všimněte si, že `rootNamespace` nemá vliv na obor názvů obsažené prvky, které odpovídají datových členů. Ovlivňuje jenom obor názvů nejkrajnější elementu.  
  
 Tyto hodnoty lze předat jako řetězce nebo instance <xref:System.Xml.XmlDictionaryString> třídu, která umožňuje jejich optimalizace v binárním formátu XML.  
  
### <a name="setting-the-maximum-objects-quota"></a>Nastavení kvóty maximální objekty  
 Některé `DataContractSerializer` mají přetížení konstruktor `maxItemsInObjectGraph` parametr. Tento parametr určuje maximální počet objektů serializátoru, který serializuje a deserializuje do jedné <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> volání metody. (Metodu vždy čte jeden kořenový objekt, ale tento objekt může mít jiné objekty v jeho datových členů. Tyto objekty může mít jiné objekty atd.) Výchozí hodnota je 65536. Všimněte si, že při serializaci nebo deserializaci pole, každá položka pole počítá jako samostatný objekt. Všimněte si také, že některé objekty může mít znázornění velké paměti, a proto nemusí být tato kvóta samostatně dostačující k zabránění útoku DOS. Další informace najdete v tématu [důležité informace o zabezpečení pro Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Pokud je potřeba zvýšit tato kvóta nad výchozí hodnotu, je důležité učinit odeslání (serializaci) a obdrželi stranách (deserializaci), protože se vztahuje na obou při čtení a zápis dat.  
  
### <a name="round-trips"></a>Odezev  
 A *odezvy* nastane, když je objekt deserializován a znovu serializovat v rámci jedné operace. Proto přejde ze souboru XML na instanci objektu a zpět znovu do datový proud XML.  
  
 Některé `DataContractSerializer` mají přetížení konstruktor `ignoreExtensionDataObject` parametr, který je nastaven na `false` ve výchozím nastavení. V tomto režimu výchozí odesláním dat na dobu odezvy z novější verze sady kontraktu dat prostřednictvím starší verzi a zpět na novější verzi, bez ztráty, tak dlouho, dokud kontraktu dat implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní. Předpokládejme například, že verze 1 `Person` obsahuje kontrakt dat `Name` a `PhoneNumber` přidá datových členů a verze 2 `Nickname` člen. Pokud `IExtensibleDataObject` je implementována, při odesílání informací z verze 2 verze 1, `Nickname` data jsou uložená a pak znovu vygenerované při dat je serializováno znovu; proto je při výměně zpráv ztracena žádná data. Další informace najdete v tématu [kontrakty dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) a [Správa verzí kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).  
  
#### <a name="security-and-schema-validity-concerns-with-round-trips"></a>Zabezpečení a aspekty platnosti schématu s odezev  
 Odezev může mít vliv na zabezpečení. Například při deserializaci a ukládání velkých objemů dat nadbytečné může být bezpečnostní riziko. Může být zabezpečení se o opětovné generování tato data se způsob, jak ověřit, zejména v případě, že se jedná o digitální podpisy. Například v předchozím scénáři může být podepisování koncový bod verze 1 `Nickname` hodnotu, která obsahuje škodlivá data. Navíc může být ke schématu platnosti obavy: koncový bod může být vhodné vždy emitování data, která výhradně dodržuje její stanovené smlouvy a nejsou žádné další hodnoty. V předchozím příkladu verze 1 koncového bodu kontraktu říká, že vysílá pouze `Name` a `PhoneNumber`a pokud se používá ověřování schématu, generování nadbytečné `Nickname` hodnota způsobuje selhání ověření.  
  
#### <a name="enabling-and-disabling-round-trips"></a>Povolení a zakázání odezev  
 Chcete-li vypnout odezev, neimplementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní. Pokud nemáte žádnou kontrolu nad typy, nastavte `ignoreExtensionDataObject` parametru `true` k dosažení stejného efektu.  
  
### <a name="object-graph-preservation"></a>Zachování objekt grafu.  
 Za normálních okolností serializátor nepotřebujete vědět o identitě objekt, jako v následujícím kódu.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#6)]
 [!code-vb[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#6)]  
  
 Následující kód vytvoří nákupní objednávka.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#7)]
 [!code-vb[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#7)]  
  
 Všimněte si, že `billTo` a `shipTo` pole se nastaví na stejnou instanci objektu. Vygenerovaný soubor XML však duplikuje informace duplicitní a bude vypadat podobně jako následující kód XML.  
  
```xml  
<PurchaseOrder>  
  <billTo><street>123 Main St.</street></billTo>  
  <shipTo><street>123 Main St.</street></shipTo>  
</PurchaseOrder>  
```  
  
 Však tento přístup má následující vlastnosti, které může být žádoucí:  
  
-   Výkon. Replikace dat je neefektivní.  
  
-   Cyklické odkazy. Pokud objekty odkazovat na sebe, klidně i prostřednictvím jiné objekty, serializaci replikací vyústí v nekonečné smyčce. (Serializátor vyvolá <xref:System.Runtime.Serialization.SerializationException> v takovém případě.)  
  
-   Sémantika. Někdy je důležité zachovat skutečnost, že dva odkazy jsou ke stejnému objektu a ne dva objekty stejné.  
  
 Pro tyto důvodů, proč, některé `DataContractSerializer` mají přetížení konstruktor `preserveObjectReferences` parametr (výchozí hodnota je `false`). Pokud tento parametr je nastaven `true`, odkazuje zvláštní metodu kódování objektu, který pouze [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jste srozuměni s tím, bude použita. Pokud nastavíte hodnotu `true`, teď podobá následující zprávě příklad kódu XML.  
  
```xml  
<PurchaseOrder ser:id="1">  
  <billTo ser:id="2"><street ser:id="3">123 Main St.</street></billTo>  
  <shipTo ser:ref="2"/>  
</PurchaseOrder>  
```  
  
 Obor názvů "pož" odkazuje na obor standardní serializace http://schemas.microsoft.com/2003/10/Serialization/. Každá položka dat je serializovat pouze jednou a zadané číslo ID a následné používá výsledek v odkazu na již serializovaná data.  
  
> [!IMPORTANT]
>  Pokud se nacházejí v kontrakt dat atributy "id" a "ref" `XMLElement`, je dodržení atribut "ref" a "id" atribut je ignorován.  
  
 Je důležité vědět o omezeních tento režim:  
  
-   Soubor XML `DataContractSerializer` vytváří s `preserveObjectReferences` nastavena na `true` není umožňuje vzájemnou spolupráci s jinými technologiemi a je přístupný pouze jiným `DataContractSerializer` instance, také s `preserveObjectReferences` nastavena na `true`.  
  
-   Neexistuje žádná podpora metadat (schéma) pro tuto funkci. Je platná pouze pro tento případ schématu, která je vytvořena při `preserveObjectReferences` je nastaven na `false`.  
  
-   Tato funkce může způsobit serializace a deserializace proces pomaleji. I když není nutné replikovat data, je nutné provést porovnání další objekt v tomto režimu.  
  
> [!CAUTION]
>  Při `preserveObjectReferences` režim povolený, je velmi důležité nastavit `maxItemsInObjectGraph` hodnota, která má správné kvótu. Vzhledem ke způsobu pole jsou zpracovávány v tomto režimu, je snadné pro útočníka vytvořit malé škodlivý zprávu, která má za následek omezený pouze systémem spotřeby velké paměti `maxItemsInObjectGraph` kvóty.  
  
### <a name="specifying-a-data-contract-surrogate"></a>Určení náhradní kontraktu dat  
 Některé `DataContractSerializer` mají přetížení konstruktor `dataContractSurrogate` parametr, který může být nastaven na `null`. Jinak můžete použít k určení *náhradní kontraktu dat*, což je typ, který implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate> rozhraní. Pak můžete použít rozhraní přizpůsobit serializaci a deserializaci procesu. Další informace najdete v tématu [náhrady kontraktů dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
## <a name="serialization"></a>Serializace  
 Následující informace platí pro všechny třídy, která dědí z <xref:System.Runtime.Serialization.XmlObjectSerializer>, včetně <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer> třídy.  
  
### <a name="simple-serialization"></a>Jednoduché serializace  
 Nejzákladnější způsob o serializaci objektu je předejte jej <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> metoda. Existují tři přetížení, jeden pro zápis do <xref:System.IO.Stream>, <xref:System.Xml.XmlWriter>, nebo <xref:System.Xml.XmlDictionaryWriter>. Pomocí <xref:System.IO.Stream> přetížení, výstup je XML v kódování UTF-8. Pomocí <xref:System.Xml.XmlDictionaryWriter> přetížení, serializátor optimalizuje její výstup pro binární formát XML.  
  
 Při použití <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> metoda serializátoru, který používá výchozí název a obor názvů pro element obálky a zapíše ho společně s obsahem (viz předchozí části "Určení the výchozí kořenový název a Namespace").  
  
 Následující příklad ukazuje zápis s <xref:System.Xml.XmlDictionaryWriter>.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#8)]
 [!code-vb[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#8)]  
  
 To vytváří XML podobný následujícímu.  
  
```xml  
<Person>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
### <a name="step-by-step-serialization"></a>Krok za krokem serializace  
 Použití <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A>, <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A>, a <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> metody k zápisu end element zapsat obsah objektu a zavřete element obálky, v uvedeném pořadí.  
  
> [!NOTE]
>  Neexistují žádné <xref:System.IO.Stream> přetížení těchto metod.  
  
 Tento krok za krokem serializace se dvě běžné způsoby. Jeden je vložit obsah, jako je například atributy nebo komentáře mezi `WriteStartObject` a `WriteObjectContent`, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#9)]
 [!code-vb[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#9)]  
  
 To vytváří XML podobný následujícímu.  
  
```xml  
<Person serializedBy="myCode">  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
 Další běžné použití je vyhýbat se používání <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> a <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> zcela a k zápisu vlastního vlastní obálky elementu (nebo i Přeskočit zápis obálku zcela), jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#10)]
 [!code-vb[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#10)]  
  
 To vytváří XML podobný následujícímu.  
  
```xml  
<MyCustomWrapper>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</MyCustomWrapper>  
```  
  
> [!NOTE]
>  Použití podrobné serializace může mít za následek neplatné schéma XML.  
  
## <a name="deserialization"></a>Deserializace  
 Následující informace platí pro všechny třídy, která dědí z <xref:System.Runtime.Serialization.XmlObjectSerializer>, včetně <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer> třídy.  
  
 Nejzákladnější možnost k deserializaci objektu je volání jednoho z <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> přetížení metody. Existují tři přetížení, jeden pro čtení s <xref:System.Xml.XmlDictionaryReader>, `XmlReader`, nebo `Stream`. Všimněte si, že `Stream` přetížení vytvoří textové <xref:System.Xml.XmlDictionaryReader> který není chráněn žádné kvóty a slouží pouze ke čtení dat důvěryhodné.  
  
 Všimněte si také, že objekt `ReadObject` metoda vrátí hodnotu, musí být přetypovat příslušného typu.  
  
 Následující kód vytvoří instanci objektu <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.XmlDictionaryReader>, pak deserializuje `Person` instance.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#11)]
 [!code-vb[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#11)]  
  
 Před voláním <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> metodu, umístěte čtecí modul XML na element obálky nebo na uzel jiný obsah, který předchází element obálky. To provedete pomocí volání <xref:System.Xml.XmlReader.Read%2A> metodu <xref:System.Xml.XmlReader> nebo jeho odvození a testování <xref:System.Xml.XmlReader.NodeType%2A>, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#12)]
 [!code-vb[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#12)]  
  
 Všimněte si, abyste si přečetli atributů na tento element obálky, před blokováním čtenáře `ReadObject`.  
  
 Při použití jednu jednoduchý `ReadObject` přetížení, deserializátor hledá výchozí název a oboru názvů na element obálky (viz předchozí části "Určení the výchozí kořenový název a Namespace") a vyvolá výjimku, pokud najde neznámé element. V předchozím příkladu `<Person>` je očekáván element obálku. <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> Metoda je volána k ověření, zda čtečka je umístěn na element, který je pojmenován podle očekávání.  
  
 Existuje způsob, jak zakázat tuto obálku element název kontrolu; Některé přetížení `ReadObject` metoda trvat logického parametru `verifyObjectName`, který je nastaven na `true` ve výchozím nastavení. Pokud nastavíte hodnotu `false`, názvem a oborem názvů elementu obálky je ignorován. To je užitečné pro čtení dat XML, která byla zapsána pomocí mechanismu serializace podrobné popsané.  
  
## <a name="using-the-netdatacontractserializer"></a>Pomocí NetDataContractSerializer  
 Hlavní rozdíl mezi `DataContractSerializer` a <xref:System.Runtime.Serialization.NetDataContractSerializer> je, že `DataContractSerializer` používá názvy kontraktu dat, zatímco `NetDataContractSerializer` výstupy úplné [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] názvy sestavení a typ v serializovaných XML. To znamená, že přesně stejné typy musí být sdílená mezi koncovými body serializace a deserializace. To znamená, že mechanismus známé typy není to nutné `NetDataContractSerializer` vzhledem k tomu, že jsou vždy známé přesný typy, které mají být deserializovat.  
  
 Mohou však nastat několik problémy:  
  
-   Zabezpečení. Načtení libovolného typu nalezen v kódu XML deserializován. To může zneužít k vynucení načítání škodlivý typy. Pomocí `NetDataContractSerializer` s nedůvěryhodných dat by mělo být provedeno pouze v případě *vazače serializace* slouží (pomocí <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> parametr vlastností nebo konstruktor). Vazač povoluje pouze bezpečné typy načíst. Mechanismus vazač je stejný jako ten, který typy, které do <xref:System.Runtime.Serialization> oboru názvů používají.  
  
-   Správa verzí. Pomocí úplné názvy typů a sestavení v souboru XML vážně omezuje, jak může být typy verzí. Nelze změnit následující: Zadejte názvy, obory názvů, názvy sestavení a verze sestavení. Nastavení <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> vlastnost nebo konstruktor parametr <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple> místo výchozí hodnotu <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Full> umožňuje změny verze sestavení, ale ne pro obecný parametr typy.  
  
-   Vzájemná funkční spolupráce. Protože [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] názvy typu a sestavení jsou zahrnuty v souboru XML, platformy jiné než [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nelze získat přístup k datům výsledné.  
  
-   Výkon. Zápis se typ a sestavení názvy výrazně zvyšuje velikost výsledný soubor XML.  
  
 Tento mechanismus lze přirovnat k binárnímu souboru nebo protokolu SOAP serializace používané [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] vzdálené komunikace (konkrétně <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>).  
  
 Pomocí `NetDataContractSerializer` je podobný používání `DataContractSerializer`, s následující rozdíly:  
  
-   Konstruktory nevyžadují zadejte typ kořenového. Může serializovat všech typů stejnou instanci systému `NetDataContractSerializer`.  
  
-   Konstruktory nepřijímají seznam známé typy. Známé typy mechanismus není nutný, pokud jsou názvy typů serializován do souboru XML.  
  
-   Konstruktory nepřijímají náhradní kontraktu data. Místo toho přijmou <xref:System.Runtime.Serialization.ISurrogateSelector> parametr s názvem `surrogateSelector` (která se mapuje <xref:System.Runtime.Serialization.NetDataContractSerializer.SurrogateSelector%2A> vlastnost). Toto je starší verze náhradní mechanismus.  
  
-   Konstruktory přijmout parametr s názvem `assemblyFormat` z <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> která se mapuje <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> vlastnost. Jak je popsáno dříve, to slouží k vylepšení možností správy verzí serializátor. Toto je stejný jako <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> mechanismus v binárním nebo SOAP serializace.  
  
-   Přijměte konstruktorů <xref:System.Runtime.Serialization.StreamingContext> parametr s názvem `context` která se mapuje <xref:System.Runtime.Serialization.NetDataContractSerializer.Context%2A> vlastnost. Můžete použít k předání informací do typy serializována. Toto použití je shodná s <xref:System.Runtime.Serialization.StreamingContext> mechanismus používaný v jiných <xref:System.Runtime.Serialization> třídy.  
  
-   <xref:System.Runtime.Serialization.NetDataContractSerializer.Serialize%2A> a <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize%2A> metody jsou aliasy pro <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> a <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> metody. Tyto existovat více konzistentní programovací model poskytnout binární nebo SOAP serializace.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Tyto funkce, najdete v části [binární serializace](../../../../docs/standard/serialization/binary-serialization.md).  
  
 Formáty XML, který `NetDataContractSerializer` a `DataContractSerializer` použití obvykle nejsou kompatibilní. To znamená pokus o s jedním z těchto serializátorů serializaci a deserializaci k ostatním není podporováno.  
  
 Rovněž Pamatujte, že `NetDataContractSerializer` výstup není kompletní [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ a název sestavení pro každý uzel v grafu objektů. Vyprodukuje tyto informace jenom tam, kde je nejednoznačný. To znamená výstupy na kořenové úrovni objekt a všechny polymorfní případech.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 <xref:System.Runtime.Serialization.NetDataContractSerializer>  
 <xref:System.Runtime.Serialization.XmlObjectSerializer>  
 [Binární serializace](../../../../docs/standard/serialization/binary-serialization.md)  
 [Typy podporované serializátorem kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)

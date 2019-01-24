---
title: Serializace a deserializace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3d71814c-bda7-424b-85b7-15084ff9377a
ms.openlocfilehash: 7ddad36c05d9972b9fc613403b68b7c793b6701d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54707569"
---
# <a name="serialization-and-deserialization"></a>Serializace a deserializace
Windows Communication Foundation (WCF) zahrnuje Serializační stroj, <xref:System.Runtime.Serialization.DataContractSerializer>. <xref:System.Runtime.Serialization.DataContractSerializer> Překládá [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objekty a XML v obou směrech. Toto téma vysvětluje, jak funguje serializátor.  
  
 Při serializaci [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] objekty, serializátor rozumí širokou škálu serializace programovacích modelů, včetně nového *kontraktu dat* modelu. Úplný seznam podporovaných typů najdete v tématu [typy podporované serializátorem kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Úvodní informace o kontraktech dat najdete v tématu [kontraktů dat pomocí](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Při deserializaci XML používá serializátor <xref:System.Xml.XmlReader> a <xref:System.Xml.XmlWriter> třídy. Podporuje také <xref:System.Xml.XmlDictionaryReader> a <xref:System.Xml.XmlDictionaryWriter> třídy, který umožňuje vytvářet optimalizované v některých případech, například když binární formát XML WCF pomocí formátu XML.  
  
 WCF obsahuje také doprovodné serializátor, <xref:System.Runtime.Serialization.NetDataContractSerializer>. <xref:System.Runtime.Serialization.NetDataContractSerializer> Je podobný <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> serializátory protože také vydává [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] názvy typů součástí serializovaná data. Používá se při stejné typy jsou sdíleny v serializaci a deserializaci skončí. Jak <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer> odvozen od běžné základní třídy <xref:System.Runtime.Serialization.XmlObjectSerializer>.  
  
> [!WARNING]
>  <xref:System.Runtime.Serialization.DataContractSerializer> Serializuje řetězce obsahující ovládací prvek znaků šestnáctkové hodnotu nižší než 20 jako entity XML. To může způsobit problém s klienta bez WCF při odesílání těchto dat na službu WCF.  
  
## <a name="creating-a-datacontractserializer-instance"></a>Vytvoření Instance třídy DataContractSerializer  
 Vytváření instance <xref:System.Runtime.Serialization.DataContractSerializer> je důležitý krok. Po vytvoření nelze změnit některé z nastavení.  
  
### <a name="specifying-the-root-type"></a>Určení typu kořenové  
 *Kořenový typ* je typ, z nichž jsou instance serializován nebo deserializován. <xref:System.Runtime.Serialization.DataContractSerializer> Má mnoho přetížení konstruktoru, ale minimálně kořenový typ je nutné zadat pomocí `type` parametru.  
  
 Označuje, že serializátor vytvořené pro určitý typ kořenového nelze použít k serializaci (nebo deserializaci) jiný typ, pokud typ je odvozen z typu root. Následující příklad ukazuje dvě třídy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#1)]
 [!code-vb[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#1)]  
  
 Tento kód vytvoří instanci objektu `DataContractSerializer` , který lze použít pouze k serializaci nebo deserializaci instance `Person` třídy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#2)]
 [!code-vb[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#2)]  
  
### <a name="specifying-known-types"></a>Určení známé typy  
 Pokud Polymorfismus je součástí serializována typy, které už se určují pomocí šablon <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut nebo některé mechanismus, musí být předán seznam možných známé typy konstruktoru serializátoru, který pomocí `knownTypes` parametru. Další informace o známých typů najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 Následující příklad ukazuje třídu `LibraryPatron`, který obsahuje kolekci určitého typu, `LibraryItem`. Druhá třída definuje `LibraryItem` typu. Třetí a čtyři třídy (`Book` a `Newspaper`) dědí `LibraryItem` třídy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#3)]  
 [!code-vb[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#3)]  
  
 Následující kód vytvoří instanci objektu serializátor pomocí `knownTypes` parametru.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#4)]
 [!code-vb[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#4)]  
  
### <a name="specifying-the-default-root-name-and-namespace"></a>Určení výchozí název kořenového adresáře a Namespace  
 Obvykle když je objekt serializován, výchozí název a obor názvů vnějšího elementu XML se stanoví podle toho, názvem kontraktu dat a obor názvů. Názvy všech vnitřní elementy se stanoví z názvů členů dat a jejich obor názvů je obor názvů kontraktu dat. Následující příklad nastaví `Name` a `Namespace` hodnoty v konstruktory <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> třídy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#5)]
 [!code-vb[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#5)]  
  
 Serializaci instancí `Person` třídy vytváří XML podobný následujícímu.  
  
```xml  
<PersonContract xmlns="http://schemas.contoso.com">  
  <AddressMember>  
    <StreetMember>123 Main Street</StreetMember>  
   </AddressMember>  
</PersonContract>  
```  
  
 Předáním hodnoty však můžete přizpůsobit výchozí název a obor názvů kořenového elementu `rootName` a `rootNamespace` parametrů <xref:System.Runtime.Serialization.DataContractSerializer> konstruktoru. Všimněte si, `rootNamespace` nemá vliv na obor názvů jeho prvky, které odpovídají na datové členy. Ovlivňuje pouze obor názvů vnějšího elementu.  
  
 Tyto hodnoty lze předat jako řetězce nebo instance <xref:System.Xml.XmlDictionaryString> třídu, která umožňuje jejich optimalizace v binárním formátu XML.  
  
### <a name="setting-the-maximum-objects-quota"></a>Nastavení kvóty maximální objektů  
 Některé `DataContractSerializer` mají přetížení konstruktoru `maxItemsInObjectGraph` parametru. Tento parametr určuje maximální počet objektů serializátoru, který serializuje a deserializuje v jediném <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> volání metody. (Metoda čte vždy jeden kořenový objekt, ale tento objekt může mít jiné objekty v její datové členy. Tyto objekty mohou mít jiné objekty atd.) Výchozí hodnota je 65536. Všimněte si, že při serializaci nebo deserializaci pole, každá položka pole se počítá jako samostatný objekt. Všimněte si také, že některé objekty možná reprezentace velké paměti a proto nemusí být tato kvóta na samotný dostatečné k zabránění útoku DOS. Další informace najdete v tématu [aspekty zabezpečení pro Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Pokud potřebujete tuto kvótu nad výchozí hodnotu zvýšit, je potřeba udělat i odeslání (serializace) a obdrželi strany (deserializaci), protože se vztahuje na oba při čtení a zápis dat.  
  
### <a name="round-trips"></a>Výměny zpráv  
 A *odezvy* nastane, pokud je objekt deserializován a znovu serializovat v rámci jedné operace. Proto se ukládá ze souboru XML na instanci objektu a zpět znovu do datový proud XML.  
  
 Některé `DataContractSerializer` mají přetížení konstruktoru `ignoreExtensionDataObject` parametr, který je nastaven na `false` ve výchozím nastavení. V tomto režimu výchozí odesláním dat na dobu odezvy z novější verze kontraktu dat prostřednictvím starší verze a zpět na novější verzi, bez ztráty, tak dlouho, dokud kontraktu dat implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní. Předpokládejme například, verze 1 `Person` obsahuje kontrakt dat `Name` a `PhoneNumber` datové členy a verze 2 přidá `Nickname` člen. Pokud `IExtensibleDataObject` je implementováno, při odesílání informací z verze 2 verze 1, `Nickname` data uložená a pak znovu emitovány při serializuje data znovu; proto je ztracena žádná data v doby odezvy. Další informace najdete v tématu [kontraktů dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) a [Správa verzí kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).  
  
#### <a name="security-and-schema-validity-concerns-with-round-trips"></a>Zabezpečení a aspekty platnosti schématu s výměny zpráv  
 Má zpáteční převod může mít vliv na zabezpečení. Ohrožení zabezpečení může být například deserializaci a ukládání velkých objemů nadbytečná data. Můžou existovat zabezpečením o opětovné generování těchto dat, že neexistuje žádný způsob, jak ověřit, zejména v případě, že se podílejí digitální podpisy. Například v předchozím scénáři může být podepisování koncový bod verze 1 `Nickname` hodnotu, která obsahuje škodlivá data. A konečně, můžou existovat obavy platnosti schématu: koncový bod může být vhodné vždy generovat data, která dodržuje výhradně její uvedené smlouvy a ne všechny dodatečné hodnoty. V předchozím příkladu kontraktu koncového bodu verze 1 říká, že vydává pouze `Name` a `PhoneNumber`a pokud se používá ověřování schématu, generování nadbytečné `Nickname` hodnotu způsobí selhání ověření.  
  
#### <a name="enabling-and-disabling-round-trips"></a>Povolení a zakázání výměny zpráv  
 Chcete-li vypnout výměny zpráv, Neimplementujte <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní. Pokud nemáte žádnou kontrolu nad tím, typy, nastavte `ignoreExtensionDataObject` parametr `true` k dosažení stejného výsledku.  
  
### <a name="object-graph-preservation"></a>Zachování grafu objektu  
 Za normálních okolností serializátor nezáleží na identity objektu, stejně jako v následujícím kódu.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#6)]
 [!code-vb[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#6)]  
  
 Následující kód vytvoří nákupní objednávky.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#7)]
 [!code-vb[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#7)]  
  
 Všimněte si, že `billTo` a `shipTo` se nastaví na stejnou instanci objektu. Vygenerovaný kód XML, ale duplikuje informace duplicitní a vypadá podobně jako následující kód XML.  
  
```xml  
<PurchaseOrder>  
  <billTo><street>123 Main St.</street></billTo>  
  <shipTo><street>123 Main St.</street></shipTo>  
</PurchaseOrder>  
```  
  
 Tento přístup však má následující vlastnosti, které mohou nežádoucí:  
  
-   Výkon. Replikace dat je neefektivní.  
  
-   Cyklické odkazy. Pokud objekty odkazují na sebe, klidně i prostřednictvím jiné objekty, serializaci pomocí replikace má za následek nekonečnou smyčku. (Serializátoru, který vyvolá <xref:System.Runtime.Serialization.SerializationException> v této situaci.)  
  
-   Sémantika. Někdy je důležité zachovat skutečnost, že jsou dva odkazy na stejný objekt a ne na dva objekty stejné.  
  
 Z těchto důvodů, některé `DataContractSerializer` mají přetížení konstruktoru `preserveObjectReferences` parametr (výchozí hodnota je `false`). Pokud tento parametr je nastaven na `true`, zvláštní metodu kódování odkazy na objekty, které rozumí pouze WCF, je použít. Pokud je nastavena na `true`, příklad kódu XML teď vypadá podobně jako následující.  
  
```xml  
<PurchaseOrder ser:id="1">  
  <billTo ser:id="2"><street ser:id="3">123 Main St.</street></billTo>  
  <shipTo ser:ref="2"/>  
</PurchaseOrder>  
```  
  
 Obor názvů "ser" odkazuje na obor názvů standard serializace, `http://schemas.microsoft.com/2003/10/Serialization/`. Každá část dat je serializovat pouze jednou a zadané identifikační číslo, a následné používá výsledek v odkazu na již serializovaná data.  
  
> [!IMPORTANT]
>  Pokud jsou k dispozici v kontraktu dat "id" a "ref" atributy `XMLElement`, neuplatňují atribut "ref" a atribut "id" je ignorován.  
  
 Je důležité pochopit, omezení pro tento režim:  
  
-   XML `DataContractSerializer` vytvoří s `preserveObjectReferences` nastavena na `true` není vzájemná spolupráce s dalšími technologiemi a je přístupný pouze jiným `DataContractSerializer` instance, také s `preserveObjectReferences` nastavena na `true`.  
  
-   Není dostupná podpora metadat (schéma) pro tuto funkci. Je platný jenom pro případ schématu, který je vytvořen při `preserveObjectReferences` je nastavena na `false`.  
  
-   Tato funkce může způsobit procesu serializace a deserializace poběží pomaleji. I když se data nemusí být replikována, je nutné provést porovnání další objekt v tomto režimu.  
  
> [!CAUTION]
>  Při `preserveObjectReferences` je povolený režim, je velmi důležité nastavit `maxItemsInObjectGraph` hodnota, která má správný kvóty. Z důvodu způsob zpracování pole v tomto režimu, je to jednoduché útočník k vytvoření malé škodlivý zprávu, která má za následek velký paměťové nároky omezena pouze `maxItemsInObjectGraph` kvóty.  
  
### <a name="specifying-a-data-contract-surrogate"></a>Určení náhrady kontraktů dat  
 Některé `DataContractSerializer` mají přetížení konstruktoru `dataContractSurrogate` parametr, který může být nastavená na `null`. V opačném případě můžete použít k určení *náhrada kontraktu dat*, což je typ, který implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate> rozhraní. Pak můžete použít rozhraní k přizpůsobení serializaci a deserializaci procesu. Další informace najdete v tématu [náhrady kontraktů dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
## <a name="serialization"></a>Serializace  
 Následující informace platí pro všechny třídy, která dědí z <xref:System.Runtime.Serialization.XmlObjectSerializer>, včetně <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer> třídy.  
  
### <a name="simple-serialization"></a>Jednoduché serializace  
 Nejzákladnější možnost k serializaci objektu je předat ji <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> metody. Existují tři přetížení, jeden pro zápis do <xref:System.IO.Stream>, <xref:System.Xml.XmlWriter>, nebo <xref:System.Xml.XmlDictionaryWriter>. S <xref:System.IO.Stream> přetížení, výstup je XML v kódování UTF-8. S <xref:System.Xml.XmlDictionaryWriter> přetížení, serializátoru, který optimalizuje jeho výstup pro binární formát XML.  
  
 Při použití <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> metoda serializátoru, který používá výchozí název a obor názvů pro element obálky a zapíše spolu s obsahem (viz předchozí části "Určení the výchozí kořenový název a Namespace").  
  
 Následující příklad ukazuje zápis s <xref:System.Xml.XmlDictionaryWriter>.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#8)]
 [!code-vb[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#8)]  
  
 Tímto se vytvoří XML podobný následujícímu.  
  
```xml  
<Person>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
### <a name="step-by-step-serialization"></a>Krok za krokem serializace  
 Použití <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A>, <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A>, a <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> metody zapsat elementu end, zapsat obsah objektu a zavření element obálky, v uvedeném pořadí.  
  
> [!NOTE]
>  Neexistují žádné <xref:System.IO.Stream> přetížení z těchto metod.  
  
 Tento krok za krokem serializace má dvě běžné použití. Vložit obsah, jako jsou atributy, je nejméně komentáře mezi `WriteStartObject` a `WriteObjectContent`, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#9)]
 [!code-vb[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#9)]  
  
 Tímto se vytvoří XML podobný následujícímu.  
  
```xml  
<Person serializedBy="myCode">  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
 Dalším běžným způsobem použití je vyhýbat se použití <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> a <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> zcela a chcete napsat vlastní element vlastní obálky (nebo i Přeskočit zápis obálku úplně), jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#10)]
 [!code-vb[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#10)]  
  
 Tímto se vytvoří XML podobný následujícímu.  
  
```xml  
<MyCustomWrapper>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</MyCustomWrapper>  
```  
  
> [!NOTE]
>  Pomocí podrobné serializace může mít za následek neplatné schéma XML.  
  
## <a name="deserialization"></a>Deserializace  
 Následující informace platí pro všechny třídy, která dědí z <xref:System.Runtime.Serialization.XmlObjectSerializer>, včetně <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Runtime.Serialization.NetDataContractSerializer> třídy.  
  
 Nejzákladnější možnost pro rekonstrukci objektu je volání jednoho z <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> přetížení metody. Existují tři přetížení, jeden pro čtení s <xref:System.Xml.XmlDictionaryReader>, `XmlReader`, nebo `Stream`. Všimněte si, že `Stream` přetížení vytvoří textové <xref:System.Xml.XmlDictionaryReader> , který není chráněn aplikací žádné kvóty a slouží pouze ke čtení důvěryhodná data.  
  
 Všimněte si také, že objekt `ReadObject` vrátí metoda musí být přetypovat na typ odpovídající.  
  
 Následující kód vytvoří instanci objektu <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.XmlDictionaryReader>, pak deserializuje `Person` instance.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#11)]
 [!code-vb[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#11)]  
  
 Před voláním <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> metodu, umístěte čtecí funkce XML na element obálky nebo na uzel není obsah, který předchází element obálky. Toto lze provést zavoláním <xref:System.Xml.XmlReader.Read%2A> metodu <xref:System.Xml.XmlReader> nebo jeho odvození a testování <xref:System.Xml.XmlReader.NodeType%2A>, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#12)]
 [!code-vb[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#12)]  
  
 Mějte na paměti, abyste si přečetli atributy na tento element obálky, ještě před čtenáře `ReadObject`.  
  
 Při použití jednoho jednoduchého `ReadObject` přetížení, deserializátor hledá výchozí název a obor názvů na element obálky (viz předchozí části "Určení the výchozí kořenový název a Namespace") a vyvolá výjimku, pokud najde neznámé element. V předchozím příkladu `<Person>` je očekáván element obálky. <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> Metoda je volána k ověření, že čtečky je umístěna na elementu, který je pojmenován podle očekávání.  
  
 Existuje způsob, jak tuto kontrolu název prvku obálky; některá přetížení `ReadObject` metoda přijímat logický parametr `verifyObjectName`, který je nastaven na `true` ve výchozím nastavení. Pokud je nastavena na `false`, název a obor názvů elementu obálky se ignoruje. To je užitečné pro čtení XML, který byl napsané s využitím podrobných serializace mechanismus je popsáno výše.  
  
## <a name="using-the-netdatacontractserializer"></a>Použití NetDataContractSerializer  
 Hlavní rozdíl mezi `DataContractSerializer` a <xref:System.Runtime.Serialization.NetDataContractSerializer> je, že `DataContractSerializer` používá názvy datových kontraktů, zatímco `NetDataContractSerializer` výstupy úplné [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] názvy sestavení a typu v serializovaném kódu XML. To znamená, že přesně stejné typy musí být sdílená mezi koncovými body serializace a deserializace. To znamená, že mechanismus známých typů není požadován spolu s `NetDataContractSerializer` protože jsou vždy známé přesné typy k deserializaci.  
  
 Však může dojít k několika problémům:  
  
-   Zabezpečení. Jakýkoli typ nalezen v souboru XML, který se deserializuje načtení. To je někdo zneužije vynutit načtení škodlivých typy. Pomocí `NetDataContractSerializer` s nedůvěryhodné dat by mělo být provedeno pouze v případě *vazač serializace* se používá (pomocí <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> parametr vlastnosti nebo konstruktoru). Vazače umožňuje pouze bezpečné typy, který se má načíst. Vazač mechanismus je stejný jako ten, který zadá <xref:System.Runtime.Serialization> použití oboru názvů.  
  
-   Správa verzí. Pomocí úplné názvy dnů v typ a sestavení v souboru XML vážně omezuje typy jak mohou být označené verzí. Nedá se změnit následující: Zadejte názvy, obory názvů, názvy sestavení a verze sestavení. Nastavení <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> vlastnost nebo konstruktor parametr <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple> místo výchozí hodnotu <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Full> umožňuje změny verze sestavení, ale ne pro obecné typy parametrů.  
  
-   Vzájemná funkční spolupráce. Protože [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] názvy typ a sestavení jsou zahrnuty v XML platformách jiných než [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] nedaří Výsledná data.  
  
-   Výkon. Zápis typ a sestavení názvy významně zvyšuje velikost výsledného kódu XML.  
  
 Tento mechanismus je podobné jako binární a SOAP serializace používané [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] vzdálené komunikace (konkrétně <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>).  
  
 Použití `NetDataContractSerializer` podobá se to používání `DataContractSerializer`, s těmito rozdíly:  
  
-   Konstruktory nevyžadují určení kořenové typu. Může serializovat libovolný typ se stejnou instanci `NetDataContractSerializer`.  
  
-   Konstruktory nepřijímají seznamu známých typů. Mechanismus známých typů není nutný, pokud jsou názvy typů serializován do souboru XML.  
  
-   Konstruktory nepřijímají náhrada kontraktu dat. Místo toho přijetí <xref:System.Runtime.Serialization.ISurrogateSelector> parametr s názvem `surrogateSelector` (která se mapuje <xref:System.Runtime.Serialization.NetDataContractSerializer.SurrogateSelector%2A> vlastnost). Toto je starší verze náhradní mechanismus.  
  
-   Konstruktory přijímají parametr s názvem `assemblyFormat` z <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> , která se mapuje <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> vlastnost. Jak je popsáno výše, to umožňuje rozšíření správy verzí možností serializátoru. To je stejný jako <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> mechanismus v binárním souboru nebo protokolu SOAP serializace.  
  
-   Konstruktory přijímají <xref:System.Runtime.Serialization.StreamingContext> parametr s názvem `context` , který mapuje <xref:System.Runtime.Serialization.NetDataContractSerializer.Context%2A> vlastnost. To slouží k předávání informací do typů serializována. Toto použití je shodná s <xref:System.Runtime.Serialization.StreamingContext> mechanismus použít v ostatních <xref:System.Runtime.Serialization> třídy.  
  
-   <xref:System.Runtime.Serialization.NetDataContractSerializer.Serialize%2A> a <xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize%2A> metody jsou zástupci pro <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> a <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> metody. Existují zajistit konzistentní programovací model s binárním souboru nebo protokolu SOAP serializace.  
  
 Další informace o těchto funkcích najdete v tématu [binární serializace](../../../../docs/standard/serialization/binary-serialization.md).  
  
 Formáty XML, který `NetDataContractSerializer` a `DataContractSerializer` použití jsou obvykle nejsou kompatibilní. To znamená pokus o s jedním z těchto serializátory serializaci a deserializaci k ostatním není podporovaný scénář.  
  
 Všimněte si také, že `NetDataContractSerializer` není výstup kompletní [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] typ a název sestavení pro každý uzel v grafu objektů. Tyto informace, jenom Pokud je nejednoznačný výstupu. To znamená výstupy na kořenové úrovni objekt a pro polymorfní případy.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.NetDataContractSerializer>
- <xref:System.Runtime.Serialization.XmlObjectSerializer>
- [Binární serializace](../../../../docs/standard/serialization/binary-serialization.md)
- [Typy podporované serializátorem kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)

---
title: Serializace a deserializace
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3d71814c-bda7-424b-85b7-15084ff9377a
ms.openlocfilehash: a6bbc2fe4bf68b50153075a251d23deebda78de5
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988658"
---
# <a name="serialization-and-deserialization"></a>Serializace a deserializace
Windows Communication Foundation (WCF) obsahuje nový modul serializace, <xref:System.Runtime.Serialization.DataContractSerializer>. <xref:System.Runtime.Serialization.DataContractSerializer> Překládá mezi objekty .NET Framework a XML v obou směrech. Toto téma vysvětluje, jak serializátor funguje.  
  
 Při serializaci .NET Framework objektů, serializátor rozumí celé řadě programovacích modelů serializace, včetně nového modelu *kontraktu dat* . Úplný seznam podporovaných typů najdete v tématu [typy podporované serializátorem kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md). Úvod do kontraktů dat najdete v tématu [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md).  
  
 Při deserializaci kódu XML serializátor používá <xref:System.Xml.XmlReader> třídy a. <xref:System.Xml.XmlWriter> Podporuje <xref:System.Xml.XmlDictionaryReader> také třídy a <xref:System.Xml.XmlDictionaryWriter> , které jim umožňují vydávat optimalizované XML v některých případech, například při použití binárního formátu XML služby WCF.  
  
 WCF zahrnuje i doprovodný serializátor <xref:System.Runtime.Serialization.NetDataContractSerializer>. Rozhraní <xref:System.Runtime.Serialization.NetDataContractSerializer> je podobné <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> serializátorům a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> , protože také generuje .NET Framework názvy typů jako součást serializovaných dat. Používá se, pokud jsou stejné typy sdíleny na serializaci a na konci serializace. A jsou odvozeny od <xref:System.Runtime.Serialization.XmlObjectSerializer>společné základní třídy,. <xref:System.Runtime.Serialization.NetDataContractSerializer> <xref:System.Runtime.Serialization.DataContractSerializer>  
  
> [!WARNING]
> <xref:System.Runtime.Serialization.DataContractSerializer> Serializovat řetězce obsahující řídicí znaky s hexadecimální hodnotou nižší než 20 jako entity XML. To může způsobit problém s klientem jiného typu než WCF při odesílání takových dat službě WCF.  
  
## <a name="creating-a-datacontractserializer-instance"></a>Vytvoření instance DataContractSerializer  
 Vytvoření instance <xref:System.Runtime.Serialization.DataContractSerializer> je důležitým krokem. Po dokončení konstrukce nemůžete změnit žádné nastavení.  
  
### <a name="specifying-the-root-type"></a>Zadání kořenového typu  
 *Kořenový typ* je typ, který instance jsou serializovány nebo deserializovány. Má mnoho přetížení konstruktoru, ale alespoň kořenový typ musí být dodán `type` pomocí parametru. <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 Serializátor vytvořený pro určitý kořenový typ nelze použít k serializaci (nebo deserializaci) jiného typu, pokud typ není odvozen z kořenového typu. Následující příklad ukazuje dvě třídy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#1)]
 [!code-vb[c_StandaloneDataContractSerializer#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#1)]  
  
 Tento kód vytvoří instanci `DataContractSerializer` `Person` třídy, kterou lze použít pouze k serializaci nebo deserializaci instancí třídy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#2)]
 [!code-vb[c_StandaloneDataContractSerializer#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#2)]  
  
### <a name="specifying-known-types"></a>Určení známých typů  
 Pokud jsou polymorfismus zapojeny do serializovaných typů, které již nejsou zpracovávány pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute> atributu nebo nějakého jiného mechanismu, je nutné předat do konstruktoru serializátoru `knownTypes` pomocí parametru seznam možných známých typů. Další informace o známých typů najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md).  
  
 Následující příklad ukazuje třídu, `LibraryPatron`, která obsahuje kolekci konkrétního typu `LibraryItem`,. Druhá třída definuje `LibraryItem` typ. Třetí a čtyři třídy (`Book` a `Newspaper`) dědí z `LibraryItem` třídy.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#3)]  
 [!code-vb[c_StandaloneDataContractSerializer#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#3)]  
  
 Následující kód vytvoří instanci serializátoru pomocí `knownTypes` parametru.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#4)]
 [!code-vb[c_StandaloneDataContractSerializer#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#4)]  
  
### <a name="specifying-the-default-root-name-and-namespace"></a>Určení výchozího kořenového názvu a oboru názvů  
 Obvykle při serializaci objektu je výchozí název a obor názvů nejvzdálenějšího elementu XML určen podle názvu a oboru názvů kontraktu dat. Názvy všech vnitřních prvků jsou určeny z názvů datových členů a jejich obor názvů je obor názvů kontraktu dat. Následující příklad nastaví `Name` a `Namespace` hodnoty v konstruktorech <xref:System.Runtime.Serialization.DataContractAttribute> tříd a <xref:System.Runtime.Serialization.DataMemberAttribute> .  
  
 [!code-csharp[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#5)]
 [!code-vb[c_StandaloneDataContractSerializer#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#5)]  
  
 Serializace instance `Person` třídy vytvoří jazyk XML podobný následujícímu.  
  
```xml  
<PersonContract xmlns="http://schemas.contoso.com">  
  <AddressMember>  
    <StreetMember>123 Main Street</StreetMember>  
   </AddressMember>  
</PersonContract>  
```  
  
 Můžete však přizpůsobit výchozí název a obor názvů kořenového prvku předáním hodnot `rootName` parametrů a `rootNamespace` do <xref:System.Runtime.Serialization.DataContractSerializer> konstruktoru. Všimněte si, `rootNamespace` že nemá vliv na obor názvů obsažených prvků, které odpovídají datovým členům. Má vliv pouze na obor názvů nejvzdálenějšího prvku.  
  
 Tyto hodnoty mohou být předány jako řetězce nebo instance <xref:System.Xml.XmlDictionaryString> třídy, aby bylo možné jejich optimalizaci použít v binárním formátu XML.  
  
### <a name="setting-the-maximum-objects-quota"></a>Nastavení maximální kvóty objektů  
 Některá `DataContractSerializer` přetížení konstruktoru `maxItemsInObjectGraph` mají parametr. Tento parametr určuje maximální počet objektů, které serializátor serializace nebo deserializace v rámci jediného <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> volání metody. (Metoda vždy přečte jeden kořenový objekt, ale tento objekt může mít v datových členech jiné objekty. Tyto objekty mohou mít jiné objekty atd.) Výchozí hodnota je 65536. Všimněte si, že při serializaci nebo deserializaci polí se všechny položky pole počítají jako samostatný objekt. Všimněte si také, že některé objekty můžou mít velké množství paměti, takže tato kvóta nemusí být dostačující k tomu, aby se zabránilo útokům DOS (Denial of Service). Další informace najdete v tématu věnovaném [bezpečnostním hlediskům pro data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md). Pokud potřebujete zvýšit tuto kvótu nad rámec výchozí hodnoty, je důležité tak učinit jak na straně odesílajícího (serializace), tak na příjmu (deserializaci), protože platí pro při čtení a zápisu dat.  
  
### <a name="round-trips"></a>Výměna cest  
 K *kruhovému přenosu* dojde v případě deserializace objektu a jeho opětovné serializace v jedné operaci. Proto přechází z formátu XML do instance objektu a zpět do datového proudu XML.  
  
 Některá `DataContractSerializer` přetížení konstruktoru `ignoreExtensionDataObject` mají parametr, který je ve výchozím nastavení nastaven na `false` hodnotu. V tomto výchozím režimu lze data odesílat z novější verze kontraktu dat prostřednictvím starší verze a zpět na novější verzi bez ztráty, pokud kontrakt dat implementuje <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní. Předpokládejme například, `Person` že verze 1 kontraktu dat `Name` obsahuje `Nickname` datové členy a `PhoneNumber` a verze 2 přidá člena. Pokud `IExtensibleDataObject` je implementována při odesílání informací z verze 2 na verzi 1 `Nickname` , jsou data uložena a poté znovu vygenerována, když jsou data znovu serializována; proto během odezvy se neztratí žádná data. Další informace najdete v tématu [kontrakty dat kompatibilní](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md) s dopředné a [verze kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-versioning.md).  
  
#### <a name="security-and-schema-validity-concerns-with-round-trips"></a>Otázky týkající se platnosti zabezpečení a schématu u zpátečních cest  
 Zpáteční cesty můžou mít vliv na zabezpečení. Například deserializace a ukládání velkých objemů nadbytečná data může představovat bezpečnostní riziko. Může dojít k potížím se zabezpečením při opětovném generování těchto dat, což neexistuje způsob, jak je ověřit, zejména pokud se jedná o digitální podpisy. Například v předchozím scénáři může koncový bod verze 1 podepsat `Nickname` hodnotu, která obsahuje škodlivá data. V některých případech se může jednat o platnosti schématu: koncový bod může chtít vždycky vygenerovat data, která striktně vyhovují příslušné uvedené smlouvě, a ne žádné další hodnoty. V předchozím příkladu kontrakt koncového bodu verze 1 říká, že posílá pouze `Name` a `PhoneNumber`a pokud se používá ověřování schématu, vygenerování nadbytečné `Nickname` hodnoty způsobí, že se ověření nezdaří.  
  
#### <a name="enabling-and-disabling-round-trips"></a>Povolení a zakázání zpátečních cest  
 Pokud chcete vypnout zpáteční cesty, Neimplementujte <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní. Pokud nemáte žádnou kontrolu nad typy, nastavte `ignoreExtensionDataObject` parametr na `true` , aby dosáhl stejného efektu.  
  
### <a name="object-graph-preservation"></a>Zachování grafu objektu  
 V normálním případě serializátor nezáleží na identitě objektu, jak je uvedeno v následujícím kódu.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#6)]
 [!code-vb[c_StandaloneDataContractSerializer#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#6)]  
  
 Následující kód vytvoří nákupní objednávku.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#7)]
 [!code-vb[c_StandaloneDataContractSerializer#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#7)]  
  
 Všimněte si `billTo` , `shipTo` že a pole jsou nastavena na stejnou instanci objektu. Vygenerovaný kód XML však duplicitní informace duplikuje a vypadá podobně jako následující kód XML.  
  
```xml  
<PurchaseOrder>  
  <billTo><street>123 Main St.</street></billTo>  
  <shipTo><street>123 Main St.</street></shipTo>  
</PurchaseOrder>  
```  
  
 Tento přístup ale má následující vlastnosti, které mohou být nežádoucí:  
  
- Předepsané. Replikace dat je neefektivní.  
  
- Cyklické odkazy. Pokud objekty odkazují samy na sebe, dokonce i přes jiné objekty, serializace podle výsledků replikace vede k nekonečné smyčce. (Serializátor vyvolá výjimku, <xref:System.Runtime.Serialization.SerializationException> Pokud k tomu dojde.)  
  
- Sémantiku. Někdy je důležité zachovat fakt, že dva odkazy odkazují na stejný objekt, a ne na dva identické objekty.  
  
 Z těchto důvodů `preserveObjectReferences` mají některá `DataContractSerializer` přetížení konstruktoru parametr (výchozí hodnota je `false`). Pokud je tento parametr nastaven na `true`, je použita speciální metoda kódování odkazů na objekty, který je použit pouze pro WCF. Při nastavení na `true`je příklad kódu XML nyní podobný následujícímu.  
  
```xml  
<PurchaseOrder ser:id="1">  
  <billTo ser:id="2"><street ser:id="3">123 Main St.</street></billTo>  
  <shipTo ser:ref="2"/>  
</PurchaseOrder>  
```  
  
 Obor názvů "ser" odkazuje na standardní obor názvů serializace `http://schemas.microsoft.com/2003/10/Serialization/`,. Každá část dat je serializována pouze jednou a s daným číslem ID a následné použití má za následek odkaz na již serializovaná data.  
  
> [!IMPORTANT]
> V případě, že jsou v kontraktu `XMLElement`dat přítomné atributy ID i "ref", je dodržen atribut "ref" a atribut "ID" se ignoruje.  
  
 Je důležité pochopit omezení tohoto režimu:  
  
- Kód XML, `DataContractSerializer` který `preserveObjectReferences` je nastaven na `true` hodnotu, nelze vzájemně spolupracovat s jinými technologiemi a lze k němu přistupovat pouze jinou `DataContractSerializer` instancí `preserveObjectReferences` , a `true`to i s nastavením na.  
  
- Pro tuto funkci neexistuje žádná podpora metadat (schémat). Vytvořené schéma je platné pouze v případě `preserveObjectReferences` , že je nastavena na. `false`  
  
- Tato funkce může způsobit pomalejší spuštění procesu serializace a deserializace. I když data není nutné replikovat, je nutné v tomto režimu provést zvláštní porovnání objektů.  
  
> [!CAUTION]
>  Když je `maxItemsInObjectGraph` režim povolený, je obzvláště důležité nastavit hodnotu na správnou kvótu. `preserveObjectReferences` Vzhledem k tomu, jak jsou v tomto režimu zpracovávány pole, je snadné vytvořit malou škodlivou zprávu, která má za následek omezenou spotřebu paměti omezenou pouze `maxItemsInObjectGraph` kvótou.  
  
### <a name="specifying-a-data-contract-surrogate"></a>Zadání náhrady pro kontrakt dat  
 Některá `DataContractSerializer` přetížení konstruktoru `dataContractSurrogate` mají parametr, který může být nastaven na `null`hodnotu. V opačném případě můžete použít k zadání *náhrady za kontrakt dat*, což je typ, který implementuje <xref:System.Runtime.Serialization.IDataContractSurrogate> rozhraní. Pak můžete použít rozhraní k přizpůsobení procesu serializace a deserializace. Další informace najdete v tématu [náhrada za kontrakty dat](../../../../docs/framework/wcf/extending/data-contract-surrogates.md).  
  
## <a name="serialization"></a>Serializace  
 Následující informace platí pro jakoukoliv třídu, která dědí z <xref:System.Runtime.Serialization.XmlObjectSerializer>třídy, <xref:System.Runtime.Serialization.DataContractSerializer> včetně tříd a <xref:System.Runtime.Serialization.NetDataContractSerializer> .  
  
### <a name="simple-serialization"></a>Jednoduchá serializace  
 Nejzákladnější způsob serializace objektu je předat <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> metodě. Existují tři přetížení, jedno pro zápis do <xref:System.IO.Stream> <xref:System.Xml.XmlWriter>, nebo <xref:System.Xml.XmlDictionaryWriter>. V případě <xref:System.IO.Stream> přetížení je výstupem XML v kódování UTF-8. <xref:System.Xml.XmlDictionaryWriter> S přetížením serializátor optimalizuje svůj výstup pro binární XML.  
  
 Při použití <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> metody serializátor používá výchozí název a obor názvů pro prvek obálky a zapíše jej společně s obsahem (viz předchozí část určení výchozího kořenového názvu a oboru názvů).  
  
 Následující příklad ukazuje zápis pomocí <xref:System.Xml.XmlDictionaryWriter>.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#8)]
 [!code-vb[c_StandaloneDataContractSerializer#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#8)]  
  
 To vytváří XML podobně jako následující.  
  
```xml  
<Person>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
### <a name="step-by-step-serialization"></a>Krok za krokem serializace  
 Použijte metody <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A>, <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObjectContent%2A> a<xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> pro zápis elementu end, zápis obsahu objektu a zavření prvku obálky, v uvedeném pořadí.  
  
> [!NOTE]
> Nejsou k dispozici žádná <xref:System.IO.Stream> přetížení těchto metod.  
  
 Tato podrobná serializace má dvě společná použití. Jedním z nich je vložení obsahu, jako jsou atributy nebo `WriteStartObject` komentáře `WriteObjectContent`mezi a, jak je znázorněno v následujícím příkladu.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#9)]
 [!code-vb[c_StandaloneDataContractSerializer#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#9)]  
  
 To vytváří XML podobně jako následující.  
  
```xml  
<Person serializedBy="myCode">  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</Person>  
```  
  
 Dalším běžným použitím je vyhnout se <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteStartObject%2A> použití <xref:System.Runtime.Serialization.XmlObjectSerializer.WriteEndObject%2A> a zcela a napsat vlastní prvek obálky (nebo dokonce přepsat obálku zcela), jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#10)]
 [!code-vb[c_StandaloneDataContractSerializer#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#10)]  
  
 To vytváří XML podobně jako následující.  
  
```xml  
<MyCustomWrapper>  
  <Name>Jay Hamlin</Name>  
  <Address>123 Main St.</Address>  
</MyCustomWrapper>  
```  
  
> [!NOTE]
> Použití serializace na základě kroku může vést ke schématu – neplatné XML.  
  
## <a name="deserialization"></a>Deserializace  
 Následující informace platí pro jakoukoliv třídu, která dědí z <xref:System.Runtime.Serialization.XmlObjectSerializer>třídy, <xref:System.Runtime.Serialization.DataContractSerializer> včetně tříd a <xref:System.Runtime.Serialization.NetDataContractSerializer> .  
  
 Nejzákladnější způsob, jak zrušit serializaci objektu, je zavolat jedno z <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> přetížení metody. Existují tři přetížení, jedno pro čtení pomocí <xref:System.Xml.XmlDictionaryReader> `XmlReader`, nebo `Stream`. Všimněte si, `Stream` že přetížení vytvoří text <xref:System.Xml.XmlDictionaryReader> , který není chráněn žádnými kvótami a měl by být použit pouze pro čtení důvěryhodných dat.  
  
 Všimněte si také, že objekt `ReadObject` , který vrací metodu, musí být převedena na příslušný typ.  
  
 Následující kód vytvoří instanci <xref:System.Runtime.Serialization.DataContractSerializer> třídy <xref:System.Xml.XmlDictionaryReader>a a `Person` poté deserializaci instance.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#11)]
 [!code-vb[c_StandaloneDataContractSerializer#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#11)]  
  
 Před voláním <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> metody umístěte čtecí modul XML na prvek obálky nebo na uzel bez obsahu, který předchází prvku obálky. To lze provést voláním <xref:System.Xml.XmlReader.Read%2A> metody <xref:System.Xml.XmlReader> nebo jejího <xref:System.Xml.XmlReader.NodeType%2A>odvození a otestováním, jak je znázorněno v následujícím kódu.  
  
 [!code-csharp[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_standalonedatacontractserializer/cs/source.cs#12)]
 [!code-vb[c_StandaloneDataContractSerializer#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_standalonedatacontractserializer/vb/source.vb#12)]  
  
 Všimněte si, že je možné číst atributy tohoto prvku obálky před tím, než se `ReadObject`čtecí modul dopustí do.  
  
 Při použití jednoho z jednoduchých `ReadObject` přetížení vyhledá deserializátor výchozí název a obor názvů v prvku obálky (viz předchozí oddíl určení výchozího kořenového názvu a oboru názvů ") a vyvolá výjimku, pokud nalezne neznámou hodnotu. objekt. V předchozím příkladu `<Person>` je očekáván prvek obálky. <xref:System.Runtime.Serialization.XmlObjectSerializer.IsStartObject%2A> Metoda je volána k ověření, zda je čtecí modul umístěn na elementu, který je pojmenován podle očekávání.  
  
 Existuje způsob, jak zakázat tuto kontrolu názvu elementu obálky; Některá přetížení `ReadObject` metody přebírají parametr `verifyObjectName`Boolean, který je ve výchozím nastavení nastaven na `true` hodnotu. Při nastavení na `false`je ignorován název a obor názvů prvku obálky. To je užitečné pro čtení XML, které bylo napsáno pomocí podrobného mechanismu serializace popsané výše.  
  
## <a name="using-the-netdatacontractserializer"></a>Použití NetDataContractSerializer  
 Hlavní `DataContractSerializer` rozdíl mezi <xref:System.Runtime.Serialization.NetDataContractSerializer> a je, že `DataContractSerializer` používá názvy kontraktů dat, zatímco `NetDataContractSerializer` výstupy jsou úplné .NET Framework sestavení a názvů typů v serializovaném kódu XML. To znamená, že mezi koncovými body serializace a deserializace musí být sdíleny přesně stejné typy. To znamená, že známý typ mechanismu není vyžadován s, `NetDataContractSerializer` protože přesné typy, které mají být deserializovány, jsou vždy známy.  
  
 Může ale dojít k několika problémům:  
  
- Bezpečnost. Je načten libovolný typ nalezený v souboru XML deserializovat. To lze zneužít k vynucení načítání škodlivých typů. Použití s nedůvěryhodnými daty by mělo být provedeno pouze v případě, že je <xref:System.Runtime.Serialization.NetDataContractSerializer.Binder%2A> použit *pořadač serializace* (pomocí vlastnosti nebo parametru konstruktoru). `NetDataContractSerializer` Pořadač povoluje načtení pouze bezpečných typů. Mechanizmus pořadače je totožný s typem <xref:System.Runtime.Serialization> , který používá obor názvů.  
  
- Správa verzí. Použití úplného typu a názvů sestavení v jazyce XML přísně omezuje způsob, jakým mohou být typy verzí. Následující nelze změnit: názvy typů, obory názvů, názvy sestavení a verze sestavení. Nastavení vlastnosti nebo parametru konstruktoru na <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Simple> místo výchozí hodnoty <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle.Full> umožňuje použít změny verze sestavení, ale ne pro obecné typy parametrů. <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A>  
  
- Vzájemné. Vzhledem k tomu, že .NET Framework typ a názvy sestavení jsou součástí XML, jiné platformy, než je .NET Framework, nemají přístup k výsledným datům.  
  
- Předepsané. Zápis typů a názvů sestavení významně zvyšuje velikost výsledného kódu XML.  
  
 Tento mechanismus je podobný binárnímu souboru nebo serializaci SOAP, kterou používá .NET Framework Vzdálená komunikace <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> (konkrétně <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>, a).  
  
 Použití rozhraní `NetDataContractSerializer` je podobné jako `DataContractSerializer`použití, s následujícími rozdíly:  
  
- Konstruktory nevyžadují zadání kořenového typu. Můžete serializovat libovolný typ se stejnou instancí `NetDataContractSerializer`.  
  
- Konstruktory nepřijímají seznam známých typů. Pokud jsou názvy typů serializovány do XML, je mechanismus známých typů zbytečné.  
  
- Konstruktory neakceptují náhradu kontraktu dat. Místo toho přijmou parametr s <xref:System.Runtime.Serialization.ISurrogateSelector> názvem `surrogateSelector` <xref:System.Runtime.Serialization.NetDataContractSerializer.SurrogateSelector%2A> (který se mapuje na vlastnost). Toto je starší náhradní mechanismus.  
  
- Konstruktory přijímají parametr s názvem `assemblyFormat` <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> , který se mapuje na <xref:System.Runtime.Serialization.NetDataContractSerializer.AssemblyFormat%2A> vlastnost. Jak bylo popsáno dříve, lze použít k vylepšení možností správy verzí serializátoru. Jedná se o stejný <xref:System.Runtime.Serialization.Formatters.FormatterAssemblyStyle> mechanismus jako v binárním souboru nebo v serializaci SOAP.  
  
- Konstruktory přijímají <xref:System.Runtime.Serialization.StreamingContext> parametr s názvem `context` , který se mapuje <xref:System.Runtime.Serialization.NetDataContractSerializer.Context%2A> na vlastnost. Tuto možnost můžete použít k předávání informací do serializovaných typů. Toto použití je shodné <xref:System.Runtime.Serialization.StreamingContext> s mechanismem používaným v jiných <xref:System.Runtime.Serialization> třídách.  
  
- <xref:System.Runtime.Serialization.NetDataContractSerializer.Serialize%2A> Metodya<xref:System.Runtime.Serialization.NetDataContractSerializer.Deserialize%2A> jsou aliasy pro <xref:System.Runtime.Serialization.XmlObjectSerializer.ReadObject%2A> metody a.<xref:System.Runtime.Serialization.XmlObjectSerializer.WriteObject%2A> Existují pro zajištění jednotnějšího programovacího modelu pomocí binárního souboru nebo serializace SOAP.  
  
 Další informace o těchto funkcích naleznete v tématu [binární serializace](../../../standard/serialization/binary-serialization.md).  
  
 Formáty XML, které jsou `NetDataContractSerializer` `DataContractSerializer` a používají obvykle, nejsou kompatibilní. To znamená, že při pokusu o serializaci jedním z těchto serializátorů a deserializace u druhého není podporován scénář.  
  
 Všimněte si také, že `NetDataContractSerializer` nevýstupuje úplný .NET Framework typ a název sestavení pro každý uzel v grafu objektů. Vypisuje tyto informace pouze tam, kde je dvojznačný. To znamená výstup na úrovni kořenového objektu a pro všechny polymorfní případy.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Runtime.Serialization.DataContractSerializer>
- <xref:System.Runtime.Serialization.NetDataContractSerializer>
- <xref:System.Runtime.Serialization.XmlObjectSerializer>
- [Binární serializace](../../../standard/serialization/binary-serialization.md)
- [Typy podporované serializátorem kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)

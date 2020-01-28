---
title: Serializace
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
ms.openlocfilehash: d29a7bc9f304b8d19e8af593166b8d847117424f
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743629"
---
# <a name="serialization"></a>Serializace
Serializace je proces převodu objektu do formátu, který lze snadno zachovat nebo přenést. Můžete například serializovat objekt, přenést ho přes Internet pomocí protokolu HTTP a deserializovat ho v cílovém počítači.

 .NET Framework nabízí tři hlavní serializace technologie optimalizované pro různé scénáře serializace. V následující tabulce jsou uvedeny tyto technologie a hlavní Framework typy související s tyto technologie.

|**Název technologie**|**Hlavní typy**|**Řešení**|
|-------------------------|--------------------|-------------------|
|**Serializace kontraktu dat**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Obecné stálost<br />Webové služby<br />FORMÁT JSON|
|**Serializace XML**|<xref:System.Xml.Serialization.XmlSerializer>|Formát XML s plnou kontrolou nad tvarem XML|
|**Serializace za běhu (binární a SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|Vzdálené komunikace pomocí rozhraní .NET|

 Při navrhování nových typů ✔️ myslet na serializaci.

## <a name="choosing-the-right-serialization-technology-to-support"></a>Vybrat technologii vpravo serializace pro podporu
 ✔️ Zvažte podporu serializace kontraktu dat v případě, že instance vašeho typu mohou být nutné trvale nebo použít ve webových službách.

 ✔️ Zvažte podporu serializace XML místo nebo kromě serializace kontraktu dat, pokud potřebujete větší kontrolu nad formátem XML, který je vytvořen při serializaci typu.

 To může být nezbytné v některých případech interoperability, kdy potřebujete použít konstrukci XML, která není podporována serializací kontraktu dat, například k vytvoření atributů XML.

 ✔️ Zvažte podporu serializace za běhu, pokud instance vašeho typu potřebují cestovat přes hranice vzdálené komunikace .NET.

 ❌ se vyhnout podpoře serializace modulu runtime nebo serializace XML pouze pro obecné důvody trvalosti. Preferovat místo toho serializaci kontraktu dat.

## <a name="supporting-data-contract-serialization"></a>Podpůrné smlouvy serializaci dat
 Typy mohou podporovat serializaci kontraktu dat použitím <xref:System.Runtime.Serialization.DataContractAttribute> na typ a <xref:System.Runtime.Serialization.DataMemberAttribute> členů (polí a vlastností) typu.

 ✔️ Zvažte označení datových členů typu public, pokud typ lze použít v částečném vztahu důvěryhodnosti.

 V úplném vztahu důvěryhodnosti mohou serializace kontraktů dat serializovat a deserializovat typy a členy NonPublic, ale pouze veřejné členy lze serializovat a deserializovat v částečném vztahu důvěryhodnosti.

 ✔️ implementovat metodu getter a setter pro všechny vlastnosti, které mají <xref:System.Runtime.Serialization.DataMemberAttribute>. Serializátory kontraktů dat vyžadují metodu Getter i setter pro typ, který se považuje za serializovatelný. (V .NET Framework 3,5 SP1 můžou být některé vlastnosti kolekce jenom pro získání.) Pokud typ nebude použit v částečném vztahu důvěryhodnosti, jeden nebo oba přístupové objekty vlastnosti mohou být NonPublic.

 ✔️ Zvažte použití zpětných volání serializace pro inicializaci deserializovaných instancí.

 Konstruktory nejsou volána, když jsou objekty deserializovat. (Pravidlo obsahuje výjimky. Konstruktory kolekcí označených pomocí <xref:System.Runtime.Serialization.CollectionDataContractAttribute> jsou volány během deserializace.) Proto je nutné implementovat logiku, která se spustí během normálního konstrukce, jako jedno ze zpětných volání serializace.

 `OnDeserializedAttribute` je nejběžněji používaný atribut zpětného volání. Další atributy řady jsou <xref:System.Runtime.Serialization.OnDeserializingAttribute>, <xref:System.Runtime.Serialization.OnSerializingAttribute>, a <xref:System.Runtime.Serialization.OnSerializedAttribute>. Jejich lze použít k označení zpětná volání, které získat spuštěny před deserializace před serializací a nakonec po serializaci, v uvedeném pořadí.

 ✔️ Zvažte použití <xref:System.Runtime.Serialization.KnownTypeAttribute> k označení konkrétních typů, které by měly být použity při deserializaci složitého grafu objektů.

 ✔️ Při vytváření nebo změně serializovatelných typů zvážit zpětnou a dopřednou kompatibilitu.

 Mějte na paměti, kterou serializovat datových proudů budoucí verze vašeho typu lze deserializovat do aktuální verze typu a naopak.

 Ujistěte se, že rozumíte tomu, že datové členy, i privátní a interní, nemohou změnit jejich názvy, typy nebo dokonce jejich pořadí v budoucích verzích typu, pokud se zvláštní péče nerozhodne zachovat kontrakt pomocí explicitních parametrů atributů kontraktu dat. .

 Testování kompatibility serializace při provádění změn serializovatelných typů. Zkuste deserializaci na novou verzi do starší verze a naopak.

 ✔️ Zvažte implementaci <xref:System.Runtime.Serialization.IExtensibleDataObject>, aby povolovala kulatou Trip mezi různými verzemi typu.

 Rozhraní umožňuje serializátor zajistit, aby žádná data nejsou ztracena během verzemi. Vlastnost <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> slouží k uložení jakýchkoli dat z budoucí verze typu, který je pro aktuální verzi neznámý, a proto nemůže být uložen ve svých datových členech. V případě, že je aktuální verze následně serializována a deserializována do budoucí verze, budou další data k dispozici v serializovaném proudu.

## <a name="supporting-xml-serialization"></a>Podpora serializace XML
 Serializace kontraktu dat je hlavní (výchozí) Serializační technologie v .NET Framework, ale existují scénáře serializace, které serializace kontraktu dat nepodporuje. Můžete například ji vám neuděluje plnou kontrolu nad tvar XML vytvořeného nebo používané serializátor. Je-li takové přesné řízení vyžadováno, je nutné použít serializaci XML a je třeba navrhnout typy pro podporu této technologie serializace.

 ❌ Vyhněte návrhu typů specificky pro serializaci XML, pokud nemáte velmi silný důvod k řízení tvaru vytvořeného XML. Tato technologie serializace bylo nahrazeno serializaci smlouvy dat, který je popsána v předchozím oddílu.

 ✔️ Zvažte implementaci rozhraní <xref:System.Xml.Serialization.IXmlSerializable>, pokud chcete ještě větší kontrolu nad tvar serializovaného XML, než když použijete atributy serializace XML. Dvě metody rozhraní, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> a <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, umožňují plně řídit serializovaný datový proud XML. Můžete také řídit schéma XML, které se generuje pro typ použitím `XmlSchemaProviderAttribute`.

## <a name="supporting-runtime-serialization"></a>Podpora modulu Runtime serializace
 Serializace za běhu je technologie, kterou používá Vzdálená komunikace .NET. Pokud si myslíte, že se vaše typy budou přenášet pomocí vzdálené komunikace .NET, musíte zajistit, aby podporovaly serializaci modulu runtime.

 Základní podporu pro serializaci za běhu lze poskytnout pomocí <xref:System.SerializableAttribute>a pokročilejší scénáře zahrnují implementaci jednoduchého Serializovatelnýho vzoru za běhu (implementace <xref:System.Runtime.Serialization.ISerializable> a poskytování konstruktoru serializace).

 ✔️ Zvažte podporu serializace za běhu, pokud budou vaše typy použity pro vzdálenou komunikaci rozhraní .NET. Například obor názvů <xref:System.AddIn?displayProperty=nameWithType> používá vzdálenou komunikaci rozhraní .NET a všechny typy vyměňované mezi `System.AddIn` doplňky musí podporovat serializaci modulu runtime.

 ✔️ Zvažte implementaci modelu serializovatelných za běhu, pokud chcete úplnou kontrolu nad procesem serializace. Například pokud chcete transformovat data jako jeho získá serializován nebo deserializován.

 Vzor je velmi snadné. Vše je třeba provést je implementovat <xref:System.Runtime.Serialization.ISerializable> rozhraní a zadat speciální konstruktor, který se používá, pokud je objekt deserializován.

 ✔️ provést ochranu konstruktoru serializace a zadat dva parametry a přesně tak, jak je uvedeno v ukázce zde.

```csharp
[Serializable]
public class Person : ISerializable
{
    protected Person(SerializationInfo info, StreamingContext context)
    {
        // ...
    }
}
```

 ✔️ explicitně implementujte <xref:System.Runtime.Serialization.ISerializable> členy.

 ✔️ použít pro <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> implementaci požadavek na propojení. Tím se zajistí, že přístup k členu má jenom plně důvěryhodný jádro a serializátor modulu runtime.

 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*

 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. z [pokynů pro návrh rozhraní: konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*

## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)

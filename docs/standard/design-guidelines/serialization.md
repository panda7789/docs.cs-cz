---
title: Serializace
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
author: KrzysztofCwalina
ms.openlocfilehash: 0259bf82e74cbca7df8da246ca2e6ba7ef4542b3
ms.sourcegitcommit: 9ee6cd851b6e176a5811ea28ed0d5935c71950f9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68868527"
---
# <a name="serialization"></a>Serializace
Serializace je proces převodu objektu do formátu, který lze snadno zachovat nebo přenést. Můžete například serializovat objekt, přenést ho přes Internet pomocí protokolu HTTP a deserializovat ho v cílovém počítači.  
  
 .NET Framework nabízí tři hlavní serializace technologie optimalizované pro různé scénáře serializace. V následující tabulce jsou uvedeny tyto technologie a hlavní Framework typy související s tyto technologie.  
  
|**Název technologie**|**Hlavní typy**|**Řešení**|  
|-------------------------|--------------------|-------------------|  
|**Serializace kontraktu dat**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Obecné stálost<br />Webové služby<br />FORMÁT JSON|  
|**Serializace XML**|<xref:System.Xml.Serialization.XmlSerializer>|Formát XML s plnou kontrolou nad tvarem XML|  
|**Serializace za běhu (binární a SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|Vzdálené komunikace pomocí rozhraní .NET|  
  
 **✓ DO** přemýšlení o serializaci při návrhu nové typy.  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>Vybrat technologii vpravo serializace pro podporu  
 **✓ CONSIDER** podporuje serializace kontraktu dat v případě, že může být nutné instance stejného typu jako trvalý, nebo použít ve webové služby.  
  
 **✓ CONSIDER** podporu serializace XML místo nebo kromě serializace kontraktu dat, pokud potřebujete větší kontrolu nad formátu XML, která je vytvořena, když je typ serializován.  
  
 To může být nezbytné v některých případech interoperability, kdy potřebujete použít konstrukci XML, která není podporována serializací kontraktu dat, například k vytvoření atributů XML.  
  
 **✓ CONSIDER** podporuje serializace Runtime v případě, že musí projít napříč hranicemi .NET Remoting instance stejného typu.  
  
 **X AVOID** podporu serializace Runtime nebo serializace XML pouze z důvodů obecné trvalost. Preferovat místo toho serializaci kontraktu dat.  
  
## <a name="supporting-data-contract-serialization"></a>Podpůrné smlouvy serializaci dat  
 Typy mohou podporovat serializaci kontraktu dat aplikováním <xref:System.Runtime.Serialization.DataContractAttribute> na typ <xref:System.Runtime.Serialization.DataMemberAttribute> a na členy (pole a vlastnosti) typu.  
  
 **✓ CONSIDER** označení datové členy vaší veřejného typu, pokud se dá použít typ v částečné důvěryhodnosti.  
  
 V úplném vztahu důvěryhodnosti mohou serializace kontraktů dat serializovat a deserializovat typy a členy NonPublic, ale pouze veřejné členy lze serializovat a deserializovat v částečném vztahu důvěryhodnosti.  
  
 **✓ DO** implementace metody getter a setter na všechny vlastnosti, které mají <xref:System.Runtime.Serialization.DataMemberAttribute>. Serializátory kontraktů dat vyžadují metodu Getter i setter pro typ, který se považuje za serializovatelný. (V .NET Framework 3,5 SP1 můžou být některé vlastnosti kolekce jenom pro získání.) Pokud typ nesmí být použity v částečným vztahem důvěryhodnosti, může být jeden nebo oba přistupující objekty vlastnost neveřejné.  
  
 **✓ CONSIDER** pomocí zpětná volání serializace pro inicializaci instance deserializovat.  
  
 Konstruktory nejsou volána, když jsou objekty deserializovat. (Pravidlo obsahuje výjimky. Konstruktory kolekcí s <xref:System.Runtime.Serialization.CollectionDataContractAttribute> označením jsou volány během deserializace.) Proto je nutné implementovat logiku, která se spustí během normálního konstrukce, jako jedno ze zpětných volání serializace.  
  
 `OnDeserializedAttribute`je nejběžněji používaný atribut zpětného volání. Další atributy řady jsou <xref:System.Runtime.Serialization.OnDeserializingAttribute>, <xref:System.Runtime.Serialization.OnSerializingAttribute>, a <xref:System.Runtime.Serialization.OnSerializedAttribute>. Jejich lze použít k označení zpětná volání, které získat spuštěny před deserializace před serializací a nakonec po serializaci, v uvedeném pořadí.  
  
 **✓ CONSIDER** pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute> k označení konkrétní typy, které se mají použít při deserializaci komplexní objekt grafu.  
  
 **✓ DO** zvažte kompatibilita zpětné a předat dál při vytváření nebo změně Serializovatelné typy.  
  
 Mějte na paměti, kterou serializovat datových proudů budoucí verze vašeho typu lze deserializovat do aktuální verze typu a naopak.  
  
 Ujistěte se, že rozumíte tomu, že datové členy, i privátní a interní, nemohou změnit jejich názvy, typy nebo dokonce jejich pořadí v budoucích verzích typu, pokud se zvláštní péče nerozhodne zachovat kontrakt pomocí explicitních parametrů atributů kontraktu dat. .  
  
 Testování kompatibility serializace při provádění změn serializovatelných typů. Zkuste deserializaci na novou verzi do starší verze a naopak.  
  
 **✓ CONSIDER** implementace <xref:System.Runtime.Serialization.IExtensibleDataObject> umožňující odezvy mezi různými verzemi typu.  
  
 Rozhraní umožňuje serializátor zajistit, aby žádná data nejsou ztracena během verzemi. <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> Vlastnost se používá k uložení jakýchkoli dat z budoucí verze typu, který je pro aktuální verzi neznámý, a proto nemůže být uložen ve svých datových členech. V případě, že je aktuální verze následně serializována a deserializována do budoucí verze, budou další data k dispozici v serializovaném proudu.  
  
## <a name="supporting-xml-serialization"></a>Podpora serializace XML  
 Serializace kontraktu dat je hlavní (výchozí) Serializační technologie v .NET Framework, ale existují scénáře serializace, které serializace kontraktu dat nepodporuje. Můžete například ji vám neuděluje plnou kontrolu nad tvar XML vytvořeného nebo používané serializátor. Je-li takové přesné řízení vyžadováno, je nutné použít serializaci XML a je třeba navrhnout typy pro podporu této technologie serializace.  
  
 **X AVOID** navrhování vaší typy speciálně pro serializaci XML, pokud nemáte velmi silné důvod k řízení obrazec XML vytvořil. Tato technologie serializace bylo nahrazeno serializaci smlouvy dat, který je popsána v předchozím oddílu.  
  
 **✓ CONSIDER** implementace <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, pokud chcete ještě větší kontrolu nad obrazec serializovaných XML než nabízejí použitím atributy serializace XML. Dvě metody rozhraní <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> a <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>umožňují plně řídit serializovaný datový proud XML. Můžete také řídit schéma XML, které se generuje pro typ `XmlSchemaProviderAttribute`použitím.  
  
## <a name="supporting-runtime-serialization"></a>Podpora modulu Runtime serializace  
 Serializace za běhu je technologie, kterou používá Vzdálená komunikace .NET. Pokud si myslíte, že se vaše typy budou přenášet pomocí vzdálené komunikace .NET, musíte zajistit, aby podporovaly serializaci modulu runtime.  
  
 Základní podporu pro serializaci za běhu lze poskytnout pomocí a pokročilejších scénářů <xref:System.SerializableAttribute>, které zahrnují implementaci jednoduchého modelu serializace za běhu (implementace <xref:System.Runtime.Serialization.ISerializable> a poskytování serializace konstruktoru).  
  
 **✓ CONSIDER** podporuje serializace Runtime v případě, že vaše typy budou použity s .NET Remoting. Například <xref:System.AddIn?displayProperty=nameWithType> obor názvů používá vzdálenou komunikaci rozhraní .NET a všechny typy vyměňované mezi `System.AddIn` doplňky musí podporovat serializaci modulu runtime.  
  
 **✓ CONSIDER** implementace vzoru serializovatelný Runtime, pokud chcete plnou kontrolu nad tímto procesem serializace. Například pokud chcete transformovat data jako jeho získá serializován nebo deserializován.  
  
 Vzor je velmi snadné. Vše je třeba provést je implementovat <xref:System.Runtime.Serialization.ISerializable> rozhraní a zadat speciální konstruktor, který se používá, pokud je objekt deserializován.  
  
 **✓ DO** proveďte konstruktor serializace chráněný a zadat dva parametry typu a s názvem přesně tak, jak je znázorněno v ukázce zde.  
  
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
  
 **✓ DO** implementovat <xref:System.Runtime.Serialization.ISerializable> členy explicitně.  
  
 **✓ DO** použít požadavek propojení na <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> implementace. Tím se zajistí, že přístup k členu má jenom plně důvěryhodný jádro a serializátor modulu runtime.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno oprávněním Pearsonova vzdělávání, Inc. pomocí [pokynů pro návrh rozhraní: Konvence, idiomy a vzory pro opakovaně použitelné knihovny .NET, druhá edice](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) , od Krzysztof Cwalina a Brad Abrams, publikovaly 22. října 2008 Addison-Wesley Professional jako součást sady Microsoft Windows Development Series.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)

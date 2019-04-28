---
title: Serialization1
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
author: KrzysztofCwalina
ms.openlocfilehash: f0ef8ab378fb3898f2d2e134f0b38668f6794ef3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650151"
---
# <a name="serialization"></a>Serializace
Serializace je proces převodu objektu do formátu, který lze snadno zachovat nebo přenášet. Například může serializovat objekt, přenosu je prostřednictvím Internetu pomocí protokolu HTTP a deserializovat ho na cílovém počítači.  
  
 Rozhraní .NET Framework nabízí tři hlavní serializace technologií, které jsou optimalizované pro různé scénáře serializace. V následující tabulce jsou uvedeny tyto technologie a hlavní Framework typy související s tyto technologie.  
  
|**Název technologie**|**Hlavní typy**|**Scénáře**|  
|-------------------------|--------------------|-------------------|  
|**Smlouvy serializaci dat**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Obecné stálost<br />Webové služby<br />FORMÁT JSON|  
|**Serializace XML**|<xref:System.Xml.Serialization.XmlSerializer>|Formát XML s plnou kontrolu nad tvar XML|  
|**Modul runtime serializace (binární a SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|Vzdálené komunikace pomocí rozhraní .NET|  
  
 **✓ DO** přemýšlení o serializaci při návrhu nové typy.  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>Vybrat technologii vpravo serializace pro podporu  
 **✓ CONSIDER** podporuje serializace kontraktu dat v případě, že může být nutné instance stejného typu jako trvalý, nebo použít ve webové služby.  
  
 **✓ CONSIDER** podporu serializace XML místo nebo kromě serializace kontraktu dat, pokud potřebujete větší kontrolu nad formátu XML, která je vytvořena, když je typ serializován.  
  
 Toto může být nutné v některých vzájemná funkční spolupráce, které scénáře, které je potřeba použít XML sestavení, která není podporována serializaci dat smlouvy, například k vytvoření atributy ve formátu XML.  
  
 **✓ CONSIDER** podporuje serializace Runtime v případě, že musí projít napříč hranicemi .NET Remoting instance stejného typu.  
  
 **X AVOID** podporu serializace Runtime nebo serializace XML pouze z důvodů obecné trvalost. Místo toho raději smlouvy serializaci dat.  
  
## <a name="supporting-data-contract-serialization"></a>Podpůrné smlouvy serializaci dat  
 Typy podporuje serializaci smlouvy dat použitím <xref:System.Runtime.Serialization.DataContractAttribute> na typ a <xref:System.Runtime.Serialization.DataMemberAttribute> do členů (polí a vlastností) typu.  
  
 **✓ CONSIDER** označení datové členy vaší veřejného typu, pokud se dá použít typ v částečné důvěryhodnosti.  
  
 V úplném vztahu důvěryhodnosti může serializátory smlouvy dat serializaci a deserializaci neveřejné typy a členy, ale můžete být pouze veřejné členy serializaci a deserializaci v částečném vztahu důvěryhodnosti.  
  
 **✓ DO** implementace metody getter a setter na všechny vlastnosti, které mají <xref:System.Runtime.Serialization.DataMemberAttribute>. Smlouva serializátory vyžadují metoda getter a setter pro typ, který má být považován za serializovatelný. (V rozhraní .NET Framework 3.5 SP1, některé vlastnosti kolekce může být jenom pro získání.) Pokud typ nesmí být použity v částečným vztahem důvěryhodnosti, může být jeden nebo oba přistupující objekty vlastnost neveřejné.  
  
 **✓ CONSIDER** pomocí zpětná volání serializace pro inicializaci instance deserializovat.  
  
 Konstruktory nejsou volána, když jsou objekty deserializovat. (Existují výjimky z pravidla. Konstruktory kolekcí označena <xref:System.Runtime.Serialization.CollectionDataContractAttribute> volá se během deserializace.) Proto jakékoli logiky, která provede během vytváření normální potřebuje k implementaci jako jeden ze zpětných volání serializace.  
  
 `OnDeserializedAttribute` se atribut nejčastěji používané zpětného volání. Další atributy řady jsou <xref:System.Runtime.Serialization.OnDeserializingAttribute>, <xref:System.Runtime.Serialization.OnSerializingAttribute>, a <xref:System.Runtime.Serialization.OnSerializedAttribute>. Jejich lze použít k označení zpětná volání, které získat spuštěny před deserializace před serializací a nakonec po serializaci, v uvedeném pořadí.  
  
 **✓ CONSIDER** pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute> k označení konkrétní typy, které se mají použít při deserializaci komplexní objekt grafu.  
  
 **✓ DO** zvažte kompatibilita zpětné a předat dál při vytváření nebo změně Serializovatelné typy.  
  
 Mějte na paměti, kterou serializovat datových proudů budoucí verze vašeho typu lze deserializovat do aktuální verze typu a naopak.  
  
 Ujistěte se, že víte, že datových členů, dokonce i privátní a interní, nelze změnit jejich názvy, typy nebo dokonce i jejich pořadí v budoucích verzích typ není-li speciální je pozor zachovat smlouvu pomocí explicitní parametrů na atributy smlouvy dat. .  
  
 Testování kompatibility serializace při provádění změn Serializovatelné typy. Zkuste deserializaci na novou verzi do starší verze a naopak.  
  
 **✓ CONSIDER** implementace <xref:System.Runtime.Serialization.IExtensibleDataObject> umožňující odezvy mezi různými verzemi typu.  
  
 Rozhraní umožňuje serializátor zajistit, aby žádná data nejsou ztracena během verzemi. <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> Vlastnost se používá k ukládání dat z budoucí verze typu, který neznámý pro aktuální verzi, a proto ji nelze uložit v její datové členy. Aktuální verze je následně serializaci a deserializaci v budoucích verzích, doplňující data nebudou mít k dispozici v serializovaném proudu.  
  
## <a name="supporting-xml-serialization"></a>Podpora serializace XML  
 Data smlouvy serializace je hlavním (výchozí) serializace technologie v rozhraní .NET Framework, ale existují serializace scénáře, které Data smlouvy serializace není podporováno. Můžete například ji vám neuděluje plnou kontrolu nad tvar XML vytvořeného nebo používané serializátor. Pokud je takové přesného vyžadováno, serializace XML musí být použit, a je potřeba navrhnout vaše typy pro podporu této technologie serializace.  
  
 **X AVOID** navrhování vaší typy speciálně pro serializaci XML, pokud nemáte velmi silné důvod k řízení obrazec XML vytvořil. Tato technologie serializace bylo nahrazeno serializaci smlouvy dat, který je popsána v předchozím oddílu.  
  
 **✓ CONSIDER** implementace <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, pokud chcete ještě větší kontrolu nad obrazec serializovaných XML než nabízejí použitím atributy serializace XML. Dvě metody rozhraní, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> a <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, umožňují plně řídit serializovaná datový proud XML. Můžete také určit schématu XML, který získá vygenerována pro typ použitím `XmlSchemaProviderAttribute`.  
  
## <a name="supporting-runtime-serialization"></a>Podpora modulu Runtime serializace  
 Modul runtime serializace je technologie, pomocí vzdálené komunikace .NET. Pokud se domníváte, že vaše typy bude přenosu pomocí vzdálené komunikace .NET, budete muset Ujistěte se, že podporují Runtime serializace.  
  
 Základní podpora pro modul Runtime serializace můžete zadat použitím <xref:System.SerializableAttribute>, a pokročilejší scénáře zahrnovat implementing jednoduchý za běhu serializovatelný vzor (implementovat <xref:System.Runtime.Serialization.ISerializable> a Poskytněte konstruktor serializace).  
  
 **✓ CONSIDER** podporuje serializace Runtime v případě, že vaše typy budou použity s .NET Remoting. Například <xref:System.AddIn?displayProperty=nameWithType> obor názvů používá vzdálené komunikace .NET, a proto všechny typy výměna mezi `System.AddIn` doplňků musí podporovat serializace za běhu.  
  
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
  
 **✓ DO** použít požadavek propojení na <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> implementace. Tím se zajistí, že pouze plně důvěryhodné, jádro a serializátor Runtime máte přístup ke členu.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Přetištěno podle oprávnění Pearson vzdělávání, Inc. z [pokyny k návrhu architektury: Konvence, Idiomy a vzory pro opakovaně použitelného knihovny .NET, 2nd Edition](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Brad Abrams publikován 22 Oct 2008, Designing Effective části této série Microsoft Windows Development.*  
  
## <a name="see-also"></a>Viz také:

- [Pokyny k návrhu architektury](../../../docs/standard/design-guidelines/index.md)
- [Pokyny k používání](../../../docs/standard/design-guidelines/usage-guidelines.md)

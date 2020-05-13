---
title: Pokyny pro serializaci
description: Tento dokument obsahuje pokyny, které je potřeba vzít v úvahu při navrhování rozhraní API, které se má serializovat, a souhrn tří hlavních serializačních technologií, které .NET nabízí.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serialization, guidelines
- binary serialization, guidelines
ms.assetid: ebbeddff-179d-443f-bf08-9c373199a73a
ms.openlocfilehash: af0b857e98ffbe0ff9f12108174b79f873c2b38f
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378379"
---
# <a name="serialization-guidelines"></a>Pokyny pro serializaci
Tento dokument obsahuje seznam pokyny k serializaci zvážit při navrhování rozhraní API.  

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]
  
 .NET nabízí tři hlavní Serializační technologie, které jsou optimalizované pro různé scénáře serializace. Následující tabulka uvádí tyto technologie a hlavní typy .NET, které souvisejí s těmito technologiemi.  
  
|Technologie|Příslušných tříd|Poznámky|  
|----------------|----------------------|-----------|  
|Smlouva serializaci dat|<xref:System.Runtime.Serialization.DataContractAttribute><br /><br /> <xref:System.Runtime.Serialization.DataMemberAttribute><br /><br /> <xref:System.Runtime.Serialization.DataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.NetDataContractSerializer><br /><br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer><br /><br /> <xref:System.Runtime.Serialization.ISerializable>|Obecné stálost<br /><br /> Webové služby<br /><br /> JSON|  
|Serializace XML|<xref:System.Xml.Serialization.XmlSerializer>|Formát XML <br />k úplnému řízení|  
|Modul runtime-serializace (binární a SOAP)|<xref:System.SerializableAttribute><br /><br /> <xref:System.Runtime.Serialization.ISerializable><br /><br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter><br /><br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|Vzdálené komunikace pomocí rozhraní .NET|  
  
 Při navrhování nových typů, byste měli rozhodnout, která, pokud existuje, těchto technologií tyto typy musí podporovat. Následující pokyny popisují postup tuto volbu a k poskytování těchto podpory. Tyto zásady nejsou určeny vám pomůže vybrat technologii, která serializace byste měli používat při provádění svou aplikaci nebo knihovny. Tyto pokyny přímo nesouvisí se návrh rozhraní API a proto nejsou v rámci oboru v tomto tématu.  
  
## <a name="guidelines"></a>Pokyny  
  
- Zamyslete serializace při navrhování nových typů.  
  
     Serializace je k posouzení důležité návrh pro každý typ, protože programů může být nutné zachovat nebo přenést instance daného typu.  
  
### <a name="choosing-the-right-serialization-technology-to-support"></a>Výběr správné technologie serializace pro podporu  
 Daného typu může podporovat none, jeden nebo více technologií serializace.  
  
- Zvažte podporu *serializace kontraktu dat* v případě, že instance vašeho typu může být nutné zachovat nebo použít ve webových službách.  
  
- Zvažte podporu *serializace XML* místo nebo kromě serializace kontraktu dat, pokud potřebujete větší kontrolu nad formátem XML, který je vytvořen při serializaci typu.  
  
     Toto může být nutné v některých případech interoperability, kde je třeba použít XML konstrukci, která není podporována serializaci dat smlouvy, například k vytvoření atributy ve formátu XML.  
  
- Zvažte podporu *serializace za běhu* , pokud instance vašeho typu potřebují cestovat přes hranice vzdálené komunikace .NET.  
  
- Vyhněte se podpora modulu runtime serializace nebo serializace XML pouze z důvodů obecné stálost. Místo toho raději smlouvy serializaci dat  
  
#### <a name="supporting-data-contract-serialization"></a>Podpora serializace kontraktu dat  
 Typy mohou podporovat serializaci kontraktu dat aplikováním <xref:System.Runtime.Serialization.DataContractAttribute> na typ a na <xref:System.Runtime.Serialization.DataMemberAttribute> členy (pole a vlastnosti) typu.  
  
 [!code-csharp[SerializationGuidelines#1](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#1)]
 [!code-vb[SerializationGuidelines#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#1)]  
  
1. Vzít v úvahu označení datové členy vašeho typu veřejné, pokud typ lze použít v částečném vztahu důvěryhodnosti. V plnou důvěryhodnost může serializátory smlouvy serializaci a deserializaci neveřejné typy a členy, ale může být pouze veřejné členy serializaci a deserializaci v částečném vztahu důvěryhodnosti.  
  
2. Na všechny vlastnosti, které mají Data MemberAttribute implementujte metodu getter a setter. Smlouva serializátory vyžadují metoda getter a setter pro typ, který má být považován za serializovatelný. Pokud typ nesmí být použity v částečným vztahem důvěryhodnosti, může být jeden nebo oba přistupující objekty vlastnost neveřejné.  
  
     [!code-csharp[SerializationGuidelines#2](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#2)]
     [!code-vb[SerializationGuidelines#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#2)]  
  
3. ZVAŽTE použití zpětných volání serializace pro inicializaci deserializovat instancí.  
  
     Konstruktory nejsou volána, když jsou objekty deserializovat. Proto je nutné implementovat logiku, která se spustí během normálního konstrukce, jako jedno ze *zpětných volání serializace*.  
  
     [!code-csharp[SerializationGuidelines#3](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#3)]
     [!code-vb[SerializationGuidelines#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#3)]  
  
     <xref:System.Runtime.Serialization.OnDeserializedAttribute> Se atribut nejčastěji používané zpětného volání. Ostatní atributy v rodině jsou <xref:System.Runtime.Serialization.OnDeserializingAttribute> , <xref:System.Runtime.Serialization.OnSerializingAttribute> a <xref:System.Runtime.Serialization.OnSerializedAttribute> . Jejich lze použít k označení zpětná volání, které získat spuštěny před deserializace před serializací a nakonec po serializaci, v uvedeném pořadí.  
  
4. ZVAŽTE použití <xref:System.Runtime.Serialization.KnownTypeAttribute> označuje konkrétní typy, které se mají používat při deserializaci komplexní objekt grafu.  
  
     Například pokud je typ deserializovaného datového členu reprezentovaný abstraktní třídou, serializátor bude potřebovat známé informace o *typu* k rozhodnutí o tom, jaký typ vytvoření instance a přiřazení k členu. Pokud známý typ není zadán pomocí atributu, bude nutné mají být předány serializátor explicitně (můžete to provést předáním známé typy konstruktoru serializátor) nebo bude je nutné zadat v konfiguračním souboru.  
  
     [!code-csharp[SerializationGuidelines#4](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#4)]
     [!code-vb[SerializationGuidelines#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#4)]  
  
     V případech, kdy seznam známých typů není známý staticky (Pokud je třída **Person** zkompilována), může **KnownTypeAttribute** ukazovat na metodu, která vrací seznam známých typů za běhu.  
  
5. Zvažte dopředné a zpětné kompatibility při vytváření nebo změně Serializovatelné typy.  
  
     Mějte na paměti, kterou serializovat datových proudů budoucí verze vašeho typu lze deserializovat do aktuální verze typu a naopak. Ujistěte se, že víte, že datových členů, dokonce i privátní a interní, nelze změnit jejich názvy, typy nebo dokonce i jejich pořadí v budoucích verzích typ není-li speciální je pozor zachovat smlouvu pomocí explicitní parametrů na atributy smlouvy data.Testování kompatibility serializace při provádění změn Serializovatelné typy. Zkuste deserializaci na novou verzi do starší verze a naopak.  
  
6. ZVAŽTE implementaci <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní, které chcete, aby verzemi mezi různými verzemi typu.  
  
     Rozhraní umožňuje serializátor zajistit, aby žádná data nejsou ztracena během verzemi. <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A> Vlastnost uloží všechna data z budoucí verze typu, který neznámý pro aktuální verzi. V případě, že je aktuální verze následně serializována a deserializována do budoucí verze, budou další data k dispozici v serializovaném proudu prostřednictvím hodnoty vlastnosti **ExtensionData –** .  
  
     [!code-csharp[SerializationGuidelines#5](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#5)]
     [!code-vb[SerializationGuidelines#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#5)]  
  
     Další informace najdete v tématu [kontrakty dat kompatibilní s dopředné](../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
#### <a name="supporting-xml-serialization"></a>Podpora serializace XML  
 Data smlouvy serializace je hlavním (výchozí) serializace technologie v rozhraní .NET Framework, ale existují serializace scénáře, že data smlouvy serializace není podporováno. Můžete například ji vám neuděluje plnou kontrolu nad tvar XML vytvořeného nebo používané serializátor. Je-li takové přesné řízení vyžadováno, je nutné použít *serializaci XML* a je třeba navrhnout typy pro podporu této technologie serializace.  
  
1. BRÁNÍ návrh vašich typů speciálně pro serializaci XML, pokud nemáte autoři kladou důvod k nastavení tvaru XML vytvořen. Tato technologie serializace bylo nahrazeno serializaci smlouvy dat, který je popsána v předchozím oddílu.  
  
     Jinými slovy, se nevztahují atributů z <xref:System.Xml.Serialization> obor názvů pro nové typy, pokud si nejste jisti, že typ bude použita k serializaci kódu XML. Následující příklad ukazuje, jak lze použít **System. XML. Serialization** k řízení tvaru vytvořeného ve formátu XML.  
  
     [!code-csharp[SerializationGuidelines#6](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#6)]
     [!code-vb[SerializationGuidelines#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#6)]  
  
2. ZVAŽTE implementaci <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, pokud chcete, aby ještě větší kontrolu nad tvar serializovaná XML než nabízejí použitím atributy serializace XML. Dvě metody rozhraní <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> a <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> umožňují plně řídit serializovaný datový proud XML. Můžete také určit schématu XML, který získá vygenerována pro typ použitím <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atributu.  
  
#### <a name="supporting-runtime-serialization"></a>Podpora serializace modulu runtime  
 *Serializace za běhu* je technologie, kterou používá Vzdálená komunikace .NET. Pokud se domníváte, že vaše typy bude přenosu pomocí vzdálené komunikace pomocí rozhraní .NET, je třeba Ujistěte se, že podporují runtime serializace.  
  
 Základní podporu pro *serializaci za běhu* lze poskytnout použitím <xref:System.SerializableAttribute> atributu a pokročilejší scénáře zahrnují implementaci jednoduchých *serializovatelných vzorů za běhu* (implementovat- <xref:System.Runtime.Serialization.ISerializable> a poskytnout konstruktor serializace).  
  
1. ZVAŽTE podporuje runtime serializace v případě, že vaše typy budou použity u vzdálené komunikace rozhraní .NET. Například <xref:System.AddIn> obor názvů používá vzdálenou komunikaci rozhraní .NET a všechny typy vyměňované mezi doplňky **System. AddIn** musí podporovat serializaci modulu runtime.  
  
     [!code-csharp[SerializationGuidelines#7](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#7)]
     [!code-vb[SerializationGuidelines#7](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#7)]  
  
2. Zvažte implementaci *modelu serializovatelných za běhu* , pokud chcete úplnou kontrolu nad procesem serializace. Například pokud chcete transformovat data jako jeho získá serializován nebo deserializován.  
  
     Vzor je velmi snadné. Vše je třeba provést je implementovat <xref:System.Runtime.Serialization.ISerializable> rozhraní a zadat speciální konstruktor, který se používá, pokud je objekt deserializován.  
  
     [!code-csharp[SerializationGuidelines#8](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#8)]
     [!code-vb[SerializationGuidelines#8](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#8)]  
  
3. Proveďte konstruktoru serializace chráněné a poskytují dva parametry typu a s názvem tak, jak je uvedeno v ukázce zde.  
  
     [!code-csharp[SerializationGuidelines#9](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#9)]
     [!code-vb[SerializationGuidelines#9](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#9)]  
  
4. Explicitně implementujte ISerializable členy.  
  
     [!code-csharp[SerializationGuidelines#10](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#10)]
     [!code-vb[SerializationGuidelines#10](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#10)]  
  
5. Použijte požadavek propojení na implementaci **ISerializable. GetObjectData** . To zajistí, že pouze plně důvěryhodné, jádro a serializátor runtime máte přístup ke členu.  
  
     [!code-csharp[SerializationGuidelines#11](../../../samples/snippets/csharp/VS_Snippets_CFX/serializationguidelines/cs/source.cs#11)]
     [!code-vb[SerializationGuidelines#11](../../../samples/snippets/visualbasic/VS_Snippets_CFX/serializationguidelines/vb/source.vb#11)]  
  
## <a name="see-also"></a>Viz také

- [Použití kontraktů dat](../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Serializátor kontraktu dat](../../../docs/framework/wcf/feature-details/data-contract-serializer.md)
- [Typy podporované serializátorem kontraktu dat](../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)
- [Binární serializace](binary-serialization.md)
- [Vzdálené komunikace pomocí rozhraní .NET](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/72x4h507(v=vs.100))
- [Serializace XML a SOAP](xml-and-soap-serialization.md)
- [Zabezpečení a serializace](../../../docs/framework/misc/security-and-serialization.md)

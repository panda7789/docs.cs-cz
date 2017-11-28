---
title: Serialization1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bebb27ac-9712-4196-9931-de19fc04dbac
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: e63428400a7868b71a2d8e52637e4b22e4c44ee7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="serialization"></a>Serializace
Serializace je proces převodu objekt do formátu, který lze snadno jako trvalý, nebo přenosu. Například může serializovat objekt, přenosu přes Internet pomocí protokolu HTTP a deserializovat u cílového počítače.  
  
 Rozhraní .NET Framework nabízí tři hlavní serializace technologie optimalizovaných pro různé scénáře serializace. V následující tabulce jsou uvedeny tyto technologie a hlavní Framework typy související s tyto technologie.  
  
|**Název technologie**|**Hlavní typy**|**Scénáře**|  
|-------------------------|--------------------|-------------------|  
|**Serializace kontraktu dat**|<xref:System.Runtime.Serialization.DataContractAttribute> <br /> <xref:System.Runtime.Serialization.DataMemberAttribute> <br /> <xref:System.Runtime.Serialization.DataContractSerializer> <br /> <xref:System.Runtime.Serialization.NetDataContractSerializer> <br /> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> <br /> <xref:System.Runtime.Serialization.ISerializable>|Obecné stálost<br />Webové služby<br />FORMÁT JSON|  
|**Serializace XML**|<xref:System.Xml.Serialization.XmlSerializer>|Formát XML s plnou kontrolu nad obrazec XML|  
|**Modul runtime serializace (binární a SOAP)**|<xref:System.SerializableAttribute> <br /> <xref:System.Runtime.Serialization.ISerializable> <br /> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> <br /> <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>|Vzdálené komunikace pomocí rozhraní .NET|  
  
 **PROVEĎTE ✓** přemýšlení o serializaci při návrhu nové typy.  
  
## <a name="choosing-the-right-serialization-technology-to-support"></a>Vybrat technologii vpravo serializace pro podporu  
 **✓ ZVAŽTE** podporuje serializace kontraktu dat v případě, že může být nutné instance stejného typu jako trvalý, nebo použít ve webové služby.  
  
 **✓ ZVAŽTE** podporu serializace XML místo nebo kromě serializace kontraktu dat, pokud potřebujete větší kontrolu nad formátu XML, která je vytvořena, když je typ serializován.  
  
 To může být nutné v některé interoperabilitu, které vytvořit scénáře, kde budete muset použít XML, která nepodporuje kontrakt serializace dat, například k vytvoření atributy XML.  
  
 **✓ ZVAŽTE** podporuje serializace Runtime v případě, že musí projít napříč hranicemi .NET Remoting instance stejného typu.  
  
 **X nepoužívejte** podporu serializace Runtime nebo serializace XML pouze z důvodů obecné trvalost. Místo toho raději serializace dat kontrakt.  
  
## <a name="supporting-data-contract-serialization"></a>Podpůrné smlouvy serializaci dat  
 Typy může podporovat serializace kontraktu dat s použitím <xref:System.Runtime.Serialization.DataContractAttribute> typu a <xref:System.Runtime.Serialization.DataMemberAttribute> typu u členů (pole a vlastnosti).  
  
 **✓ ZVAŽTE** označení datové členy vaší veřejného typu, pokud se dá použít typ v částečné důvěryhodnosti.  
  
 V režimu plné důvěryhodnosti serializátorů kontrakt dat lze serializaci a deserializaci neveřejní typy a členy, ale pouze veřejné členy může serializovat a deserializovat v částečné důvěryhodnosti.  
  
 **PROVEĎTE ✓** implementace metody getter a setter na všechny vlastnosti, které mají <xref:System.Runtime.Serialization.DataMemberAttribute>. Kontrakt serializátory vyžadují metoda getter a setter pro typ, který má být považovány za serializable. (V rozhraní .NET Framework 3.5 SP1, některé vlastnosti kolekce může být pouze pro získání.) Pokud typ nesmí být použity v částečným vztahem důvěryhodnosti, může být jeden nebo oba přistupující objekty vlastnost neveřejné.  
  
 **✓ ZVAŽTE** pomocí zpětná volání serializace pro inicializaci instance deserializovat.  
  
 Konstruktory nejsou volána, když jsou objekty deserializovat. (Existují zde výjimky z pravidla. Konstruktory kolekcí označené jako <xref:System.Runtime.Serialization.CollectionDataContractAttribute> volá se během deserializace.) Proto všechny logiky, která provede během normálního vytváření musí implementovat jako jeden z zpětná volání serializace.  
  
 `OnDeserializedAttribute`je atribut nejčastěji používané zpětného volání. Další atributy řady jsou <xref:System.Runtime.Serialization.OnDeserializingAttribute>, <xref:System.Runtime.Serialization.OnSerializingAttribute>, a <xref:System.Runtime.Serialization.OnSerializedAttribute>. Jejich lze použít k označení zpětná volání, které získat spuštěny před deserializace před serializací a nakonec po serializaci, v uvedeném pořadí.  
  
 **✓ ZVAŽTE** pomocí <xref:System.Runtime.Serialization.KnownTypeAttribute> k označení konkrétní typy, které se mají použít při deserializaci komplexní objekt grafu.  
  
 **PROVEĎTE ✓** zvažte kompatibilita zpětné a předat dál při vytváření nebo změně Serializovatelné typy.  
  
 Mějte na paměti, kterou serializovat datových proudů budoucí verze vašeho typu lze deserializovat do aktuální verze typu a naopak.  
  
 Ujistěte se, že víte, že datové členy, i privátní a interní, nelze změnit jejich názvy, typy a i jejich pořadí v budoucích verzích typ Pokud zvláštní je pozor na zachovat smlouvu pomocí explicitní parametry atributů kontraktu dat .  
  
 Testování kompatibility serializace při provádění změn Serializovatelné typy. Zkuste deserializaci na novou verzi do starší verze a naopak.  
  
 **✓ ZVAŽTE** implementace <xref:System.Runtime.Serialization.IExtensibleDataObject> umožňující odezvy mezi různými verzemi typu.  
  
 Rozhraní umožňuje serializátor zajistit, aby žádná data nejsou ztracena během verzemi. <xref:System.Runtime.Serialization.IExtensibleDataObject.ExtensionData%2A?displayProperty=nameWithType> Vlastnost se používá k ukládání dat z budoucí verze typ, který neznámý na aktuální verzi, a proto ji nelze uložit v jeho datových členů. Při aktuální verze je následně serializaci a deserializaci v budoucí verzi, bude další data k dispozici v serializovaném datovém proudu.  
  
## <a name="supporting-xml-serialization"></a>Podpora serializace XML  
 Serializace kontraktu dat je main (výchozí) serializace technologie v rozhraní .NET Framework, ale existují scénáře serializace, která serializace kontraktu dat nepodporuje. Můžete například ji vám neuděluje plnou kontrolu nad tvar XML vytvořeného nebo používané serializátor. Pokud je potřeba takový jemné řízení, serializace XML musí být použit a je třeba navrhnout vaše typy pro podporu této technologie serializace.  
  
 **X nepoužívejte** navrhování vaší typy speciálně pro serializaci XML, pokud nemáte velmi silné důvod k řízení obrazec XML vytvořil. Tato technologie serializace bylo nahrazeno serializaci smlouvy dat, který je popsána v předchozím oddílu.  
  
 **✓ ZVAŽTE** implementace <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, pokud chcete ještě větší kontrolu nad obrazec serializovaných XML než nabízejí použitím atributy serializace XML. Dvě metody rozhraní, <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> a <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A>, vám umožní plně řídit serializovaný datový proud XML. Můžete také ovládat schématu XML, který získá vygeneruje pro typ s použitím `XmlSchemaProviderAttribute`.  
  
## <a name="supporting-runtime-serialization"></a>Podpora modulu Runtime serializace  
 Modul runtime serializace je technologie, pomocí .NET Remoting. Pokud si myslíte, že vaše typy bude přenosu pomocí .NET Remoting, budete muset Ujistěte se, že podporují Runtime serializace.  
  
 Základní podpora pro serializaci Runtime lze zadat použitím <xref:System.SerializableAttribute>, a zahrnovat pokročilejší scénáře implementace jednoduchého serializovatelný vzoru Runtime (implementovat <xref:System.Runtime.Serialization.ISerializable> a zadejte serializace konstruktor).  
  
 **✓ ZVAŽTE** podporuje serializace Runtime v případě, že vaše typy budou použity s .NET Remoting. Například <xref:System.AddIn?displayProperty=nameWithType> používá obor názvů .NET Remoting, a proto všechny typy vyměňují mezi `System.AddIn` doplňky potřebujete pro podporu serializace modulu Runtime.  
  
 **✓ ZVAŽTE** implementace vzoru serializovatelný Runtime, pokud chcete plnou kontrolu nad tímto procesem serializace. Například pokud chcete transformovat data jako jeho získá serializován nebo deserializován.  
  
 Vzor je velmi snadné. Vše je třeba provést je implementovat <xref:System.Runtime.Serialization.ISerializable> rozhraní a zadat speciální konstruktor, který se používá, pokud je objekt deserializován.  
  
 **PROVEĎTE ✓** proveďte konstruktor serializace chráněný a zadat dva parametry typu a s názvem přesně tak, jak je znázorněno v ukázce zde.  
  
```  
[Serializable]  
public class Person : ISerializable {  
    protected Person(SerializationInfo info, StreamingContext context) {  
        ...  
    }  
}  
```  
  
 **PROVEĎTE ✓** implementovat `ISerializable` členy explicitně.  
  
 **PROVEĎTE ✓** použít požadavek propojení na <xref:System.Runtime.Serialization.ISerializable.GetObjectData%2A?displayProperty=nameWithType> implementace. Tím se zajistí, že který pouze plně důvěryhodné jádra a serializátor Runtime měl přístup ke členu.  
  
 *Části © 2005, 2009 Microsoft Corporation. Všechna práva vyhrazena.*  
  
 *Provedení podle oprávnění Pearson Education, Inc. z [pokynů pro návrh Framework: konvence, Idioms a vzory pro jedno použití knihovny .NET, 2. vydání](http://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina a Abrams Brada publikovaná 22 Oct 2008 pomocí Designing Effective jako součást vývoj řady Microsoft Windows.*  
  
## <a name="see-also"></a>Viz také  
 [Pokyny pro návrh Framework](../../../docs/standard/design-guidelines/index.md)  
 [Pokyny týkající se používání](../../../docs/standard/design-guidelines/usage-guidelines.md)

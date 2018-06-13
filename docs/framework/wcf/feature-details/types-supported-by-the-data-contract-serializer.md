---
title: Typy podporované serializátorem kontraktu dat
ms.date: 03/30/2017
helpviewer_keywords:
- serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
ms.openlocfilehash: 9a6279b9850ce5cd3d23cffeaf233dec1b360deb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33504887"
---
# <a name="types-supported-by-the-data-contract-serializer"></a>Typy podporované serializátorem kontraktu dat
Windows Communication Foundation (WCF) používá <xref:System.Runtime.Serialization.DataContractSerializer> jako výchozí modul serializace k převedení dat do XML a převést zpět na data XML. <xref:System.Runtime.Serialization.DataContractSerializer> Je určená k serializaci *kontrakt dat* typy. Však podporuje mnoho dalších typů, které lze chápat tak, že má implicitní data kontrakt. Následuje seznam všech typů, které lze serializovat:  
  
-   Všechny veřejně viditelný typy, které mají konstruktor, který nemá žádné parametry.  
  
-   Datové typy kontrakt. Toto jsou typy, ke kterému <xref:System.Runtime.Serialization.DataContractAttribute> byl použit atribut. Nové vlastní typy, které představují obchodní objekty by za normálních okolností se vytvořit jako data typy kontrakt. Další informace najdete v tématu [pomocí kontrakty dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md) a [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
-   Typy kolekcí. Toto jsou typy, které představují seznam data. Můžou to být regulární pole typy nebo typy kolekcí, například <xref:System.Collections.ArrayList> a <xref:System.Collections.Generic.Dictionary%602>. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Atribut lze použít k přizpůsobení serializace těchto typů, ale není nutné. Další informace najdete v tématu [typy kolekcí v kontraktech dat](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
  
-   Výčtové typy. Výčty, včetně příznak výčty jsou serializable. Volitelně může být výčtové typy označen <xref:System.Runtime.Serialization.DataContractAttribute> atribut, v takovém případě musí každý člen, který je součástí serializace označené <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut. Nejsou členy, které nejsou označené serializovat. Další informace najdete v tématu [výčtové typy v kontraktech dat](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
-   Primitivní typy rozhraní .NET framework. Následující typy integrovaná v rozhraní .NET Framework lze všechny serializovat a jsou považovány za primitivní typy: <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Boolean>, <xref:System.Char>, <xref:System.Decimal>, <xref:System.Object>, a <xref:System.String>.  
  
-   Jiné primitivní typy. Tyto typy nejsou primitiv v rozhraní .NET Framework, ale jsou považovány za primitiv v serializovaném formátu XML. Tyto typy jsou <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>, <xref:System.Xml.XmlQualifiedName>a pole <xref:System.Byte>.  
  
    > [!NOTE]
    >  Na rozdíl od jiných primitivní typy <xref:System.DateTimeOffset> není známý typ ve výchozím nastavení. Další informace najdete v tématu [známé typy kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)).  
  
-   Typy označené jako <xref:System.SerializableAttribute> atribut. Mnoho typů, které jsou součástí [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] základní třídy knihovny patří do této kategorie patří. <xref:System.Runtime.Serialization.DataContractSerializer> Plně podporuje tento serializace programovací model, který byl používán vzdálené komunikace rozhraní .NET Framework, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>, včetně podpory <xref:System.Runtime.Serialization.ISerializable> rozhraní.  
  
-   Typy, které představují nezpracované XML nebo typy, které představují [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] relační data. <xref:System.Xml.XmlElement> a pole <xref:System.Xml.XmlNode> typy se podporují jako způsob reprezentace XML přímo. Kromě toho typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní jsou podporovány, včetně související <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atribut a <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement> typy. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.DataTable> Typu a <xref:System.Data.DataSet> typu (i jejich typu odvozené třídy) všechny implementovat <xref:System.Xml.Serialization.IXmlSerializable> rozhraní a proto nevejde se do této kategorie patří. Další informace najdete v tématu [typy XML a ADO.NET v kontraktech dat](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).  
  
## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a>Režim vztahu omezení použití určitých typů v částečné důvěryhodnosti  
 Následuje seznam omezení při použití určitých typů ve scénářích s částečnou důvěryhodností režimu:  
  
-   K serializaci nebo deserializaci typ, který implementuje <xref:System.Runtime.Serialization.ISerializable> z částečně důvěryhodného kódu pomocí <xref:System.Runtime.Serialization.DataContractSerializer> vyžaduje <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> a <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> oprávnění.  
  
-   Při spuštění kódu WCF [částečné důvěryhodnosti](../../../../docs/framework/wcf/feature-details/partial-trust.md) režimu, serializace a deserializace `readonly` pole (obě `public` a `private`) není podporován. Je to proto, že generovaný IL je nelze ověřit a proto vyžaduje zvýšená oprávnění.  
  
-   Jak <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> jsou podporovány v prostředí s částečnou důvěryhodností. Však použít <xref:System.Runtime.Serialization.DataContractSerializer> se vztahují následující podmínky:  
  
    -   Všechny serializovatelný `[DataContract]` typy musí být veřejné.  
  
    -   Všechny serializovatelný `[DataMember]` polí a vlastností v `[DataContract]` typ musí být veřejné a pro čtení a zápis. Serializace a deserializace `readonly` polí není podporováno při spuštění WCF v aplikaci částečně důvěryhodné.  
  
    -   `[Serializable]` / `ISerializable]` Programovací model není podporována v prostředí s částečnou důvěryhodností.  
  
    -   Známé typy musí být zadaná v konfiguraci úrovně počítače nebo kód (`Machine.config`). Známé typy nelze zadat v konfiguraci na úrovni aplikace z bezpečnostních důvodů.  
  
-   Typy, které implementují <xref:System.Runtime.Serialization.IObjectReference> vyvolána výjimka v prostředí částečně důvěryhodné, protože <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> metoda vyžaduje oprávnění zabezpečení `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]`.  
  
## <a name="additional-notes-on-serialization"></a>Další poznámky k serializaci  
 Následující pravidla platí i pro typy podporované systémem serializátor kontraktu dat:  
  
-   Obecné typy jsou plně podporovány serializátor kontraktu dat.  
  
-   Serializátor kontraktu dat plně podporuje typy s možnou hodnotou Null.  
  
-   Typy rozhraní jsou považovány buď jako <xref:System.Object> nebo v případě rozhraní pro kolekce, jako typy kolekcí.  
  
-   Struktury a třídy jsou podporovány.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Nepodporuje programovací model používané <xref:System.Xml.Serialization.XmlSerializer> a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové služby. Konkrétně nepodporuje atributů, například <xref:System.Xml.Serialization.XmlElementAttribute> a <xref:System.Xml.Serialization.XmlAttributeAttribute>. Povolení podpory pro tento programovací model, musí se použít přepnout WCF <xref:System.Xml.Serialization.XmlSerializer> místo <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
-   <xref:System.DBNull> Typ považuje zvláštním způsobem. Je typu singleton, a při deserializaci deserializátor respektuje jednoznačné omezení a všechny body `DBNull` odkazy na instanci typu singleton. Protože `DBNull` je typu serializable se vyžaduje <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> oprávnění.  
  
## <a name="see-also"></a>Viz také  
 [Typy XML a ADO.NET v kontraktech dat](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)  
 [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md)  
 [Typy kolekcí v kontraktech dat](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)  
 [Výčtové typy v kontraktech dat](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)

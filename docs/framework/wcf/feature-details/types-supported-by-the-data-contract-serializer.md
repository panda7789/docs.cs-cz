---
title: Typy podporované serializátorem kontraktu dat
ms.date: 03/30/2017
helpviewer_keywords:
- serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
ms.openlocfilehash: 1b98b6b3da08ba7a0a37e0c26f58dd4d3ef115b1
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65592199"
---
# <a name="types-supported-by-the-data-contract-serializer"></a>Typy podporované serializátorem kontraktu dat
Windows Communication Foundation (WCF) používá <xref:System.Runtime.Serialization.DataContractSerializer> jako výchozí web serializace převést data na XML a převést zpět na data XML. <xref:System.Runtime.Serialization.DataContractSerializer> Slouží k serializaci *kontraktu dat* typy. Ale podporuje mnoho jiných typů, které si lze představit jako kontrakt implicitní data. Následuje úplný seznam typů, které lze serializovat:  
  
- Všechny veřejně viditelné typy, které mají konstruktor, který nemá žádné parametry.  
  
- Typy kontraktů dat. Toto jsou typy, ke kterému <xref:System.Runtime.Serialization.DataContractAttribute> byl použit atribut. Nové vlastní typy, které představují obchodní objekty by měl obvykle vytvořit, protože data typy kontraktů. Další informace najdete v tématu [kontraktů dat pomocí](../../../../docs/framework/wcf/feature-details/using-data-contracts.md) a [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md).  
  
- Typy kolekcí. Toto jsou typy, které představují seznam data. Může jít o pravidelných polí typy nebo typy kolekcí, jako například <xref:System.Collections.ArrayList> a <xref:System.Collections.Generic.Dictionary%602>. <xref:System.Runtime.Serialization.CollectionDataContractAttribute> Atribut lze použít k přizpůsobení serializaci z těchto typů, ale není potřeba. Další informace najdete v tématu [typy kolekcí v kontraktech dat](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
  
- Výčtové typy. Výčty, včetně příznaku výčty jsou serializovatelné. Volitelně může být označena výčtové typy <xref:System.Runtime.Serialization.DataContractAttribute> atribut, v takovém případě musí být označené každého člena, který se účastní serializace <xref:System.Runtime.Serialization.EnumMemberAttribute> atribut. Členy, které nejsou označené nejsou serializována. Další informace najdete v tématu [výčtové typy v kontraktech dat](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
- Primitivní typy rozhraní .NET framework. Následující typy, které jsou součástí rozhraní .NET Framework lze všechny serializovat a jsou považovány za jednoduché typy: <xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Boolean>, <xref:System.Char>, <xref:System.Decimal>, <xref:System.Object>, a <xref:System.String>.  
  
- Jiné primitivní typy. Tyto typy nejsou primitivních elementů v rozhraní .NET Framework, ale jsou považovány za primitivy ve formuláři serializovaná XML. Tyto typy jsou <xref:System.DateTime>, <xref:System.DateTimeOffset>, <xref:System.TimeSpan>, <xref:System.Guid>, <xref:System.Uri>, <xref:System.Xml.XmlQualifiedName>a pole <xref:System.Byte>.  
  
    > [!NOTE]
    >  Na rozdíl od jiných primitivní typy <xref:System.DateTimeOffset> není známý typ ve výchozím nastavení. Další informace najdete v tématu [známé typy kontraktů dat.](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)).  
  
- Typy označené <xref:System.SerializableAttribute> atribut. Do této kategorie patří mnoho typů, které jsou zahrnuty v knihovně základních tříd rozhraní .NET Framework. <xref:System.Runtime.Serialization.DataContractSerializer> Plně podporuje tento serializace programovací model, který se používá ve vzdálené komunikace rozhraní .NET Framework, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>a <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>, včetně podpory pro <xref:System.Runtime.Serialization.ISerializable> rozhraní.  
  
- Typy, které představují nezpracovaná XML nebo typy, které představují [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] relační data. <xref:System.Xml.XmlElement> a pole <xref:System.Xml.XmlNode> typy jsou podporované jako způsob reprezentace XML přímo. Kromě toho typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní jsou podporované. zahrnuje to související <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atribut a <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement> typy. [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] <xref:System.Data.DataTable> Typ a <xref:System.Data.DataSet> typu (stejně jako jeho typu odvozené třídy) implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní a proto se vejde do této kategorie. Další informace najdete v tématu [typy XML a ADO.NET v kontraktech dat](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).  
  
## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a>Omezení používání určitých typů v částečné důvěryhodnosti režimu  
 Následuje seznam omezení při použití určitých typů ve scénářích s částečnou důvěryhodností režimu:  
  
- K serializaci nebo deserializaci typ, který implementuje <xref:System.Runtime.Serialization.ISerializable> částečně důvěryhodným kódem pomocí <xref:System.Runtime.Serialization.DataContractSerializer> vyžaduje <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> a <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> oprávnění.  
  
- Při spouštění kódu WCF v [částečném vztahu důvěryhodnosti](../../../../docs/framework/wcf/feature-details/partial-trust.md) režimu, serializace a deserializace `readonly` pole (obojí `public` a `private`) se nepodporuje. Je to proto, že generovaný jazyk IL nejde ověřit a proto vyžaduje zvýšenou úroveň oprávnění.  
  
- Jak <xref:System.Runtime.Serialization.DataContractSerializer> a <xref:System.Xml.Serialization.XmlSerializer> jsou podporovány v prostředí s částečnou důvěryhodností. Nicméně použití <xref:System.Runtime.Serialization.DataContractSerializer> podléhá následující podmínky:  
  
    - Všechny serializovatelný `[DataContract]` typy musejí být veřejné.  
  
    - Všechny serializovatelný `[DataMember]` pole nebo vlastnosti v `[DataContract]` typ musí být veřejný a čtení a zápisu. Serializace a deserializace `readonly` polí není podporováno při spouštění v částečně důvěryhodné aplikaci WCF.  
  
    - `[Serializable]` / `ISerializable]` Programovacího modelu není podporován v částečném vztahu důvěryhodnosti prostředí.  
  
    - Známé typy musí být zadán v kódu nebo konfigurace na úrovni počítače (`Machine.config`). Známé typy nelze zadat v konfigurace na úrovni aplikace z bezpečnostních důvodů.  
  
- Typy, které implementují <xref:System.Runtime.Serialization.IObjectReference> vyvolání výjimky v částečně důvěryhodném prostředí, protože <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> metoda vyžaduje oprávnění zabezpečení `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]`.  
  
## <a name="additional-notes-on-serialization"></a>Další poznámky k serializaci  
 Následující pravidla platí také pro typy podporované serializátorem kontraktu dat:  
  
- Obecné typy jsou plně podporované serializátorem kontraktu dat.  
  
- Typy s možnou hodnotou Null jsou plně podporované serializátorem kontraktu dat.  
  
- Typy rozhraní se považují buď jako <xref:System.Object> nebo v případě rozhraní pro kolekce, jako typy kolekcí.  
  
- Struktury a třídy jsou podporovány.  
  
- <xref:System.Runtime.Serialization.DataContractSerializer> Nepodporuje programovací model používaný <xref:System.Xml.Serialization.XmlSerializer> a [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové služby. Konkrétně se nepodporuje atributů, jako je <xref:System.Xml.Serialization.XmlElementAttribute> a <xref:System.Xml.Serialization.XmlAttributeAttribute>. Povolení podpory pro tento model programování, musí být WCF přepnout do použít <xref:System.Xml.Serialization.XmlSerializer> místo <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
- <xref:System.DBNull> Typ je zpracováván zvláštním způsobem. Jde o typ singleton, a po deserializace deserializátor respektuje jednoznačné omezení a všechny body `DBNull` odkazy na instanci typu singleton. Protože `DBNull` je serializovatelný typ., se vyžaduje <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> oprávnění.  
  
## <a name="see-also"></a>Viz také:

- [Typy XML a ADO.NET v kontraktech dat](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)
- [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md)
- [Typy kolekcí v kontraktech dat](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)
- [Výčtové typy v kontraktech dat](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)

---
title: Typy podporované serializátorem kontraktu dat
ms.date: 03/30/2017
helpviewer_keywords:
- serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
ms.openlocfilehash: f3eedda6c9493688680099f4b07810aebf69ff8a
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249458"
---
# <a name="types-supported-by-the-data-contract-serializer"></a>Typy podporované serializátorem kontraktu dat

Windows Communication Foundation (WCF) používá <xref:System.Runtime.Serialization.DataContractSerializer> jako výchozí serializační modul k převodu dat do xml a k převodu XML zpět na data. Je <xref:System.Runtime.Serialization.DataContractSerializer> určen k serializaci typů *kontraktů dat.* Podporuje však mnoho dalších typů, které si lze myslet jako s implicitní smlouvy dat. Následuje úplný seznam typů, které lze serializovat:

- Všechny veřejně viditelné typy, které mají konstruktor, který nemá parametry.

- Typy kontraktů dat. Jedná se o <xref:System.Runtime.Serialization.DataContractAttribute> typy, na které byl atribut použit. Nové vlastní typy, které představují obchodní objekty by měly být obvykle vytvořeny jako typy kontraktů dat. Další informace naleznete [v tématu Using Data Contracts](../../../../docs/framework/wcf/feature-details/using-data-contracts.md) and [Serializable Types](../../../../docs/framework/wcf/feature-details/serializable-types.md).

- Typy kolekce. Jedná se o typy, které představují seznamy dat. Mohou to být pravidelná pole typů nebo <xref:System.Collections.ArrayList> typů <xref:System.Collections.Generic.Dictionary%602>kolekcí, například a . Atribut <xref:System.Runtime.Serialization.CollectionDataContractAttribute> lze přizpůsobit serializace těchto typů, ale není vyžadováno. Další informace naleznete [v tématu Typy kolekce v datových kontraktech](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).

- Typy výčtu. Výčty, včetně výčtů příznaku, jsou serializovatelné. Volitelně mohou být typy výčtu <xref:System.Runtime.Serialization.DataContractAttribute> označeny atributem, v takovém případě musí být <xref:System.Runtime.Serialization.EnumMemberAttribute> každý člen, který se účastní serializace, označen atributem. Členy, které nejsou označeny nejsou serializovány. Další informace naleznete [v tématu Typy výčtu v datových kontraktech](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).

- Primitivní typy rozhraní .NET Framework. Následující typy integrované do rozhraní .NET Framework lze serializovat a <xref:System.Byte>jsou <xref:System.SByte> <xref:System.Int16>považovány <xref:System.Int32> <xref:System.Int64>za <xref:System.UInt16> <xref:System.UInt32>primitivní <xref:System.UInt64> <xref:System.Single>typy: , , , , , , , <xref:System.Double> <xref:System.Boolean>, <xref:System.Char> <xref:System.Decimal>, , <xref:System.Object>, , , , , a <xref:System.String>.

- Jiné primitivní typy. Tyto typy nejsou primitivy v rozhraní .NET Framework, ale jsou považovány za primitiva v serializovaném formuláři XML. Jedná se <xref:System.DateTime> <xref:System.DateTimeOffset>o <xref:System.TimeSpan> <xref:System.Byte>, <xref:System.Uri> <xref:System.Xml.XmlQualifiedName>, , <xref:System.Guid>, , a pole .

  > [!NOTE]
  > Na rozdíl od <xref:System.DateTimeOffset> jiných primitivních typů není ve výchozím nastavení známým typem. Další informace naleznete v [tématu Data Contract Známé typy](../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)).

- Typy označené <xref:System.SerializableAttribute> atributem. Do této kategorie spadá mnoho typů zahrnutých do knihovny základních tříd rozhraní .NET Framework. Plně <xref:System.Runtime.Serialization.DataContractSerializer> podporuje tento programovací model serializace, který byl používán <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>vzdálené <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter>komunikace rozhraní .NET Framework, a , včetně podpory <xref:System.Runtime.Serialization.ISerializable> pro rozhraní.

- Typy, které představují nezpracovaná XML nebo typy, které představují ADO.NET relační data. A <xref:System.Xml.XmlElement> pole <xref:System.Xml.XmlNode> typů jsou podporovány jako způsob, jak reprezentovat XML přímo. Kromě toho typy, <xref:System.Xml.Serialization.IXmlSerializable> které implementují rozhraní <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> jsou podporovány, včetně související atribut a <xref:System.Xml.Linq.XDocument> a <xref:System.Xml.Linq.XElement> typy. Typ<xref:System.Data.DataTable> ADO.NET a <xref:System.Data.DataSet> typ (stejně jako jeho zadané odvozené <xref:System.Xml.Serialization.IXmlSerializable> třídy) všechny implementovat rozhraní a proto se vejde do této kategorie. Další informace naleznete v tématu [XML a ADO.NET typy v datových kontraktech](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md).

## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a>Omezení používání určitých typů v režimu částečné důvěryhodnosti

Následuje seznam omezení při použití určitých typů ve scénářích režimu částečné důvěryhodnosti:

- Chcete-li serializovat nebo rekonstruovat typ, <xref:System.Runtime.Serialization.ISerializable> který implementuje <xref:System.Runtime.Serialization.DataContractSerializer> v <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> částečně <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> důvěryhodném kódu pomocí vyžaduje a oprávnění.

- Při spuštění kódu WCF v režimu [částečné důvěryhodnosti](../../../../docs/framework/wcf/feature-details/partial-trust.md) není serializace a deserializace `readonly` polí (jak a `public` `private`) podporována. Důvodem je, že generované IL je neověřitelné a proto vyžaduje zvýšená oprávnění.

- A <xref:System.Runtime.Serialization.DataContractSerializer> jsou <xref:System.Xml.Serialization.XmlSerializer> podporovány v prostředí částečné důvěryhodnosti. Použití <xref:System.Runtime.Serialization.DataContractSerializer> však podléhá následujícím podmínkám:

  - Všechny serializovatelné `[DataContract]` typy musí být veřejné.

  - Všechna serializovatelná `[DataMember]` pole nebo `[DataContract]` vlastnosti typu musí být veřejné a číst i zapisovat. Serializace a deserializace `readonly` polí není podporována při spuštění WCF v částečně důvěryhodné aplikaci.

  - Programovací `[Serializable]` / `ISerializable]` model není podporován v prostředí částečné důvěryhodnosti.

  - Známé typy musí být zadány v`Machine.config`konfiguraci kódu nebo na úrovni počítače ( ). Známé typy nelze zadat v konfiguraci na úrovni aplikace z bezpečnostních důvodů.

- Typy, <xref:System.Runtime.Serialization.IObjectReference> které implementují vyvolat výjimku <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> v částečně důvěryhodném prostředí, protože metoda vyžaduje oprávnění `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]`zabezpečení .

## <a name="additional-notes-on-serialization"></a>Další poznámky k serializaci

Následující pravidla platí také pro typy podporované serializátorem kontraktů dat:

- Obecné typy jsou plně podporovány serializátorem kontraktů dat.

- Typy hodnot s možnou hodnotou s nulou jsou plně podporovány serializátorem kontraktů dat.

- Typy rozhraní jsou považovány <xref:System.Object> buď jako nebo, v případě rozhraní kolekce, jako typy kolekcí.

- Podporovány jsou struktury i třídy.

- Programovací <xref:System.Runtime.Serialization.DataContractSerializer> model používaný a ASP.NET <xref:System.Xml.Serialization.XmlSerializer> webových služeb. Zejména nepodporuje atributy jako <xref:System.Xml.Serialization.XmlElementAttribute> a <xref:System.Xml.Serialization.XmlAttributeAttribute>. Chcete-li povolit podporu pro tento programovací model, WCF musí být přepnuty použít <xref:System.Xml.Serialization.XmlSerializer> místo . <xref:System.Runtime.Serialization.DataContractSerializer>

- Typ <xref:System.DBNull> je ošetřen zvláštním způsobem. Jedná se o typ singleton a při deserializaci deserializátor respektuje `DBNull` omezení singleton a odkazuje na všechny odkazy na instanci singleton. Protože `DBNull` je serializovatelný typ, <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> vyžaduje oprávnění.

## <a name="see-also"></a>Viz také

- [Typy XML a ADO.NET v kontraktech dat](../../../../docs/framework/wcf/feature-details/xml-and-ado-net-types-in-data-contracts.md)
- [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)
- [Serializovatelné typy](../../../../docs/framework/wcf/feature-details/serializable-types.md)
- [Typy kolekcí v kontraktech dat](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md)
- [Výčtové typy v kontraktech dat](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md)

---
title: Typy podporované serializátorem kontraktu dat
description: Podívejte se na úplný seznam typů, které serializátor kontraktu dat WCF podporuje pro serializaci a deserializaci.
ms.date: 03/30/2017
helpviewer_keywords:
- serialization [WCF], supported types
ms.assetid: 7381b200-437a-4506-9556-d77bf1bc3f34
ms.openlocfilehash: ef9d2e61ab7121c97bd474bb151fee32907b1dac
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246529"
---
# <a name="types-supported-by-the-data-contract-serializer"></a>Typy podporované serializátorem kontraktu dat

Windows Communication Foundation (WCF) používá <xref:System.Runtime.Serialization.DataContractSerializer> jako svůj výchozí Serializační modul nástroj k převodu dat do formátu XML a k převodu XML zpátky na data. <xref:System.Runtime.Serialization.DataContractSerializer>Je určen k serializaci typů *kontraktů dat* . Podporuje ale mnoho dalších typů, což se dá představit jako u implicitního kontraktu dat. Následuje úplný seznam typů, které mohou být serializovány:

- Všechny veřejně viditelné typy, které mají konstruktor, který nemá parametry.

- Typy kontraktů dat. Jedná se o typy, na které byl <xref:System.Runtime.Serialization.DataContractAttribute> atribut použit. Nové vlastní typy, které reprezentují obchodní objekty, by se normálně měly vytvářet jako typy kontraktů dat. Další informace najdete v tématu [použití datových kontraktů](using-data-contracts.md) a [serializovatelných typů](serializable-types.md).

- Typy kolekcí. Jedná se o typy, které představují seznamy dat. Může se jednat o běžná pole typů nebo typů kolekcí, jako jsou <xref:System.Collections.ArrayList> a <xref:System.Collections.Generic.Dictionary%602> . <xref:System.Runtime.Serialization.CollectionDataContractAttribute>Atribut lze použít k přizpůsobení serializace těchto typů, ale není vyžadováno. Další informace najdete v tématu [typy kolekcí v kontraktech dat](collection-types-in-data-contracts.md).

- Výčtové typy. Výčty, včetně výčtů příznaků, jsou serializovatelné. V případě potřeby lze označit výčtové typy pomocí <xref:System.Runtime.Serialization.DataContractAttribute> atributu. v takovém případě musí být každý člen, který je součástí serializace, označen <xref:System.Runtime.Serialization.EnumMemberAttribute> atributem. Členy, kteří nejsou označeni, nejsou serializovány. Další informace najdete v tématu [výčtové typy v kontraktech dat](enumeration-types-in-data-contracts.md).

- .NET Framework primitivních typů. Následující typy integrované do .NET Framework mohou být serializovány a jsou považovány za primitivní typy: <xref:System.Byte> , <xref:System.SByte> , <xref:System.Int16> , <xref:System.Int32> , <xref:System.Int64> , <xref:System.UInt16> , <xref:System.UInt32> , <xref:System.UInt64> , <xref:System.Single> , <xref:System.Double> , <xref:System.Boolean> , <xref:System.Char> ,, a <xref:System.Decimal> <xref:System.Object> <xref:System.String> .

- Jiné primitivní typy. Tyto typy nejsou primitivními prvky v .NET Framework, ale jsou považovány za primitivnís v serializovaném formátu XML. Tyto typy jsou <xref:System.DateTime> ,,,,, <xref:System.DateTimeOffset> <xref:System.TimeSpan> <xref:System.Guid> <xref:System.Uri> <xref:System.Xml.XmlQualifiedName> a pole <xref:System.Byte> .

  > [!NOTE]
  > Na rozdíl od jiných primitivních typů <xref:System.DateTimeOffset> není ve výchozím nastavení známý typ. Další informace najdete v tématu [známé typy kontraktu dat](data-contract-known-types.md).

- Typy označené <xref:System.SerializableAttribute> atributem. Do této kategorie patří mnoho typů, které jsou součástí knihovny tříd .NET Framework Base. <xref:System.Runtime.Serialization.DataContractSerializer>Plně podporuje tento model programování serializace, který byl použit .NET Framework vzdálené komunikace, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> a, <xref:System.Runtime.Serialization.Formatters.Soap.SoapFormatter> včetně podpory <xref:System.Runtime.Serialization.ISerializable> rozhraní.

- Typy, které reprezentují nezpracované XML nebo typy, které reprezentují relační data ADO.NET. <xref:System.Xml.XmlElement>Pole a <xref:System.Xml.XmlNode> typy jsou podporovány jako způsob, jak přímo reprezentovat XML. Kromě toho jsou podporovány typy, které implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní, včetně souvisejících <xref:System.Xml.Serialization.XmlSchemaProviderAttribute> atributů a <xref:System.Xml.Linq.XDocument> <xref:System.Xml.Linq.XElement> typů a. Typ ADO.NET <xref:System.Data.DataTable> a <xref:System.Data.DataSet> typ (stejně jako jeho typové odvozené třídy) implementují <xref:System.Xml.Serialization.IXmlSerializable> rozhraní a proto se vejdou do této kategorie. Další informace najdete v tématu [typy XML a ADO.NET v kontraktech dat](xml-and-ado-net-types-in-data-contracts.md).

## <a name="limitations-of-using-certain-types-in-partial-trust-mode"></a>Omezení používání určitých typů v režimu s částečnou důvěryhodností

Následuje seznam omezení při použití určitých typů ve scénářích s částečnou důvěryhodností:

- Pro serializaci nebo deserializaci typu, který implementuje <xref:System.Runtime.Serialization.ISerializable> v částečně důvěryhodném kódu pomocí <xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> oprávnění a <xref:System.Security.Permissions.SecurityPermissionAttribute.UnmanagedCode%2A> .

- Při spuštění kódu WCF v režimu [částečné důvěryhodnosti](partial-trust.md) není podporována serializace a deserializace `readonly` polí ( `public` a `private` ). Důvodem je, že vygenerovaná úroveň důvěryhodnosti je neověřená, a proto vyžaduje zvýšená oprávnění.

- <xref:System.Runtime.Serialization.DataContractSerializer>A <xref:System.Xml.Serialization.XmlSerializer> jsou podporovány v prostředí s částečným vztahem důvěryhodnosti. Použití nástroje však <xref:System.Runtime.Serialization.DataContractSerializer> podléhá následujícím podmínkám:

  - Všechny serializovatelné `[DataContract]` typy musí být veřejné.

  - Všechna serializovatelný `[DataMember]` pole nebo vlastnosti v `[DataContract]` typu musí být veřejná a musí mít oprávnění ke čtení a zápisu. Serializace a deserializace `readonly` polí není podporována při spuštění WCF v částečně důvěryhodné aplikaci.

  - `[Serializable]` / `ISerializable]` Programovací model není podporován v prostředí s částečným vztahem důvěryhodnosti.

  - V kódu nebo konfiguraci na úrovni počítače () musí být zadané známé typy `Machine.config` . Známé typy nelze v konfiguraci na úrovni aplikace zadat z bezpečnostních důvodů.

- Typy, které implementují <xref:System.Runtime.Serialization.IObjectReference> výjimku v částečně důvěryhodném prostředí, protože <xref:System.Runtime.Serialization.IObjectReference.GetRealObject%2A> metoda vyžaduje oprávnění zabezpečení `[SecurityPermission(SecurityAction.LinkDemand, Flags=SecurityPermissionFlag.SerializationFormatter)]` .

## <a name="additional-notes-on-serialization"></a>Další poznámky k serializaci

Následující pravidla platí také pro typy podporované serializátorem kontraktu dat:

- Obecné typy jsou plně podporovány serializátorem kontraktu dat.

- Serializátor kontraktu dat plně podporuje typy hodnot s možnou hodnotou null.

- Typy rozhraní jsou ošetřeny buď jako <xref:System.Object> nebo, v případě rozhraní kolekce jako typy kolekce.

- Jsou podporovány jak struktury, tak třídy.

- Nepodporuje <xref:System.Runtime.Serialization.DataContractSerializer> programovací model používaný <xref:System.Xml.Serialization.XmlSerializer> ASP.NET webovými službami a. Konkrétně nepodporuje atributy jako <xref:System.Xml.Serialization.XmlElementAttribute> a <xref:System.Xml.Serialization.XmlAttributeAttribute> . Chcete-li povolit podporu pro tento programovací model, musí být WCF přepnuto na použití <xref:System.Xml.Serialization.XmlSerializer> namísto <xref:System.Runtime.Serialization.DataContractSerializer> .

- <xref:System.DBNull>Typ je zpracován zvláštním způsobem. Je to typ singleton a po deserializaci deserializace respektuje omezení singleton a odkazuje na všechny `DBNull` odkazy na instanci typu singleton. Protože `DBNull` je serializovatelný typ, vyžaduje <xref:System.Security.Permissions.SecurityPermissionAttribute.SerializationFormatter%2A> oprávnění.

## <a name="see-also"></a>Viz také

- [Typy XML a ADO.NET v kontraktech dat](xml-and-ado-net-types-in-data-contracts.md)
- [Použití kontraktů dat](using-data-contracts.md)
- [Serializovatelné typy](serializable-types.md)
- [Typy kolekcí v kontraktech dat](collection-types-in-data-contracts.md)
- [Výčtové typy v kontraktech dat](enumeration-types-in-data-contracts.md)

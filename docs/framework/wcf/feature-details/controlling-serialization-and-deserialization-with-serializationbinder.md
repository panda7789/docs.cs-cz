---
title: Řízení serializace a deserializace pomocí třídy SerializationBinder
ms.date: 07/14/2020
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
ms.openlocfilehash: 5a7d0bf2aabfcdf789a77cf0fcfeb26357575806
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/17/2020
ms.locfileid: "86444479"
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>Řízení serializace a deserializace pomocí třídy SerializationBinder

> [!WARNING]
> <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>***není bezpečné a nelze ji zabezpečit*** . Další informace najdete v [příručce zabezpečení BinaryFormatter](../../../standard/serialization/binaryformatter-security-guide.md).

Během serializace přenáší formátovací modul informace potřebné k vytvoření instance objektu správného typu a verze. Tyto informace obecně obsahují úplný název typu a název sestavení objektu. Ve výchozím nastavení deserializace používá tyto informace k vytvoření instance identického objektu. Někteří uživatelé mohou potřebovat určit, která třída se má serializovat a deserializovat, buď protože původní třída nesmí existovat na počítači provádějícím deserializaci, původní třída byla přesunuta mezi sestaveními nebo na serveru a klientovi je vyžadována jiná verze třídy. Další informace najdete v tématu [použití pořadače serializace](../samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
> Tato funkce je k dispozici pouze v případě, že používáte <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> nebo <xref:System.Runtime.Serialization.NetDataContractSerializer> .  
  
## <a name="using-serializationbinder"></a>Použití SerializationBinder  
 <xref:System.Runtime.Serialization.SerializationBinder>je abstraktní třída, která slouží k řízení skutečných typů použitých během serializace a deserializace. Chcete-li řídit typy používané při serializaci a deserializaci, odvodit třídu z <xref:System.Runtime.Serialization.SerializationBinder> a <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> Přepsat <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> metody a. <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)>Metoda přijímá <xref:System.Type> a vrátí sestavení a název typu. <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)>Metoda přebírá sestavení a název typu a vrátí <xref:System.Type> .  
  
## <a name="see-also"></a>Viz také

- [Serializace a deserializace](serialization-and-deserialization.md)
- [Použití vazače serializace](../samples/usage-of-serialization-binder.md)

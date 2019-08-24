---
title: Řízení serializace a deserializace pomocí třídy SerializationBinder
ms.date: 03/30/2017
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
ms.openlocfilehash: 29d48560cf25cd5c2e34d7a512d8c7079c65879e
ms.sourcegitcommit: 37616676fde89153f563a485fc6159fc57326fc2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/23/2019
ms.locfileid: "69988214"
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>Řízení serializace a deserializace pomocí třídy SerializationBinder
Během serializace přenáší formátovací modul informace potřebné k vytvoření instance objektu správného typu a verze. Tyto informace obecně obsahují úplný název typu a název sestavení objektu. Ve výchozím nastavení deserializace používá tyto informace k vytvoření instance identického objektu. Někteří uživatelé mohou potřebovat určit, která třída se má serializovat a deserializovat, buď protože původní třída nesmí existovat na počítači provádějícím deserializaci, původní třída byla přesunuta mezi sestaveními nebo je vyžadována jiná verze třídy na Server a klient. Další informace najdete v tématu [použití pořadače serializace](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
> Tato funkce je k dispozici pouze v <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> případě, <xref:System.Runtime.Serialization.NetDataContractSerializer>že používáte nebo.  
  
## <a name="using-serializationbinder"></a>Použití SerializationBinder  
 <xref:System.Runtime.Serialization.SerializationBinder>je abstraktní třída, která slouží k řízení skutečných typů použitých během serializace a deserializace. Chcete-li řídit typy používané při serializaci a deserializaci, odvodit <xref:System.Runtime.Serialization.SerializationBinder> třídu z a <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> přepsat <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> metody a. <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> Metoda<xref:System.Type> přijímá a vrátí sestavení a název typu. Metoda přebírá sestavení a název typu a <xref:System.Type>vrátí. <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)>  
  
## <a name="see-also"></a>Viz také:

- [Serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)
- [Použití vazače serializace](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)

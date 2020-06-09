---
title: Řízení serializace a deserializace pomocí třídy SerializationBinder
ms.date: 03/30/2017
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
ms.openlocfilehash: 1101a3caf2a033b4dbbc5f45737f187c58adbef2
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595567"
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>Řízení serializace a deserializace pomocí třídy SerializationBinder
Během serializace přenáší formátovací modul informace potřebné k vytvoření instance objektu správného typu a verze. Tyto informace obecně obsahují úplný název typu a název sestavení objektu. Ve výchozím nastavení deserializace používá tyto informace k vytvoření instance identického objektu. Někteří uživatelé mohou potřebovat určit, která třída se má serializovat a deserializovat, buď protože původní třída nesmí existovat na počítači provádějícím deserializaci, původní třída byla přesunuta mezi sestaveními nebo na serveru a klientovi je vyžadována jiná verze třídy. Další informace najdete v tématu [použití pořadače serializace](../samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
> Tato funkce je k dispozici pouze v případě, že používáte <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> nebo <xref:System.Runtime.Serialization.NetDataContractSerializer> .  
  
## <a name="using-serializationbinder"></a>Použití SerializationBinder  
 <xref:System.Runtime.Serialization.SerializationBinder>je abstraktní třída, která slouží k řízení skutečných typů použitých během serializace a deserializace. Chcete-li řídit typy používané při serializaci a deserializaci, odvodit třídu z <xref:System.Runtime.Serialization.SerializationBinder> a <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> Přepsat <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> metody a. <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)>Metoda přijímá <xref:System.Type> a vrátí sestavení a název typu. <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)>Metoda přebírá sestavení a název typu a vrátí <xref:System.Type> .  
  
## <a name="see-also"></a>Viz také

- [Serializace a deserializace](serialization-and-deserialization.md)
- [Použití vazače serializace](../samples/usage-of-serialization-binder.md)

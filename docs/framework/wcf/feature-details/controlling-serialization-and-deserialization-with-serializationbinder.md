---
title: Řízení serializace a deserializace pomocí třídy SerializationBinder
ms.date: 03/30/2017
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
ms.openlocfilehash: 3252413606f4aaf45a825d8d0a6f4af8763ef6be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>Řízení serializace a deserializace pomocí třídy SerializationBinder
Během serializace formátování přenáší informace požadované pro vytvoření instance objektu správný typ a verze. Tyto informace zahrnují obecně zadejte úplný název a název sestavení objektu. Ve výchozím nastavení používá deserializace tyto informace k vytvoření instance objektu stejné. Někteří uživatelé mohou potřebovat k řízení které třídy k serializaci a deserializaci, buď protože původní třída nemusí existovat v počítači provádění deserializace, původní třída přesunul mezi sestavení nebo jinou verzi třídy je vyžadován na Server a klienta. Další informace najdete v tématu [použití vazače serializace](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
>  Tato funkce je dostupná pouze při použití <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> nebo <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
## <a name="using-serializationbinder"></a>Pomocí třídy SerializationBinder  
 <xref:System.Runtime.Serialization.SerializationBinder>je abstraktní třídu použít k řízení skutečné typy používané během serializace a deserializace. Pokud chcete řídit typy používané během serializace a deserializace, odvození třídy z <xref:System.Runtime.Serialization.SerializationBinder> a přepsat <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> a <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> metody. <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> Metoda trvá <xref:System.Type> a vrátí název sestavení a typu. <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> Metoda přebírá název sestavení a typ a vrátí <xref:System.Type>.  
  
## <a name="see-also"></a>Viz také  
 [Serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [Použití vazače serializace](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)

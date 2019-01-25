---
title: Řízení serializace a deserializace pomocí třídy SerializationBinder
ms.date: 03/30/2017
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
ms.openlocfilehash: 518a9bc88dd291f608f736a47a107549e399eb94
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629498"
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>Řízení serializace a deserializace pomocí třídy SerializationBinder
Během serializace formátovací modul přenáší informace potřebné k vytvoření instance objektu správný typ a verze. Tyto informace obecně zahrnuje úplný název typu a název objektu sestavení. Ve výchozím nastavení používá deserializace tyto informace k vytvoření instance objektu stejné. Někteří uživatelé muset které třídu k serializaci a deserializaci buď protože původní třídy nemusí existovat v počítači, provádí se serializace ovládacího prvku, původní třídy přesunula mezi sestaveními, nebo na jinou verzi třídy je vyžadován na Server a klienta. Další informace najdete v tématu [použití vazače serializace](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
>  Tato funkce je dostupná jenom při použití <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> nebo <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
## <a name="using-serializationbinder"></a>Pomocí třídy SerializationBinder  
 <xref:System.Runtime.Serialization.SerializationBinder>je abstraktní třídu použít k řízení skutečné typy používané během serializace a deserializace. Pokud chcete řídit typy používané během serializace a deserializace, odvoďte třídu z <xref:System.Runtime.Serialization.SerializationBinder> a přepsat <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> a <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> metody. <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> Přijímá metodu <xref:System.Type> a vrátí sestavení a zadejte název. <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> Metoda přebírá sestavení a zadejte název a vrátí <xref:System.Type>.  
  
## <a name="see-also"></a>Viz také:
- [Serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)
- [Použití vazače serializace](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)

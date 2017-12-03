---
title: "Řízení serializace a deserializace pomocí třídy SerializationBinder"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ba8dcecf-acc7-467c-939d-021bbac797d4
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 67afc6dbc069678c8fb692f70bc0e7a0a12b1076
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="controlling-serialization-and-deserialization-with-serializationbinder"></a>Řízení serializace a deserializace pomocí třídy SerializationBinder
Během serializace formátování přenáší informace požadované pro vytvoření instance objektu správný typ a verze. Tyto informace zahrnují obecně zadejte úplný název a název sestavení objektu. Ve výchozím nastavení používá deserializace tyto informace k vytvoření instance objektu stejné. Někteří uživatelé mohou potřebovat k řízení které třídy k serializaci a deserializaci, buď protože původní třída nemusí existovat v počítači provádění deserializace, původní třída přesunul mezi sestavení nebo jinou verzi třídy je vyžadován na Server a klienta. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Použití vazače serializace](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md).  
  
> [!WARNING]
>  Tato funkce je dostupná pouze při použití <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> nebo <xref:System.Runtime.Serialization.NetDataContractSerializer>.  
  
## <a name="using-serializationbinder"></a>Pomocí třídy SerializationBinder  
 <xref:System.Runtime.Serialization.SerializationBinder>je abstraktní třídu použít k řízení skutečné typy používané během serializace a deserializace. Pokud chcete řídit typy používané během serializace a deserializace, odvození třídy z <xref:System.Runtime.Serialization.SerializationBinder> a přepsat <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> a <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> metody. <xref:System.Runtime.Serialization.SerializationBinder.BindToName(System.Type,System.String@,System.String@)> Metoda trvá <xref:System.Type> a vrátí název sestavení a typu. <xref:System.Runtime.Serialization.SerializationBinder.BindToType(System.String,System.String)> Metoda přebírá název sestavení a typ a vrátí <xref:System.Type>.  
  
## <a name="see-also"></a>Viz také  
 [Serializace a deserializace](../../../../docs/framework/wcf/feature-details/serialization-and-deserialization.md)  
 [Použití vazače serializace](../../../../docs/framework/wcf/samples/usage-of-serialization-binder.md)

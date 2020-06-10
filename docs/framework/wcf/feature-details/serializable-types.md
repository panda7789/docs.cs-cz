---
title: Serializovatelné typy
ms.date: 03/30/2017
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
ms.openlocfilehash: e65fcb93c5c36bb289b825cef58b3adc6f5155f5
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84586101"
---
# <a name="serializable-types"></a>Serializovatelné typy
Ve výchozím nastavení jsou <xref:System.Runtime.Serialization.DataContractSerializer> všechny veřejně viditelné typy serializovány. Všechny veřejné vlastnosti pro čtení i zápis a pole typu jsou serializovány.  
  
 Můžete změnit výchozí chování pomocí <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> atributů a na typy a členy, které tato funkce může být užitečná v situacích, kdy máte typy, které nejsou pod vaší kontrolou a nelze je upravit pro přidání atributů. <xref:System.Runtime.Serialization.DataContractSerializer>Rozpozná takové "neoznačené" typy.  
  
## <a name="serialization-defaults"></a>Výchozí hodnoty serializace  
 Atributy a můžete použít <xref:System.Runtime.Serialization.DataContractAttribute> <xref:System.Runtime.Serialization.DataMemberAttribute> k explicitnímu řízení nebo přizpůsobení serializace typů a členů. Kromě toho můžete tyto atributy použít u soukromých polí. Nicméně i typy, které nejsou označeny těmito atributy, jsou serializovány a deserializovány. Platí následující pravidla a výjimky:  
  
- <xref:System.Runtime.Serialization.DataContractSerializer>Odvodí kontrakt dat z typů bez atributů pomocí výchozích vlastností nově vytvořených typů.  
  
- Všechna veřejná pole a vlastnosti s veřejnými `get` a `set` metodami jsou serializovány, pokud atribut nepoužijete <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> pro daného člena.  
  
- Sémantika serializace je podobná těm z <xref:System.Xml.Serialization.XmlSerializer> .  
  
- V neoznačených typech jsou serializovány pouze veřejné typy s konstruktory, které nemají parametry. Výjimkou z tohoto pravidla se <xref:System.Runtime.Serialization.ExtensionDataObject> používá s <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraním.  
  
- Pole jen pro čtení, vlastnosti bez `get` metody nebo `set` a vlastnosti s interními nebo soukromými `set` nebo `get` metodami nejsou serializovány. Tyto vlastnosti jsou ignorovány a není vyvolána žádná výjimka, s výjimkou případů, kdy jsou kolekce pouze pro Get.  
  
- <xref:System.Xml.Serialization.XmlSerializer>atributy (například `XmlElement` , `XmlAttribute` ,, `XmlIgnore` `XmlInclude` a tak dále) jsou ignorovány.  
  
- Pokud nepoužijete <xref:System.Runtime.Serialization.DataContractAttribute> atribut na daný typ, serializátor ignoruje všechny členy v tomto typu, na který <xref:System.Runtime.Serialization.DataMemberAttribute> je atribut použit.  
  
- <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A>Vlastnost je podporována v typech, které nejsou označeny <xref:System.Runtime.Serialization.DataContractAttribute> atributem. To zahrnuje podporu pro <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut u neoznačených typů.  
  
- Chcete-li odhlásit z procesu serializace pro veřejné členy, vlastnosti nebo pole, použijte <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atribut pro daného člena.  
  
## <a name="inheritance"></a>Dědičnost  
 Neoznačené typy (typy bez <xref:System.Runtime.Serialization.DataContractAttribute> atributu) můžou dědit z typů, které mají tento atribut, ale reverzní není povolený: typy s atributem nemůžou dědit z neoznačených typů. Toto pravidlo je vynutilo primárně, aby se zajistila zpětná kompatibilita s kódem napsaným v dřívějších verzích .NET Framework.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Typy podporované serializátorem kontraktu dat](types-supported-by-the-data-contract-serializer.md)

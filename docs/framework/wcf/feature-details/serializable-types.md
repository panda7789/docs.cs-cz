---
title: "Serializovatelné typy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6f053edc688080293b6fae927049bf6776551b7c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="serializable-types"></a>Serializovatelné typy
Ve výchozím nastavení <xref:System.Runtime.Serialization.DataContractSerializer> serializuje všechny typy veřejně viditelný. Všechny veřejné vlastnosti a pole typu se serializují.  
  
 Můžete změnit výchozí chování použitím <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy typy a členy této funkce může být užitečné v situacích, kdy máte typy, které nejsou ve vaší kontrole a nemůže být upraven k přidání atributů. <xref:System.Runtime.Serialization.DataContractSerializer> Rozpozná takové "Zrušit označení" typy.  
  
## <a name="serialization-defaults"></a>Výchozí serializace  
 Můžete použít <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy explicitně řízení nebo upravit serializaci typů a členů. Kromě toho můžete použít tyto atributy pro soukromá pole. I typy, které nejsou označené jako tyto atributy se však serializovat a deserializovat. Platí následující pravidla a výjimky:  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Odvodí kontraktu dat z typů bez atributů s použitím výchozí vlastnosti nově vytvořený typů.  
  
-   Všechny veřejné polí a vlastností s veřejnou `get` a `set` se serializují metody, pokud použijete <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atribut tohoto člena.  
  
-   Sémantika serializace je podobné jako u <xref:System.Xml.Serialization.XmlSerializer>.  
  
-   Zrušit označení typy jsou serializovat pouze veřejné typů pomocí konstruktorů, které nemají parametry. Výjimka, která má toto pravidlo je <xref:System.Runtime.Serialization.ExtensionDataObject> použít s <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní.  
  
-   Pole jen pro čtení, vlastnosti bez `get` nebo `set` metody a vlastnosti s interní nebo privátní `set` nebo `get` nejsou serializované metody. Tyto vlastnosti jsou ignorovány a nedojde k výjimce, s výjimkou pouze pro získání kolekce.  
  
-   <xref:System.Xml.Serialization.XmlSerializer>atributy (například `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`a tak dále) jsou ignorovány.  
  
-   Pokud se nevztahují <xref:System.Runtime.Serialization.DataContractAttribute> atribut k danému typu serializátor ignoruje kteréhokoli člena v tomto typu, ke kterému <xref:System.Runtime.Serialization.DataMemberAttribute> atribut se používá.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> Vlastnost je podporována v typech neoznačené <xref:System.Runtime.Serialization.DataContractAttribute> atribut. To zahrnuje podporu pro <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut na neoznačených typy.  
  
-   Chcete-li "chodit" procesu serializace pro veřejné členy, vlastnosti nebo pole, použít <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atribut tohoto člena.  
  
## <a name="inheritance"></a>Dědičnost  
 Zrušit označení typy (typy bez <xref:System.Runtime.Serialization.DataContractAttribute> atribut) může dědit vlastnosti z typů, které mají tento atribut; však není povoleno naopak: typy s atributem nelze zrušit označení typy dědí. Toto pravidlo se vynucuje hlavně kvůli zajištění zpětné kompatibility s kód napsaný v dřívějších verzích [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [Typy podporované systémem serializátor kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)

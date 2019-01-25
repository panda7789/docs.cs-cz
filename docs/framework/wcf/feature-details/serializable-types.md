---
title: Serializovatelné typy
ms.date: 03/30/2017
ms.assetid: f1c8539a-6a79-4413-b294-896f0957b2cd
ms.openlocfilehash: 0fe29d2eb2b50d2515d71745bc062255dbfb60ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54608047"
---
# <a name="serializable-types"></a>Serializovatelné typy
Ve výchozím nastavení <xref:System.Runtime.Serialization.DataContractSerializer> serializuje všechny veřejně viditelné typy. Všechny vlastnosti veřejné čtení a zápis a pole typu se serializují.  
  
 Výchozí chování lze změnit použitím <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy k typům a členům této funkce může být užitečné v situacích, ve kterých máte typy, které nejsou pod vaší kontrolou a nelze ji upravit a přidat atributy. <xref:System.Runtime.Serialization.DataContractSerializer> Rozpoznává tyto "zrušeno označení" typy.  
  
## <a name="serialization-defaults"></a>Výchozí serializace  
 Můžete použít <xref:System.Runtime.Serialization.DataContractAttribute> a <xref:System.Runtime.Serialization.DataMemberAttribute> atributy explicitně řídit nebo přizpůsobení serializaci typů a členů. Kromě toho můžete použít tyto atributy k privátním položkám. Ale i typy, které nejsou označené tyto atributy jsou serializovat a deserializovat. Platí následující pravidla a výjimky:  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> Odvodí kontraktu dat z typů bez atributů s použitím výchozí vlastnosti typů nově vytvořený.  
  
-   Všechny veřejné polí a vlastností s veřejnou `get` a `set` metody serializován, jestliže nenainstalujete opravu <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atribut pro tohoto člena.  
  
-   Sémantika serializace je podobné jako u <xref:System.Xml.Serialization.XmlSerializer>.  
  
-   Zrušit označení typy jsou serializovat pouze veřejné typy s konstruktory, které nemají parametry. Výjimkou z tohoto pravidla je <xref:System.Runtime.Serialization.ExtensionDataObject> použít s <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní.  
  
-   Pole jen pro čtení, vlastnosti bez `get` nebo `set` metody a vlastnosti s interní nebo privátní `set` nebo `get` metody nejsou serializována. Tyto vlastnosti jsou ignorovány a není vyvolána žádná výjimka, s výjimkou kolekce jenom pro získání.  
  
-   <xref:System.Xml.Serialization.XmlSerializer> atributy (například `XmlElement`, `XmlAttribute`, `XmlIgnore`, `XmlInclude`, a tak dále) jsou ignorovány.  
  
-   Pokud se nevztahují <xref:System.Runtime.Serialization.DataContractAttribute> atributů pro daný typ serializátor ignoruje libovolnému členovi v tomto typu, na který <xref:System.Runtime.Serialization.DataMemberAttribute> atribut se používá.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer.KnownTypes%2A> Vlastnost je podporována v typech neoznačené <xref:System.Runtime.Serialization.DataContractAttribute> atribut. To zahrnuje podporu <xref:System.Runtime.Serialization.KnownTypeAttribute> atribut na neoznačených typy.  
  
-   Chcete-li "odhlásit" procesu serializace pro veřejné členy, vlastnosti nebo pole, použijte <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute> atribut pro tohoto člena.  
  
## <a name="inheritance"></a>Dědičnost  
 Zrušit označení typy (typy bez <xref:System.Runtime.Serialization.DataContractAttribute> atribut) může dědit z typů, které mají tento atribut; však není povolená opačně: typy s atributem nemůže dědit z zrušeno označení typy. Toto pravidlo je vynuceno především k zajištění zpětné kompatibility s kódem napsaným v dřívějších verzích [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)].  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Runtime.Serialization.IgnoreDataMemberAttribute>
- <xref:System.Runtime.Serialization.DataContractAttribute>
- <xref:System.Runtime.Serialization.DataMemberAttribute>
- <xref:System.Xml.Serialization.XmlSerializer>
- [Typy podporované serializátorem kontraktu dat](../../../../docs/framework/wcf/feature-details/types-supported-by-the-data-contract-serializer.md)

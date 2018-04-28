---
title: Správa verzí kontraktů dat
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- versioning [WCF], data contracts
- versioning [WCF]
- data contracts [WCF], versioning
ms.assetid: 4a0700cb-5f5f-4137-8705-3a3ecf06461f
caps.latest.revision: 35
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f232cb1cf98fe01aa0542c2a4b459fb7fc7b5089
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2018
---
# <a name="data-contract-versioning"></a>Správa verzí kontraktů dat
Jak vyvíjet aplikace, budete také muset změnit data měnící použití služby. Toto téma vysvětluje, jak kontrakty dat verze. Toto téma popisuje mechanismy Správa verzí kontraktů dat. Úplný přehled a správa verzí závazné pokyny najdete v tématu [osvědčené postupy: Správa verzí kontraktů dat](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md).  
  
## <a name="breaking-vs-nonbreaking-changes"></a>Pozastavení vs. Pevných změny  
 Může být nejnovější změny kontraktu dat nebo pevných. Při změně kontraktu dat pevných způsobem, aplikace pomocí starší verze kontraktu může komunikovat s pomocí novější verze aplikace a aplikace pomocí novější verze nástroje kontrakt může komunikovat s aplikací pomocí starší verze. Na druhé straně narušující změně znemožňuje komunikaci v jednom či obou směrech.  
  
 Všechny změny na typ, které nemají vliv na tom, jak je odeslaných a přijatých jsou pevných. Tyto změny neměňte kontrakt dat, pouze s podkladovým typem. Například můžete změnit název pole pevných způsobem, pokud se pak můžete nastavit <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> k názvu starší verze. Následující kód ukazuje verze 1 kontraktu dat.  
  
 [!code-csharp[C_DataContractVersioning#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#1)]
 [!code-vb[C_DataContractVersioning#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#1)]  
  
 Následující kód ukazuje pevných změnu.  
  
 [!code-csharp[C_DataContractVersioning#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#2)]
 [!code-vb[C_DataContractVersioning#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#2)]  
  
 Některé změny upravit velikost přenášených dat, ale může nebo nemusí být dopadem na dřívější kód. Následující změny jsou vždy nejnovější:  
  
-   Změna <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A> nebo <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A> hodnota kontraktu dat.  
  
-   Změna pořadí datových členů pomocí <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute>.  
  
-   Přejmenování člena.  
  
-   Změna kontrakt dat datového členu. Například změna typu dat člena z celé číslo na řetězec, nebo z typu s kontraktu dat s názvem "Zákazník" na typ s kontraktu dat s názvem "Osoba".  
  
 Následující změny je také možné.  
  
## <a name="adding-and-removing-data-members"></a>Přidávání a odebírání datové členy  
 Ve většině případů přidáním nebo odebráním datový člen není narušující změně, pokud požadujete striktní schématu platnosti (ověření proti staré schéma nové instance).  
  
 Když je typ s další pole deserializovat do typu s chybějící pole, doplňující informace se ignoruje. (Může být také uložen pro účely odezvy; Další informace najdete v části [kontrakty dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)).  
  
 Když je typ s chybějící pole deserializovat do typu s další pole, je navíc pole ponecháno na výchozí hodnotě, obvykle nula nebo `null`. (Výchozí hodnota může být změněn; Další informace najdete v tématu [verze proti chybám zpětná volání serializace tolerantní](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md).)  
  
 Například můžete použít `CarV1` – třída v klientském počítači a `CarV2` třída na služby, nebo můžete použít `CarV1` třídy ve službě a `CarV2` – třída v klientském počítači.  
  
 [!code-csharp[C_DataContractVersioning#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_datacontractversioning/cs/source.cs#3)]
 [!code-vb[C_DataContractVersioning#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_datacontractversioning/vb/source.vb#3)]  
  
 Koncový bod verze 2 úspěšně může odesílat data do koncového bodu verze 1. Serializaci verze 2 `Car` kontrakt dat vypočítá XML podobný následujícímu.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
    <HorsePower>300</HorsePower>  
</Car>  
```  
  
 Deserializace modulu v V1 nebyly nalezeny odpovídající data člena `HorsePower` pole a zahodí data.  
  
 Koncový bod verze 1 také může odesílat data do koncového bodu verze 2. Serializaci verze 1 `Car` kontrakt dat vypočítá XML podobný následujícímu.  
  
```xml  
<Car>  
    <Model>Porsche</Model>  
</Car>  
```  
  
 Verze 2 deserializátor nebude vědět, co je potřeba nastavit `HorsePower` pole, protože neexistuje žádná odpovídající data v příchozím kódu XML. Místo toho pole je nastaveno na výchozí hodnotu 0.  
  
## <a name="required-data-members"></a>Požadované datové členy  
 Člen data mohou být označeny jako nich vyžaduje nastavením <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> vlastnost <xref:System.Runtime.Serialization.DataMemberAttribute> k `true`. Pokud data chybí požadovaný při deserializaci, je vyvolána výjimka namísto nastavování datového člena na výchozí hodnotu.  
  
 Přidání člena požadovaných dat je narušující změně. To znamená novější typ stále možné odeslat do koncových bodů s starší typ, ale ne naopak. Odebrání člena data, která byla označena jako v jakékoli předchozí verze je také narušující změně.  
  
 Změna <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> hodnota vlastnosti z `true` k `false` není dopadem na dřívější kód, ale změna ze `false` k `true` může být nejnovější Pokud všechny předchozí verze typu nemají datového člena v.  
  
> [!NOTE]
>  I když <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> je nastavena na `true`, příchozích dat může mít hodnotu null nebo nula a typ musí být připraveno pro zpracování této možnosti. Nepoužívejte <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A> jako vhodný mechanismus zabezpečení k ochraně proti chybná příchozí data.  
  
## <a name="omitted-default-values"></a>Není zadán výchozí hodnoty  
 Je možné (i když se nedoporučuje se) nastavit `EmitDefaultValue` vlastnost v atributu DataMemberAttribute `false`, jak je popsáno v [výchozí hodnoty členů Data](../../../../docs/framework/wcf/feature-details/data-member-default-values.md). Pokud toto nastavení je `false`, datový člen nebude vygenerované, pokud je nastaveno na výchozí hodnotu (obvykle nebo má nulovou hodnotu). To není kompatibilní s požadovaná data členů v různých verzích dvěma způsoby:  
  
-   Kontrakt dat s dat člena, který je nutné v jedné verze nemůže přijímat výchozí (nebo má nulovou hodnotu) data z jiné verze, ve kterém má datový člen `EmitDefaultValue` nastavena na `false`.  
  
-   Požadovaná data člena, který má `EmitDefaultValue` nastavena na `false` nelze použít k serializaci jeho výchozí (nebo má nulovou hodnotu), hodnotu, ale mohou přijímat hodnota k deserializaci. Vzniká tak problém odezvy (data lze číst v ale stejná data nelze zapsat pak). Proto pokud `IsRequired` je `true` a `EmitDefaultValue` je `false` v jedné verzi stejné kombinace by se měly používat na všech ostatních verzí tak, aby žádná verze kontrakt dat budou moci vytvořit hodnotu, která nemá za následek dobu odezvy.  
  
## <a name="schema-considerations"></a>Důležité informace o schématu  
 Vysvětlení, co schématu pro typy kontraktů dat vytváří, najdete v článku [Přehled schématu kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md).  
  
 Schéma [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vytváří pro typy kontraktů dat umožňuje žádné předpisy pro správu verzí. To znamená schéma exportovaný z konkrétní verzi typu, obsahuje pouze data členů v této verzi. Implementace <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní schéma pro typ nezmění.  
  
 Datové členy exportují do schématu jako volitelné elementy ve výchozím nastavení. To znamená `minOccurs` (atribut XML) hodnota nastavena na hodnotu 0. Členy požadovaná data jsou exportovaný s `minOccurs` nastavena na hodnotu 1.  
  
 Mnoho změn považuje za pevná jsou ve skutečnosti nejnovější Pokud stoprocentní schématu je potřeba. V předchozím příkladu `CarV1` instanci s jenom na `Model` element by vyhodnotit proti `CarV2` schématu (které má oba `Model` a `Horsepower`, ale obě jsou volitelné). Naopak však není pravda: `CarV2` instance dojde k selhání ověření na základě `CarV1` schématu.  
  
 Odezvy také zahrnuje několik dalších důležitých informací. Další informace najdete v části "Schématu aspekty" v [kontrakty dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
### <a name="other-permitted-changes"></a>Ostatní povolené změny  
 Implementace <xref:System.Runtime.Serialization.IExtensibleDataObject> rozhraní je pevných změnu. Ale odezvy podporu neexistuje pro verze typu starší než verze, ve kterém <xref:System.Runtime.Serialization.IExtensibleDataObject> byl implementován. Další informace najdete v tématu [kontrakty dat dopřednou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md).  
  
## <a name="enumerations"></a>Výčty  
 Přidání nebo odebrání člena výčtu je narušující změně. Změna názvu člena výčtu je porušením, pokud jeho název smlouvy je udržováno stejné jako v předchozí verzi aplikace pomocí `EnumMemberAtttribute` atribut. Další informace najdete v tématu [výčtové typy v kontraktech dat](../../../../docs/framework/wcf/feature-details/enumeration-types-in-data-contracts.md).  
  
## <a name="collections"></a>Kolekce  
 Většinu změn kolekce jsou pevných protože většina typy kolekcí se zaměňovat navzájem v datovém modelu kontrakt. Ale provedení noncustomized kolekce přizpůsobit nebo naopak je narušující změně. Změna nastavení přizpůsobení kolekce je taky narušující změně; To znamená změna jeho názvu kontraktu dat a obor názvů, opakující se název elementu, klíčovým prvkem název a hodnotu název elementu. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] kolekce přizpůsobení, najdete v části [typy kolekcí v kontraktech dat](../../../../docs/framework/wcf/feature-details/collection-types-in-data-contracts.md).  
Změna kontrakt dat obsahu kolekce (například změna ze seznamu celých čísel na seznam řetězců) je samozřejmě narušující změně.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Name%2A>  
 <xref:System.Runtime.Serialization.DataContractAttribute.Namespace%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.Order%2A>  
 <xref:System.Runtime.Serialization.DataMemberAttribute.IsRequired%2A>  
 <xref:System.Runtime.Serialization.SerializationException>  
 <xref:System.Runtime.Serialization.IExtensibleDataObject>  
 [Zpětná volání serializace tolerantní k verzím](../../../../docs/framework/wcf/feature-details/version-tolerant-serialization-callbacks.md)  
 [Osvědčené postupy: Správa verzí kontraktů dat](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 [Ekvivalence kontraktů dat](../../../../docs/framework/wcf/feature-details/data-contract-equivalence.md)  
 [Kontrakty dat s dopřednou kompatibilitou](../../../../docs/framework/wcf/feature-details/forward-compatible-data-contracts.md)

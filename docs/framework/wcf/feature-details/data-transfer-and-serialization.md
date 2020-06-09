---
title: Přenos a serializace dat
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: b07937b0a94c24a934b17d6cf21b726ee0d4362e
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593481"
---
# <a name="data-transfer-and-serialization"></a>Přenos a serializace dat
V připojeném systému jsou služby a klienti závislé na výměně dat za účelem provedení jakékoli úlohy. Jako vývojář služby nebo klienta musíte taky pochopit, jak Windows Communication Foundation (WCF) zpracovává data a serializaci dat, aby bylo možné vytvářet aplikace, které jsou efektivní a snadno se udržují.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Určování přenosu dat v kontraktech služby](specifying-data-transfer-in-service-contracts.md)  
 Popisuje základní koncepty přenosu dat v rámci služeb.  
  
 [Použití kontraktů dat](using-data-contracts.md)  
 Popisuje, jaké jsou kontrakty dat a jak je vytvořit a používat.  
  
 [Serializátor kontraktu dat](data-contract-serializer.md)  
 Popisuje, jak provést serializaci dat s <xref:System.Runtime.Serialization.DataContractSerializer> třídou nebo libovolným rozšířením <xref:System.Runtime.Serialization.XmlObjectSerializer> třídy.  
  
 [Používání třídy XmlSerializer](using-the-xmlserializer-class.md)  
 Popisuje, jak a proč použít <xref:System.Xml.Serialization.XmlSerializer> třídu, alternativu ke <xref:System.Runtime.Serialization.DataContractSerializer> třídě.  
  
 [Použití kontraktů zpráv](using-message-contracts.md)  
 Popisuje, jak kontrakty zpráv umožňují přesné řízení zpráv protokolu SOAP.  
  
 [Používání třídy Message](using-the-message-class.md)  
 Popisuje, jak používat funkce třídy zpráv.  
  
 [Filtrování](filtering.md)  
 Popisuje filtrování, které umožňuje předběžné zpracování zprávy na základě různých kritérií.  
  
 [Objemná data a streamování](large-data-and-streaming.md)  
 Popisuje, jak odeslat velký blok dat, jako je například binární soubor.  
  
 [Důležité informace o zabezpečení pro data](security-considerations-for-data.md)  
 Popisuje položky, které je třeba znát při přenosu a serializaci dat programování.  
  
 [Strukturální přehled přenosu dat](data-transfer-architectural-overview.md)  
 Popisuje zobrazení celkového návrhu přenosu dat v rámci služby WCF.  
  
## <a name="reference"></a>Referenční informace  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a>Související oddíly  
 [Rozšiřování kodérů a serializátorů](../extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a>Viz také

- [Osvědčené postupy: Správa verzí kontraktů dat](../best-practices-data-contract-versioning.md)
- [Správa verzí služby](../service-versioning.md)

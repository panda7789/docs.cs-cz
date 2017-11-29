---
title: "Přenos a serializace dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 41357c9a039414ac692bac69337b2963d5c6b341
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="data-transfer-and-serialization"></a>Přenos a serializace dat
V systému připojený služeb a klientů závisí na výměnu dat k provedení jakékoli úlohy. Jako vývojář služeb nebo klienta, je potřeba také pochopit, jak [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zpracovává data a serializace dat před vytvořením aplikace, které jsou efektivní a snadno spravovat.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Určování přenosu dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 Popisuje základní koncepty přenosu dat do služby.  
  
 [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 Popisuje, jaká data měnící se a jak vytvořit a používat je.  
  
 [Serializátor kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 Popisuje, jak provést serializace dat pomocí <xref:System.Runtime.Serialization.DataContractSerializer> třídu nebo prodloužení <xref:System.Runtime.Serialization.XmlObjectSerializer> – třída.  
  
 [Používání třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 Popisuje, jak a proč používat <xref:System.Xml.Serialization.XmlSerializer> třídy alternativu k <xref:System.Runtime.Serialization.DataContractSerializer> třídy.  
  
 [Použití kontraktů zpráv](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 Popisuje, jak povolit kontrakty zpráv dobrou kontrolu protokolu SOAP zprávy.  
  
 [Používání třídy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 Popisuje, jak používat funkce tříd zprávy.  
  
 [Filtrování](../../../../docs/framework/wcf/feature-details/filtering.md)  
 Popisuje filtrování, která umožňuje předběžné zpracování zpráv na základě různých kritérií.  
  
 [Velkého množství dat a vysílání datového proudu](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 Popisuje, jak k odeslání velkého bloku dat, jako je binární soubor.  
  
 [Důležité informace o zabezpečení pro Data](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 Popisuje položky, které budou vědět, když přenos dat a serializace.  
  
 [Strukturální Přehled přenosu dat](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 Popisuje zobrazení celkového návrhu přenosu dat v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a>Související oddíly  
 [Rozšiřování kodérů a Serializátorů](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a>Viz také  
 [Osvědčené postupy: Správa verzí kontraktů dat](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)  
 [Správa verzí služeb](../../../../docs/framework/wcf/service-versioning.md)

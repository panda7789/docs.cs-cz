---
title: Přenos a serializace dat
ms.date: 03/30/2017
helpviewer_keywords:
- data serialization [WCF]
- data transfer [WCF]
ms.assetid: 0f03c635-f3e7-4c5c-9463-3cb0135e221e
ms.openlocfilehash: 5192030fa2eda45431dd8a3765603d3081b93fa3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54595315"
---
# <a name="data-transfer-and-serialization"></a>Přenos a serializace dat
V připojené systému služeb a klientů závisí na výměny dat k provedení jakékoli úlohy. Jako vývojář službu nebo klienta musíte pochopit, jak Windows Communication Foundation (WCF) zpracovává data a serializace dat k vytvoření aplikace, které jsou efektivní a snadno udržovat.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Určování přenosu dat v kontraktech služby](../../../../docs/framework/wcf/feature-details/specifying-data-transfer-in-service-contracts.md)  
 Popisuje základní koncepty přenosy dat služby.  
  
 [Použití kontraktů dat](../../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
 Popisuje, jaká data smluv jsou a tom, jak vytvořit a použít je.  
  
 [Serializátor kontraktu dat](../../../../docs/framework/wcf/feature-details/data-contract-serializer.md)  
 Popisuje, jak provést serializace dat pomocí <xref:System.Runtime.Serialization.DataContractSerializer> třídy nebo jakéhokoli rozšíření <xref:System.Runtime.Serialization.XmlObjectSerializer> třídy.  
  
 [Používání třídy XmlSerializer](../../../../docs/framework/wcf/feature-details/using-the-xmlserializer-class.md)  
 Popisuje, jak a proč používat <xref:System.Xml.Serialization.XmlSerializer> třídy, je alternativou k <xref:System.Runtime.Serialization.DataContractSerializer> třídy.  
  
 [Použití kontraktů zpráv](../../../../docs/framework/wcf/feature-details/using-message-contracts.md)  
 Popisuje, jak povolit kontraktů zpráv přesné řízení zprávy protokolu SOAP.  
  
 [Používání třídy Message](../../../../docs/framework/wcf/feature-details/using-the-message-class.md)  
 Popisuje, jak používat funkce třídy zpráv.  
  
 [Filtrování](../../../../docs/framework/wcf/feature-details/filtering.md)  
 Popisuje, filtrování, která umožňuje předběžné zpracování zprávy na základě různých kritérií.  
  
 [Objemná data a streamování](../../../../docs/framework/wcf/feature-details/large-data-and-streaming.md)  
 Popisuje postup odesílání velkých blok dat, jako je například binární soubor.  
  
 [Důležité informace o zabezpečení dat](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md)  
 Popisuje položky, které chcete mít na paměti při programování přenos a serializace dat.  
  
 [Strukturální přehled přenosu dat](../../../../docs/framework/wcf/feature-details/data-transfer-architectural-overview.md)  
 Popisuje zobrazení celkového návrhu přenosu dat ve službě WCF.  
  
## <a name="reference"></a>Odkaz  
 <xref:System.ServiceModel>  
  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
  
 <xref:System.Xml.Serialization.XmlSerializer>  
  
 <xref:System.Runtime.Serialization>  
  
 <xref:System.Xml.Serialization>  
  
## <a name="related-sections"></a>Související oddíly  
 [Rozšiřování kodérů a serializátorů](../../../../docs/framework/wcf/extending/extending-encoders-and-serializers.md)  
  
## <a name="see-also"></a>Viz také:
- [Osvědčené postupy: Správa verzí kontraktů dat](../../../../docs/framework/wcf/best-practices-data-contract-versioning.md)
- [Správa verzí služby](../../../../docs/framework/wcf/service-versioning.md)

---
title: Vlastní formátování zpráv
ms.date: 03/30/2017
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
ms.openlocfilehash: af1596c65fc87a68bc3dc2ab5ab2d82133e0fed4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59196239"
---
# <a name="custom-message-formatters"></a>Vlastní formátování zpráv
Obsah ve zprávě je často ve formátu XML, který není obvykle vhodné formátu pro aplikaci. Aplikace manipulovat s objekty, získávání a nastavování jejich vlastností. Windows Communication Foundation (WCF) používá *kontraktu dat* převést <xref:System.ServiceModel.Channels.Message> objektu do objektu snadno zpracovat aplikace. Tyto procesy jsou volány serializace a deserializace. Všimněte si, že tyto stejné podmínky se používají k popisu serializace a deserializace provádí přenosové vrstvy do a z přenosový formát zprávy, což je nesouvisejících procesu.  
  
 Pokud potřebujete implementovat specializovaný převod mezi zpráv a objekty, které nelze provést pomocí kontraktu dat, můžete použít vlastní zprávu formátování. K tomu úpravě nebo rozšiřování chování při spuštění konkrétní kontrakt operace na klientovi nebo službu.  
  
## <a name="custom-message-formatters-on-the-client"></a>Vlastní formátování zpráv na straně klienta  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Rozhraní definuje metody, které se používají k řízení převodu zprávy do objektů a objektů do zprávy pro klientské aplikace.  
  
 Musí implementovat toto rozhraní. Nejprve přepsat <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> metodu pro deserializaci zprávy. Tato metoda je volána po přijetí příchozí zprávy, ale předtím, než se odesílají do operace klienta.  
  
 V dalším kroku přepsat <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> metoda k serializaci objektu. Tato metoda je volána před odesláním odchozí zprávy.  
  
 Chcete-li vložit vlastní formátovací modul do aplikace služby, přiřaďte <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> objektu <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> vlastnost pomocí na chování operace. Informace o chování najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="custom-message-formatters-on-the-service"></a>Vlastní formátování zpráv ve službě  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Rozhraní definuje metody, které provádějí převod <xref:System.ServiceModel.Channels.Message> do parametry operace a parametry do objektu <xref:System.ServiceModel.Channels.Message> objektu v aplikaci služby.  
  
 Musí implementovat toto rozhraní. Nejprve přepsat <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> metodu pro deserializaci zprávy. Tato metoda je volána po přijetí příchozí zprávy, ale předtím, než se odesílají do operace klienta.  
  
 V dalším kroku přepsat <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> metoda k serializaci objektu. Tato metoda je volána před odesláním odchozí zprávy.  
  
 Chcete-li vložit vlastní formátovací modul do aplikace služby, přiřaďte <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> objektu <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> vlastnost pomocí na chování operace. Informace o chování najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>
- <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>
- [Konfigurace a rozšíření modulu runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)

---
title: "Vlastní formátování zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 01998d0ac732f63f6771c47bfc76a8207a5531f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="custom-message-formatters"></a>Vlastní formátování zpráv
Obsah zprávy je často ve formátu XML, což je obvykle není vhodné formát pro aplikaci. Aplikace pracovat s objekty, získávání a nastavování jejich vlastností. [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]používá *kontrakt dat* převést <xref:System.ServiceModel.Channels.Message> objektu na objekt jednoduše zvládne aplikace. Tyto procesy se nazývají serializace a deserializace. Upozorňujeme, že jsou popsat serializaci a deserializaci provádí přenosové vrstvy do a z přenosový formát zprávy, což je proces nesouvisejícími tyto stejných podmínek.  
  
 Pokud potřebujete implementovat specializované převod mezi zpráv a objekty, které nelze provádět prostřednictvím kontraktu dat můžete použít vlastní zprávu při formátování. To lze proveďte změnou nebo rozšíření chování při spuštění operace konkrétní kontrakt na klienta nebo služby.  
  
## <a name="custom-message-formatters-on-the-client"></a>Vlastní formátování zpráv na straně klienta  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> Rozhraní definuje metody, které jsou používány k ovládání převod zpráv do objekty a objekty do zprávy pro klientské aplikace.  
  
 Musí toto rozhraní implementovat. Nejprve přepsat <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> metodu pro deserializaci zprávu. Tato metoda je volána po přijetí příchozí zprávy, ale před odeslaných operace klienta.  
  
 V dalším kroku přepsat <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> metoda o serializaci objektu. Tato metoda je volána před odesláním odchozí zprávy.  
  
 Vlastní formátování vložení do aplikace služby, přiřadit <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter> do objektu <xref:System.ServiceModel.Dispatcher.ClientOperation.Formatter%2A> vlastnost pomocí chování operaci. Informace o chování najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="custom-message-formatters-on-the-service"></a>Vlastní formátování zpráv ve službě  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> Rozhraní definuje metody, které převést <xref:System.ServiceModel.Channels.Message> objektu do parametrů operace a parametrů do <xref:System.ServiceModel.Channels.Message> objektu v aplikaci služby.  
  
 Musí toto rozhraní implementovat. Nejprve přepsat <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.DeserializeReply%2A> metodu pro deserializaci zprávu. Tato metoda je volána po přijetí příchozí zprávy, ale před odeslaných operace klienta.  
  
 V dalším kroku přepsat <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter.SerializeRequest%2A> metoda o serializaci objektu. Tato metoda je volána před odesláním odchozí zprávy.  
  
 Vlastní formátování vložení do aplikace služby, přiřadit <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter> do objektu <xref:System.ServiceModel.Dispatcher.DispatchOperation.Formatter%2A> vlastnost pomocí chování operaci. Informace o chování najdete v tématu [konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter>  
 <xref:System.ServiceModel.Dispatcher.IDispatchMessageFormatter>  
 [Konfigurace a rozšíření modulu Runtime s chováním](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)

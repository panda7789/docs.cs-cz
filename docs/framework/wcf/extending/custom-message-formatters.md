---
title: Vlastní formátování zpráv
ms.date: 03/30/2017
ms.assetid: c07435f3-5214-4791-8961-2c2b61306d71
ms.openlocfilehash: 301c508a0c639985e226dc55f62431ad8bb9c12b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487669"
---
# <a name="custom-message-formatters"></a>Vlastní formátování zpráv
Obsah zprávy je často ve formátu XML, což je obvykle není vhodné formát pro aplikaci. Aplikace pracovat s objekty, získávání a nastavování jejich vlastností. Windows Communication Foundation (WCF) používá *kontrakt dat* převést <xref:System.ServiceModel.Channels.Message> objektu na objekt jednoduše zvládne aplikace. Tyto procesy se nazývají serializace a deserializace. Upozorňujeme, že jsou popsat serializaci a deserializaci provádí přenosové vrstvy do a z přenosový formát zprávy, což je proces nesouvisejícími tyto stejných podmínek.  
  
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
 [Konfigurace a rozšíření modulu runtime pomocí chování](../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)

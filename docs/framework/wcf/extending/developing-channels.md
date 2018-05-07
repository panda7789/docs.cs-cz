---
title: Vývoj kanálů
ms.date: 03/30/2017
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
ms.openlocfilehash: def60ec0cce8da71e7e2d98ff456420949360aed
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="developing-channels"></a>Vývoj kanálů
K vývoji pro protokol nebo přenos kanálu, který lze použít s Windows Communication Foundation (WCF) aplikační vrstvu vyžaduje několik kroků. Toto téma popisuje kroky a bodů na konkrétní témata pro další informace. Zjistit model kanálu a různé typy, které jsou uvedené v tomto tématu najdete v části [přehled modelu kanálu](../../../../docs/framework/wcf/extending/channel-model-overview.md). Kanál ukázku dokončení přenosu, najdete [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md).  
  
## <a name="the-channel-development-task-list"></a>Seznam úkolů vývoj kanálu  
 Takto vypadají kroky k vytvoření kanálu definovaný uživatelem. Musí být všechny kanály:  
  
1.  Rozhodněte, které kanálu vzory Exchange zprávu (<xref:System.ServiceModel.Channels.IOutputChannel>, <xref:System.ServiceModel.Channels.IInputChannel>, <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IRequestChannel>, nebo <xref:System.ServiceModel.Channels.IReplyChannel>) vaší <xref:System.ServiceModel.Channels.IChannelFactory> a <xref:System.ServiceModel.Channels.IChannelListener> podporovat, a také, zda bude podporovat sessionful variace tato rozhraní. Podrobnosti najdete v tématu [výběr vzorce výměny zpráv](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md).  
  
2.  Vytvoření postupu kanálu a naslouchací proces (<xref:System.ServiceModel.Channels.IChannelFactory> a <xref:System.ServiceModel.Channels.IChannelListener>) podporující vaše vzorce výměny zpráv. Podrobnosti o vývoji objekty Factory najdete v tématu [klienta: objekty pro vytváření kanálů a kanály](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md). Podrobnosti o vývoji naslouchací procesy najdete v tématu [služba: moduly pro naslouchání kanálů a kanály](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md).  
  
3.  Ujistěte se, že jsou všechny výjimky sítě normalizovány na buď <xref:System.TimeoutException?displayProperty=nameWithType> nebo odpovídající odvozené třídy <xref:System.ServiceModel.CommunicationException>. Podrobnosti najdete v tématu [zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
4.  Pokud chcete povolit použití z aplikační vrstvu, přidejte <xref:System.ServiceModel.Channels.BindingElement> vlastní kanál, přidá do kanálu zásobníku. Další informace najdete v tématu [vytvoření BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md).  
  
 Následující kroky jsou požadovány pro povolení podrobnější na aplikační vrstvu podpory:  
  
1.  Přidáte oddíl rozšíření element vazby ke zveřejnění nového elementu vazby v konfiguraci systému. Další informace najdete v tématu [konfigurace a podpora metadat](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
2.  Přidejte rozšíření metadata pro komunikaci funkce pro ostatní koncové body. Další informace najdete v tématu [konfigurace a podpora metadat](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
3.  Přidejte vazbu, která předem nakonfiguruje zásobníku elementů vazby podle dobře definovaný profil. Další informace najdete v tématu [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
4.  Přidáte oddíl vazby a konfigurace prvku vazby ke zveřejnění vazby ke konfiguraci systému. Další informace najdete v tématu [konfigurace a podpora metadat](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření vazeb](../../../../docs/framework/wcf/extending/extending-bindings.md)

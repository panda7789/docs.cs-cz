---
title: Vývoj kanálů
ms.date: 03/30/2017
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
ms.openlocfilehash: 74a54972ffa7d00d702a2339665d18acdcbf93ef
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54519135"
---
# <a name="developing-channels"></a>Vývoj kanálů
Aplikační vrstva pro vývoj pro protokol nebo přenos kanál, který lze použít s Windows Communication Foundation (WCF), vyžaduje několik kroků. Toto téma popisuje tyto kroky a odkazuje na konkrétní témata pro další informace. Model kanálů a různé typy, které jsou uvedené v tomto tématu najdete v tématu [přehled modelu kanálu](../../../../docs/framework/wcf/extending/channel-model-overview.md). Dokončení přenosu kanál ukázku najdete v tématu [přenosu: UDP](../../../../docs/framework/wcf/samples/transport-udp.md).  
  
## <a name="the-channel-development-task-list"></a>Seznam úkolů vývoj kanálu  
 Kroky k vytvoření kanálu uživatelem definované jsou následující. Musí se všechny kanály:  
  
1.  Rozhodněte, které kanálu zpráv Exchange vzory (<xref:System.ServiceModel.Channels.IOutputChannel>, <xref:System.ServiceModel.Channels.IInputChannel>, <xref:System.ServiceModel.Channels.IDuplexChannel>, <xref:System.ServiceModel.Channels.IRequestChannel>, nebo <xref:System.ServiceModel.Channels.IReplyChannel>) vaše <xref:System.ServiceModel.Channels.IChannelFactory> a <xref:System.ServiceModel.Channels.IChannelListener> bude podporovat, a také určuje, zda bude podporovat který neobsahuje relace změny těchto rozhraní. Podrobnosti najdete v tématu [výběr vzoru výměny zpráv](../../../../docs/framework/wcf/extending/choosing-a-message-exchange-pattern.md).  
  
2.  Vytvořte objekt pro vytváření kanálů a naslouchací proces (<xref:System.ServiceModel.Channels.IChannelFactory> a <xref:System.ServiceModel.Channels.IChannelListener>), které podporují vaše vzorce výměny zpráv. Podrobnosti o vývoji továrny najdete v tématu [klienta: Kanál objektů Factory a kanály](../../../../docs/framework/wcf/extending/client-channel-factories-and-channels.md). Podrobnosti o vývoji naslouchacích procesů najdete v tématu [služby: Naslouchací objekty kanálů a kanály](../../../../docs/framework/wcf/extending/service-channel-listeners-and-channels.md).  
  
3.  Ujistěte se, že všechny výjimky pro konkrétní sítě jsou normalizovány na buď <xref:System.TimeoutException?displayProperty=nameWithType> nebo odpovídající odvozenou třídu <xref:System.ServiceModel.CommunicationException>. Podrobnosti najdete v tématu [zpracování výjimek a chyb](../../../../docs/framework/wcf/extending/handling-exceptions-and-faults.md).  
  
4.  Pokud chcete povolit použití z aplikační vrstvy, přidejte <xref:System.ServiceModel.Channels.BindingElement> vlastní kanál, který přidá do kanálu zásobníku. Další informace najdete v tématu [vytvoření BindingElement](../../../../docs/framework/wcf/extending/creating-a-bindingelement.md).  
  
 Následující kroky jsou požadovány pro úplnější podpory v aplikační vrstvě povolení:  
  
1.  Přidání sekce rozšíření elementu vazby vystavit nový element vazby na konfigurační systém. Další informace najdete v tématu [konfigurace a podpora metadat](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
2.  Přidejte rozšíření metadat pro komunikaci funkce pro další koncové body. Další informace najdete v tématu [konfigurace a podpora metadat](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
3.  Přidáte vazbu, která předem nakonfiguruje sady elementů vazby podle přesně definovaného profilu. Další informace najdete v tématu [Creating User-Defined vazby](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
4.  Přidáte vazbu oddíl a vazeb konfiguračního prvku vystavit vazby na konfigurační systém. Další informace najdete v tématu [konfigurace a podpora metadat](../../../../docs/framework/wcf/extending/configuration-and-metadata-support.md).  
  
## <a name="see-also"></a>Viz také:
- [Rozšíření vazeb](../../../../docs/framework/wcf/extending/extending-bindings.md)

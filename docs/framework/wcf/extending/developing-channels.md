---
title: Vývoj kanálů
ms.date: 03/30/2017
ms.assetid: 0513af9f-a0c2-457b-9a50-5b6bfee48513
ms.openlocfilehash: 8d0ecb9ea473b78dfc648a1087ae2261406f2b4f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795786"
---
# <a name="developing-channels"></a>Vývoj kanálů
Pro vývoj protokolu nebo přenosového kanálu, který je možné použít s aplikační vrstvou Windows Communication Foundation (WCF), je potřeba provést několik kroků. Toto téma popisuje tyto kroky a odkazuje na konkrétní témata, kde najdete další informace. Pro pochopení modelu kanálů a různých typů, které jsou uvedeny v tomto tématu, naleznete informace v tématu [Přehled modelů kanálů](channel-model-overview.md). Kompletní ukázku přenosového kanálu najdete v tématu [přenos: UDP](../samples/transport-udp.md).  
  
## <a name="the-channel-development-task-list"></a>Seznam úkolů pro vývoj kanálu  
 Postup vytvoření uživatelem definovaného kanálu je následující. Všechny kanály musí:  
  
1. Rozhodněte se, který ze zpráv kanálu se vzory<xref:System.ServiceModel.Channels.IOutputChannel>výměny <xref:System.ServiceModel.Channels.IInputChannel>zpráv <xref:System.ServiceModel.Channels.IDuplexChannel>( <xref:System.ServiceModel.Channels.IRequestChannel>,, <xref:System.ServiceModel.Channels.IReplyChannel>, nebo <xref:System.ServiceModel.Channels.IChannelFactory> ) <xref:System.ServiceModel.Channels.IChannelListener> , bude podporovat a taky to, jestli bude podporovat relaci. variace těchto rozhraní. Podrobnosti najdete v tématu [Volba vzoru výměny zpráv](choosing-a-message-exchange-pattern.md).  
  
2. Vytvořte objekt pro vytváření kanálů a naslouchací<xref:System.ServiceModel.Channels.IChannelFactory> proces <xref:System.ServiceModel.Channels.IChannelListener>(a), který podporuje váš vzor výměny zpráv. Podrobnosti o vývoji továren naleznete v tématu [Client: Továrny kanálů a kanály](client-channel-factories-and-channels.md). Podrobnosti o vývoji posluchačů najdete v [tématu Služba: Naslouchací procesy kanálu a](service-channel-listeners-and-channels.md)kanály.  
  
3. Zajistěte, aby všechny výjimky specifické pro síť byly normalizovány na buď <xref:System.TimeoutException?displayProperty=nameWithType> nebo odpovídající odvozenou <xref:System.ServiceModel.CommunicationException>třídu třídy. Podrobnosti najdete v tématu [zpracování výjimek a chyb](handling-exceptions-and-faults.md).  
  
4. Pokud chcete povolit použití z aplikační vrstvy, přidejte do <xref:System.ServiceModel.Channels.BindingElement> zásobníku kanálů, který přidá vlastní kanál. Další informace najdete v tématu [Vytvoření BindingElement](creating-a-bindingelement.md).  
  
 Aby bylo možné zvýšit kompletní podporu na aplikační vrstvu, je nutné provést následující další kroky:  
  
1. Přidejte část rozšíření elementu vazby, která zpřístupňuje nový prvek vazby na konfigurační systém. Další informace najdete v tématu [Konfigurace a podpora metadat](configuration-and-metadata-support.md).  
  
2. Přidejte rozšíření metadat pro komunikaci s funkcemi do jiných koncových bodů. Další informace najdete v tématu [Konfigurace a podpora metadat](configuration-and-metadata-support.md).  
  
3. Přidejte vazbu, která předem nakonfiguruje zásobník prvků vazby podle dobře definovaného profilu. Další informace najdete v tématu [vytváření uživatelsky definovaných vazeb](creating-user-defined-bindings.md).  
  
4. Přidáním oddílu vazby a elementu konfigurace vazby zpřístupníte vazbu ke konfiguračnímu systému. Další informace najdete v tématu [Konfigurace a podpora metadat](configuration-and-metadata-support.md).  
  
## <a name="see-also"></a>Viz také:

- [Rozšíření vazeb](extending-bindings.md)

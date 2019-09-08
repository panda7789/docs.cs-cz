---
title: Programování na úrovni kanálu klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: 4f24c558b1d5303b2417416beb14555539f498ea
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797267"
---
# <a name="client-channel-level-programming"></a>Programování na úrovni kanálu klienta
Toto téma popisuje, jak vytvořit klientskou aplikaci Windows Communication Foundation (WCF) bez použití <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> třídy a jejího přidruženého objektového modelu.  
  
## <a name="sending-messages"></a>Odesílání zpráv  
 Aby bylo možné odesílat zprávy a přijímat a zpracovávat odpovědi, je nutné provést následující kroky:  
  
1. Vytvořte vazbu.  
  
2. Sestavte objekt pro vytváření kanálů.  
  
3. Vytvořte kanál.  
  
4. Odešlete žádost a přečtěte odpověď.  
  
5. Zavřete všechny objekty kanálu.  
  
#### <a name="creating-a-binding"></a>Vytvoření vazby  
 Podobně jako u přijímajícího případu (viz [programování na úrovni kanálu služby](service-channel-level-programming.md)), odesílání zpráv začíná vytvořením vazby. Tento příklad vytvoří nový <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> a <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> přidá do kolekce elementů.  
  
#### <a name="building-a-channelfactory"></a>Vytvoření třídy ChannelFactory  
 Místo vytvoření <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, tentokrát <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> vytvoříme voláním <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> na vazbu, kde je <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>parametr typu. Zatímco naslouchací procesy kanálu používají stranu, která čeká na příchozí zprávy, používají se strany kanálů, které iniciují komunikaci k vytvoření kanálu. Stejně jako naslouchací procesy kanálu musí být nejprve otevřeny objekty pro vytváření kanálů, aby bylo možné je použít.  
  
#### <a name="creating-a-channel"></a>Vytvoření kanálu  
 Pak zavolejte <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> na <xref:System.ServiceModel.Channels.IRequestChannel>vytvořit. Toto volání přebírá adresu koncového bodu, se kterým chceme komunikovat pomocí nového vytvořeného kanálu. Jakmile budeme mít kanál, zavoláme na něj otevřené, abychom ho umístili do stavu připraveného ke komunikaci. V závislosti na povaze přenosu může toto volání Open iniciovat připojení k cílovému koncovému bodu nebo nemůže v síti vůbec nic dělat.  
  
#### <a name="sending-a-request-and-reading-the-reply"></a>Odeslání žádosti a čtení odpovědi  
 Po otevření kanálu můžeme vytvořit zprávu a použít metodu žádosti kanálu k odeslání požadavku a počkat, až se odpověď vrátí zpět. Když se tato metoda vrátí, máme zprávu s odpovědí, kterou můžeme přečíst a zjistit, co byla odpověď koncového bodu.  
  
#### <a name="closing-objects"></a>Zavření objektů  
 Aby se předešlo nevracení prostředků, zavřou se objekty používané v komunikacích, když už je nepotřebujete.  
  
 Následující příklad kódu ukazuje základního klienta využívajícího objekt pro vytváření kanálů k odeslání zprávy a načtení odpovědi.  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]

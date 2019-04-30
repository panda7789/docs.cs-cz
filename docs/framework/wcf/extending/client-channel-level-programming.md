---
title: Programování na úrovni kanálu klienta
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: ea56c99d7d122dd20fc217f8ecb2937bcf81bec3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61923263"
---
# <a name="client-channel-level-programming"></a>Programování na úrovni kanálu klienta
Toto téma popisuje, jak psát aplikace klienta Windows Communication Foundation (WCF) bez použití <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> třídy a jeho přidruženého objektu modelu.  
  
## <a name="sending-messages"></a>Odesílání zpráv  
 Až bude připravená pro zasílání zpráv a příjem a zpracování odpovědi, se vyžaduje následující kroky:  
  
1. Vytvoření vazby.  
  
2. Vytvoření objektu pro vytváření kanálů.  
  
3. Vytvoření kanálu.  
  
4. Odešle žádost a čtení odpovědi.  
  
5. Zavřete všechny objekty kanálu.  
  
#### <a name="creating-a-binding"></a>Vytvoření vazby  
 Podobně jako přijímající případu (naleznete v tématu [programování na úrovni kanálu služby](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), odesílání zpráv začíná tím, že vytvoříte vazbu. Tento příklad vytvoří nový <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> a přidá <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> jeho elementů kolekce.  
  
#### <a name="building-a-channelfactory"></a>Vytváření třídy ChannelFactory  
 Místo vytváření <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, tentokrát vytvoříme <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> voláním <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> u vazby, kde je parametr typu <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>. Zatímco strana, která čeká na příchozí zprávy používají moduly pro naslouchání kanálů, objekty pro vytváření kanálů používá na straně, který inicializuje komunikaci k vytvoření kanálu. Stejně jako moduly pro naslouchání kanálů objekty pro vytváření kanálů musí byly nejprve otevřeny dříve, než je možné.  
  
#### <a name="creating-a-channel"></a>Vytvoření kanálu  
 Potom říkáme <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> k vytvoření <xref:System.ServiceModel.Channels.IRequestChannel>. Toto volání přebírá adresu koncového bodu, se kterou chceme, aby na komunikaci pomocí nového kanálu vytváří. Jakmile budeme mít nějaký kanál, říkáme Otevřít na něj umístíte ve stavu Připraveno pro komunikaci. V závislosti na povaze přenos toto volání Open může iniciovat připojení ke koncovému bodu cíl nebo může nedělat nic vůbec v síti.  
  
#### <a name="sending-a-request-and-reading-the-reply"></a>Odesílání požadavku a odpovědi pro čtení  
 Jakmile budeme mít otevřený kanálu, můžete vytvořit zprávu a pomocí metody požadavku kanálu můžete odeslat požadavek a čekat na odpověď opět online. Po návratu tato metoda máme zprávu odpovědi, který jsme může číst a zjistěte, co byla odpověď koncový bod.  
  
#### <a name="closing-objects"></a>Zavírání objektů  
 Aby se zabránilo nevrácení prostředků, můžeme zavřít objekty používané v rámci komunikace, když už nejsou povinné.  
  
 Následující příklad kódu ukazuje základní klienta se objekt pro vytváření kanálů pro odeslání zprávy a čtení odpovědi.  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]

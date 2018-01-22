---
title: "Síť rovnocenných počítačů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad6cb67b-fd1c-4ca1-a767-b410da2e16ca
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a26f10a323b44e7954245ab90a02f62745e84e87
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="peer-to-peer-networking"></a><span data-ttu-id="a2c79-102">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="a2c79-102">Peer-to-Peer Networking</span></span>
<span data-ttu-id="a2c79-103">Rovnocenného kanálu je technologie komunikace více stran, peer-to-peer (P2P) v [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a2c79-103">Peer Channel is a multiparty, peer-to-peer (P2P) communication technology in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="a2c79-104">Poskytuje zabezpečené a škálovatelné na základě zpráv P2P komunikační kanál pro vývojáře aplikací.</span><span class="sxs-lookup"><span data-stu-id="a2c79-104">It provides a secure and scalable message-based P2P communication channel for application developers.</span></span> <span data-ttu-id="a2c79-105">Jedním z příkladů běžných více stran aplikace, které mohou těžit z rovnocenného kanálu je spolupráce aplikaci, například chat, kde skupinu osob chat sebou způsobem peer-to-peer bez serverů.</span><span class="sxs-lookup"><span data-stu-id="a2c79-105">One common example of a multiparty application that can benefit from Peer Channel is a collaborative application, such as chat, where a group of people chat with one another in a peer-to-peer manner without servers.</span></span> <span data-ttu-id="a2c79-106">Rovnocenného kanálu umožňuje P2P spolupráce, distribuce obsahu, Vyrovnávání zatížení a distribuované zpracování spotřebních a podnikových scénářích.</span><span class="sxs-lookup"><span data-stu-id="a2c79-106">Peer Channel enables P2P collaboration, content distribution, load balancing, and distributed processing for both consumer and enterprise scenarios.</span></span>  
  
 <span data-ttu-id="a2c79-107">Rovnocenného kanálu je ve výchozím nastavení povolené na [!INCLUDE[wv](../../../../includes/wv-md.md)], jako je všechny [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a2c79-107">Peer Channel is enabled by default on [!INCLUDE[wv](../../../../includes/wv-md.md)], as is all of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span> <span data-ttu-id="a2c79-108">Pro přístup k rovnocenného kanálu třídy, přidejte odkazy na System.ServiceModel.dll do projektu.</span><span class="sxs-lookup"><span data-stu-id="a2c79-108">To access Peer Channel classes, add references to System.ServiceModel.dll to your project.</span></span>  
  
 <span data-ttu-id="a2c79-109">Následující části obsahují informace o peer-to-peer sítě a používání tříd rovnocenného kanálu vytvořit peer povoleno síťových aplikací.</span><span class="sxs-lookup"><span data-stu-id="a2c79-109">The following sections contain information about peer-to-peer networking and the use of Peer Channel classes to create peer-enabled network applications.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2c79-110">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a2c79-110">In This Section</span></span>  
 <span data-ttu-id="a2c79-111">[Peer scénáře kanálů](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md): Popisuje nepodporuje rozhraní API sdílené kanál, vývojové scénáře, jako je zasílání zpráv a spolupráci, publikování/předplatné distribuované zpracování a hry.</span><span class="sxs-lookup"><span data-stu-id="a2c79-111">[Peer Channel Scenarios](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md):  Describes development scenarios supported by the Peer Channel APIs, such as publication/subscription messaging, collaboration, distributed processing, and gaming.</span></span>  
  
 <span data-ttu-id="a2c79-112">[Peer koncepty kanálu](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md): Popisuje sdílené mřížky, partnerské uzly, zabezpečení rovnocenného kanálu a překladače partnerských uzlů.</span><span class="sxs-lookup"><span data-stu-id="a2c79-112">[Peer Channel Concepts](../../../../docs/framework/wcf/feature-details/peer-channel-concepts.md):  Describes Peer Meshes, Peer Nodes, Peer Channel security, and Peer Resolvers.</span></span>  
  
 <span data-ttu-id="a2c79-113">[Vytvoření aplikace kanálu sdílené](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md): obsahuje pokyny týkající se vývoje aplikací rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="a2c79-113">[Building a Peer Channel Application](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md):  Provides guidance on developing Peer Channel applications.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="a2c79-114">Příklady kódu rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="a2c79-114">Peer Channel Code Examples</span></span>  
 [<span data-ttu-id="a2c79-115">Překladač vlastní sdílené rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="a2c79-115">Peer Channel Custom Peer Resolver</span></span>](http://msdn.microsoft.com/library/5b75a2bb-7ff1-4a14-abe7-3debf0537d23)  
  
## <a name="peer-channel-team-blog"></a><span data-ttu-id="a2c79-116">Blog týmu rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="a2c79-116">Peer Channel Team blog</span></span>  
 <span data-ttu-id="a2c79-117">[Blog týmu rovnocenného kanálu](http://go.microsoft.com/fwlink/?LinkID=114530) (http://go.microsoft.com/fwlink/?LinkID=114530)</span><span class="sxs-lookup"><span data-stu-id="a2c79-117">[Peer Channel Team Blog](http://go.microsoft.com/fwlink/?LinkID=114530) (http://go.microsoft.com/fwlink/?LinkID=114530)</span></span>

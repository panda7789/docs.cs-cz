---
title: Rozšíření vrstvy kanálu
ms.date: 03/30/2017
helpviewer_keywords:
- extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
ms.openlocfilehash: 76ca76d7973403c657b8f68bfde9619df36f220e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797134"
---
# <a name="extending-the-channel-layer"></a><span data-ttu-id="b1ff6-102">Rozšíření vrstvy kanálu</span><span class="sxs-lookup"><span data-stu-id="b1ff6-102">Extending the Channel Layer</span></span>
<span data-ttu-id="b1ff6-103">Vrstva kanálu zodpovídá za výměnu zpráv mezi klienty a službami.</span><span class="sxs-lookup"><span data-stu-id="b1ff6-103">The channel layer is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="b1ff6-104">Rozšíření kanálů můžou implementovat nové funkce protokolu, jako je zabezpečení nebo funkce přenosu, jako je implementace nového síťového přenosu pro přenos zpráv SOAP.</span><span class="sxs-lookup"><span data-stu-id="b1ff6-104">Channel extensions can implement new protocol functionality, such as security, or transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b1ff6-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="b1ff6-105">In This Section</span></span>  
 [<span data-ttu-id="b1ff6-106">Přehled modelu kanálu</span><span class="sxs-lookup"><span data-stu-id="b1ff6-106">Channel Model Overview</span></span>](channel-model-overview.md)  
 <span data-ttu-id="b1ff6-107">Poskytuje podrobný přehled o tom, jaké kanály jsou, funkce, které poskytují, a jak fungují jak ve službě, tak v klientské aplikaci.</span><span class="sxs-lookup"><span data-stu-id="b1ff6-107">Provides a high-level overview of what channels are, the features that they provide and how they work both in a service and a client application.</span></span>  
  
 [<span data-ttu-id="b1ff6-108">Vývoj kanálů</span><span class="sxs-lookup"><span data-stu-id="b1ff6-108">Developing Channels</span></span>](developing-channels.md)  
 <span data-ttu-id="b1ff6-109">Podrobně popisuje role, které jsou aktérem různých typů infrastruktury kanálu, jak funguje stavový modul a životní cyklus stavu, jak zpracovávat výjimky a chyby, jak implementovat podporu metadat a jak kanály fungují s kodéry zpráv.</span><span class="sxs-lookup"><span data-stu-id="b1ff6-109">Describes in depth the roles that the various channel infrastructure types play, how the state engine and state lifecycle works, how to handle exceptions and faults, how to implement metadata support, and how channels work with message encoders.</span></span>  
  
 [<span data-ttu-id="b1ff6-110">Vlastní kodéry</span><span class="sxs-lookup"><span data-stu-id="b1ff6-110">Custom Encoders</span></span>](custom-encoders.md)  
 <span data-ttu-id="b1ff6-111">Popisuje roli, kterou kodéry zpráv hrají v kanálech a jak je sestavit.</span><span class="sxs-lookup"><span data-stu-id="b1ff6-111">Describes the role that message encoders play in channels and how to build one.</span></span>  
  
 [<span data-ttu-id="b1ff6-112">Vlastní upgrady streamů</span><span class="sxs-lookup"><span data-stu-id="b1ff6-112">Custom Stream Upgrades</span></span>](custom-stream-upgrades.md)  
 <span data-ttu-id="b1ff6-113">Popisuje proces upgradu datových proudů poskytovaných přenosy orientovanými na proud.</span><span class="sxs-lookup"><span data-stu-id="b1ff6-113">Describes the process of upgrading the streams provided by stream-oriented transports.</span></span>

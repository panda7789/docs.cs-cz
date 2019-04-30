---
title: Rozšíření vrstvy kanálu
ms.date: 03/30/2017
helpviewer_keywords:
- extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
ms.openlocfilehash: e60d8ef1a5191c6407b01eb1a2456a06aeeb1914
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857906"
---
# <a name="extending-the-channel-layer"></a><span data-ttu-id="83537-102">Rozšíření vrstvy kanálu</span><span class="sxs-lookup"><span data-stu-id="83537-102">Extending the Channel Layer</span></span>
<span data-ttu-id="83537-103">Kanál vrstvu je zodpovědná za výměny zpráv mezi klienty a služby.</span><span class="sxs-lookup"><span data-stu-id="83537-103">The channel layer is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="83537-104">Rozšíření kanálu můžete implementovat nové funkce protokolu, jako je zabezpečení nebo přenos funkce, jako je například implementace nového síťového přenosu přenášet zprávy protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="83537-104">Channel extensions can implement new protocol functionality, such as security, or transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="83537-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="83537-105">In This Section</span></span>  
 [<span data-ttu-id="83537-106">Přehled modelu kanálu</span><span class="sxs-lookup"><span data-stu-id="83537-106">Channel Model Overview</span></span>](../../../../docs/framework/wcf/extending/channel-model-overview.md)  
 <span data-ttu-id="83537-107">Poskytuje základní přehled o jaké kanály jsou funkce, které obsahují a jak pracují v službu a klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="83537-107">Provides a high-level overview of what channels are, the features that they provide and how they work both in a service and a client application.</span></span>  
  
 [<span data-ttu-id="83537-108">Vývoj kanálů</span><span class="sxs-lookup"><span data-stu-id="83537-108">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)  
 <span data-ttu-id="83537-109">Podrobně popisuje role, které přehrát různých typů kanálů infrastruktury, jak funguje životní cyklus pro modul a stavu stavu, způsob zpracování výjimek a chyb, jak implementovat podpora metadat a fungování kanálů pomocí zprávy kodérů.</span><span class="sxs-lookup"><span data-stu-id="83537-109">Describes in depth the roles that the various channel infrastructure types play, how the state engine and state lifecycle works, how to handle exceptions and faults, how to implement metadata support, and how channels work with message encoders.</span></span>  
  
 [<span data-ttu-id="83537-110">Vlastní kodéry</span><span class="sxs-lookup"><span data-stu-id="83537-110">Custom Encoders</span></span>](../../../../docs/framework/wcf/extending/custom-encoders.md)  
 <span data-ttu-id="83537-111">Popisuje role, které hrají kodérů zpráv do kanálů a jak takovou sestavit.</span><span class="sxs-lookup"><span data-stu-id="83537-111">Describes the role that message encoders play in channels and how to build one.</span></span>  
  
 [<span data-ttu-id="83537-112">Vlastní upgrady streamů</span><span class="sxs-lookup"><span data-stu-id="83537-112">Custom Stream Upgrades</span></span>](../../../../docs/framework/wcf/extending/custom-stream-upgrades.md)  
 <span data-ttu-id="83537-113">Popisuje postup upgradu datové proudy poskytované orientovaný na stream přenosy.</span><span class="sxs-lookup"><span data-stu-id="83537-113">Describes the process of upgrading the streams provided by stream-oriented transports.</span></span>

---
title: "Rozšíření vrstvy kanálu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5a1a1bb0b1f2c5e6b42ee793f18f5ad442b1fe8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="extending-the-channel-layer"></a><span data-ttu-id="31306-102">Rozšíření vrstvy kanálu</span><span class="sxs-lookup"><span data-stu-id="31306-102">Extending the Channel Layer</span></span>
<span data-ttu-id="31306-103">Vrstvy kanálu je zodpovědná za výměny zpráv mezi klienty a služby.</span><span class="sxs-lookup"><span data-stu-id="31306-103">The channel layer is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="31306-104">Kanál rozšíření můžete implementovat nové funkce protokolu, například zabezpečení nebo funkce přenosu, například implementace nový síťový přenos pro přenos protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="31306-104">Channel extensions can implement new protocol functionality, such as security, or transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="31306-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="31306-105">In This Section</span></span>  
 [<span data-ttu-id="31306-106">Přehled modelu kanálu</span><span class="sxs-lookup"><span data-stu-id="31306-106">Channel Model Overview</span></span>](../../../../docs/framework/wcf/extending/channel-model-overview.md)  
 <span data-ttu-id="31306-107">Poskytuje přehled jsou jaké kanály, funkce, které obsahují a jak pracují v službu a klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="31306-107">Provides a high-level overview of what channels are, the features that they provide and how they work both in a service and a client application.</span></span>  
  
 [<span data-ttu-id="31306-108">Vývoj kanálů</span><span class="sxs-lookup"><span data-stu-id="31306-108">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)  
 <span data-ttu-id="31306-109">Popisuje podrobněji role, které přehrání různé typy infrastruktury kanál, Princip životního cyklu pro stav a modul stavu, postupy: zpracování výjimek a chyb, jak implementovat podporu metadat a jak fungují kanály s kodéry zprávy.</span><span class="sxs-lookup"><span data-stu-id="31306-109">Describes in depth the roles that the various channel infrastructure types play, how the state engine and state lifecycle works, how to handle exceptions and faults, how to implement metadata support, and how channels work with message encoders.</span></span>  
  
 [<span data-ttu-id="31306-110">Vlastní kodéry</span><span class="sxs-lookup"><span data-stu-id="31306-110">Custom Encoders</span></span>](../../../../docs/framework/wcf/extending/custom-encoders.md)  
 <span data-ttu-id="31306-111">Popisuje roli zpráva kodéry hrát v kanály a jak vytvořit jeden.</span><span class="sxs-lookup"><span data-stu-id="31306-111">Describes the role that message encoders play in channels and how to build one.</span></span>  
  
 [<span data-ttu-id="31306-112">Vlastní upgrady streamů</span><span class="sxs-lookup"><span data-stu-id="31306-112">Custom Stream Upgrades</span></span>](../../../../docs/framework/wcf/extending/custom-stream-upgrades.md)  
 <span data-ttu-id="31306-113">Popisuje postup upgradu datové proudy poskytované orientované na datový proud přenosy.</span><span class="sxs-lookup"><span data-stu-id="31306-113">Describes the process of upgrading the streams provided by stream-oriented transports.</span></span>

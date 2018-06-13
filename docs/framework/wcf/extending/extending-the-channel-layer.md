---
title: Rozšíření vrstvy kanálu
ms.date: 03/30/2017
helpviewer_keywords:
- extending channels [WCF]
ms.assetid: 4238db74-2fb6-4dc8-a326-f58527230810
ms.openlocfilehash: e60d8ef1a5191c6407b01eb1a2456a06aeeb1914
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488231"
---
# <a name="extending-the-channel-layer"></a><span data-ttu-id="89c95-102">Rozšíření vrstvy kanálu</span><span class="sxs-lookup"><span data-stu-id="89c95-102">Extending the Channel Layer</span></span>
<span data-ttu-id="89c95-103">Vrstvy kanálu je zodpovědná za výměny zpráv mezi klienty a služby.</span><span class="sxs-lookup"><span data-stu-id="89c95-103">The channel layer is responsible for the exchange of messages between clients and services.</span></span> <span data-ttu-id="89c95-104">Kanál rozšíření můžete implementovat nové funkce protokolu, například zabezpečení nebo funkce přenosu, například implementace nový síťový přenos pro přenos protokolu SOAP zprávy.</span><span class="sxs-lookup"><span data-stu-id="89c95-104">Channel extensions can implement new protocol functionality, such as security, or transport functionality, such as implementing a new network transport to carry SOAP messages.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="89c95-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="89c95-105">In This Section</span></span>  
 [<span data-ttu-id="89c95-106">Přehled modelu kanálu</span><span class="sxs-lookup"><span data-stu-id="89c95-106">Channel Model Overview</span></span>](../../../../docs/framework/wcf/extending/channel-model-overview.md)  
 <span data-ttu-id="89c95-107">Poskytuje přehled jsou jaké kanály, funkce, které obsahují a jak pracují v službu a klientskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="89c95-107">Provides a high-level overview of what channels are, the features that they provide and how they work both in a service and a client application.</span></span>  
  
 [<span data-ttu-id="89c95-108">Vývoj kanálů</span><span class="sxs-lookup"><span data-stu-id="89c95-108">Developing Channels</span></span>](../../../../docs/framework/wcf/extending/developing-channels.md)  
 <span data-ttu-id="89c95-109">Popisuje podrobněji role, které přehrání různé typy infrastruktury kanál, Princip životního cyklu pro stav a modul stavu, postupy: zpracování výjimek a chyb, jak implementovat podporu metadat a jak fungují kanály s kodéry zprávy.</span><span class="sxs-lookup"><span data-stu-id="89c95-109">Describes in depth the roles that the various channel infrastructure types play, how the state engine and state lifecycle works, how to handle exceptions and faults, how to implement metadata support, and how channels work with message encoders.</span></span>  
  
 [<span data-ttu-id="89c95-110">Vlastní kodéry</span><span class="sxs-lookup"><span data-stu-id="89c95-110">Custom Encoders</span></span>](../../../../docs/framework/wcf/extending/custom-encoders.md)  
 <span data-ttu-id="89c95-111">Popisuje roli zpráva kodéry hrát v kanály a jak vytvořit jeden.</span><span class="sxs-lookup"><span data-stu-id="89c95-111">Describes the role that message encoders play in channels and how to build one.</span></span>  
  
 [<span data-ttu-id="89c95-112">Vlastní upgrady streamů</span><span class="sxs-lookup"><span data-stu-id="89c95-112">Custom Stream Upgrades</span></span>](../../../../docs/framework/wcf/extending/custom-stream-upgrades.md)  
 <span data-ttu-id="89c95-113">Popisuje postup upgradu datové proudy poskytované orientované na datový proud přenosy.</span><span class="sxs-lookup"><span data-stu-id="89c95-113">Describes the process of upgrading the streams provided by stream-oriented transports.</span></span>

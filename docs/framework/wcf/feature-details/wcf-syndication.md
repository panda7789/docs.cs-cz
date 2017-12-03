---
title: Syndikace WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: syndication [WCF]
ms.assetid: ebf80384-0fc9-4919-a1e8-23ca2a13e300
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 14f2aa18b1fba92f5559b463d90dcfb5b34e2a3f
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-syndication"></a><span data-ttu-id="cf795-102">Syndikace WCF</span><span class="sxs-lookup"><span data-stu-id="cf795-102">WCF Syndication</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="cf795-103">poskytuje podporu pro snadno pracovat s informační kanály syndikace v Atom, RSS nebo dalších vlastních formátů, které umožňuje číst a jejich vytvoření a také je vystavit na koncový bod služby.</span><span class="sxs-lookup"><span data-stu-id="cf795-103"> provides support to easily work with syndication feeds in Atom, RSS or other custom formats, which allows you to read and create them as well as expose them on a service endpoint.</span></span> <span data-ttu-id="cf795-104">Témata v této části popisují tato programovací model pro syndikace podrobně.</span><span class="sxs-lookup"><span data-stu-id="cf795-104">The topics in this section describe this programming model for syndication in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="cf795-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="cf795-105">In This Section</span></span>  
 [<span data-ttu-id="cf795-106">Syndikace WCF – přehled</span><span class="sxs-lookup"><span data-stu-id="cf795-106">WCF Syndication Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication-overview.md)  
 <span data-ttu-id="cf795-107">Poskytuje přehled podpory syndikace poskytované [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="cf795-107">Provides an overview of syndication support provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="cf795-108">Architektura syndikace</span><span class="sxs-lookup"><span data-stu-id="cf795-108">Architecture of Syndication</span></span>](../../../../docs/framework/wcf/feature-details/architecture-of-syndication.md)  
 <span data-ttu-id="cf795-109">Popisuje třídy v objektový model a rozšiřitelnost syndikace.</span><span class="sxs-lookup"><span data-stu-id="cf795-109">Describes the classes in the object model and the extensibility of syndication.</span></span>  
  
 [<span data-ttu-id="cf795-110">Jak mapuje modelu objektu syndikace WCF na Atom a RSS</span><span class="sxs-lookup"><span data-stu-id="cf795-110">How the WCF Syndication Object Model Maps to Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)  
 <span data-ttu-id="cf795-111">Popisuje zastoupení informační kanály v rámci modelu objektu syndikace WCF a jak se převedou na RSS a Atom kanály.</span><span class="sxs-lookup"><span data-stu-id="cf795-111">Describes how feeds are represented within the WCF Syndication Object Model and how they are converted to RSS and Atom feeds.</span></span>  
  
 [<span data-ttu-id="cf795-112">Postupy: vytvoření základního kanálu RSS</span><span class="sxs-lookup"><span data-stu-id="cf795-112">How to: Create a Basic RSS Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-rss-feed.md)  
 <span data-ttu-id="cf795-113">Ukazuje, jak vytvořit službu, která zpřístupňuje základní informační kanál RSS.</span><span class="sxs-lookup"><span data-stu-id="cf795-113">Shows how to create a service that makes a basic RSS feed available.</span></span>  
  
 [<span data-ttu-id="cf795-114">Postupy: vytvoření základního informačního kanálu Atom</span><span class="sxs-lookup"><span data-stu-id="cf795-114">How to: Create a Basic Atom Feed</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-atom-feed.md)  
 <span data-ttu-id="cf795-115">Ukazuje, jak vytvořit službu, která zpřístupňuje základní importován informační kanál ATOM.</span><span class="sxs-lookup"><span data-stu-id="cf795-115">Shows how to create a service that makes a basic ATOM feed available.</span></span>  
  
 [<span data-ttu-id="cf795-116">Postupy: vystavení informačního kanálu jako Atom a RSS</span><span class="sxs-lookup"><span data-stu-id="cf795-116">How to: Expose a Feed as Both Atom and RSS</span></span>](../../../../docs/framework/wcf/feature-details/how-to-expose-a-feed-as-both-atom-and-rss.md)  
 <span data-ttu-id="cf795-117">Ukazuje, jak vytvořit službu, která zpřístupňuje stejné informačního kanálu ATOM a RSS.</span><span class="sxs-lookup"><span data-stu-id="cf795-117">Shows how to create a service that makes the same feed available with ATOM and RSS.</span></span>  
  
 [<span data-ttu-id="cf795-118">Rozšiřitelnost syndikace</span><span class="sxs-lookup"><span data-stu-id="cf795-118">Syndication Extensibility</span></span>](../../../../docs/framework/wcf/feature-details/syndication-extensibility.md)  
 <span data-ttu-id="cf795-119">Popisuje metody přidávání vlastní elementy a atributy do syndikace informačního kanálu.</span><span class="sxs-lookup"><span data-stu-id="cf795-119">Describes the methods of adding custom elements and attributes to a syndication feed.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="cf795-120">Odkaz</span><span class="sxs-lookup"><span data-stu-id="cf795-120">Reference</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="cf795-121">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="cf795-121">Related Sections</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf795-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf795-122">See Also</span></span>  
 [<span data-ttu-id="cf795-123">Model programování webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="cf795-123">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="cf795-124">Částečná důvěryhodnost</span><span class="sxs-lookup"><span data-stu-id="cf795-124">Partial Trust</span></span>](../../../../docs/framework/wcf/feature-details/partial-trust.md)

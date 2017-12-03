---
title: "Zjišťování WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0c9b083180870e451816b54dddc10068ca7ec5db
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="wcf-discovery"></a><span data-ttu-id="e81c4-102">Zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="e81c4-102">WCF Discovery</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="e81c4-103">poskytuje podporu pro povolení služby umožňuje vzájemnou spolupráci způsobem pomocí protokolu WS-Discovery být zjistitelný za běhu.</span><span class="sxs-lookup"><span data-stu-id="e81c4-103"> provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="e81c4-104">služby může informovat jejich dostupnost k síti pomocí vícesměrového vysílání zprávy nebo na proxy serveru zjišťování.</span><span class="sxs-lookup"><span data-stu-id="e81c4-104"> services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="e81c4-105">Klientské aplikace může hledat v síti nebo proxy server zjišťování k vyhledání služeb, které splňují zadaná kritéria.</span><span class="sxs-lookup"><span data-stu-id="e81c4-105">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="e81c4-106">Témata v této části poskytují přehled a programovací model pro tuto funkci podrobně popisují.</span><span class="sxs-lookup"><span data-stu-id="e81c4-106">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e81c4-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e81c4-107">In This Section</span></span>  
 [<span data-ttu-id="e81c4-108">Přehled zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="e81c4-108">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 <span data-ttu-id="e81c4-109">Poskytuje přehled podpory WS-Discovery poskytuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e81c4-109">Provides an overview of WS-Discovery support provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="e81c4-110">Objektový Model zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="e81c4-110">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)  
 <span data-ttu-id="e81c4-111">Popisuje třídy v objektovém modelu a rozšiřitelnost WS-Discovery podpory.</span><span class="sxs-lookup"><span data-stu-id="e81c4-111">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="e81c4-112">Postupy: programové přidání možností rozpoznání do klienta a služby WCF</span><span class="sxs-lookup"><span data-stu-id="e81c4-112">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="e81c4-113">Ukazuje, jak vytvořit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby zjistitelný.</span><span class="sxs-lookup"><span data-stu-id="e81c4-113">Shows how to make a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service discoverable.</span></span>  
  
 [<span data-ttu-id="e81c4-114">Implementace Proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="e81c4-114">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 <span data-ttu-id="e81c4-115">Popisuje kroky potřebné k provedení zjišťování proxy, zjistitelný služba, která registruje s proxy serverem, zjišťování a klient, který používá zjišťování proxy k vyhledání zjistitelný služby.</span><span class="sxs-lookup"><span data-stu-id="e81c4-115">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="e81c4-116">Správa verzí zjišťování</span><span class="sxs-lookup"><span data-stu-id="e81c4-116">Discovery Versioning</span></span>](../../../../docs/framework/wcf/feature-details/discovery-versioning.md)  
 <span data-ttu-id="e81c4-117">Poskytuje stručný přehled na prototypu implementace některé nové funkce zjišťování.</span><span class="sxs-lookup"><span data-stu-id="e81c4-117">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="e81c4-118">Také nabízí přehled o tom, jak vybrat zjišťování verze se má použít.</span><span class="sxs-lookup"><span data-stu-id="e81c4-118">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="e81c4-119">Konfigurace zjišťování v konfiguračním souboru</span><span class="sxs-lookup"><span data-stu-id="e81c4-119">Configuring Discovery in a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="e81c4-120">Ukazuje, jak nakonfigurovat zjišťování v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="e81c4-120">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="e81c4-121">Pomocí kanálem klienta zjišťování</span><span class="sxs-lookup"><span data-stu-id="e81c4-121">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 <span data-ttu-id="e81c4-122">Ukazuje, jak k použití kanálu klienta zjišťování při zápisu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="e81c4-122">Shows how to use a Discovery Client Channel when writing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application.</span></span>

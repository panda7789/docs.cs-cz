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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fda50f14d9003b81f93840571b8b27f874f7730b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="wcf-discovery"></a><span data-ttu-id="a0269-102">Zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="a0269-102">WCF Discovery</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="a0269-103">poskytuje podporu pro povolení služby umožňuje vzájemnou spolupráci způsobem pomocí protokolu WS-Discovery být zjistitelný za běhu.</span><span class="sxs-lookup"><span data-stu-id="a0269-103"> provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="a0269-104">služby může informovat jejich dostupnost k síti pomocí vícesměrového vysílání zprávy nebo na proxy serveru zjišťování.</span><span class="sxs-lookup"><span data-stu-id="a0269-104"> services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="a0269-105">Klientské aplikace může hledat v síti nebo proxy server zjišťování k vyhledání služeb, které splňují zadaná kritéria.</span><span class="sxs-lookup"><span data-stu-id="a0269-105">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="a0269-106">Témata v této části poskytují přehled a programovací model pro tuto funkci podrobně popisují.</span><span class="sxs-lookup"><span data-stu-id="a0269-106">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a0269-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a0269-107">In This Section</span></span>  
 [<span data-ttu-id="a0269-108">Přehled zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="a0269-108">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 <span data-ttu-id="a0269-109">Poskytuje přehled podpory WS-Discovery poskytuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span><span class="sxs-lookup"><span data-stu-id="a0269-109">Provides an overview of WS-Discovery support provided by [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
 [<span data-ttu-id="a0269-110">Objektový Model zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="a0269-110">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)  
 <span data-ttu-id="a0269-111">Popisuje třídy v objektovém modelu a rozšiřitelnost WS-Discovery podpory.</span><span class="sxs-lookup"><span data-stu-id="a0269-111">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="a0269-112">Postupy: programové přidání možností rozpoznání do klienta a služby WCF</span><span class="sxs-lookup"><span data-stu-id="a0269-112">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="a0269-113">Ukazuje, jak vytvořit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby zjistitelný.</span><span class="sxs-lookup"><span data-stu-id="a0269-113">Shows how to make a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service discoverable.</span></span>  
  
 [<span data-ttu-id="a0269-114">Implementace Proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="a0269-114">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 <span data-ttu-id="a0269-115">Popisuje kroky potřebné k provedení zjišťování proxy, zjistitelný služba, která registruje s proxy serverem, zjišťování a klient, který používá zjišťování proxy k vyhledání zjistitelný služby.</span><span class="sxs-lookup"><span data-stu-id="a0269-115">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="a0269-116">Správa verzí zjišťování</span><span class="sxs-lookup"><span data-stu-id="a0269-116">Discovery Versioning</span></span>](../../../../docs/framework/wcf/feature-details/discovery-versioning.md)  
 <span data-ttu-id="a0269-117">Poskytuje stručný přehled na prototypu implementace některé nové funkce zjišťování.</span><span class="sxs-lookup"><span data-stu-id="a0269-117">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="a0269-118">Také nabízí přehled o tom, jak vybrat zjišťování verze se má použít.</span><span class="sxs-lookup"><span data-stu-id="a0269-118">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="a0269-119">Konfigurace zjišťování v konfiguračním souboru</span><span class="sxs-lookup"><span data-stu-id="a0269-119">Configuring Discovery in a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="a0269-120">Ukazuje, jak nakonfigurovat zjišťování v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a0269-120">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="a0269-121">Pomocí kanálem klienta zjišťování</span><span class="sxs-lookup"><span data-stu-id="a0269-121">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 <span data-ttu-id="a0269-122">Ukazuje, jak k použití kanálu klienta zjišťování při zápisu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="a0269-122">Shows how to use a Discovery Client Channel when writing a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client application.</span></span>

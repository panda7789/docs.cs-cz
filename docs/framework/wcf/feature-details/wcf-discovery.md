---
title: Zjišťování WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
ms.openlocfilehash: 63c6589cb2ecff9f0a5e7c8bb61b454f6516c98c
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600176"
---
# <a name="wcf-discovery"></a><span data-ttu-id="42c7a-102">Zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="42c7a-102">WCF Discovery</span></span>
<span data-ttu-id="42c7a-103">Windows Communication Foundation (WCF) poskytuje podporu pro povolení zjistitelnosti služeb za běhu pomocí protokolu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="42c7a-103">Windows Communication Foundation (WCF) provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> <span data-ttu-id="42c7a-104">Služby WCF mohou oznámit jejich dostupnost síti pomocí zprávy vícesměrového vysílání nebo proxy server zjišťování.</span><span class="sxs-lookup"><span data-stu-id="42c7a-104">WCF services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="42c7a-105">Klientské aplikace mohou vyhledat služby, které splňují sadu kritérií, a proxy server zjišťování.</span><span class="sxs-lookup"><span data-stu-id="42c7a-105">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="42c7a-106">Témata v této části poskytují přehled a popisují programovací model pro tuto funkci podrobněji.</span><span class="sxs-lookup"><span data-stu-id="42c7a-106">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="42c7a-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="42c7a-107">In This Section</span></span>  
 [<span data-ttu-id="42c7a-108">Přehled zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="42c7a-108">WCF Discovery Overview</span></span>](wcf-discovery-overview.md)  
 <span data-ttu-id="42c7a-109">Poskytuje přehled podpory WS-Discovery poskytované službou WCF.</span><span class="sxs-lookup"><span data-stu-id="42c7a-109">Provides an overview of WS-Discovery support provided by WCF.</span></span>  
  
 [<span data-ttu-id="42c7a-110">Objektový model zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="42c7a-110">WCF Discovery Object Model</span></span>](wcf-discovery-object-model.md)  
 <span data-ttu-id="42c7a-111">Popisuje třídy v objektovém modelu a rozšiřitelnost pro podporu WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="42c7a-111">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="42c7a-112">Postupy: Programové přidání zjistitelnosti do klienta a služby WCF</span><span class="sxs-lookup"><span data-stu-id="42c7a-112">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="42c7a-113">Ukazuje, jak nastavit službu Windows Communication Foundation (WCF) jako zjistitelnou.</span><span class="sxs-lookup"><span data-stu-id="42c7a-113">Shows how to make a Windows Communication Foundation (WCF) service discoverable.</span></span>  
  
 [<span data-ttu-id="42c7a-114">Implementace proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="42c7a-114">Implementing a Discovery Proxy</span></span>](implementing-a-discovery-proxy.md)  
 <span data-ttu-id="42c7a-115">Popisuje kroky potřebné k implementaci proxy zjišťování, zjistitelné služby, která se registruje pomocí proxy zjišťování, a klienta, který používá proxy zjišťování k vyhledání zjistitelné služby.</span><span class="sxs-lookup"><span data-stu-id="42c7a-115">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="42c7a-116">Správa verzí zjišťování</span><span class="sxs-lookup"><span data-stu-id="42c7a-116">Discovery Versioning</span></span>](discovery-versioning.md)  
 <span data-ttu-id="42c7a-117">Poskytuje stručný přehled implementace prototypů některých nových funkcí zjišťování.</span><span class="sxs-lookup"><span data-stu-id="42c7a-117">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="42c7a-118">Poskytuje také přehled o tom, jak vybrat verzi zjišťování, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="42c7a-118">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="42c7a-119">Konfigurace zjišťování v konfiguračním souboru</span><span class="sxs-lookup"><span data-stu-id="42c7a-119">Configuring Discovery in a Configuration File</span></span>](configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="42c7a-120">Ukazuje, jak nakonfigurovat zjišťování v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="42c7a-120">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="42c7a-121">Použití kanálu klienta zjišťování</span><span class="sxs-lookup"><span data-stu-id="42c7a-121">Using the Discovery Client Channel</span></span>](using-the-discovery-client-channel.md)  
 <span data-ttu-id="42c7a-122">Ukazuje, jak použít kanál klienta zjišťování při psaní klientské aplikace WCF.</span><span class="sxs-lookup"><span data-stu-id="42c7a-122">Shows how to use a Discovery Client Channel when writing a WCF client application.</span></span>

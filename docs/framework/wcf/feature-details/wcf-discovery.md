---
title: Zjišťování WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], discovery
- Windows Communication Foundation [WCF], discovery
- discovery [WCF]
ms.assetid: 462c4913-f388-45a9-9042-28ae96a4e735
ms.openlocfilehash: 175f79096d2bbda81a602d38e027d5a6d871fa12
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768690"
---
# <a name="wcf-discovery"></a><span data-ttu-id="4e8e9-102">Zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="4e8e9-102">WCF Discovery</span></span>
<span data-ttu-id="4e8e9-103">Windows Communication Foundation (WCF) poskytuje podporu pro povolení služby být zjistitelné za běhu pomocí protokolu WS-Discovery interoperabilní způsobem.</span><span class="sxs-lookup"><span data-stu-id="4e8e9-103">Windows Communication Foundation (WCF) provides support to enable services to be discoverable at runtime in an interoperable way using the WS-Discovery protocol.</span></span> <span data-ttu-id="4e8e9-104">Služby WCF můžete oznamujeme jejich dostupnosti, síť pomocí vícesměrového vysílání zprávy nebo na proxy serveru zjišťování.</span><span class="sxs-lookup"><span data-stu-id="4e8e9-104">WCF services can announce their availability to the network using a multicast message or to a discovery proxy server.</span></span> <span data-ttu-id="4e8e9-105">Klientské aplikace můžete vyhledávat v síti nebo server proxy zjišťování k vyhledání služby, které splňují sadu kritérií.</span><span class="sxs-lookup"><span data-stu-id="4e8e9-105">Client applications can search the network or a discovery proxy server to find services that meet a set of criteria.</span></span> <span data-ttu-id="4e8e9-106">Témata v této části poskytují přehled a programovací model pro tuto funkci podrobně popisují.</span><span class="sxs-lookup"><span data-stu-id="4e8e9-106">The topics in this section provide an overview and describe the programming model for this feature in detail.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4e8e9-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4e8e9-107">In This Section</span></span>  
 [<span data-ttu-id="4e8e9-108">Přehled zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="4e8e9-108">WCF Discovery Overview</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-overview.md)  
 <span data-ttu-id="4e8e9-109">Poskytuje přehled podpory WS-Discovery poskytuje WCF.</span><span class="sxs-lookup"><span data-stu-id="4e8e9-109">Provides an overview of WS-Discovery support provided by WCF.</span></span>  
  
 [<span data-ttu-id="4e8e9-110">Objektový model zjišťování WCF</span><span class="sxs-lookup"><span data-stu-id="4e8e9-110">WCF Discovery Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-discovery-object-model.md)  
 <span data-ttu-id="4e8e9-111">Popisuje třídy v objektovém modelu a rozšíření podpory WS-Discovery.</span><span class="sxs-lookup"><span data-stu-id="4e8e9-111">Describes the classes in the object model and extensibility of WS-Discovery support.</span></span>  
  
 [<span data-ttu-id="4e8e9-112">Postupy: Programové přidání možností rozpoznání do klienta a služby WCF</span><span class="sxs-lookup"><span data-stu-id="4e8e9-112">How to: Programmatically Add Discoverability to a WCF Service and Client</span></span>](../../../../docs/framework/wcf/feature-details/how-to-programmatically-add-discoverability-to-a-wcf-service-and-client.md)  
 <span data-ttu-id="4e8e9-113">Ukazuje, jak zjistitelnost služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="4e8e9-113">Shows how to make a Windows Communication Foundation (WCF) service discoverable.</span></span>  
  
 [<span data-ttu-id="4e8e9-114">Implementace proxy zjišťování</span><span class="sxs-lookup"><span data-stu-id="4e8e9-114">Implementing a Discovery Proxy</span></span>](../../../../docs/framework/wcf/feature-details/implementing-a-discovery-proxy.md)  
 <span data-ttu-id="4e8e9-115">Popisuje kroky potřebné k implementaci proxy zjišťování, zjistitelné služby, která se registruje pomocí proxy zjišťování a klient používající zjišťování proxy k vyhledání zjistitelné služby.</span><span class="sxs-lookup"><span data-stu-id="4e8e9-115">Describes the steps required to implement a discovery proxy, a discoverable service that registers with the discovery proxy, and a client that uses the discovery proxy to find the discoverable service.</span></span>  
  
 [<span data-ttu-id="4e8e9-116">Správa verzí zjišťování</span><span class="sxs-lookup"><span data-stu-id="4e8e9-116">Discovery Versioning</span></span>](../../../../docs/framework/wcf/feature-details/discovery-versioning.md)  
 <span data-ttu-id="4e8e9-117">Poskytuje stručný přehled prototypu provádění některé nové funkce zjišťování.</span><span class="sxs-lookup"><span data-stu-id="4e8e9-117">Provides a brief overview of a prototype implementation of some new discovery features.</span></span> <span data-ttu-id="4e8e9-118">Poskytuje také přehled o tom, jak vybrat zjišťování verze se má použít.</span><span class="sxs-lookup"><span data-stu-id="4e8e9-118">It also gives an overview on how to select the discovery version to use.</span></span>  
  
 [<span data-ttu-id="4e8e9-119">Konfigurace zjišťování v konfiguračním souboru</span><span class="sxs-lookup"><span data-stu-id="4e8e9-119">Configuring Discovery in a Configuration File</span></span>](../../../../docs/framework/wcf/feature-details/configuring-discovery-in-a-configuration-file.md)  
 <span data-ttu-id="4e8e9-120">Ukazuje, jak nakonfigurovat zjišťování v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="4e8e9-120">Shows how to configure Discovery in configuration.</span></span>  
  
 [<span data-ttu-id="4e8e9-121">Použití kanálu klienta zjišťování</span><span class="sxs-lookup"><span data-stu-id="4e8e9-121">Using the Discovery Client Channel</span></span>](../../../../docs/framework/wcf/feature-details/using-the-discovery-client-channel.md)  
 <span data-ttu-id="4e8e9-122">Ukazuje způsob použití kanálu klienta zjišťování při psaní klientských aplikací WCF.</span><span class="sxs-lookup"><span data-stu-id="4e8e9-122">Shows how to use a Discovery Client Channel when writing a WCF client application.</span></span>

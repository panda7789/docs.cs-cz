---
title: WS-MetadataExchange Bindings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: a7267fa8e71a7bbe202bce9897ea09079307be50
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="24916-102">WS-MetadataExchange Bindings</span><span class="sxs-lookup"><span data-stu-id="24916-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="24916-103">Toto téma popisuje, jak se vytvářejí výchozí metadata exchange vazby pro různé přenosy.</span><span class="sxs-lookup"><span data-stu-id="24916-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="24916-104">Výchozí vazby</span><span class="sxs-lookup"><span data-stu-id="24916-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="24916-105">Výchozí název vazby</span><span class="sxs-lookup"><span data-stu-id="24916-105">Default Binding Name</span></span>|<span data-ttu-id="24916-106">Jak je vytvořený vazby</span><span class="sxs-lookup"><span data-stu-id="24916-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="24916-107">MexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="24916-107">MexHttpBinding</span></span>|<span data-ttu-id="24916-108">A <xref:System.ServiceModel.WSHttpBinding> s zabezpečení na úrovni přenosu zakázána.</span><span class="sxs-lookup"><span data-stu-id="24916-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="24916-109">MexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="24916-109">MexHttpsBinding</span></span>|<span data-ttu-id="24916-110">A <xref:System.ServiceModel.WSHttpBinding> podporující zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="24916-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="24916-111">MexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="24916-111">MexNamedPipeBinding</span></span>|<span data-ttu-id="24916-112">A <xref:System.ServiceModel.Channels.CustomBinding> s <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> pomocí výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="24916-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="24916-113">MexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="24916-113">MexTcpBinding</span></span>|<span data-ttu-id="24916-114">A <xref:System.ServiceModel.Channels.CustomBinding> s <xref:System.ServiceModel.Channels.TcpTransportBindingElement> pomocí výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="24916-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|

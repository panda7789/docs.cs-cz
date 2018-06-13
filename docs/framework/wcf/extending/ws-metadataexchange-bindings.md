---
title: WS-MetadataExchange Bindings
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 384e5bb05ba4263f245f6901b84e2388ea19bd73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488621"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="9ff82-102">WS-MetadataExchange Bindings</span><span class="sxs-lookup"><span data-stu-id="9ff82-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="9ff82-103">Toto téma popisuje, jak se vytvářejí výchozí metadata exchange vazby pro různé přenosy.</span><span class="sxs-lookup"><span data-stu-id="9ff82-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="9ff82-104">Výchozí vazby</span><span class="sxs-lookup"><span data-stu-id="9ff82-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="9ff82-105">Výchozí název vazby</span><span class="sxs-lookup"><span data-stu-id="9ff82-105">Default Binding Name</span></span>|<span data-ttu-id="9ff82-106">Jak je vytvořený vazby</span><span class="sxs-lookup"><span data-stu-id="9ff82-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="9ff82-107">MexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="9ff82-107">MexHttpBinding</span></span>|<span data-ttu-id="9ff82-108">A <xref:System.ServiceModel.WSHttpBinding> s zabezpečení na úrovni přenosu zakázána.</span><span class="sxs-lookup"><span data-stu-id="9ff82-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="9ff82-109">MexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="9ff82-109">MexHttpsBinding</span></span>|<span data-ttu-id="9ff82-110">A <xref:System.ServiceModel.WSHttpBinding> podporující zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="9ff82-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="9ff82-111">MexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="9ff82-111">MexNamedPipeBinding</span></span>|<span data-ttu-id="9ff82-112">A <xref:System.ServiceModel.Channels.CustomBinding> s <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> pomocí výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="9ff82-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="9ff82-113">MexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="9ff82-113">MexTcpBinding</span></span>|<span data-ttu-id="9ff82-114">A <xref:System.ServiceModel.Channels.CustomBinding> s <xref:System.ServiceModel.Channels.TcpTransportBindingElement> pomocí výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="9ff82-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|

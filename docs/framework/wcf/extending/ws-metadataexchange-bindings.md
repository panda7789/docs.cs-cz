---
title: WS-MetadataExchange Bindings
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 03e6e6d5ee7e69b397acd0f51b8037f02c1804ec
ms.sourcegitcommit: 0888d7b24f475c346a3f444de8d83ec1ca7cd234
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2018
ms.locfileid: "53767345"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="92fc4-102">WS-MetadataExchange Bindings</span><span class="sxs-lookup"><span data-stu-id="92fc4-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="92fc4-103">Toto téma popisuje, jak jsou vytvořeny výchozím vazbám metadata exchange pro různé přenosy.</span><span class="sxs-lookup"><span data-stu-id="92fc4-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="92fc4-104">Výchozí vazby</span><span class="sxs-lookup"><span data-stu-id="92fc4-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="92fc4-105">Výchozí název vazby</span><span class="sxs-lookup"><span data-stu-id="92fc4-105">Default Binding Name</span></span>|<span data-ttu-id="92fc4-106">Jak vytvořit vazbu</span><span class="sxs-lookup"><span data-stu-id="92fc4-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="92fc4-107">mexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="92fc4-107">mexHttpBinding</span></span>|<span data-ttu-id="92fc4-108">A <xref:System.ServiceModel.WSHttpBinding> se zabezpečením na úrovni přenosu zakázán.</span><span class="sxs-lookup"><span data-stu-id="92fc4-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="92fc4-109">mexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="92fc4-109">mexHttpsBinding</span></span>|<span data-ttu-id="92fc4-110">A <xref:System.ServiceModel.WSHttpBinding> , který podporuje zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="92fc4-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="92fc4-111">mexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="92fc4-111">mexNamedPipeBinding</span></span>|<span data-ttu-id="92fc4-112">A <xref:System.ServiceModel.Channels.CustomBinding> s <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> pomocí výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="92fc4-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="92fc4-113">mexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="92fc4-113">mexTcpBinding</span></span>|<span data-ttu-id="92fc4-114">A <xref:System.ServiceModel.Channels.CustomBinding> s <xref:System.ServiceModel.Channels.TcpTransportBindingElement> pomocí výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="92fc4-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|

---
title: WS-MetadataExchange Bindings
ms.date: 03/30/2017
ms.assetid: 10f8de5d-b81d-4ea7-b37e-7f2c00c39714
ms.openlocfilehash: 03e6e6d5ee7e69b397acd0f51b8037f02c1804ec
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61795470"
---
# <a name="ws-metadataexchange-bindings"></a><span data-ttu-id="17204-102">WS-MetadataExchange Bindings</span><span class="sxs-lookup"><span data-stu-id="17204-102">WS-MetadataExchange Bindings</span></span>
<span data-ttu-id="17204-103">Toto téma popisuje, jak jsou vytvořeny výchozím vazbám metadata exchange pro různé přenosy.</span><span class="sxs-lookup"><span data-stu-id="17204-103">This topic describes how the default metadata exchange bindings are constructed for various transports.</span></span>  
  
## <a name="the-default-bindings"></a><span data-ttu-id="17204-104">Výchozí vazby</span><span class="sxs-lookup"><span data-stu-id="17204-104">The Default Bindings</span></span>  
  
|<span data-ttu-id="17204-105">Výchozí název vazby</span><span class="sxs-lookup"><span data-stu-id="17204-105">Default Binding Name</span></span>|<span data-ttu-id="17204-106">Jak vytvořit vazbu</span><span class="sxs-lookup"><span data-stu-id="17204-106">How the binding is constructed</span></span>|  
|--------------------------|------------------------------------|  
|<span data-ttu-id="17204-107">mexHttpBinding</span><span class="sxs-lookup"><span data-stu-id="17204-107">mexHttpBinding</span></span>|<span data-ttu-id="17204-108">A <xref:System.ServiceModel.WSHttpBinding> se zabezpečením na úrovni přenosu zakázán.</span><span class="sxs-lookup"><span data-stu-id="17204-108">A <xref:System.ServiceModel.WSHttpBinding> with transport-level security disabled.</span></span>|  
|<span data-ttu-id="17204-109">mexHttpsBinding</span><span class="sxs-lookup"><span data-stu-id="17204-109">mexHttpsBinding</span></span>|<span data-ttu-id="17204-110">A <xref:System.ServiceModel.WSHttpBinding> , který podporuje zabezpečení na úrovni přenosu.</span><span class="sxs-lookup"><span data-stu-id="17204-110">A <xref:System.ServiceModel.WSHttpBinding> that supports transport-level security.</span></span>|  
|<span data-ttu-id="17204-111">mexNamedPipeBinding</span><span class="sxs-lookup"><span data-stu-id="17204-111">mexNamedPipeBinding</span></span>|<span data-ttu-id="17204-112">A <xref:System.ServiceModel.Channels.CustomBinding> s <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> pomocí výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="17204-112">A  <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement> using the default values.</span></span>|  
|<span data-ttu-id="17204-113">mexTcpBinding</span><span class="sxs-lookup"><span data-stu-id="17204-113">mexTcpBinding</span></span>|<span data-ttu-id="17204-114">A <xref:System.ServiceModel.Channels.CustomBinding> s <xref:System.ServiceModel.Channels.TcpTransportBindingElement> pomocí výchozích hodnot.</span><span class="sxs-lookup"><span data-stu-id="17204-114">A <xref:System.ServiceModel.Channels.CustomBinding> with a <xref:System.ServiceModel.Channels.TcpTransportBindingElement> using default values.</span></span>|

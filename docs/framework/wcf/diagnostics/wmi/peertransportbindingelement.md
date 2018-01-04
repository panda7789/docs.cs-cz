---
title: PeerTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 25893b1f3cf6cf20ae674bade5090a70c5f381a2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="94794-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="94794-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="94794-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="94794-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="94794-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="94794-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="94794-105">Metody</span><span class="sxs-lookup"><span data-stu-id="94794-105">Methods</span></span>  
 <span data-ttu-id="94794-106">Třída PeerTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="94794-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="94794-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="94794-107">Properties</span></span>  
 <span data-ttu-id="94794-108">Třída PeerTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="94794-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="94794-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="94794-109">ListenIPAddress</span></span>  
 <span data-ttu-id="94794-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="94794-110">Data type: string</span></span>  
  
 <span data-ttu-id="94794-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="94794-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94794-112">IP adresa, na kterém naslouchá uzlu sdílené zprávy.</span><span class="sxs-lookup"><span data-stu-id="94794-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="94794-113">port</span><span class="sxs-lookup"><span data-stu-id="94794-113">Port</span></span>  
 <span data-ttu-id="94794-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="94794-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="94794-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="94794-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94794-116">Port síťového rozhraní, v němž je tato vazba procesy peer kanál zprávy.</span><span class="sxs-lookup"><span data-stu-id="94794-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="94794-117">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="94794-117">Security</span></span>  
 <span data-ttu-id="94794-118">Datový typ: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="94794-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="94794-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="94794-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="94794-120">Nastavení zabezpečení rovnocenného přenosu.</span><span class="sxs-lookup"><span data-stu-id="94794-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="94794-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="94794-121">Requirements</span></span>  
  
|<span data-ttu-id="94794-122">MOF</span><span class="sxs-lookup"><span data-stu-id="94794-122">MOF</span></span>|<span data-ttu-id="94794-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="94794-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="94794-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="94794-124">Namespace</span></span>|<span data-ttu-id="94794-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="94794-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="94794-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="94794-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

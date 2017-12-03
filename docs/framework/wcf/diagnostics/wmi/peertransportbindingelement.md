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
ms.openlocfilehash: 193000acf2f3c8a0eddb2552559ee40a0f5fced9
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="72e71-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="72e71-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="72e71-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="72e71-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72e71-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="72e71-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="72e71-105">Metody</span><span class="sxs-lookup"><span data-stu-id="72e71-105">Methods</span></span>  
 <span data-ttu-id="72e71-106">Třída PeerTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="72e71-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="72e71-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="72e71-107">Properties</span></span>  
 <span data-ttu-id="72e71-108">Třída PeerTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="72e71-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="72e71-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="72e71-109">ListenIPAddress</span></span>  
 <span data-ttu-id="72e71-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="72e71-110">Data type: string</span></span>  
  
 <span data-ttu-id="72e71-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="72e71-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72e71-112">IP adresa, na kterém naslouchá uzlu sdílené zprávy.</span><span class="sxs-lookup"><span data-stu-id="72e71-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="72e71-113">port</span><span class="sxs-lookup"><span data-stu-id="72e71-113">Port</span></span>  
 <span data-ttu-id="72e71-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="72e71-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="72e71-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="72e71-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72e71-116">Port síťového rozhraní, v němž je tato vazba procesy peer kanál zprávy.</span><span class="sxs-lookup"><span data-stu-id="72e71-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="72e71-117">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="72e71-117">Security</span></span>  
 <span data-ttu-id="72e71-118">Datový typ: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="72e71-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="72e71-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="72e71-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="72e71-120">Nastavení zabezpečení rovnocenného přenosu.</span><span class="sxs-lookup"><span data-stu-id="72e71-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72e71-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="72e71-121">Requirements</span></span>  
  
|<span data-ttu-id="72e71-122">MOF</span><span class="sxs-lookup"><span data-stu-id="72e71-122">MOF</span></span>|<span data-ttu-id="72e71-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="72e71-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="72e71-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="72e71-124">Namespace</span></span>|<span data-ttu-id="72e71-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="72e71-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="72e71-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="72e71-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

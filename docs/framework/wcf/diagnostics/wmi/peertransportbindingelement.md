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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 48364c2bcfa50476ac5f9f00f87c17f97dc14017
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="cd235-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="cd235-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="cd235-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="cd235-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd235-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd235-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="cd235-105">Metody</span><span class="sxs-lookup"><span data-stu-id="cd235-105">Methods</span></span>  
 <span data-ttu-id="cd235-106">Třída PeerTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="cd235-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cd235-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cd235-107">Properties</span></span>  
 <span data-ttu-id="cd235-108">Třída PeerTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="cd235-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="cd235-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="cd235-109">ListenIPAddress</span></span>  
 <span data-ttu-id="cd235-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="cd235-110">Data type: string</span></span>  
  
 <span data-ttu-id="cd235-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cd235-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd235-112">IP adresa, na kterém naslouchá uzlu sdílené zprávy.</span><span class="sxs-lookup"><span data-stu-id="cd235-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="cd235-113">port</span><span class="sxs-lookup"><span data-stu-id="cd235-113">Port</span></span>  
 <span data-ttu-id="cd235-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="cd235-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="cd235-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cd235-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd235-116">Port síťového rozhraní, v němž je tato vazba procesy peer kanál zprávy.</span><span class="sxs-lookup"><span data-stu-id="cd235-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="cd235-117">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="cd235-117">Security</span></span>  
 <span data-ttu-id="cd235-118">Datový typ: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="cd235-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="cd235-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cd235-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cd235-120">Nastavení zabezpečení rovnocenného přenosu.</span><span class="sxs-lookup"><span data-stu-id="cd235-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd235-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cd235-121">Requirements</span></span>  
  
|<span data-ttu-id="cd235-122">MOF</span><span class="sxs-lookup"><span data-stu-id="cd235-122">MOF</span></span>|<span data-ttu-id="cd235-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cd235-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cd235-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="cd235-124">Namespace</span></span>|<span data-ttu-id="cd235-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cd235-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cd235-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd235-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

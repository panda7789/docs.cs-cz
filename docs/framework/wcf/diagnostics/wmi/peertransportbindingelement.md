---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 68e6a25e4e3f47c556363e2fd5aa8d3bb9946449
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485642"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="99866-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="99866-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="99866-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="99866-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99866-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99866-104">Syntax</span></span>  
  
```  
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="99866-105">Metody</span><span class="sxs-lookup"><span data-stu-id="99866-105">Methods</span></span>  
 <span data-ttu-id="99866-106">Třída PeerTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="99866-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="99866-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="99866-107">Properties</span></span>  
 <span data-ttu-id="99866-108">Třída PeerTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="99866-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="99866-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="99866-109">ListenIPAddress</span></span>  
 <span data-ttu-id="99866-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="99866-110">Data type: string</span></span>  
  
 <span data-ttu-id="99866-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="99866-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99866-112">IP adresa, na kterém naslouchá uzlu sdílené zprávy.</span><span class="sxs-lookup"><span data-stu-id="99866-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="99866-113">port</span><span class="sxs-lookup"><span data-stu-id="99866-113">Port</span></span>  
 <span data-ttu-id="99866-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="99866-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="99866-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="99866-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99866-116">Port síťového rozhraní, v němž je tato vazba procesy peer kanál zprávy.</span><span class="sxs-lookup"><span data-stu-id="99866-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="99866-117">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="99866-117">Security</span></span>  
 <span data-ttu-id="99866-118">Datový typ: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="99866-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="99866-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="99866-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="99866-120">Nastavení zabezpečení rovnocenného přenosu.</span><span class="sxs-lookup"><span data-stu-id="99866-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99866-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="99866-121">Requirements</span></span>  
  
|<span data-ttu-id="99866-122">MOF</span><span class="sxs-lookup"><span data-stu-id="99866-122">MOF</span></span>|<span data-ttu-id="99866-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="99866-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="99866-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="99866-124">Namespace</span></span>|<span data-ttu-id="99866-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="99866-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="99866-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="99866-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 437ccc0446e3cc05596ab12b7908177b7f78e431
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54670651"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="3b689-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="3b689-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="3b689-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="3b689-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b689-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b689-104">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="3b689-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3b689-105">Methods</span></span>  
 <span data-ttu-id="3b689-106">Třídě PeerTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="3b689-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="3b689-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="3b689-107">Properties</span></span>  
 <span data-ttu-id="3b689-108">Třídě PeerTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="3b689-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="3b689-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="3b689-109">ListenIPAddress</span></span>  
 <span data-ttu-id="3b689-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="3b689-110">Data type: string</span></span>  
  
 <span data-ttu-id="3b689-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="3b689-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b689-112">IP adresa, na kterém naslouchá partnerský uzel pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="3b689-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="3b689-113">Port</span><span class="sxs-lookup"><span data-stu-id="3b689-113">Port</span></span>  
 <span data-ttu-id="3b689-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="3b689-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="3b689-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="3b689-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b689-116">Port síťového rozhraní, na které bude tato vazba procesy navázání partnerského vztahu mezi kanálu zpráv.</span><span class="sxs-lookup"><span data-stu-id="3b689-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="3b689-117">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3b689-117">Security</span></span>  
 <span data-ttu-id="3b689-118">Datový typ: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="3b689-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="3b689-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="3b689-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="3b689-120">Nastavení zabezpečení rovnocenného přenosu.</span><span class="sxs-lookup"><span data-stu-id="3b689-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b689-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="3b689-121">Requirements</span></span>  
  
|<span data-ttu-id="3b689-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="3b689-122">MOF</span></span>|<span data-ttu-id="3b689-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="3b689-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="3b689-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="3b689-124">Namespace</span></span>|<span data-ttu-id="3b689-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="3b689-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3b689-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b689-126">See also</span></span>
- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: 58bf07b0429ca2435b5aae3683ef69951a10003e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185180"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="ccd2b-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="ccd2b-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="ccd2b-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="ccd2b-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ccd2b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ccd2b-104">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ccd2b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ccd2b-105">Methods</span></span>  
 <span data-ttu-id="ccd2b-106">Třídě PeerTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="ccd2b-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="ccd2b-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="ccd2b-107">Properties</span></span>  
 <span data-ttu-id="ccd2b-108">Třídě PeerTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="ccd2b-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="ccd2b-109">Třída listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="ccd2b-109">ListenIPAddress</span></span>  
 <span data-ttu-id="ccd2b-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="ccd2b-110">Data type: string</span></span>  
  
 <span data-ttu-id="ccd2b-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ccd2b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ccd2b-112">IP adresa, na kterém naslouchá partnerský uzel pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="ccd2b-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="ccd2b-113">Port</span><span class="sxs-lookup"><span data-stu-id="ccd2b-113">Port</span></span>  
 <span data-ttu-id="ccd2b-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="ccd2b-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="ccd2b-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ccd2b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ccd2b-116">Port síťového rozhraní, na které bude tato vazba procesy navázání partnerského vztahu mezi kanálu zpráv.</span><span class="sxs-lookup"><span data-stu-id="ccd2b-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="ccd2b-117">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="ccd2b-117">Security</span></span>  
 <span data-ttu-id="ccd2b-118">Datový typ: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="ccd2b-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="ccd2b-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="ccd2b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="ccd2b-120">Nastavení zabezpečení rovnocenného přenosu.</span><span class="sxs-lookup"><span data-stu-id="ccd2b-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ccd2b-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ccd2b-121">Requirements</span></span>  
  
|<span data-ttu-id="ccd2b-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="ccd2b-122">MOF</span></span>|<span data-ttu-id="ccd2b-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="ccd2b-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="ccd2b-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="ccd2b-124">Namespace</span></span>|<span data-ttu-id="ccd2b-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="ccd2b-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ccd2b-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="ccd2b-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

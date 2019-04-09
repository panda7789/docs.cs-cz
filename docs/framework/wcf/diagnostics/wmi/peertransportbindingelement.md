---
title: PeerTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 40bf6be2-8087-4cb3-a66c-408d53eb9269
ms.openlocfilehash: ba9031dad96f12c7c48b03f1da4af1b3adc6dd4f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59194059"
---
# <a name="peertransportbindingelement"></a><span data-ttu-id="37992-102">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="37992-102">PeerTransportBindingElement</span></span>
<span data-ttu-id="37992-103">PeerTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="37992-103">PeerTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="37992-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="37992-104">Syntax</span></span>  
  
```csharp
class PeerTransportBindingElement : TransportBindingElement  
{  
  string ListenIPAddress;  
  sint32 Port;  
  PeerSecuritySettings Security;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="37992-105">Metody</span><span class="sxs-lookup"><span data-stu-id="37992-105">Methods</span></span>  
 <span data-ttu-id="37992-106">Třídě PeerTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="37992-106">The PeerTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="37992-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="37992-107">Properties</span></span>  
 <span data-ttu-id="37992-108">Třídě PeerTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="37992-108">The PeerTransportBindingElement class has the following properties:</span></span>  
  
### <a name="listenipaddress"></a><span data-ttu-id="37992-109">ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="37992-109">ListenIPAddress</span></span>  
 <span data-ttu-id="37992-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="37992-110">Data type: string</span></span>  
  
 <span data-ttu-id="37992-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="37992-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37992-112">IP adresa, na kterém naslouchá partnerský uzel pro zprávy.</span><span class="sxs-lookup"><span data-stu-id="37992-112">The IP address on which the peer node listens for messages.</span></span>  
  
### <a name="port"></a><span data-ttu-id="37992-113">Port</span><span class="sxs-lookup"><span data-stu-id="37992-113">Port</span></span>  
 <span data-ttu-id="37992-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="37992-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="37992-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="37992-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37992-116">Port síťového rozhraní, na které bude tato vazba procesy navázání partnerského vztahu mezi kanálu zpráv.</span><span class="sxs-lookup"><span data-stu-id="37992-116">The network interface port on which this binding processes peer channel messages.</span></span>  
  
### <a name="security"></a><span data-ttu-id="37992-117">Zabezpečení</span><span class="sxs-lookup"><span data-stu-id="37992-117">Security</span></span>  
 <span data-ttu-id="37992-118">Datový typ: PeerSecuritySettings</span><span class="sxs-lookup"><span data-stu-id="37992-118">Data type: PeerSecuritySettings</span></span>  
  
 <span data-ttu-id="37992-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="37992-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="37992-120">Nastavení zabezpečení rovnocenného přenosu.</span><span class="sxs-lookup"><span data-stu-id="37992-120">Peer transport security settings.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="37992-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="37992-121">Requirements</span></span>  
  
|<span data-ttu-id="37992-122">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="37992-122">MOF</span></span>|<span data-ttu-id="37992-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="37992-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="37992-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="37992-124">Namespace</span></span>|<span data-ttu-id="37992-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="37992-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="37992-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="37992-126">See also</span></span>

- <xref:System.ServiceModel.Channels.PeerTransportBindingElement>

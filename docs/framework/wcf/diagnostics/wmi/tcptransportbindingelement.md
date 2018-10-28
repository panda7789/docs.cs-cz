---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 04326484bbf1f07c66ad8fb401642880f9ba8c6e
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50193926"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="df997-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="df997-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="df997-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="df997-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df997-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df997-104">Syntax</span></span>  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="df997-105">Metody</span><span class="sxs-lookup"><span data-stu-id="df997-105">Methods</span></span>  
 <span data-ttu-id="df997-106">Třída TcpTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="df997-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="df997-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="df997-107">Properties</span></span>  
 <span data-ttu-id="df997-108">Třída TcpTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="df997-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="df997-109">connectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="df997-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="df997-110">Datový typ: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="df997-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="df997-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="df997-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="df997-112">Nastavení fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="df997-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="df997-113">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="df997-113">ListenBacklog</span></span>  
 <span data-ttu-id="df997-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="df997-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="df997-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="df997-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="df997-116">Maximální počet připojení zařazených do fronty požadavků, které mohou být nevyřízeny.</span><span class="sxs-lookup"><span data-stu-id="df997-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="df997-117">portSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="df997-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="df997-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="df997-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="df997-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="df997-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="df997-120">Logická hodnota určující, zda je pro toto připojení povoleno sdílení portu TCP.</span><span class="sxs-lookup"><span data-stu-id="df997-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="df997-121">teredoEnabled</span><span class="sxs-lookup"><span data-stu-id="df997-121">TeredoEnabled</span></span>  
 <span data-ttu-id="df997-122">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="df997-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="df997-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="df997-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="df997-124">Logická hodnota určující, zda je povolena Teredo (technologie pro oslovování klientů, kteří jsou za firewally).</span><span class="sxs-lookup"><span data-stu-id="df997-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df997-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df997-125">Requirements</span></span>  
  
|<span data-ttu-id="df997-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="df997-126">MOF</span></span>|<span data-ttu-id="df997-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="df997-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="df997-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="df997-128">Namespace</span></span>|<span data-ttu-id="df997-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="df997-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df997-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="df997-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

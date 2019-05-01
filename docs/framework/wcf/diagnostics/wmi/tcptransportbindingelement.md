---
title: TcpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
ms.openlocfilehash: 6d2717bc2d1d14e369af2b9c5a8c0affb67501d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61956543"
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="4fc8a-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="4fc8a-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="4fc8a-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="4fc8a-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fc8a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fc8a-104">Syntax</span></span>  
  
```csharp
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="4fc8a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4fc8a-105">Methods</span></span>  
 <span data-ttu-id="4fc8a-106">Třída TcpTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="4fc8a-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4fc8a-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4fc8a-107">Properties</span></span>  
 <span data-ttu-id="4fc8a-108">Třída TcpTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="4fc8a-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="4fc8a-109">ConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="4fc8a-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="4fc8a-110">Datový typ: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="4fc8a-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="4fc8a-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4fc8a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4fc8a-112">Nastavení fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="4fc8a-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="4fc8a-113">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="4fc8a-113">ListenBacklog</span></span>  
 <span data-ttu-id="4fc8a-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4fc8a-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="4fc8a-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4fc8a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4fc8a-116">Maximální počet připojení zařazených do fronty požadavků, které mohou být nevyřízeny.</span><span class="sxs-lookup"><span data-stu-id="4fc8a-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="4fc8a-117">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="4fc8a-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="4fc8a-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="4fc8a-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="4fc8a-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4fc8a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4fc8a-120">Logická hodnota určující, zda je pro toto připojení povoleno sdílení portu TCP.</span><span class="sxs-lookup"><span data-stu-id="4fc8a-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="4fc8a-121">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="4fc8a-121">TeredoEnabled</span></span>  
 <span data-ttu-id="4fc8a-122">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="4fc8a-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="4fc8a-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4fc8a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4fc8a-124">Logická hodnota určující, zda je povolena Teredo (technologie pro oslovování klientů, kteří jsou za firewally).</span><span class="sxs-lookup"><span data-stu-id="4fc8a-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4fc8a-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4fc8a-125">Requirements</span></span>  
  
|<span data-ttu-id="4fc8a-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="4fc8a-126">MOF</span></span>|<span data-ttu-id="4fc8a-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4fc8a-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4fc8a-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="4fc8a-128">Namespace</span></span>|<span data-ttu-id="4fc8a-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4fc8a-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4fc8a-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4fc8a-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

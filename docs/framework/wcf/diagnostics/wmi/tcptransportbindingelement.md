---
title: TcpTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33bbc1e5-44e4-4ee3-b7b5-801dc78956e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6e230cbccee211fbda219000fbbd2cda5275776b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="tcptransportbindingelement"></a><span data-ttu-id="d5123-102">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="d5123-102">TcpTransportBindingElement</span></span>
<span data-ttu-id="d5123-103">TcpTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="d5123-103">TcpTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5123-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5123-104">Syntax</span></span>  
  
```  
class TcpTransportBindingElement : ConnectionOrientedTransportBindingElement  
{  
  TcpConnectionPoolSettings ConnectionPoolSettings;  
  sint32 ListenBacklog;  
  boolean PortSharingEnabled;  
  boolean TeredoEnabled;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d5123-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d5123-105">Methods</span></span>  
 <span data-ttu-id="d5123-106">Třída TcpTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="d5123-106">The TcpTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d5123-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d5123-107">Properties</span></span>  
 <span data-ttu-id="d5123-108">Třída TcpTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d5123-108">The TcpTransportBindingElement class has the following properties:</span></span>  
  
### <a name="connectionpoolsettings"></a><span data-ttu-id="d5123-109">ConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="d5123-109">ConnectionPoolSettings</span></span>  
 <span data-ttu-id="d5123-110">Datový typ: TcpConnectionPoolSettings</span><span class="sxs-lookup"><span data-stu-id="d5123-110">Data type: TcpConnectionPoolSettings</span></span>  
  
 <span data-ttu-id="d5123-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d5123-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d5123-112">Nastavení fondu připojení.</span><span class="sxs-lookup"><span data-stu-id="d5123-112">The connection pool settings.</span></span>  
  
### <a name="listenbacklog"></a><span data-ttu-id="d5123-113">listenBacklog</span><span class="sxs-lookup"><span data-stu-id="d5123-113">ListenBacklog</span></span>  
 <span data-ttu-id="d5123-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d5123-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="d5123-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d5123-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d5123-116">Maximální počet požadavků ve frontě připojení, které může být dokončena.</span><span class="sxs-lookup"><span data-stu-id="d5123-116">The maximum number of queued connection requests that can be pending.</span></span>  
  
### <a name="portsharingenabled"></a><span data-ttu-id="d5123-117">PortSharingEnabled</span><span class="sxs-lookup"><span data-stu-id="d5123-117">PortSharingEnabled</span></span>  
 <span data-ttu-id="d5123-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="d5123-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="d5123-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d5123-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d5123-120">Logická hodnota, která určuje, zda je povoleno sdílení portů TCP pro toto připojení.</span><span class="sxs-lookup"><span data-stu-id="d5123-120">A boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span>  
  
### <a name="teredoenabled"></a><span data-ttu-id="d5123-121">TeredoEnabled</span><span class="sxs-lookup"><span data-stu-id="d5123-121">TeredoEnabled</span></span>  
 <span data-ttu-id="d5123-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="d5123-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="d5123-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d5123-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d5123-124">Logická hodnota, která určuje, zda je povoleno Teredo (technologie pro adresování klienty, kteří jsou za bránami firewall).</span><span class="sxs-lookup"><span data-stu-id="d5123-124">A boolean value that specifies whether Teredo (a technology for addressing clients that are behind firewalls) is enabled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5123-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5123-125">Requirements</span></span>  
  
|<span data-ttu-id="d5123-126">MOF</span><span class="sxs-lookup"><span data-stu-id="d5123-126">MOF</span></span>|<span data-ttu-id="d5123-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d5123-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d5123-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="d5123-128">Namespace</span></span>|<span data-ttu-id="d5123-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d5123-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d5123-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5123-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>

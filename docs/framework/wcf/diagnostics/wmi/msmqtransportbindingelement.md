---
title: MsmqTransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c4cfa3d58127fa560f39ce0dcfe51b97ded6223a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="2bbb4-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="2bbb4-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="2bbb4-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="2bbb4-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2bbb4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2bbb4-104">Syntax</span></span>  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="2bbb4-105">Metody</span><span class="sxs-lookup"><span data-stu-id="2bbb4-105">Methods</span></span>  
 <span data-ttu-id="2bbb4-106">Třída prvkem MsmqTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="2bbb4-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="2bbb4-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="2bbb4-107">Properties</span></span>  
 <span data-ttu-id="2bbb4-108">Třída prvkem MsmqTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="2bbb4-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="2bbb4-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="2bbb4-109">MaxPoolSize</span></span>  
 <span data-ttu-id="2bbb4-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="2bbb4-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="2bbb4-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2bbb4-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2bbb4-112">Maximální velikost fondu, který obsahuje objekty interní MSMQ zprávy.</span><span class="sxs-lookup"><span data-stu-id="2bbb4-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="2bbb4-113">Třída QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="2bbb4-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="2bbb4-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="2bbb4-114">Data type: string</span></span>  
  
 <span data-ttu-id="2bbb4-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2bbb4-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2bbb4-116">Hodnota výčtu, která určuje přenosu kanál komunikace ve frontě, která používá tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="2bbb4-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="2bbb4-117">Třída UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="2bbb4-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="2bbb4-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="2bbb4-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="2bbb4-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="2bbb4-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="2bbb4-120">Vrátí logickou hodnotu, která určuje, zda mají být převedeny fronty adresy pomocí služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2bbb4-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2bbb4-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="2bbb4-121">Requirements</span></span>  
  
|<span data-ttu-id="2bbb4-122">MOF</span><span class="sxs-lookup"><span data-stu-id="2bbb4-122">MOF</span></span>|<span data-ttu-id="2bbb4-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="2bbb4-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="2bbb4-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="2bbb4-124">Namespace</span></span>|<span data-ttu-id="2bbb4-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="2bbb4-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2bbb4-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="2bbb4-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

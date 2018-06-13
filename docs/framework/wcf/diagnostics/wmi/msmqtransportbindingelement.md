---
title: MsmqTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 1c89f073-9ed3-4025-a8c5-13535a0f526b
ms.openlocfilehash: 643ab0f30c771f79df8ef7dd885013d5186fba59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485905"
---
# <a name="msmqtransportbindingelement"></a><span data-ttu-id="e64a8-102">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e64a8-102">MsmqTransportBindingElement</span></span>
<span data-ttu-id="e64a8-103">MsmqTransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="e64a8-103">MsmqTransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e64a8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e64a8-104">Syntax</span></span>  
  
```  
class MsmqTransportBindingElement : MsmqBindingElementBase  
{  
  sint32 MaxPoolSize;  
  string QueueTransferProtocol;  
  boolean UseActiveDirectory;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e64a8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e64a8-105">Methods</span></span>  
 <span data-ttu-id="e64a8-106">Třída prvkem MsmqTransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="e64a8-106">The MsmqTransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e64a8-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e64a8-107">Properties</span></span>  
 <span data-ttu-id="e64a8-108">Třída prvkem MsmqTransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="e64a8-108">The MsmqTransportBindingElement class has the following properties:</span></span>  
  
### <a name="maxpoolsize"></a><span data-ttu-id="e64a8-109">MaxPoolSize</span><span class="sxs-lookup"><span data-stu-id="e64a8-109">MaxPoolSize</span></span>  
 <span data-ttu-id="e64a8-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e64a8-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="e64a8-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e64a8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e64a8-112">Maximální velikost fondu, který obsahuje objekty interní MSMQ zprávy.</span><span class="sxs-lookup"><span data-stu-id="e64a8-112">The maximum size of the pool that contains internal MSMQ message objects.</span></span>  
  
### <a name="queuetransferprotocol"></a><span data-ttu-id="e64a8-113">Třída QueueTransferProtocol</span><span class="sxs-lookup"><span data-stu-id="e64a8-113">QueueTransferProtocol</span></span>  
 <span data-ttu-id="e64a8-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="e64a8-114">Data type: string</span></span>  
  
 <span data-ttu-id="e64a8-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e64a8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e64a8-116">Hodnota výčtu, která určuje přenosu kanál komunikace ve frontě, která používá tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="e64a8-116">An enumeration value that indicates the queued communication channel transport that this binding uses.</span></span>  
  
### <a name="useactivedirectory"></a><span data-ttu-id="e64a8-117">Třída UseActiveDirectory</span><span class="sxs-lookup"><span data-stu-id="e64a8-117">UseActiveDirectory</span></span>  
 <span data-ttu-id="e64a8-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="e64a8-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="e64a8-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e64a8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e64a8-120">Vrátí logickou hodnotu, která určuje, zda mají být převedeny fronty adresy pomocí služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="e64a8-120">Returns a Boolean value that indicates whether queue addresses should be converted using Active Directory.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e64a8-121">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e64a8-121">Requirements</span></span>  
  
|<span data-ttu-id="e64a8-122">MOF</span><span class="sxs-lookup"><span data-stu-id="e64a8-122">MOF</span></span>|<span data-ttu-id="e64a8-123">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e64a8-123">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e64a8-124">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="e64a8-124">Namespace</span></span>|<span data-ttu-id="e64a8-125">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e64a8-125">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e64a8-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="e64a8-126">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>

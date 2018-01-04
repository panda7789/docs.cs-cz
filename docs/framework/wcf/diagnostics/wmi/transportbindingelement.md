---
title: TransportBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54ecfbee-53c0-410c-a7fa-a98f2e40c545
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 062b45eb5d627903142ca1a5fd4db6df0855384b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="transportbindingelement"></a><span data-ttu-id="f08b9-102">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f08b9-102">TransportBindingElement</span></span>
<span data-ttu-id="f08b9-103">TransportBindingElement</span><span class="sxs-lookup"><span data-stu-id="f08b9-103">TransportBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f08b9-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f08b9-104">Syntax</span></span>  
  
```  
class TransportBindingElement : BindingElement  
{  
  boolean ManualAddressing;  
  sint64 MaxBufferPoolSize;  
  sint64 MaxReceivedMessageSize;  
  string Scheme;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f08b9-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f08b9-105">Methods</span></span>  
 <span data-ttu-id="f08b9-106">Třída TransportBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="f08b9-106">The TransportBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f08b9-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f08b9-107">Properties</span></span>  
 <span data-ttu-id="f08b9-108">Třída TransportBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="f08b9-108">The TransportBindingElement class has the following properties:</span></span>  
  
### <a name="manualaddressing"></a><span data-ttu-id="f08b9-109">manualAddressing</span><span class="sxs-lookup"><span data-stu-id="f08b9-109">ManualAddressing</span></span>  
 <span data-ttu-id="f08b9-110">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="f08b9-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="f08b9-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f08b9-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f08b9-112">Logická hodnota, která určuje, jestli uživatel chce převzít kontrolu nad adresování zprávy.</span><span class="sxs-lookup"><span data-stu-id="f08b9-112">A boolean value that specifies whether the user wants to take control of message addressing.</span></span>  
  
### <a name="maxbufferpoolsize"></a><span data-ttu-id="f08b9-113">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="f08b9-113">MaxBufferPoolSize</span></span>  
 <span data-ttu-id="f08b9-114">Datový typ: sint64</span><span class="sxs-lookup"><span data-stu-id="f08b9-114">Data type: sint64</span></span>  
  
 <span data-ttu-id="f08b9-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f08b9-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f08b9-116">Velikost fondu maximální vyrovnávací paměti pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="f08b9-116">The maximum buffer pool size for the binding.</span></span>  
  
### <a name="maxreceivedmessagesize"></a><span data-ttu-id="f08b9-117">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="f08b9-117">MaxReceivedMessageSize</span></span>  
 <span data-ttu-id="f08b9-118">Datový typ: sint64</span><span class="sxs-lookup"><span data-stu-id="f08b9-118">Data type: sint64</span></span>  
  
 <span data-ttu-id="f08b9-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f08b9-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f08b9-120">Maximální velikost zprávy, která je zpracovávané touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="f08b9-120">The maximum size for a message that is processed by this binding.</span></span>  
  
### <a name="scheme"></a><span data-ttu-id="f08b9-121">Schéma</span><span class="sxs-lookup"><span data-stu-id="f08b9-121">Scheme</span></span>  
 <span data-ttu-id="f08b9-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="f08b9-122">Data type: string</span></span>  
  
 <span data-ttu-id="f08b9-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f08b9-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f08b9-124">Schéma identifikátoru URI pro přenos.</span><span class="sxs-lookup"><span data-stu-id="f08b9-124">The URI scheme for the transport.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f08b9-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f08b9-125">Requirements</span></span>  
  
|<span data-ttu-id="f08b9-126">MOF</span><span class="sxs-lookup"><span data-stu-id="f08b9-126">MOF</span></span>|<span data-ttu-id="f08b9-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f08b9-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f08b9-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="f08b9-128">Namespace</span></span>|<span data-ttu-id="f08b9-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f08b9-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f08b9-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="f08b9-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TransportBindingElement>

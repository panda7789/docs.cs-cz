---
title: BinaryMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: adac65808853ec75e37245c8c9fa031a533c22a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="f3d3e-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="f3d3e-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="f3d3e-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="f3d3e-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3d3e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3d3e-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="f3d3e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="f3d3e-105">Methods</span></span>  
 <span data-ttu-id="f3d3e-106">Třída BinaryMessageEncodingBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="f3d3e-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="f3d3e-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="f3d3e-107">Properties</span></span>  
 <span data-ttu-id="f3d3e-108">Třída BinaryMessageEncodingBindingElement má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="f3d3e-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="f3d3e-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="f3d3e-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="f3d3e-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="f3d3e-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="f3d3e-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f3d3e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f3d3e-112">Celé číslo, které definuje počet zpráv lze číst souběžně bez přidělení nového čtečky.</span><span class="sxs-lookup"><span data-stu-id="f3d3e-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="f3d3e-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="f3d3e-113">MaxSessionSize</span></span>  
 <span data-ttu-id="f3d3e-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="f3d3e-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="f3d3e-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f3d3e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f3d3e-116">Hodnota, která určuje velikost v bajtech vyrovnávací paměti používané pro kódování.</span><span class="sxs-lookup"><span data-stu-id="f3d3e-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="f3d3e-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="f3d3e-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="f3d3e-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="f3d3e-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="f3d3e-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f3d3e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f3d3e-120">Celé číslo, které definuje počet zpráv lze najednou odeslat bez přiděluje nový zapisovače.</span><span class="sxs-lookup"><span data-stu-id="f3d3e-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="f3d3e-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="f3d3e-121">ReaderQuotas</span></span>  
 <span data-ttu-id="f3d3e-122">Datový typ: XmlDictionaryReaderQuotas, který</span><span class="sxs-lookup"><span data-stu-id="f3d3e-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="f3d3e-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="f3d3e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="f3d3e-124">Kvóty čtečky.</span><span class="sxs-lookup"><span data-stu-id="f3d3e-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f3d3e-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="f3d3e-125">Requirements</span></span>  
  
|<span data-ttu-id="f3d3e-126">MOF</span><span class="sxs-lookup"><span data-stu-id="f3d3e-126">MOF</span></span>|<span data-ttu-id="f3d3e-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="f3d3e-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="f3d3e-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="f3d3e-128">Namespace</span></span>|<span data-ttu-id="f3d3e-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="f3d3e-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f3d3e-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="f3d3e-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

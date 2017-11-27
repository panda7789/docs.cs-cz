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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 09d43ed76ef70f4478aa1029c254a7b1686a8d08
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="e4eb5-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="e4eb5-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="e4eb5-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="e4eb5-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4eb5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e4eb5-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e4eb5-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e4eb5-105">Methods</span></span>  
 <span data-ttu-id="e4eb5-106">Třída BinaryMessageEncodingBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e4eb5-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e4eb5-107">Properties</span></span>  
 <span data-ttu-id="e4eb5-108">Třída BinaryMessageEncodingBindingElement má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="e4eb5-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="e4eb5-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="e4eb5-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e4eb5-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="e4eb5-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e4eb5-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e4eb5-112">Celé číslo, které definuje počet zpráv lze číst souběžně bez přidělení nového čtečky.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="e4eb5-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="e4eb5-113">MaxSessionSize</span></span>  
 <span data-ttu-id="e4eb5-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e4eb5-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e4eb5-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e4eb5-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e4eb5-116">Hodnota, která určuje velikost v bajtech vyrovnávací paměti používané pro kódování.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="e4eb5-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="e4eb5-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="e4eb5-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e4eb5-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="e4eb5-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e4eb5-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e4eb5-120">Celé číslo, které definuje počet zpráv lze najednou odeslat bez přiděluje nový zapisovače.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="e4eb5-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="e4eb5-121">ReaderQuotas</span></span>  
 <span data-ttu-id="e4eb5-122">Datový typ: XmlDictionaryReaderQuotas, který</span><span class="sxs-lookup"><span data-stu-id="e4eb5-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="e4eb5-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e4eb5-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e4eb5-124">Kvóty čtečky.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e4eb5-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4eb5-125">Requirements</span></span>  
  
|<span data-ttu-id="e4eb5-126">MOF</span><span class="sxs-lookup"><span data-stu-id="e4eb5-126">MOF</span></span>|<span data-ttu-id="e4eb5-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e4eb5-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e4eb5-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="e4eb5-128">Namespace</span></span>|<span data-ttu-id="e4eb5-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e4eb5-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e4eb5-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="e4eb5-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

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
ms.openlocfilehash: 45f80b9ac7ca052ea3a8d7d89b35413b167eacfa
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="df25b-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="df25b-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="df25b-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="df25b-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df25b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="df25b-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="df25b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="df25b-105">Methods</span></span>  
 <span data-ttu-id="df25b-106">Třída BinaryMessageEncodingBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="df25b-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="df25b-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="df25b-107">Properties</span></span>  
 <span data-ttu-id="df25b-108">Třída BinaryMessageEncodingBindingElement má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="df25b-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="df25b-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="df25b-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="df25b-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="df25b-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="df25b-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="df25b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="df25b-112">Celé číslo, které definuje počet zpráv lze číst souběžně bez přidělení nového čtečky.</span><span class="sxs-lookup"><span data-stu-id="df25b-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="df25b-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="df25b-113">MaxSessionSize</span></span>  
 <span data-ttu-id="df25b-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="df25b-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="df25b-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="df25b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="df25b-116">Hodnota, která určuje velikost v bajtech vyrovnávací paměti používané pro kódování.</span><span class="sxs-lookup"><span data-stu-id="df25b-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="df25b-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="df25b-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="df25b-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="df25b-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="df25b-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="df25b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="df25b-120">Celé číslo, které definuje počet zpráv lze najednou odeslat bez přiděluje nový zapisovače.</span><span class="sxs-lookup"><span data-stu-id="df25b-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="df25b-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="df25b-121">ReaderQuotas</span></span>  
 <span data-ttu-id="df25b-122">Datový typ: XmlDictionaryReaderQuotas, který</span><span class="sxs-lookup"><span data-stu-id="df25b-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="df25b-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="df25b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="df25b-124">Kvóty čtečky.</span><span class="sxs-lookup"><span data-stu-id="df25b-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="df25b-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="df25b-125">Requirements</span></span>  
  
|<span data-ttu-id="df25b-126">MOF</span><span class="sxs-lookup"><span data-stu-id="df25b-126">MOF</span></span>|<span data-ttu-id="df25b-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="df25b-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="df25b-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="df25b-128">Namespace</span></span>|<span data-ttu-id="df25b-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="df25b-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df25b-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="df25b-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

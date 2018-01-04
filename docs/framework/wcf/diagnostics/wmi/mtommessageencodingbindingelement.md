---
title: MtomMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3cc36d7daed1a2cfaf050cbfe9661951117ff66d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="51ea8-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="51ea8-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="51ea8-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="51ea8-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51ea8-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="51ea8-104">Syntax</span></span>  
  
```  
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="51ea8-105">Metody</span><span class="sxs-lookup"><span data-stu-id="51ea8-105">Methods</span></span>  
 <span data-ttu-id="51ea8-106">Třída MtomMessageEncodingBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="51ea8-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="51ea8-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="51ea8-107">Properties</span></span>  
 <span data-ttu-id="51ea8-108">Třída MtomMessageEncodingBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="51ea8-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="51ea8-109">Kódování</span><span class="sxs-lookup"><span data-stu-id="51ea8-109">Encoding</span></span>  
 <span data-ttu-id="51ea8-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="51ea8-110">Data type: string</span></span>  
  
 <span data-ttu-id="51ea8-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="51ea8-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51ea8-112">Kódování znakové sady, který se má použít pro vysílání zpráv v vazby.</span><span class="sxs-lookup"><span data-stu-id="51ea8-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="51ea8-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="51ea8-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="51ea8-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="51ea8-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="51ea8-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="51ea8-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51ea8-116">Celé číslo, které definuje počet zpráv lze číst souběžně bez přidělení nového čtečky.</span><span class="sxs-lookup"><span data-stu-id="51ea8-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="51ea8-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="51ea8-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="51ea8-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="51ea8-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="51ea8-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="51ea8-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51ea8-120">Celé číslo, které definuje počet zpráv lze najednou odeslat bez přiděluje nový zapisovače.</span><span class="sxs-lookup"><span data-stu-id="51ea8-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="51ea8-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="51ea8-121">ReaderQuotas</span></span>  
 <span data-ttu-id="51ea8-122">Datový typ: XmlDictionaryReaderQuotas, který</span><span class="sxs-lookup"><span data-stu-id="51ea8-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="51ea8-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="51ea8-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="51ea8-124">Kvóty čtečky.</span><span class="sxs-lookup"><span data-stu-id="51ea8-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51ea8-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="51ea8-125">Requirements</span></span>  
  
|<span data-ttu-id="51ea8-126">MOF</span><span class="sxs-lookup"><span data-stu-id="51ea8-126">MOF</span></span>|<span data-ttu-id="51ea8-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="51ea8-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="51ea8-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="51ea8-128">Namespace</span></span>|<span data-ttu-id="51ea8-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="51ea8-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="51ea8-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="51ea8-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

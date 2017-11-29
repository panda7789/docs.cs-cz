---
title: TextMessageEncodingBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6e1eccbaae35a16fe4fb133296698d347c190e94
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="57e2a-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="57e2a-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="57e2a-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="57e2a-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57e2a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57e2a-104">Syntax</span></span>  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="57e2a-105">Metody</span><span class="sxs-lookup"><span data-stu-id="57e2a-105">Methods</span></span>  
 <span data-ttu-id="57e2a-106">Třída TextMessageEncodingBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="57e2a-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="57e2a-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="57e2a-107">Properties</span></span>  
 <span data-ttu-id="57e2a-108">Třída TextMessageEncodingBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="57e2a-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="57e2a-109">Kódování</span><span class="sxs-lookup"><span data-stu-id="57e2a-109">Encoding</span></span>  
 <span data-ttu-id="57e2a-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="57e2a-110">Data type: string</span></span>  
  
 <span data-ttu-id="57e2a-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57e2a-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57e2a-112">Kódování znakové sady, který se má použít pro vysílání zpráv v vazby.</span><span class="sxs-lookup"><span data-stu-id="57e2a-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="57e2a-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="57e2a-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="57e2a-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="57e2a-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="57e2a-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57e2a-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57e2a-116">Celé číslo, které definuje počet zpráv lze číst souběžně bez přidělení nového čtečky.</span><span class="sxs-lookup"><span data-stu-id="57e2a-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="57e2a-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="57e2a-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="57e2a-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="57e2a-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="57e2a-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57e2a-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57e2a-120">Celé číslo, které definuje počet zpráv lze najednou odeslat bez přiděluje nový zapisovače.</span><span class="sxs-lookup"><span data-stu-id="57e2a-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="57e2a-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="57e2a-121">ReaderQuotas</span></span>  
 <span data-ttu-id="57e2a-122">Datový typ: XmlDictionaryReaderQuotas, který</span><span class="sxs-lookup"><span data-stu-id="57e2a-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="57e2a-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57e2a-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57e2a-124">Kvóty čtečky.</span><span class="sxs-lookup"><span data-stu-id="57e2a-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57e2a-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57e2a-125">Requirements</span></span>  
  
|<span data-ttu-id="57e2a-126">MOF</span><span class="sxs-lookup"><span data-stu-id="57e2a-126">MOF</span></span>|<span data-ttu-id="57e2a-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="57e2a-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="57e2a-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="57e2a-128">Namespace</span></span>|<span data-ttu-id="57e2a-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="57e2a-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57e2a-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="57e2a-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

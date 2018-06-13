---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: 03a33f01fe6b6f75e81749c96c31770009350b05
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486560"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="1f087-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="1f087-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="1f087-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="1f087-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f087-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1f087-104">Syntax</span></span>  
  
```  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="1f087-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1f087-105">Methods</span></span>  
 <span data-ttu-id="1f087-106">Třída BinaryMessageEncodingBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="1f087-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1f087-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1f087-107">Properties</span></span>  
 <span data-ttu-id="1f087-108">Třída BinaryMessageEncodingBindingElement má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1f087-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="1f087-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="1f087-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="1f087-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="1f087-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="1f087-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1f087-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f087-112">Celé číslo, které definuje počet zpráv lze číst souběžně bez přidělení nového čtečky.</span><span class="sxs-lookup"><span data-stu-id="1f087-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="1f087-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="1f087-113">MaxSessionSize</span></span>  
 <span data-ttu-id="1f087-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="1f087-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="1f087-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1f087-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f087-116">Hodnota, která určuje velikost v bajtech vyrovnávací paměti používané pro kódování.</span><span class="sxs-lookup"><span data-stu-id="1f087-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="1f087-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="1f087-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="1f087-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="1f087-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="1f087-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1f087-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f087-120">Celé číslo, které definuje počet zpráv lze najednou odeslat bez přiděluje nový zapisovače.</span><span class="sxs-lookup"><span data-stu-id="1f087-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="1f087-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="1f087-121">ReaderQuotas</span></span>  
 <span data-ttu-id="1f087-122">Datový typ: XmlDictionaryReaderQuotas, který</span><span class="sxs-lookup"><span data-stu-id="1f087-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="1f087-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1f087-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1f087-124">Kvóty čtečky.</span><span class="sxs-lookup"><span data-stu-id="1f087-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1f087-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1f087-125">Requirements</span></span>  
  
|<span data-ttu-id="1f087-126">MOF</span><span class="sxs-lookup"><span data-stu-id="1f087-126">MOF</span></span>|<span data-ttu-id="1f087-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1f087-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1f087-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="1f087-128">Namespace</span></span>|<span data-ttu-id="1f087-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1f087-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1f087-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="1f087-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

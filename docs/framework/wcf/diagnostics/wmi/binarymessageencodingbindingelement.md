---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: 330496d5f0f80affcb6bc44a1f66f4321a635f00
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54580587"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="8fcf7-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="8fcf7-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="8fcf7-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="8fcf7-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8fcf7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8fcf7-104">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="8fcf7-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8fcf7-105">Methods</span></span>  
 <span data-ttu-id="8fcf7-106">Třídě BinaryMessageEncodingBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="8fcf7-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8fcf7-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8fcf7-107">Properties</span></span>  
 <span data-ttu-id="8fcf7-108">Třídě BinaryMessageEncodingBindingElement má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="8fcf7-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="8fcf7-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="8fcf7-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="8fcf7-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="8fcf7-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="8fcf7-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8fcf7-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8fcf7-112">Celé číslo, které definuje počet zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="8fcf7-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="8fcf7-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="8fcf7-113">MaxSessionSize</span></span>  
 <span data-ttu-id="8fcf7-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="8fcf7-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="8fcf7-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8fcf7-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8fcf7-116">Hodnota, která určuje velikost v bajtech, použité pro kódování vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="8fcf7-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="8fcf7-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="8fcf7-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="8fcf7-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="8fcf7-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="8fcf7-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8fcf7-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8fcf7-120">Celé číslo, které definuje počet zpráv souběžně poslaných bez přidělení nových modulů pro zápis.</span><span class="sxs-lookup"><span data-stu-id="8fcf7-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="8fcf7-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="8fcf7-121">ReaderQuotas</span></span>  
 <span data-ttu-id="8fcf7-122">Datový typ: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="8fcf7-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="8fcf7-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8fcf7-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8fcf7-124">Kvóty čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="8fcf7-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8fcf7-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8fcf7-125">Requirements</span></span>  
  
|<span data-ttu-id="8fcf7-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="8fcf7-126">MOF</span></span>|<span data-ttu-id="8fcf7-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8fcf7-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8fcf7-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="8fcf7-128">Namespace</span></span>|<span data-ttu-id="8fcf7-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8fcf7-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8fcf7-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8fcf7-130">See also</span></span>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: 326fe6a7ca8dc5dba0dd64b1c5fc97cec49279c7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50180875"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="e49b0-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="e49b0-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="e49b0-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="e49b0-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e49b0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e49b0-104">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e49b0-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e49b0-105">Methods</span></span>  
 <span data-ttu-id="e49b0-106">Třídě BinaryMessageEncodingBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="e49b0-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e49b0-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e49b0-107">Properties</span></span>  
 <span data-ttu-id="e49b0-108">Třídě BinaryMessageEncodingBindingElement má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="e49b0-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="e49b0-109">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="e49b0-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="e49b0-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e49b0-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="e49b0-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e49b0-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e49b0-112">Celé číslo, které definuje počet zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="e49b0-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="e49b0-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="e49b0-113">MaxSessionSize</span></span>  
 <span data-ttu-id="e49b0-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e49b0-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e49b0-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e49b0-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e49b0-116">Hodnota, která určuje velikost v bajtech, použité pro kódování vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e49b0-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="e49b0-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="e49b0-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="e49b0-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e49b0-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="e49b0-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e49b0-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e49b0-120">Celé číslo, které definuje počet zpráv souběžně poslaných bez přidělení nových modulů pro zápis.</span><span class="sxs-lookup"><span data-stu-id="e49b0-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="e49b0-121">readerQuotas</span><span class="sxs-lookup"><span data-stu-id="e49b0-121">ReaderQuotas</span></span>  
 <span data-ttu-id="e49b0-122">Datový typ: XmlDictionaryReaderQuotas, který</span><span class="sxs-lookup"><span data-stu-id="e49b0-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="e49b0-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e49b0-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e49b0-124">Kvóty čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="e49b0-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e49b0-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e49b0-125">Requirements</span></span>  
  
|<span data-ttu-id="e49b0-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="e49b0-126">MOF</span></span>|<span data-ttu-id="e49b0-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e49b0-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e49b0-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="e49b0-128">Namespace</span></span>|<span data-ttu-id="e49b0-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e49b0-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e49b0-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="e49b0-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

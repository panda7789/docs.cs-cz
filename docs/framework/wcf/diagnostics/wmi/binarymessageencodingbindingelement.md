---
title: BinaryMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: e2bb3cdd-3bbd-4bb5-85fe-570457500a66
ms.openlocfilehash: e0551e7b4b05151490625912742aa6b26ef0216e
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59145675"
---
# <a name="binarymessageencodingbindingelement"></a><span data-ttu-id="c5e76-102">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="c5e76-102">BinaryMessageEncodingBindingElement</span></span>
<span data-ttu-id="c5e76-103">BinaryMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="c5e76-103">BinaryMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c5e76-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c5e76-104">Syntax</span></span>  
  
```csharp  
class BinaryMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  sint32 MaxReadPoolSize;  
  sint32 MaxSessionSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="c5e76-105">Metody</span><span class="sxs-lookup"><span data-stu-id="c5e76-105">Methods</span></span>  
 <span data-ttu-id="c5e76-106">Třídě BinaryMessageEncodingBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="c5e76-106">The BinaryMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="c5e76-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c5e76-107">Properties</span></span>  
 <span data-ttu-id="c5e76-108">Třídě BinaryMessageEncodingBindingElement má následující vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c5e76-108">The BinaryMessageEncodingBindingElement class has the following properties.</span></span>  
  
## <a name="maxreadpoolsize"></a><span data-ttu-id="c5e76-109">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="c5e76-109">MaxReadPoolSize</span></span>  
 <span data-ttu-id="c5e76-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="c5e76-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="c5e76-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c5e76-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5e76-112">Celé číslo, které definuje počet zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="c5e76-112">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
## <a name="maxsessionsize"></a><span data-ttu-id="c5e76-113">maxSessionSize</span><span class="sxs-lookup"><span data-stu-id="c5e76-113">MaxSessionSize</span></span>  
 <span data-ttu-id="c5e76-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="c5e76-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="c5e76-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c5e76-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5e76-116">Hodnota, která určuje velikost v bajtech, použité pro kódování vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="c5e76-116">A value that specifies the size, in bytes, of the buffer used for encoding.</span></span>  
  
## <a name="maxwritepoolsize"></a><span data-ttu-id="c5e76-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="c5e76-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="c5e76-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="c5e76-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="c5e76-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c5e76-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5e76-120">Celé číslo, které definuje počet zpráv souběžně poslaných bez přidělení nových modulů pro zápis.</span><span class="sxs-lookup"><span data-stu-id="c5e76-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
## <a name="readerquotas"></a><span data-ttu-id="c5e76-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="c5e76-121">ReaderQuotas</span></span>  
 <span data-ttu-id="c5e76-122">Datový typ: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="c5e76-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="c5e76-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="c5e76-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="c5e76-124">Kvóty čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="c5e76-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c5e76-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="c5e76-125">Requirements</span></span>  
  
|<span data-ttu-id="c5e76-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="c5e76-126">MOF</span></span>|<span data-ttu-id="c5e76-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="c5e76-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="c5e76-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="c5e76-128">Namespace</span></span>|<span data-ttu-id="c5e76-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="c5e76-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c5e76-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c5e76-130">See also</span></span>

- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>

---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: 83fa879fbef94e2dc9c142dfb92a51a54a7b60cb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486524"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="7c846-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="7c846-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="7c846-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="7c846-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c846-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7c846-104">Syntax</span></span>  
  
```  
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="7c846-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7c846-105">Methods</span></span>  
 <span data-ttu-id="7c846-106">Třída MtomMessageEncodingBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="7c846-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7c846-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7c846-107">Properties</span></span>  
 <span data-ttu-id="7c846-108">Třída MtomMessageEncodingBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="7c846-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="7c846-109">Kódování</span><span class="sxs-lookup"><span data-stu-id="7c846-109">Encoding</span></span>  
 <span data-ttu-id="7c846-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="7c846-110">Data type: string</span></span>  
  
 <span data-ttu-id="7c846-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7c846-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7c846-112">Kódování znakové sady, který se má použít pro vysílání zpráv v vazby.</span><span class="sxs-lookup"><span data-stu-id="7c846-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="7c846-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="7c846-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="7c846-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="7c846-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="7c846-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7c846-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7c846-116">Celé číslo, které definuje počet zpráv lze číst souběžně bez přidělení nového čtečky.</span><span class="sxs-lookup"><span data-stu-id="7c846-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="7c846-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="7c846-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="7c846-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="7c846-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="7c846-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7c846-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7c846-120">Celé číslo, které definuje počet zpráv lze najednou odeslat bez přiděluje nový zapisovače.</span><span class="sxs-lookup"><span data-stu-id="7c846-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="7c846-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="7c846-121">ReaderQuotas</span></span>  
 <span data-ttu-id="7c846-122">Datový typ: XmlDictionaryReaderQuotas, který</span><span class="sxs-lookup"><span data-stu-id="7c846-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="7c846-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7c846-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7c846-124">Kvóty čtečky.</span><span class="sxs-lookup"><span data-stu-id="7c846-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c846-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7c846-125">Requirements</span></span>  
  
|<span data-ttu-id="7c846-126">MOF</span><span class="sxs-lookup"><span data-stu-id="7c846-126">MOF</span></span>|<span data-ttu-id="7c846-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7c846-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7c846-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="7c846-128">Namespace</span></span>|<span data-ttu-id="7c846-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7c846-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7c846-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c846-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

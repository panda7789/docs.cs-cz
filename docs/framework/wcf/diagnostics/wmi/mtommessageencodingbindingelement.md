---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: aed65311d2b36a5dc764511de04e34c4bfb69d7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61963241"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="d1c09-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="d1c09-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="d1c09-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="d1c09-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1c09-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1c09-104">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d1c09-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d1c09-105">Methods</span></span>  
 <span data-ttu-id="d1c09-106">Třída MtomMessageEncodingBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="d1c09-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d1c09-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d1c09-107">Properties</span></span>  
 <span data-ttu-id="d1c09-108">Třída MtomMessageEncodingBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d1c09-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="d1c09-109">Kódování</span><span class="sxs-lookup"><span data-stu-id="d1c09-109">Encoding</span></span>  
 <span data-ttu-id="d1c09-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d1c09-110">Data type: string</span></span>  
  
 <span data-ttu-id="d1c09-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d1c09-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d1c09-112">Kódování znakové sady, chcete-li být použito pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="d1c09-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="d1c09-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="d1c09-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="d1c09-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d1c09-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="d1c09-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d1c09-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d1c09-116">Celé číslo, které definuje počet zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="d1c09-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="d1c09-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="d1c09-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="d1c09-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d1c09-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="d1c09-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d1c09-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d1c09-120">Celé číslo, které definuje počet zpráv souběžně poslaných bez přidělení nových modulů pro zápis.</span><span class="sxs-lookup"><span data-stu-id="d1c09-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="d1c09-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="d1c09-121">ReaderQuotas</span></span>  
 <span data-ttu-id="d1c09-122">Datový typ: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="d1c09-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="d1c09-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d1c09-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d1c09-124">Kvóty čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="d1c09-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d1c09-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d1c09-125">Requirements</span></span>  
  
|<span data-ttu-id="d1c09-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="d1c09-126">MOF</span></span>|<span data-ttu-id="d1c09-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d1c09-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d1c09-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="d1c09-128">Namespace</span></span>|<span data-ttu-id="d1c09-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d1c09-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1c09-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1c09-130">See also</span></span>

- <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

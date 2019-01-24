---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 188a766807cd779ac51df390b1332641584dbb06
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54662709"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="86f85-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="86f85-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="86f85-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="86f85-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86f85-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="86f85-104">Syntax</span></span>  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="86f85-105">Metody</span><span class="sxs-lookup"><span data-stu-id="86f85-105">Methods</span></span>  
 <span data-ttu-id="86f85-106">Třída TextMessageEncodingBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="86f85-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="86f85-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="86f85-107">Properties</span></span>  
 <span data-ttu-id="86f85-108">Třída TextMessageEncodingBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="86f85-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="86f85-109">Kódování</span><span class="sxs-lookup"><span data-stu-id="86f85-109">Encoding</span></span>  
 <span data-ttu-id="86f85-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="86f85-110">Data type: string</span></span>  
  
 <span data-ttu-id="86f85-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="86f85-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="86f85-112">Kódování znakové sady, chcete-li být použito pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="86f85-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="86f85-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="86f85-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="86f85-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="86f85-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="86f85-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="86f85-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="86f85-116">Celé číslo, které definuje počet zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="86f85-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="86f85-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="86f85-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="86f85-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="86f85-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="86f85-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="86f85-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="86f85-120">Celé číslo, které definuje počet zpráv souběžně poslaných bez přidělení nových modulů pro zápis.</span><span class="sxs-lookup"><span data-stu-id="86f85-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="86f85-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="86f85-121">ReaderQuotas</span></span>  
 <span data-ttu-id="86f85-122">Datový typ: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="86f85-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="86f85-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="86f85-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="86f85-124">Kvóty čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="86f85-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86f85-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="86f85-125">Requirements</span></span>  
  
|<span data-ttu-id="86f85-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="86f85-126">MOF</span></span>|<span data-ttu-id="86f85-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="86f85-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="86f85-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="86f85-128">Namespace</span></span>|<span data-ttu-id="86f85-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="86f85-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="86f85-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="86f85-130">See also</span></span>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

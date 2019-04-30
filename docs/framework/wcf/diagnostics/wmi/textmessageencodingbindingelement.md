---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 67c1083daa9acfd204d4de50d4e9178b25aafcf0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61858387"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="57505-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="57505-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="57505-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="57505-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57505-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57505-104">Syntax</span></span>  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="57505-105">Metody</span><span class="sxs-lookup"><span data-stu-id="57505-105">Methods</span></span>  
 <span data-ttu-id="57505-106">Třída TextMessageEncodingBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="57505-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="57505-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="57505-107">Properties</span></span>  
 <span data-ttu-id="57505-108">Třída TextMessageEncodingBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="57505-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="57505-109">Kódování</span><span class="sxs-lookup"><span data-stu-id="57505-109">Encoding</span></span>  
 <span data-ttu-id="57505-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="57505-110">Data type: string</span></span>  
  
 <span data-ttu-id="57505-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57505-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57505-112">Kódování znakové sady, chcete-li být použito pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="57505-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="57505-113">MaxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="57505-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="57505-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="57505-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="57505-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57505-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57505-116">Celé číslo, které definuje počet zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="57505-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="57505-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="57505-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="57505-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="57505-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="57505-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57505-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57505-120">Celé číslo, které definuje počet zpráv souběžně poslaných bez přidělení nových modulů pro zápis.</span><span class="sxs-lookup"><span data-stu-id="57505-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="57505-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="57505-121">ReaderQuotas</span></span>  
 <span data-ttu-id="57505-122">Datový typ: XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="57505-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="57505-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57505-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57505-124">Kvóty čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="57505-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57505-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57505-125">Requirements</span></span>  
  
|<span data-ttu-id="57505-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="57505-126">MOF</span></span>|<span data-ttu-id="57505-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="57505-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="57505-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="57505-128">Namespace</span></span>|<span data-ttu-id="57505-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="57505-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57505-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="57505-130">See also</span></span>

- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

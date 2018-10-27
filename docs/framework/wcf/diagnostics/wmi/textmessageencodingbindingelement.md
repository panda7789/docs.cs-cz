---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: 2371c38aebe2bd8d6da93d702801556fad986ef9
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452570"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="5466e-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="5466e-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="5466e-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="5466e-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5466e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5466e-104">Syntax</span></span>  
  
```csharp
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="5466e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="5466e-105">Methods</span></span>  
 <span data-ttu-id="5466e-106">Třída TextMessageEncodingBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="5466e-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="5466e-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="5466e-107">Properties</span></span>  
 <span data-ttu-id="5466e-108">Třída TextMessageEncodingBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="5466e-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="5466e-109">Kódování</span><span class="sxs-lookup"><span data-stu-id="5466e-109">Encoding</span></span>  
 <span data-ttu-id="5466e-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="5466e-110">Data type: string</span></span>  
  
 <span data-ttu-id="5466e-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5466e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5466e-112">Kódování znakové sady, chcete-li být použito pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="5466e-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="5466e-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="5466e-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="5466e-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="5466e-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="5466e-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5466e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5466e-116">Celé číslo, které definuje počet zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="5466e-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="5466e-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="5466e-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="5466e-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="5466e-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="5466e-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5466e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5466e-120">Celé číslo, které definuje počet zpráv souběžně poslaných bez přidělení nových modulů pro zápis.</span><span class="sxs-lookup"><span data-stu-id="5466e-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="5466e-121">readerQuotas</span><span class="sxs-lookup"><span data-stu-id="5466e-121">ReaderQuotas</span></span>  
 <span data-ttu-id="5466e-122">Datový typ: XmlDictionaryReaderQuotas, který</span><span class="sxs-lookup"><span data-stu-id="5466e-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="5466e-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="5466e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="5466e-124">Kvóty čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="5466e-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5466e-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="5466e-125">Requirements</span></span>  
  
|<span data-ttu-id="5466e-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="5466e-126">MOF</span></span>|<span data-ttu-id="5466e-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="5466e-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="5466e-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="5466e-128">Namespace</span></span>|<span data-ttu-id="5466e-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="5466e-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5466e-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="5466e-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

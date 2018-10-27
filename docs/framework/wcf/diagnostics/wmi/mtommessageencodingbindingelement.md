---
title: MtomMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 4a9c6c3d-e561-4b2d-a693-7e84bdd3534a
ms.openlocfilehash: 49a640a666131491366646d6d486d25a515e35bf
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185703"
---
# <a name="mtommessageencodingbindingelement"></a><span data-ttu-id="d9b0c-102">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="d9b0c-102">MtomMessageEncodingBindingElement</span></span>
<span data-ttu-id="d9b0c-103">MtomMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="d9b0c-103">MtomMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d9b0c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d9b0c-104">Syntax</span></span>  
  
```csharp
class MtomMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d9b0c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d9b0c-105">Methods</span></span>  
 <span data-ttu-id="d9b0c-106">Třída MtomMessageEncodingBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-106">The MtomMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d9b0c-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d9b0c-107">Properties</span></span>  
 <span data-ttu-id="d9b0c-108">Třída MtomMessageEncodingBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d9b0c-108">The MtomMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="d9b0c-109">Kódování</span><span class="sxs-lookup"><span data-stu-id="d9b0c-109">Encoding</span></span>  
 <span data-ttu-id="d9b0c-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="d9b0c-110">Data type: string</span></span>  
  
 <span data-ttu-id="d9b0c-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d9b0c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9b0c-112">Kódování znakové sady, chcete-li být použito pro vysílání zpráv z vazby.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="d9b0c-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="d9b0c-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="d9b0c-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d9b0c-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="d9b0c-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d9b0c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9b0c-116">Celé číslo, které definuje počet zpráv lze souběžně číst bez přidělení nových čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="d9b0c-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="d9b0c-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="d9b0c-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d9b0c-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="d9b0c-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d9b0c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9b0c-120">Celé číslo, které definuje počet zpráv souběžně poslaných bez přidělení nových modulů pro zápis.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="d9b0c-121">readerQuotas</span><span class="sxs-lookup"><span data-stu-id="d9b0c-121">ReaderQuotas</span></span>  
 <span data-ttu-id="d9b0c-122">Datový typ: XmlDictionaryReaderQuotas, který</span><span class="sxs-lookup"><span data-stu-id="d9b0c-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="d9b0c-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d9b0c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d9b0c-124">Kvóty čtecích zařízení.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d9b0c-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d9b0c-125">Requirements</span></span>  
  
|<span data-ttu-id="d9b0c-126">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="d9b0c-126">MOF</span></span>|<span data-ttu-id="d9b0c-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d9b0c-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d9b0c-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="d9b0c-128">Namespace</span></span>|<span data-ttu-id="d9b0c-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d9b0c-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d9b0c-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="d9b0c-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>

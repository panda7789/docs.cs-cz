---
title: TextMessageEncodingBindingElement
ms.date: 03/30/2017
ms.assetid: 885e2d7a-3436-4093-bc5f-0a404c62acdc
ms.openlocfilehash: f9b94e946413967cc14282e85743a23327683b89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486013"
---
# <a name="textmessageencodingbindingelement"></a><span data-ttu-id="38291-102">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="38291-102">TextMessageEncodingBindingElement</span></span>
<span data-ttu-id="38291-103">TextMessageEncodingBindingElement</span><span class="sxs-lookup"><span data-stu-id="38291-103">TextMessageEncodingBindingElement</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38291-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="38291-104">Syntax</span></span>  
  
```  
class TextMessageEncodingBindingElement : MessageEncodingBindingElement  
{  
  string Encoding;  
  sint32 MaxReadPoolSize;  
  sint32 MaxWritePoolSize;  
  XmlDictionaryReaderQuotas ReaderQuotas;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="38291-105">Metody</span><span class="sxs-lookup"><span data-stu-id="38291-105">Methods</span></span>  
 <span data-ttu-id="38291-106">Třída TextMessageEncodingBindingElement nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="38291-106">The TextMessageEncodingBindingElement class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="38291-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="38291-107">Properties</span></span>  
 <span data-ttu-id="38291-108">Třída TextMessageEncodingBindingElement má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="38291-108">The TextMessageEncodingBindingElement class has the following properties:</span></span>  
  
### <a name="encoding"></a><span data-ttu-id="38291-109">Kódování</span><span class="sxs-lookup"><span data-stu-id="38291-109">Encoding</span></span>  
 <span data-ttu-id="38291-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="38291-110">Data type: string</span></span>  
  
 <span data-ttu-id="38291-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="38291-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38291-112">Kódování znakové sady, který se má použít pro vysílání zpráv v vazby.</span><span class="sxs-lookup"><span data-stu-id="38291-112">The character set encoding to be used for emitting messages on the binding.</span></span>  
  
### <a name="maxreadpoolsize"></a><span data-ttu-id="38291-113">maxReadPoolSize</span><span class="sxs-lookup"><span data-stu-id="38291-113">MaxReadPoolSize</span></span>  
 <span data-ttu-id="38291-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="38291-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="38291-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="38291-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38291-116">Celé číslo, které definuje počet zpráv lze číst souběžně bez přidělení nového čtečky.</span><span class="sxs-lookup"><span data-stu-id="38291-116">An integer that defines how many messages can be read simultaneously without allocating new readers.</span></span>  
  
### <a name="maxwritepoolsize"></a><span data-ttu-id="38291-117">maxWritePoolSize</span><span class="sxs-lookup"><span data-stu-id="38291-117">MaxWritePoolSize</span></span>  
 <span data-ttu-id="38291-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="38291-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="38291-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="38291-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38291-120">Celé číslo, které definuje počet zpráv lze najednou odeslat bez přiděluje nový zapisovače.</span><span class="sxs-lookup"><span data-stu-id="38291-120">An integer that defines how many messages can be sent simultaneously without allocating new writers.</span></span>  
  
### <a name="readerquotas"></a><span data-ttu-id="38291-121">ReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="38291-121">ReaderQuotas</span></span>  
 <span data-ttu-id="38291-122">Datový typ: XmlDictionaryReaderQuotas, který</span><span class="sxs-lookup"><span data-stu-id="38291-122">Data type: XmlDictionaryReaderQuotas</span></span>  
  
 <span data-ttu-id="38291-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="38291-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="38291-124">Kvóty čtečky.</span><span class="sxs-lookup"><span data-stu-id="38291-124">The quotas of the readers.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="38291-125">Požadavky</span><span class="sxs-lookup"><span data-stu-id="38291-125">Requirements</span></span>  
  
|<span data-ttu-id="38291-126">MOF</span><span class="sxs-lookup"><span data-stu-id="38291-126">MOF</span></span>|<span data-ttu-id="38291-127">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="38291-127">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="38291-128">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="38291-128">Namespace</span></span>|<span data-ttu-id="38291-129">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="38291-129">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="38291-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="38291-130">See Also</span></span>  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>

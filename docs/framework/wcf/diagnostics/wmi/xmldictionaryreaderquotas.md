---
title: XmlDictionaryReaderQuotas
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 06c0ff11752ae1030e574182cfb825fb87ddc8c7
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="dc217-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="dc217-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="dc217-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="dc217-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dc217-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dc217-104">Syntax</span></span>  
  
```  
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="dc217-105">Metody</span><span class="sxs-lookup"><span data-stu-id="dc217-105">Methods</span></span>  
 <span data-ttu-id="dc217-106">Třída XmlDictionaryReaderQuotas, který nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="dc217-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="dc217-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="dc217-107">Properties</span></span>  
 <span data-ttu-id="dc217-108">Třída XmlDictionaryReaderQuotas, který má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="dc217-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="dc217-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="dc217-109">MaxArrayLength</span></span>  
 <span data-ttu-id="dc217-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="dc217-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="dc217-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="dc217-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dc217-112">Maximální povolená délka pole.</span><span class="sxs-lookup"><span data-stu-id="dc217-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="dc217-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="dc217-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="dc217-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="dc217-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="dc217-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="dc217-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dc217-116">Maximální povolená bajtů vrácených pro každý pro čtení.</span><span class="sxs-lookup"><span data-stu-id="dc217-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="dc217-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="dc217-117">MaxDepth</span></span>  
 <span data-ttu-id="dc217-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="dc217-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="dc217-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="dc217-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dc217-120">Maximální hloubka vnořeného uzlu pro každý pro čtení.</span><span class="sxs-lookup"><span data-stu-id="dc217-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="dc217-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="dc217-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="dc217-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="dc217-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="dc217-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="dc217-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dc217-124">Maximální počet znaků v názvu tabulky povolené.</span><span class="sxs-lookup"><span data-stu-id="dc217-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="dc217-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="dc217-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="dc217-126">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="dc217-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="dc217-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="dc217-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="dc217-128">Maximální počet znaků v obsahu elementu XML povolen.</span><span class="sxs-lookup"><span data-stu-id="dc217-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="dc217-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="dc217-129">Requirements</span></span>  
  
|<span data-ttu-id="dc217-130">MOF</span><span class="sxs-lookup"><span data-stu-id="dc217-130">MOF</span></span>|<span data-ttu-id="dc217-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="dc217-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="dc217-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="dc217-132">Namespace</span></span>|<span data-ttu-id="dc217-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="dc217-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dc217-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="dc217-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>

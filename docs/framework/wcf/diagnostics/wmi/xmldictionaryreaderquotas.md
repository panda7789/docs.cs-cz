---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: 78914d52a9e57fe2e48adcfc0d7b6f911a0d8b3a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487825"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="b4992-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="b4992-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="b4992-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="b4992-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b4992-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b4992-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="b4992-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b4992-105">Methods</span></span>  
 <span data-ttu-id="b4992-106">Třída XmlDictionaryReaderQuotas, který nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="b4992-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b4992-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b4992-107">Properties</span></span>  
 <span data-ttu-id="b4992-108">Třída XmlDictionaryReaderQuotas, který má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="b4992-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="b4992-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="b4992-109">MaxArrayLength</span></span>  
 <span data-ttu-id="b4992-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="b4992-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="b4992-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b4992-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4992-112">Maximální povolená délka pole.</span><span class="sxs-lookup"><span data-stu-id="b4992-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="b4992-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="b4992-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="b4992-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="b4992-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="b4992-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b4992-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4992-116">Maximální povolená bajtů vrácených pro každý pro čtení.</span><span class="sxs-lookup"><span data-stu-id="b4992-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="b4992-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="b4992-117">MaxDepth</span></span>  
 <span data-ttu-id="b4992-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="b4992-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="b4992-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b4992-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4992-120">Maximální hloubka vnořeného uzlu pro každý pro čtení.</span><span class="sxs-lookup"><span data-stu-id="b4992-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="b4992-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="b4992-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="b4992-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="b4992-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="b4992-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b4992-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4992-124">Maximální počet znaků v názvu tabulky povolené.</span><span class="sxs-lookup"><span data-stu-id="b4992-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="b4992-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="b4992-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="b4992-126">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="b4992-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="b4992-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b4992-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b4992-128">Maximální počet znaků v obsahu elementu XML povolen.</span><span class="sxs-lookup"><span data-stu-id="b4992-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b4992-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b4992-129">Requirements</span></span>  
  
|<span data-ttu-id="b4992-130">MOF</span><span class="sxs-lookup"><span data-stu-id="b4992-130">MOF</span></span>|<span data-ttu-id="b4992-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b4992-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b4992-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="b4992-132">Namespace</span></span>|<span data-ttu-id="b4992-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b4992-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b4992-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="b4992-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>

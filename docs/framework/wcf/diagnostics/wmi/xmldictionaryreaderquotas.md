---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: 9bc519509b00383be333ac605688950d2709117c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199471"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="d5588-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="d5588-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="d5588-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="d5588-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5588-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5588-104">Syntax</span></span>  
  
```csharp
class XmlDictionaryReaderQuotas  
{  
  sint32 MaxArrayLength;  
  sint32 MaxBytesPerRead;  
  sint32 MaxDepth;  
  sint32 MaxNameTableCharCount;  
  sint32 MaxStringContentLength;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="d5588-105">Metody</span><span class="sxs-lookup"><span data-stu-id="d5588-105">Methods</span></span>  
 <span data-ttu-id="d5588-106">Třídu XmlDictionaryReaderQuotas, který nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="d5588-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="d5588-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="d5588-107">Properties</span></span>  
 <span data-ttu-id="d5588-108">Třídu XmlDictionaryReaderQuotas, který má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="d5588-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="d5588-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="d5588-109">MaxArrayLength</span></span>  
 <span data-ttu-id="d5588-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d5588-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="d5588-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d5588-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d5588-112">Maximální povolená délka pole.</span><span class="sxs-lookup"><span data-stu-id="d5588-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="d5588-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="d5588-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="d5588-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d5588-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="d5588-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d5588-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d5588-116">Maximální povolené bajty vrácené na při každém čtení.</span><span class="sxs-lookup"><span data-stu-id="d5588-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="d5588-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="d5588-117">MaxDepth</span></span>  
 <span data-ttu-id="d5588-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d5588-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="d5588-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d5588-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d5588-120">Maximální hloubku vnořeného uzlu při každém čtení.</span><span class="sxs-lookup"><span data-stu-id="d5588-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="d5588-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="d5588-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="d5588-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d5588-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="d5588-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d5588-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d5588-124">Maximum znaků povolených v názvu tabulky.</span><span class="sxs-lookup"><span data-stu-id="d5588-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="d5588-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="d5588-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="d5588-126">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="d5588-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="d5588-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="d5588-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="d5588-128">Maximum znaků povolených v obsahu prvku XML.</span><span class="sxs-lookup"><span data-stu-id="d5588-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d5588-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="d5588-129">Requirements</span></span>  
  
|<span data-ttu-id="d5588-130">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="d5588-130">MOF</span></span>|<span data-ttu-id="d5588-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="d5588-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="d5588-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="d5588-132">Namespace</span></span>|<span data-ttu-id="d5588-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="d5588-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d5588-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5588-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>

---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: f1c12a0a60397a84d4e9ff0241c4182b4511af5c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214881"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="4dd56-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4dd56-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="4dd56-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="4dd56-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4dd56-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4dd56-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="4dd56-105">Metody</span><span class="sxs-lookup"><span data-stu-id="4dd56-105">Methods</span></span>  
 <span data-ttu-id="4dd56-106">Třídu XmlDictionaryReaderQuotas, který nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="4dd56-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="4dd56-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="4dd56-107">Properties</span></span>  
 <span data-ttu-id="4dd56-108">Třídu XmlDictionaryReaderQuotas, který má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="4dd56-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="4dd56-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="4dd56-109">MaxArrayLength</span></span>  
 <span data-ttu-id="4dd56-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4dd56-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="4dd56-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4dd56-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4dd56-112">Maximální povolená délka pole.</span><span class="sxs-lookup"><span data-stu-id="4dd56-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="4dd56-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="4dd56-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="4dd56-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4dd56-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="4dd56-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4dd56-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4dd56-116">Maximální povolené bajty vrácené na při každém čtení.</span><span class="sxs-lookup"><span data-stu-id="4dd56-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="4dd56-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="4dd56-117">MaxDepth</span></span>  
 <span data-ttu-id="4dd56-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4dd56-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="4dd56-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4dd56-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4dd56-120">Maximální hloubku vnořeného uzlu při každém čtení.</span><span class="sxs-lookup"><span data-stu-id="4dd56-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="4dd56-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="4dd56-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="4dd56-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4dd56-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="4dd56-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4dd56-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4dd56-124">Maximum znaků povolených v názvu tabulky.</span><span class="sxs-lookup"><span data-stu-id="4dd56-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="4dd56-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="4dd56-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="4dd56-126">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="4dd56-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="4dd56-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="4dd56-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="4dd56-128">Maximum znaků povolených v obsahu prvku XML.</span><span class="sxs-lookup"><span data-stu-id="4dd56-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4dd56-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="4dd56-129">Requirements</span></span>  
  
|<span data-ttu-id="4dd56-130">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="4dd56-130">MOF</span></span>|<span data-ttu-id="4dd56-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="4dd56-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="4dd56-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="4dd56-132">Namespace</span></span>|<span data-ttu-id="4dd56-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="4dd56-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4dd56-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4dd56-134">See also</span></span>

- <xref:System.Xml.XmlDictionaryReaderQuotas>
- <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>

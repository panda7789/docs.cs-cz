---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: 9bc519509b00383be333ac605688950d2709117c
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50044226"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="cfa41-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="cfa41-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="cfa41-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="cfa41-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cfa41-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cfa41-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="cfa41-105">Metody</span><span class="sxs-lookup"><span data-stu-id="cfa41-105">Methods</span></span>  
 <span data-ttu-id="cfa41-106">Třídu XmlDictionaryReaderQuotas, který nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="cfa41-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="cfa41-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="cfa41-107">Properties</span></span>  
 <span data-ttu-id="cfa41-108">Třídu XmlDictionaryReaderQuotas, který má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="cfa41-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="cfa41-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="cfa41-109">MaxArrayLength</span></span>  
 <span data-ttu-id="cfa41-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="cfa41-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="cfa41-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cfa41-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cfa41-112">Maximální povolená délka pole.</span><span class="sxs-lookup"><span data-stu-id="cfa41-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="cfa41-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="cfa41-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="cfa41-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="cfa41-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="cfa41-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cfa41-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cfa41-116">Maximální povolené bajty vrácené na při každém čtení.</span><span class="sxs-lookup"><span data-stu-id="cfa41-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="cfa41-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="cfa41-117">MaxDepth</span></span>  
 <span data-ttu-id="cfa41-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="cfa41-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="cfa41-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cfa41-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cfa41-120">Maximální hloubku vnořeného uzlu při každém čtení.</span><span class="sxs-lookup"><span data-stu-id="cfa41-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="cfa41-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="cfa41-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="cfa41-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="cfa41-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="cfa41-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cfa41-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cfa41-124">Maximum znaků povolených v názvu tabulky.</span><span class="sxs-lookup"><span data-stu-id="cfa41-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="cfa41-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="cfa41-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="cfa41-126">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="cfa41-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="cfa41-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="cfa41-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="cfa41-128">Maximum znaků povolených v obsahu prvku XML.</span><span class="sxs-lookup"><span data-stu-id="cfa41-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cfa41-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cfa41-129">Requirements</span></span>  
  
|<span data-ttu-id="cfa41-130">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="cfa41-130">MOF</span></span>|<span data-ttu-id="cfa41-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="cfa41-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="cfa41-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="cfa41-132">Namespace</span></span>|<span data-ttu-id="cfa41-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="cfa41-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cfa41-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="cfa41-134">See Also</span></span>  
 <xref:System.Xml.XmlDictionaryReaderQuotas>  
 <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>

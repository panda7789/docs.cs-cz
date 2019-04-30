---
title: XmlDictionaryReaderQuotas
ms.date: 03/30/2017
ms.assetid: 9b4ca8b4-0a89-4758-97ab-528a8ce18f07
ms.openlocfilehash: f1c12a0a60397a84d4e9ff0241c4182b4511af5c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61858426"
---
# <a name="xmldictionaryreaderquotas"></a><span data-ttu-id="e66af-102">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="e66af-102">XmlDictionaryReaderQuotas</span></span>
<span data-ttu-id="e66af-103">XmlDictionaryReaderQuotas</span><span class="sxs-lookup"><span data-stu-id="e66af-103">XmlDictionaryReaderQuotas</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e66af-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e66af-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="e66af-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e66af-105">Methods</span></span>  
 <span data-ttu-id="e66af-106">Třídu XmlDictionaryReaderQuotas, který nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="e66af-106">The XmlDictionaryReaderQuotas class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e66af-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e66af-107">Properties</span></span>  
 <span data-ttu-id="e66af-108">Třídu XmlDictionaryReaderQuotas, který má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="e66af-108">The XmlDictionaryReaderQuotas class has the following properties:</span></span>  
  
### <a name="maxarraylength"></a><span data-ttu-id="e66af-109">MaxArrayLength</span><span class="sxs-lookup"><span data-stu-id="e66af-109">MaxArrayLength</span></span>  
 <span data-ttu-id="e66af-110">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e66af-110">Data type: sint32</span></span>  
  
 <span data-ttu-id="e66af-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e66af-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e66af-112">Maximální povolená délka pole.</span><span class="sxs-lookup"><span data-stu-id="e66af-112">The maximum allowed array length.</span></span>  
  
### <a name="maxbytesperread"></a><span data-ttu-id="e66af-113">MaxBytesPerRead</span><span class="sxs-lookup"><span data-stu-id="e66af-113">MaxBytesPerRead</span></span>  
 <span data-ttu-id="e66af-114">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e66af-114">Data type: sint32</span></span>  
  
 <span data-ttu-id="e66af-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e66af-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e66af-116">Maximální povolené bajty vrácené na při každém čtení.</span><span class="sxs-lookup"><span data-stu-id="e66af-116">The maximum allowed bytes returned for each read.</span></span>  
  
### <a name="maxdepth"></a><span data-ttu-id="e66af-117">MaxDepth</span><span class="sxs-lookup"><span data-stu-id="e66af-117">MaxDepth</span></span>  
 <span data-ttu-id="e66af-118">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e66af-118">Data type: sint32</span></span>  
  
 <span data-ttu-id="e66af-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e66af-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e66af-120">Maximální hloubku vnořeného uzlu při každém čtení.</span><span class="sxs-lookup"><span data-stu-id="e66af-120">The maximum nested node depth for each read.</span></span>  
  
### <a name="maxnametablecharcount"></a><span data-ttu-id="e66af-121">MaxNameTableCharCount</span><span class="sxs-lookup"><span data-stu-id="e66af-121">MaxNameTableCharCount</span></span>  
 <span data-ttu-id="e66af-122">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e66af-122">Data type: sint32</span></span>  
  
 <span data-ttu-id="e66af-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e66af-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e66af-124">Maximum znaků povolených v názvu tabulky.</span><span class="sxs-lookup"><span data-stu-id="e66af-124">The maximum characters allowed in a table name.</span></span>  
  
### <a name="maxstringcontentlength"></a><span data-ttu-id="e66af-125">MaxStringContentLength</span><span class="sxs-lookup"><span data-stu-id="e66af-125">MaxStringContentLength</span></span>  
 <span data-ttu-id="e66af-126">Datový typ: sint32</span><span class="sxs-lookup"><span data-stu-id="e66af-126">Data type: sint32</span></span>  
  
 <span data-ttu-id="e66af-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e66af-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e66af-128">Maximum znaků povolených v obsahu prvku XML.</span><span class="sxs-lookup"><span data-stu-id="e66af-128">The maximum characters allowed in XML element content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e66af-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e66af-129">Requirements</span></span>  
  
|<span data-ttu-id="e66af-130">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="e66af-130">MOF</span></span>|<span data-ttu-id="e66af-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e66af-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e66af-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="e66af-132">Namespace</span></span>|<span data-ttu-id="e66af-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e66af-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e66af-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e66af-134">See also</span></span>

- <xref:System.Xml.XmlDictionaryReaderQuotas>
- <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>

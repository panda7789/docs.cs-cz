---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 2e38eb2c2d42ffc5436562b254a42215ccabbab2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59768654"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="e27f2-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="e27f2-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="e27f2-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="e27f2-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e27f2-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e27f2-104">Syntax</span></span>  
  
```csharp
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="e27f2-105">Metody</span><span class="sxs-lookup"><span data-stu-id="e27f2-105">Methods</span></span>  
 <span data-ttu-id="e27f2-106">Třídě ServiceDebugBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="e27f2-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="e27f2-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="e27f2-107">Properties</span></span>  
 <span data-ttu-id="e27f2-108">Třídě ServiceDebugBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="e27f2-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="e27f2-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="e27f2-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="e27f2-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="e27f2-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="e27f2-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e27f2-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e27f2-112">Určuje, zda služba zveřejňuje své WSDL na adrese řídí `HttpGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="e27f2-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="e27f2-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="e27f2-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="e27f2-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="e27f2-114">Data type: string</span></span>  
  
 <span data-ttu-id="e27f2-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e27f2-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e27f2-116">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTP.</span><span class="sxs-lookup"><span data-stu-id="e27f2-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="e27f2-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="e27f2-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="e27f2-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="e27f2-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="e27f2-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e27f2-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e27f2-120">Určuje, zda služba zveřejňuje své WSDL přes HTTPS na adrese kontrolované pomocí `HttpsGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="e27f2-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="e27f2-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="e27f2-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="e27f2-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="e27f2-122">Data type: string</span></span>  
  
 <span data-ttu-id="e27f2-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e27f2-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e27f2-124">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTPS.</span><span class="sxs-lookup"><span data-stu-id="e27f2-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="e27f2-125">Třídu IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="e27f2-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="e27f2-126">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="e27f2-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="e27f2-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="e27f2-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="e27f2-128">Určuje, jestli se má být řízená informace výjimky zařazená do podrobností chyb SOAP vrácena klientům pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="e27f2-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e27f2-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e27f2-129">Requirements</span></span>  
  
|<span data-ttu-id="e27f2-130">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="e27f2-130">MOF</span></span>|<span data-ttu-id="e27f2-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="e27f2-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="e27f2-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="e27f2-132">Namespace</span></span>|<span data-ttu-id="e27f2-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="e27f2-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e27f2-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e27f2-134">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceDebugBehavior>

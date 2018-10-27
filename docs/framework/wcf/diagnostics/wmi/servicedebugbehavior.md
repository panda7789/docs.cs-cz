---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: 68b2350f257bc95d8e17f4b9049d67c7f67becae
ms.sourcegitcommit: b22705f1540b237c566721018f974822d5cd8758
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/19/2018
ms.locfileid: "49452859"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="57ea3-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="57ea3-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="57ea3-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="57ea3-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57ea3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57ea3-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="57ea3-105">Metody</span><span class="sxs-lookup"><span data-stu-id="57ea3-105">Methods</span></span>  
 <span data-ttu-id="57ea3-106">Třídě ServiceDebugBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="57ea3-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="57ea3-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="57ea3-107">Properties</span></span>  
 <span data-ttu-id="57ea3-108">Třídě ServiceDebugBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="57ea3-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="57ea3-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="57ea3-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="57ea3-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="57ea3-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="57ea3-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57ea3-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57ea3-112">Určuje, zda služba zveřejňuje své WSDL na adrese řídí `HttpGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="57ea3-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="57ea3-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="57ea3-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="57ea3-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="57ea3-114">Data type: string</span></span>  
  
 <span data-ttu-id="57ea3-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57ea3-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57ea3-116">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTP.</span><span class="sxs-lookup"><span data-stu-id="57ea3-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="57ea3-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="57ea3-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="57ea3-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="57ea3-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="57ea3-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57ea3-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57ea3-120">Určuje, zda služba zveřejňuje své WSDL přes HTTPS na adrese kontrolované pomocí `HttpsGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="57ea3-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="57ea3-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="57ea3-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="57ea3-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="57ea3-122">Data type: string</span></span>  
  
 <span data-ttu-id="57ea3-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57ea3-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57ea3-124">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTPS.</span><span class="sxs-lookup"><span data-stu-id="57ea3-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="57ea3-125">Třídu IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="57ea3-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="57ea3-126">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="57ea3-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="57ea3-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57ea3-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57ea3-128">Určuje, jestli se má být řízená informace výjimky zařazená do podrobností chyb SOAP vrácena klientům pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="57ea3-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57ea3-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57ea3-129">Requirements</span></span>  
  
|<span data-ttu-id="57ea3-130">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="57ea3-130">MOF</span></span>|<span data-ttu-id="57ea3-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="57ea3-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="57ea3-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="57ea3-132">Namespace</span></span>|<span data-ttu-id="57ea3-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="57ea3-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57ea3-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="57ea3-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>

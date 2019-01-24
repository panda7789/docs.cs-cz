---
title: ServiceDebugBehavior
ms.date: 03/30/2017
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
ms.openlocfilehash: d6f0e4741aa10bff450a29cfd7a9e63e226c6495
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54498879"
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="8675d-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="8675d-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="8675d-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="8675d-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8675d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8675d-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="8675d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="8675d-105">Methods</span></span>  
 <span data-ttu-id="8675d-106">Třídě ServiceDebugBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="8675d-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="8675d-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="8675d-107">Properties</span></span>  
 <span data-ttu-id="8675d-108">Třídě ServiceDebugBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="8675d-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="8675d-109">HttpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="8675d-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="8675d-110">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="8675d-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="8675d-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8675d-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8675d-112">Určuje, zda služba zveřejňuje své WSDL na adrese řídí `HttpGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="8675d-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="8675d-113">HttpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="8675d-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="8675d-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8675d-114">Data type: string</span></span>  
  
 <span data-ttu-id="8675d-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8675d-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8675d-116">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTP.</span><span class="sxs-lookup"><span data-stu-id="8675d-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="8675d-117">HttpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="8675d-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="8675d-118">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="8675d-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="8675d-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8675d-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8675d-120">Určuje, zda služba zveřejňuje své WSDL přes HTTPS na adrese kontrolované pomocí `HttpsGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="8675d-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="8675d-121">HttpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="8675d-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="8675d-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="8675d-122">Data type: string</span></span>  
  
 <span data-ttu-id="8675d-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8675d-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8675d-124">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTPS.</span><span class="sxs-lookup"><span data-stu-id="8675d-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="8675d-125">Třídu IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="8675d-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="8675d-126">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="8675d-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="8675d-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="8675d-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="8675d-128">Určuje, jestli se má být řízená informace výjimky zařazená do podrobností chyb SOAP vrácena klientům pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="8675d-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8675d-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="8675d-129">Requirements</span></span>  
  
|<span data-ttu-id="8675d-130">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="8675d-130">MOF</span></span>|<span data-ttu-id="8675d-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="8675d-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="8675d-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="8675d-132">Namespace</span></span>|<span data-ttu-id="8675d-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="8675d-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8675d-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8675d-134">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceDebugBehavior>

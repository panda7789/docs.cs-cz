---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: e96a732f8b3b4d78d597429905cc7dd290dcc606
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33485997"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="33b61-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="33b61-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="33b61-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="33b61-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33b61-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33b61-104">Syntax</span></span>  
  
```  
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="33b61-105">Metody</span><span class="sxs-lookup"><span data-stu-id="33b61-105">Methods</span></span>  
 <span data-ttu-id="33b61-106">Třída ServiceMetadataBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="33b61-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="33b61-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="33b61-107">Properties</span></span>  
 <span data-ttu-id="33b61-108">Třída ServiceMetadataBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="33b61-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="33b61-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="33b61-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="33b61-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="33b61-110">Data type: string</span></span>  
  
 <span data-ttu-id="33b61-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="33b61-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="33b61-112">Nastaví umístění, do kterého službu přesměruje požadavků na metadata.</span><span class="sxs-lookup"><span data-stu-id="33b61-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="33b61-113">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="33b61-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="33b61-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="33b61-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="33b61-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="33b61-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="33b61-116">Určuje, zda služba zveřejňuje jeho WSDL na adrese řízené `HttpGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="33b61-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="33b61-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="33b61-117">HttpGetUrl</span></span>  
 <span data-ttu-id="33b61-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="33b61-118">Data type: string</span></span>  
  
 <span data-ttu-id="33b61-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="33b61-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="33b61-120">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="33b61-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="33b61-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="33b61-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="33b61-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="33b61-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="33b61-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="33b61-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="33b61-124">Určuje, zda služba zveřejňuje jeho WSDL přes protokol HTTPS na adrese řízené `HttpsGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="33b61-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="33b61-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="33b61-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="33b61-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="33b61-126">Data type: string</span></span>  
  
 <span data-ttu-id="33b61-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="33b61-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="33b61-128">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="33b61-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33b61-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33b61-129">Requirements</span></span>  
  
|<span data-ttu-id="33b61-130">MOF</span><span class="sxs-lookup"><span data-stu-id="33b61-130">MOF</span></span>|<span data-ttu-id="33b61-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="33b61-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="33b61-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="33b61-132">Namespace</span></span>|<span data-ttu-id="33b61-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="33b61-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="33b61-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="33b61-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>

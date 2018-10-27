---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 19a04b6432f1ecc38a3b906b7e677175863134db
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188830"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="52668-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="52668-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="52668-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="52668-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52668-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52668-104">Syntax</span></span>  
  
```csharp
class ServiceMetadataBehavior : Behavior  
{  
  string ExternalMetadataLocation;  
  boolean HttpGetEnabled;  
  string HttpGetUrl;  
  boolean HttpsGetEnabled;  
  string HttpsGetUrl;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="52668-105">Metody</span><span class="sxs-lookup"><span data-stu-id="52668-105">Methods</span></span>  
 <span data-ttu-id="52668-106">Třídu ServiceMetadataBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="52668-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="52668-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="52668-107">Properties</span></span>  
 <span data-ttu-id="52668-108">Třídu ServiceMetadataBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="52668-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="52668-109">externalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="52668-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="52668-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="52668-110">Data type: string</span></span>  
  
 <span data-ttu-id="52668-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="52668-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52668-112">Nastaví umístění, do kterého služba přesměruje požadavky metadat.</span><span class="sxs-lookup"><span data-stu-id="52668-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="52668-113">httpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="52668-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="52668-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="52668-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="52668-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="52668-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52668-116">Určuje, zda služba zveřejňuje své WSDL na adrese řídí `HttpGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="52668-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="52668-117">Vlastnost httpGetUrl</span><span class="sxs-lookup"><span data-stu-id="52668-117">HttpGetUrl</span></span>  
 <span data-ttu-id="52668-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="52668-118">Data type: string</span></span>  
  
 <span data-ttu-id="52668-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="52668-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52668-120">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTP.</span><span class="sxs-lookup"><span data-stu-id="52668-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="52668-121">httpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="52668-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="52668-122">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="52668-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="52668-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="52668-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52668-124">Určuje, zda služba zveřejňuje své WSDL přes HTTPS na adrese kontrolované pomocí `HttpsGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="52668-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="52668-125">Vlastnost httpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="52668-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="52668-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="52668-126">Data type: string</span></span>  
  
 <span data-ttu-id="52668-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="52668-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="52668-128">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTPS.</span><span class="sxs-lookup"><span data-stu-id="52668-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52668-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="52668-129">Requirements</span></span>  
  
|<span data-ttu-id="52668-130">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="52668-130">MOF</span></span>|<span data-ttu-id="52668-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="52668-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="52668-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="52668-132">Namespace</span></span>|<span data-ttu-id="52668-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="52668-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52668-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="52668-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>

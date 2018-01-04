---
title: ServiceMetadataBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c05f6be9fc0507b7e2f1de4374e3b9bbe3e2a10e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="7385e-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="7385e-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="7385e-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="7385e-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7385e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7385e-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="7385e-105">Metody</span><span class="sxs-lookup"><span data-stu-id="7385e-105">Methods</span></span>  
 <span data-ttu-id="7385e-106">Třída ServiceMetadataBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="7385e-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="7385e-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="7385e-107">Properties</span></span>  
 <span data-ttu-id="7385e-108">Třída ServiceMetadataBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="7385e-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="7385e-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="7385e-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="7385e-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="7385e-110">Data type: string</span></span>  
  
 <span data-ttu-id="7385e-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7385e-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7385e-112">Nastaví umístění, do kterého službu přesměruje požadavků na metadata.</span><span class="sxs-lookup"><span data-stu-id="7385e-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="7385e-113">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="7385e-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="7385e-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="7385e-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="7385e-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7385e-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7385e-116">Určuje, zda služba zveřejňuje jeho WSDL na adrese řízené `HttpGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="7385e-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="7385e-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="7385e-117">HttpGetUrl</span></span>  
 <span data-ttu-id="7385e-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="7385e-118">Data type: string</span></span>  
  
 <span data-ttu-id="7385e-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7385e-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7385e-120">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="7385e-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="7385e-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="7385e-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="7385e-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="7385e-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="7385e-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7385e-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7385e-124">Určuje, zda služba zveřejňuje jeho WSDL přes protokol HTTPS na adrese řízené `HttpsGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="7385e-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="7385e-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="7385e-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="7385e-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="7385e-126">Data type: string</span></span>  
  
 <span data-ttu-id="7385e-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="7385e-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="7385e-128">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="7385e-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7385e-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="7385e-129">Requirements</span></span>  
  
|<span data-ttu-id="7385e-130">MOF</span><span class="sxs-lookup"><span data-stu-id="7385e-130">MOF</span></span>|<span data-ttu-id="7385e-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="7385e-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="7385e-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="7385e-132">Namespace</span></span>|<span data-ttu-id="7385e-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="7385e-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7385e-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="7385e-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>

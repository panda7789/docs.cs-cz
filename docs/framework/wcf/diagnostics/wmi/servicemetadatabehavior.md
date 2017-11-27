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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9d10fdd9e33b078fa392e0ef359372913f9ba133
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="57d6c-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="57d6c-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="57d6c-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="57d6c-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57d6c-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57d6c-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="57d6c-105">Metody</span><span class="sxs-lookup"><span data-stu-id="57d6c-105">Methods</span></span>  
 <span data-ttu-id="57d6c-106">Třída ServiceMetadataBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="57d6c-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="57d6c-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="57d6c-107">Properties</span></span>  
 <span data-ttu-id="57d6c-108">Třída ServiceMetadataBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="57d6c-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="57d6c-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="57d6c-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="57d6c-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="57d6c-110">Data type: string</span></span>  
  
 <span data-ttu-id="57d6c-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57d6c-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57d6c-112">Nastaví umístění, do kterého službu přesměruje požadavků na metadata.</span><span class="sxs-lookup"><span data-stu-id="57d6c-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="57d6c-113">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="57d6c-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="57d6c-114">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="57d6c-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="57d6c-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57d6c-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57d6c-116">Určuje, zda služba zveřejňuje jeho WSDL na adrese řízené `HttpGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="57d6c-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="57d6c-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="57d6c-117">HttpGetUrl</span></span>  
 <span data-ttu-id="57d6c-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="57d6c-118">Data type: string</span></span>  
  
 <span data-ttu-id="57d6c-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57d6c-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57d6c-120">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="57d6c-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="57d6c-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="57d6c-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="57d6c-122">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="57d6c-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="57d6c-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57d6c-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57d6c-124">Určuje, zda služba zveřejňuje jeho WSDL přes protokol HTTPS na adrese řízené `HttpsGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="57d6c-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="57d6c-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="57d6c-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="57d6c-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="57d6c-126">Data type: string</span></span>  
  
 <span data-ttu-id="57d6c-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="57d6c-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="57d6c-128">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="57d6c-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57d6c-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="57d6c-129">Requirements</span></span>  
  
|<span data-ttu-id="57d6c-130">MOF</span><span class="sxs-lookup"><span data-stu-id="57d6c-130">MOF</span></span>|<span data-ttu-id="57d6c-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="57d6c-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="57d6c-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="57d6c-132">Namespace</span></span>|<span data-ttu-id="57d6c-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="57d6c-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="57d6c-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="57d6c-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceMetadataBehavior>

---
title: ServiceDebugBehavior
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a5ec9061-1e95-43fb-b0d9-dbd0a7bc3c44
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: af2dbd9e06876622b57379e17dbb4503cddbaac1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="servicedebugbehavior"></a><span data-ttu-id="b3d52-102">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="b3d52-102">ServiceDebugBehavior</span></span>
<span data-ttu-id="b3d52-103">ServiceDebugBehavior</span><span class="sxs-lookup"><span data-stu-id="b3d52-103">ServiceDebugBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3d52-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b3d52-104">Syntax</span></span>  
  
```  
class ServiceDebugBehavior : Behavior  
{  
  boolean HttpHelpPageEnabled;  
  string HttpHelpPageUrl;  
  boolean HttpsHelpPageEnabled;  
  string HttpsHelpPageUrl;  
  boolean IncludeExceptionDetailInFaults;  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="b3d52-105">Metody</span><span class="sxs-lookup"><span data-stu-id="b3d52-105">Methods</span></span>  
 <span data-ttu-id="b3d52-106">Třída ServiceDebugBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="b3d52-106">The ServiceDebugBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="b3d52-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b3d52-107">Properties</span></span>  
 <span data-ttu-id="b3d52-108">Třída ServiceDebugBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="b3d52-108">The ServiceDebugBehavior class has the following properties:</span></span>  
  
### <a name="httphelppageenabled"></a><span data-ttu-id="b3d52-109">httpHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="b3d52-109">HttpHelpPageEnabled</span></span>  
 <span data-ttu-id="b3d52-110">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="b3d52-110">Data type: boolean</span></span>  
  
 <span data-ttu-id="b3d52-111">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b3d52-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b3d52-112">Určuje, zda služba zveřejňuje jeho WSDL na adrese řízené `HttpGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="b3d52-112">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httphelppageurl"></a><span data-ttu-id="b3d52-113">httpHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="b3d52-113">HttpHelpPageUrl</span></span>  
 <span data-ttu-id="b3d52-114">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="b3d52-114">Data type: string</span></span>  
  
 <span data-ttu-id="b3d52-115">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b3d52-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b3d52-116">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="b3d52-116">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpshelppageenabled"></a><span data-ttu-id="b3d52-117">httpsHelpPageEnabled</span><span class="sxs-lookup"><span data-stu-id="b3d52-117">HttpsHelpPageEnabled</span></span>  
 <span data-ttu-id="b3d52-118">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="b3d52-118">Data type: boolean</span></span>  
  
 <span data-ttu-id="b3d52-119">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b3d52-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b3d52-120">Určuje, zda služba zveřejňuje jeho WSDL přes protokol HTTPS na adrese řízené `HttpsGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="b3d52-120">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpshelppageurl"></a><span data-ttu-id="b3d52-121">httpsHelpPageUrl</span><span class="sxs-lookup"><span data-stu-id="b3d52-121">HttpsHelpPageUrl</span></span>  
 <span data-ttu-id="b3d52-122">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="b3d52-122">Data type: string</span></span>  
  
 <span data-ttu-id="b3d52-123">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b3d52-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b3d52-124">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí protokolu HTTPS.</span><span class="sxs-lookup"><span data-stu-id="b3d52-124">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
### <a name="includeexceptiondetailinfaults"></a><span data-ttu-id="b3d52-125">Třídu IncludeExceptionDetailInFaults</span><span class="sxs-lookup"><span data-stu-id="b3d52-125">IncludeExceptionDetailInFaults</span></span>  
 <span data-ttu-id="b3d52-126">Datový typ: logická hodnota</span><span class="sxs-lookup"><span data-stu-id="b3d52-126">Data type: boolean</span></span>  
  
 <span data-ttu-id="b3d52-127">Přístup k typu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="b3d52-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="b3d52-128">Určuje, zda mají být zahrnuty informace o spravovaných výjimce podrobností chyb SOAP vrácených klientům pro účely ladění.</span><span class="sxs-lookup"><span data-stu-id="b3d52-128">Specifies whether to include managed exception information in the detail of SOAP faults returned to the clients for debugging purposes.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3d52-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="b3d52-129">Requirements</span></span>  
  
|<span data-ttu-id="b3d52-130">MOF</span><span class="sxs-lookup"><span data-stu-id="b3d52-130">MOF</span></span>|<span data-ttu-id="b3d52-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="b3d52-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="b3d52-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="b3d52-132">Namespace</span></span>|<span data-ttu-id="b3d52-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="b3d52-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="b3d52-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="b3d52-134">See Also</span></span>  
 <xref:System.ServiceModel.Description.ServiceDebugBehavior>

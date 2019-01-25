---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 76e28b18cd595a4a18f573dfe9539b646196c944
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720337"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="1837b-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="1837b-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="1837b-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="1837b-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1837b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1837b-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="1837b-105">Metody</span><span class="sxs-lookup"><span data-stu-id="1837b-105">Methods</span></span>  
 <span data-ttu-id="1837b-106">Třídu ServiceMetadataBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="1837b-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="1837b-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="1837b-107">Properties</span></span>  
 <span data-ttu-id="1837b-108">Třídu ServiceMetadataBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="1837b-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="1837b-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="1837b-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="1837b-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="1837b-110">Data type: string</span></span>  
  
 <span data-ttu-id="1837b-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1837b-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1837b-112">Nastaví umístění, do kterého služba přesměruje požadavky metadat.</span><span class="sxs-lookup"><span data-stu-id="1837b-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="1837b-113">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="1837b-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="1837b-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="1837b-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="1837b-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1837b-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1837b-116">Určuje, zda služba zveřejňuje své WSDL na adrese řídí `HttpGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="1837b-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="1837b-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="1837b-117">HttpGetUrl</span></span>  
 <span data-ttu-id="1837b-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="1837b-118">Data type: string</span></span>  
  
 <span data-ttu-id="1837b-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1837b-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1837b-120">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTP.</span><span class="sxs-lookup"><span data-stu-id="1837b-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="1837b-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="1837b-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="1837b-122">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="1837b-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="1837b-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1837b-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1837b-124">Určuje, zda služba zveřejňuje své WSDL přes HTTPS na adrese kontrolované pomocí `HttpsGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="1837b-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="1837b-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="1837b-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="1837b-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="1837b-126">Data type: string</span></span>  
  
 <span data-ttu-id="1837b-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="1837b-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="1837b-128">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTPS.</span><span class="sxs-lookup"><span data-stu-id="1837b-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1837b-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="1837b-129">Requirements</span></span>  
  
|<span data-ttu-id="1837b-130">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="1837b-130">MOF</span></span>|<span data-ttu-id="1837b-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="1837b-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="1837b-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="1837b-132">Namespace</span></span>|<span data-ttu-id="1837b-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="1837b-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1837b-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1837b-134">See also</span></span>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>

---
title: ServiceMetadataBehavior
ms.date: 03/30/2017
ms.assetid: 0f194476-72f1-467e-bdce-674306316e64
ms.openlocfilehash: 1d99af064205447c2f11f6f19258551c1e88d386
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59160326"
---
# <a name="servicemetadatabehavior"></a><span data-ttu-id="21946-102">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="21946-102">ServiceMetadataBehavior</span></span>
<span data-ttu-id="21946-103">ServiceMetadataBehavior</span><span class="sxs-lookup"><span data-stu-id="21946-103">ServiceMetadataBehavior</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21946-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21946-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="21946-105">Metody</span><span class="sxs-lookup"><span data-stu-id="21946-105">Methods</span></span>  
 <span data-ttu-id="21946-106">Třídu ServiceMetadataBehavior nedefinuje žádné metody.</span><span class="sxs-lookup"><span data-stu-id="21946-106">The ServiceMetadataBehavior class does not define any methods.</span></span>  
  
## <a name="properties"></a><span data-ttu-id="21946-107">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="21946-107">Properties</span></span>  
 <span data-ttu-id="21946-108">Třídu ServiceMetadataBehavior má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="21946-108">The ServiceMetadataBehavior class has the following properties:</span></span>  
  
### <a name="externalmetadatalocation"></a><span data-ttu-id="21946-109">ExternalMetadataLocation</span><span class="sxs-lookup"><span data-stu-id="21946-109">ExternalMetadataLocation</span></span>  
 <span data-ttu-id="21946-110">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="21946-110">Data type: string</span></span>  
  
 <span data-ttu-id="21946-111">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="21946-111">Access type: Read-only</span></span>  
  
 <span data-ttu-id="21946-112">Nastaví umístění, do kterého služba přesměruje požadavky metadat.</span><span class="sxs-lookup"><span data-stu-id="21946-112">Sets the location to which the service redirects metadata requests.</span></span>  
  
### <a name="httpgetenabled"></a><span data-ttu-id="21946-113">HttpGetEnabled</span><span class="sxs-lookup"><span data-stu-id="21946-113">HttpGetEnabled</span></span>  
 <span data-ttu-id="21946-114">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="21946-114">Data type: boolean</span></span>  
  
 <span data-ttu-id="21946-115">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="21946-115">Access type: Read-only</span></span>  
  
 <span data-ttu-id="21946-116">Určuje, zda služba zveřejňuje své WSDL na adrese řídí `HttpGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="21946-116">Controls whether the service publishes its WSDL at the address controlled by the `HttpGetUrl` attribute.</span></span>  
  
### <a name="httpgeturl"></a><span data-ttu-id="21946-117">HttpGetUrl</span><span class="sxs-lookup"><span data-stu-id="21946-117">HttpGetUrl</span></span>  
 <span data-ttu-id="21946-118">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="21946-118">Data type: string</span></span>  
  
 <span data-ttu-id="21946-119">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="21946-119">Access type: Read-only</span></span>  
  
 <span data-ttu-id="21946-120">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTP.</span><span class="sxs-lookup"><span data-stu-id="21946-120">Sets the location at which the service WSDL is published for retrieval using HTTP.</span></span>  
  
### <a name="httpsgetenabled"></a><span data-ttu-id="21946-121">HttpsGetEnabled</span><span class="sxs-lookup"><span data-stu-id="21946-121">HttpsGetEnabled</span></span>  
 <span data-ttu-id="21946-122">Datový typ: boolean</span><span class="sxs-lookup"><span data-stu-id="21946-122">Data type: boolean</span></span>  
  
 <span data-ttu-id="21946-123">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="21946-123">Access type: Read-only</span></span>  
  
 <span data-ttu-id="21946-124">Určuje, zda služba zveřejňuje své WSDL přes HTTPS na adrese kontrolované pomocí `HttpsGetUrl` atribut.</span><span class="sxs-lookup"><span data-stu-id="21946-124">Controls whether the service publishes its WSDL over HTTPS at the address controlled by the `HttpsGetUrl` attribute.</span></span>  
  
### <a name="httpsgeturl"></a><span data-ttu-id="21946-125">HttpsGetUrl</span><span class="sxs-lookup"><span data-stu-id="21946-125">HttpsGetUrl</span></span>  
 <span data-ttu-id="21946-126">Datový typ: řetězec</span><span class="sxs-lookup"><span data-stu-id="21946-126">Data type: string</span></span>  
  
 <span data-ttu-id="21946-127">Typ přístupu: jen pro čtení</span><span class="sxs-lookup"><span data-stu-id="21946-127">Access type: Read-only</span></span>  
  
 <span data-ttu-id="21946-128">Nastaví umístění, kde je služba WSDL zveřejněna k získání pomocí HTTPS.</span><span class="sxs-lookup"><span data-stu-id="21946-128">Sets the location at which the service WSDL is published for retrieval using HTTPS.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="21946-129">Požadavky</span><span class="sxs-lookup"><span data-stu-id="21946-129">Requirements</span></span>  
  
|<span data-ttu-id="21946-130">SOUBOR MOF</span><span class="sxs-lookup"><span data-stu-id="21946-130">MOF</span></span>|<span data-ttu-id="21946-131">Deklarované v Servicemodel.mof.</span><span class="sxs-lookup"><span data-stu-id="21946-131">Declared in Servicemodel.mof.</span></span>|  
|---------|-----------------------------------|  
|<span data-ttu-id="21946-132">Obor názvů</span><span class="sxs-lookup"><span data-stu-id="21946-132">Namespace</span></span>|<span data-ttu-id="21946-133">Definované v root\ServiceModel</span><span class="sxs-lookup"><span data-stu-id="21946-133">Defined in root\ServiceModel</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="21946-134">Viz také:</span><span class="sxs-lookup"><span data-stu-id="21946-134">See also</span></span>

- <xref:System.ServiceModel.Description.ServiceMetadataBehavior>

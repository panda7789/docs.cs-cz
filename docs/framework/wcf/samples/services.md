---
title: Ukázky – WCF Services
ms.date: 03/30/2017
ms.assetid: 462a2218-f8c6-4fb7-95bc-64765459c429
ms.openlocfilehash: 9c4c6c0083a685f2f85b01ed3a5bed377708dd13
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67425455"
---
# <a name="services"></a><span data-ttu-id="a7db9-102">Služby</span><span class="sxs-lookup"><span data-stu-id="a7db9-102">Services</span></span>

<span data-ttu-id="a7db9-103">Tato část obsahuje ukázky, které předvádějí služby Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="a7db9-103">This section contains samples that demonstrate Windows Communication Foundation (WCF) services.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="a7db9-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a7db9-104">In this section</span></span>

- <span data-ttu-id="a7db9-105">[Hosting](../../../../docs/framework/wcf/feature-details/hosting.md)</span><span class="sxs-lookup"><span data-stu-id="a7db9-105">[Hosting](../../../../docs/framework/wcf/feature-details/hosting.md)</span></span>\
<span data-ttu-id="a7db9-106">Ukazuje hostování služby WCF.</span><span class="sxs-lookup"><span data-stu-id="a7db9-106">Demonstrates hosting WCF services.</span></span>

- <span data-ttu-id="a7db9-107">[Vzájemná spolupráce služeb](service-interoperability.md)</span><span class="sxs-lookup"><span data-stu-id="a7db9-107">[Service Interoperability](service-interoperability.md)</span></span>\
<span data-ttu-id="a7db9-108">Ukazuje interakce mezi WCF a další technologie služby.</span><span class="sxs-lookup"><span data-stu-id="a7db9-108">Demonstrates interaction between WCF and other service technologies.</span></span>

- <span data-ttu-id="a7db9-109">[Chování](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="a7db9-109">[Behaviors](behaviors.md)</span></span>\
<span data-ttu-id="a7db9-110">Ukazuje chování služby WCF.</span><span class="sxs-lookup"><span data-stu-id="a7db9-110">Demonstrates WCF service behaviors.</span></span>

- <span data-ttu-id="a7db9-111">[Zabezpečení služby](service-security.md)</span><span class="sxs-lookup"><span data-stu-id="a7db9-111">[Service Security](service-security.md)</span></span>\
<span data-ttu-id="a7db9-112">Ukazuje zabezpečení služby WCF.</span><span class="sxs-lookup"><span data-stu-id="a7db9-112">Demonstrates WCF service security.</span></span>

- <span data-ttu-id="a7db9-113">[Zjednodušená konfigurace pro služby WCF](simplified-configuration-for-wcf-services.md)</span><span class="sxs-lookup"><span data-stu-id="a7db9-113">[Simplified Configuration for WCF Services](simplified-configuration-for-wcf-services.md)</span></span>\
<span data-ttu-id="a7db9-114">Ukazuje, jak implementovat a konfigurovat typické službu a klienta pomocí WCF.</span><span class="sxs-lookup"><span data-stu-id="a7db9-114">Demonstrates how to implement and configure a typical service and client using WCF.</span></span>

- <span data-ttu-id="a7db9-115">[Používání standardních koncových bodů](usage-of-standard-endpoints.md)</span><span class="sxs-lookup"><span data-stu-id="a7db9-115">[Usage of Standard Endpoints](usage-of-standard-endpoints.md)</span></span>\
<span data-ttu-id="a7db9-116">Popisuje způsob použití standardních koncových bodů v konfiguračních souborech služby.</span><span class="sxs-lookup"><span data-stu-id="a7db9-116">Demonstrates how to use standard endpoints in service configuration files.</span></span>

- <span data-ttu-id="a7db9-117">[Zásady rozšířené ochrany](extended-protection-policy.md)</span><span class="sxs-lookup"><span data-stu-id="a7db9-117">[Extended Protection Policy](extended-protection-policy.md)</span></span>\
<span data-ttu-id="a7db9-118">Ukazuje iniciativy zabezpečení pro ochranu před útoky (typu MITM) man-in-the-middle rozšířenou ochranu.</span><span class="sxs-lookup"><span data-stu-id="a7db9-118">Demonstrates Extended Protection, a security initiative for protecting against man-in-the-middle (MITM) attacks.</span></span>

- <span data-ttu-id="a7db9-119">[Objekt pro vytváření kanálů konfigurace](configuration-channel-factory.md)</span><span class="sxs-lookup"><span data-stu-id="a7db9-119">[Configuration Channel Factory](configuration-channel-factory.md)</span></span>\
<span data-ttu-id="a7db9-120">Ukazuje použití <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span><span class="sxs-lookup"><span data-stu-id="a7db9-120">Demonstrates the usage of the <xref:System.ServiceModel.Configuration.ConfigurationChannelFactory%601>.</span></span>

- <span data-ttu-id="a7db9-121">[Adresování](addressing.md)</span><span class="sxs-lookup"><span data-stu-id="a7db9-121">[Addressing](addressing.md)</span></span>\
<span data-ttu-id="a7db9-122">Ukazuje různé aspekty a vlastnosti adresy koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="a7db9-122">Demonstrates various aspects and features of endpoint addresses.</span></span>

- <span data-ttu-id="a7db9-123">[Dnešní](imperative.md)</span><span class="sxs-lookup"><span data-stu-id="a7db9-123">[Imperative](imperative.md)</span></span>\
<span data-ttu-id="a7db9-124">Ukazuje, jak definovat <xref:System.ServiceModel.WSHttpBinding> služby promocí kódu, místo definování `wsHttpBinding` vazby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="a7db9-124">Demonstrates how to define a <xref:System.ServiceModel.WSHttpBinding> for a service using code, instead of defining the `wsHttpBinding` binding in configuration.</span></span>

- <span data-ttu-id="a7db9-125">[Více kontraktů](multiple-contracts.md)</span><span class="sxs-lookup"><span data-stu-id="a7db9-125">[Multiple Contracts](multiple-contracts.md)</span></span>\
<span data-ttu-id="a7db9-126">Ukazuje, jak implementovat více než jeden kontrakt na služby a jak nakonfigurovat koncové body pro komunikaci s každým implementovaných kontraktů.</span><span class="sxs-lookup"><span data-stu-id="a7db9-126">Demonstrates how to implement more than one contract on a service and how to configure endpoints for communicating with each of the implemented contracts.</span></span>

- <span data-ttu-id="a7db9-127">[Více koncových bodů](multiple-endpoints.md)</span><span class="sxs-lookup"><span data-stu-id="a7db9-127">[Multiple Endpoints](multiple-endpoints.md)</span></span>\
<span data-ttu-id="a7db9-128">Ukazuje, jak konfigurovat několik koncových bodů ve službě a komunikovat s každého koncového bodu z klienta.</span><span class="sxs-lookup"><span data-stu-id="a7db9-128">Demonstrates how to configure multiple endpoints on a service and how to communicate with each endpoint from a client.</span></span>

- <span data-ttu-id="a7db9-129">[Víc koncových bodů na jedné adrese ListenUri](multiple-endpoints-at-a-single-listenuri.md)</span><span class="sxs-lookup"><span data-stu-id="a7db9-129">[Multiple Endpoints at a Single ListenUri](multiple-endpoints-at-a-single-listenuri.md)</span></span>\
<span data-ttu-id="a7db9-130">Ukazuje, služby, který je hostitelem více koncových bodů na jedné `ListenUri`.</span><span class="sxs-lookup"><span data-stu-id="a7db9-130">Demonstrates a service that hosts multiple endpoints at a single `ListenUri`.</span></span>

- <span data-ttu-id="a7db9-131">[OperationContextScope](operationcontextscope.md)</span><span class="sxs-lookup"><span data-stu-id="a7db9-131">[OperationContextScope](operationcontextscope.md)</span></span>\
<span data-ttu-id="a7db9-132">Ukazuje, jak odeslat další informace o volání WCF pomocí hlavičky.</span><span class="sxs-lookup"><span data-stu-id="a7db9-132">Demonstrates how to send extra information on a WCF call using headers.</span></span>

- <span data-ttu-id="a7db9-133">[Popis služby](service-description.md)</span><span class="sxs-lookup"><span data-stu-id="a7db9-133">[Service Description](service-description.md)</span></span>\
<span data-ttu-id="a7db9-134">Ukazuje, jak může služba načíst jeho informace popisu služby za běhu.</span><span class="sxs-lookup"><span data-stu-id="a7db9-134">Demonstrates how a service can retrieve its service description information at runtime.</span></span>

- <span data-ttu-id="a7db9-135">[ConcurrencyMode.Reentrant](concurrencymode-reentrant.md)</span><span class="sxs-lookup"><span data-stu-id="a7db9-135">[ConcurrencyMode.Reentrant](concurrencymode-reentrant.md)</span></span>\
<span data-ttu-id="a7db9-136">Popisuje způsob použití vícenásobné souběžný režim na implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="a7db9-136">Demonstrates how to use the Reentrant concurrency mode on a service implementation.</span></span>

---
title: Přehled integrace s aplikacemi modelu COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: 182e5f41498d8f5e3fcbc4b84aa7e86b67ce3ccc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59087622"
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="499a5-102">Přehled integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="499a5-102">Integrating with COM Applications Overview</span></span>
<span data-ttu-id="499a5-103">Windows Communication Foundation (WCF) poskytuje vývojářům spravovaného kódu s bohaté prostředí pro vytváření propojených aplikací.</span><span class="sxs-lookup"><span data-stu-id="499a5-103">Windows Communication Foundation (WCF) provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="499a5-104">Nicméně pokud máte značné investice v nespravovaném kódu na základě modelu COM a nechcete, aby k migraci, můžete stále integrovat webových služeb WCF přímo do vašeho existujícího kódu pomocí monikeru služby WCF.</span><span class="sxs-lookup"><span data-stu-id="499a5-104">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate WCF Web services directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="499a5-105">Moniker služby je možné z široký rozsah COM vývoj prostředí, jako je například Office VBA, Visual Basic 6.0 nebo Visual C++ 6.0.</span><span class="sxs-lookup"><span data-stu-id="499a5-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="499a5-106">Moniker služby používá komunikační kanál WCF pro veškerou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="499a5-106">The service moniker uses a WCF communication channel for all communication.</span></span> <span data-ttu-id="499a5-107">Mechanismy zabezpečení a identity pro tento kanál se liší od těch, které ve standardní proxy modelu COM a DCOM používá.</span><span class="sxs-lookup"><span data-stu-id="499a5-107">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="499a5-108">Navíc vzhledem k tomu monikeru služby používá komunikační kanál WCF výchozího časového limitu je jedna minuta pro všechna volání.</span><span class="sxs-lookup"><span data-stu-id="499a5-108">In addition, because the service moniker uses a WCF communication channel the default timeout period is one minute for all calls.</span></span>  
  
 <span data-ttu-id="499a5-109">Moniker služby se používá s `GetObject` funkce nespravované developer poskytnout přístup silného typu, COM specifické pro volání webových služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="499a5-109">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling WCF Web services.</span></span> <span data-ttu-id="499a5-110">Tento postup vyžaduje místní, viditelný modulem COM definici kontraktu služby WCF Web a vazbu, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="499a5-110">This requires a local, COM-visible definition of the WCF Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="499a5-111">Stejně jako ostatní klienti WCF monikeru služby nezbytné vytvořit zadaný kanál ke službě, i když dojde k vytváření tohoto kanálu transparentně na programátorovi modelu COM, při prvním volání metody.</span><span class="sxs-lookup"><span data-stu-id="499a5-111">Like other WCF clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>  
  
 <span data-ttu-id="499a5-112">Společné s ostatními WCF klienty, při použití monikeru zadejte aplikace, adresa, vazba a kontrakt ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="499a5-112">In common with other WCF clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="499a5-113">Kontrakt lze zadat v jednom z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="499a5-113">The contract can be specified in one of the following ways:</span></span>  
  
-   <span data-ttu-id="499a5-114">Typu kontraktu – smlouvy je zaregistrovaný jako typ viditelné modelu COM v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="499a5-114">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>  
  
-   <span data-ttu-id="499a5-115">Smlouva WSDL – smlouvy se dodává ve formě dokument WSDL.</span><span class="sxs-lookup"><span data-stu-id="499a5-115">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="499a5-116">Smlouva MEX – smlouvy je načten v době běhu z koncového bodu metadat Exchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="499a5-116">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="499a5-117">Parametry nepodporuje Monikeru služby</span><span class="sxs-lookup"><span data-stu-id="499a5-117">Parameters Supported by the Service Moniker</span></span>  
 <span data-ttu-id="499a5-118">V následující tabulce jsou uvedeny parametry, které jsou podporovány monikeru služby.</span><span class="sxs-lookup"><span data-stu-id="499a5-118">The following table shows the parameters that are supported by the service moniker.</span></span>  
  
|<span data-ttu-id="499a5-119">Parametr</span><span class="sxs-lookup"><span data-stu-id="499a5-119">Parameter</span></span>|<span data-ttu-id="499a5-120">Popis</span><span class="sxs-lookup"><span data-stu-id="499a5-120">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="499a5-121">Adresa URL umístění služby.</span><span class="sxs-lookup"><span data-stu-id="499a5-121">URL location of the service.</span></span>|  
|`binding`|<span data-ttu-id="499a5-122">Název oddílu vazby z konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="499a5-122">Binding section name from the application configuration.</span></span>|  
|`bindingConfiguration`|<span data-ttu-id="499a5-123">Instance s názvem vazby z v rámci oddílu s názvem vazby.</span><span class="sxs-lookup"><span data-stu-id="499a5-123">Named binding instance from within the named binding section.</span></span>|  
|`contract`|<span data-ttu-id="499a5-124">Identifikátor rozhraní (IID), která představuje kontraktu služby nebo název kontraktu (ze MEX).</span><span class="sxs-lookup"><span data-stu-id="499a5-124">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|  
|`wsdl`|<span data-ttu-id="499a5-125">Dokument WSDL, který poskytuje alternativní formy definici kontraktu.</span><span class="sxs-lookup"><span data-stu-id="499a5-125">WSDL document that provides an alternative form of contract definition.</span></span>|  
|`spnIdentity`|<span data-ttu-id="499a5-126">Identita serveru hlavní název (SPN) který se má použít ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="499a5-126">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|  
|`upnIdentity`|<span data-ttu-id="499a5-127">Hlavní název (UPN) identity uživatele se použije ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="499a5-127">User principal name (UPN) identity to be used to communicate with the service.</span></span>|  
|`dnsIdentity`|<span data-ttu-id="499a5-128">Identitu DNS, který se má použít ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="499a5-128">DNS identity to be used to communicate with the service.</span></span>|  
|`mexAddress`|<span data-ttu-id="499a5-129">Adresa URL umístění metadat Exchange (MEX) koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="499a5-129">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|  
|`mexBinding`|<span data-ttu-id="499a5-130">Název oddílu vazby z konfigurace aplikace pro připojení ke koncovému bodu MEX.</span><span class="sxs-lookup"><span data-stu-id="499a5-130">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|  
|`mexBindingConfiguration`|<span data-ttu-id="499a5-131">Instance s názvem vazby z v rámci oddílu s názvem vazby pro připojení ke koncovému bodu MEX.</span><span class="sxs-lookup"><span data-stu-id="499a5-131">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|  
|`bindingNamespace`|<span data-ttu-id="499a5-132">Namespace názvu oddílu vazby z načtené MEX</span><span class="sxs-lookup"><span data-stu-id="499a5-132">Namespace of the binding section name from the retrieved MEX.</span></span>|  
|`contractNamespace`|<span data-ttu-id="499a5-133">Namespace kontraktu v MEX načtené</span><span class="sxs-lookup"><span data-stu-id="499a5-133">Namespace of the contract from the retrieved MEX.</span></span>|  
|`mexSpnIdentity`|<span data-ttu-id="499a5-134">Identita serveru hlavní název (SPN) který se má použít ke komunikaci s koncovým bodem MEX.</span><span class="sxs-lookup"><span data-stu-id="499a5-134">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexUpnIdentity`|<span data-ttu-id="499a5-135">Hlavní název (UPN) identity uživatele se použije ke komunikaci s koncovým bodem MEX.</span><span class="sxs-lookup"><span data-stu-id="499a5-135">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexDnsIdentity`|<span data-ttu-id="499a5-136">Identitu DNS, který se má použít ke komunikaci s koncovým bodem MEX.</span><span class="sxs-lookup"><span data-stu-id="499a5-136">DNS identity to be used to communicate with the MEX endpoint.</span></span>|  
|`serializer`|<span data-ttu-id="499a5-137">Vyžaduje použití aplikace "xml" nebo "kontraktu dat datacontract" serializátor.</span><span class="sxs-lookup"><span data-stu-id="499a5-137">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="499a5-138">I když používají klienti zcela založená na modelu COM, vyžaduje monikeru služby WCF a podpory .NET Framework 2.0 nainstalované v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="499a5-138">Even when used with entirely COM-based clients, the service moniker requires WCF and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="499a5-139">Je velmi důležité, aby klientské aplikace, které použití monikeru služby načíst příslušnou verzi modulu runtime rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="499a5-139">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="499a5-140">Při použití monikeru v rámci aplikace Office, může být nutný k zajištění, že je načtena správná framework verze konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="499a5-140">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="499a5-141">Například s Excelem, následující text by měl umístit do souboru s názvem Excel.exe.config ve stejném adresáři jako soubor Excel.exe:</span><span class="sxs-lookup"><span data-stu-id="499a5-141">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  <span data-ttu-id="499a5-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="499a5-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a><span data-ttu-id="499a5-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="499a5-143">See also</span></span>

- [<span data-ttu-id="499a5-144">Postupy: Registrace a konfigurace Monikeru služby</span><span class="sxs-lookup"><span data-stu-id="499a5-144">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)

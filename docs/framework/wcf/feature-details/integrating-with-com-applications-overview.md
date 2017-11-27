---
title: "Přehled integrace s aplikacemi modelu COM"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4e995fc66a925cb0ebe272c9dceca1ba63b9459d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="abffd-102">Přehled integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="abffd-102">Integrating with COM Applications Overview</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="abffd-103">bohaté prostředí pro vytváření propojených aplikací poskytuje vývojářům spravovaného kódu.</span><span class="sxs-lookup"><span data-stu-id="abffd-103"> provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="abffd-104">Ale pokud máte významné investice v nespravovaném kódu založené na modelu COM a nechcete, aby k migraci, můžete stále integrovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] webové služby přímo do existujícího kódu pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] monikeru služby.</span><span class="sxs-lookup"><span data-stu-id="abffd-104">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web services directly into your existing code by using the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service moniker.</span></span> <span data-ttu-id="abffd-105">Monikeru služby lze použít z celý na základě rozsahu COM vývojových prostředí, například Office VBA, Visual Basic 6.0 nebo Visual C++ verze 6.0.</span><span class="sxs-lookup"><span data-stu-id="abffd-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="abffd-106">Používá monikeru služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komunikační kanál pro veškerou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="abffd-106">The service moniker uses a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] communication channel for all communication.</span></span> <span data-ttu-id="abffd-107">Mechanismy zabezpečení a identita pro tento kanál se liší od těch, které používá v standardní COM a modelu DCOM proxy.</span><span class="sxs-lookup"><span data-stu-id="abffd-107">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="abffd-108">Kromě toho protože používá monikeru služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komunikační kanál výchozího časového limitu je jedna minuta pro všechna volání.</span><span class="sxs-lookup"><span data-stu-id="abffd-108">In addition, because the service moniker uses a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] communication channel the default timeout period is one minute for all calls.</span></span>  
  
 <span data-ttu-id="abffd-109">Monikeru služby se používá s `GetObject` funkce nespravované vývojáře poskytnout přístup silného typu, COM specifické pro volání [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] webové služby.</span><span class="sxs-lookup"><span data-stu-id="abffd-109">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web services.</span></span> <span data-ttu-id="abffd-110">To vyžaduje, aby definice místní, COM – viditelné [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] webového kontrakt služby a vazby, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="abffd-110">This requires a local, COM-visible definition of the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="abffd-111">Stejně jako jiné [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienty, monikeru služby musí vytvořit typové kanál ke službě, i když tento kanál konstrukce transparentně dojde k programátory COM při prvním volání metoda.</span><span class="sxs-lookup"><span data-stu-id="abffd-111">Like other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>  
  
 <span data-ttu-id="abffd-112">Společné s další [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientů, při použití přezdívka, aplikace zadejte adresy, vazby a smlouvy ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="abffd-112">In common with other [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="abffd-113">Kontrakt lze zadat v jednom z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="abffd-113">The contract can be specified in one of the following ways:</span></span>  
  
-   <span data-ttu-id="abffd-114">Typové kontrakt – kontrakt je zaregistrován jako typ viditelné modelu COM v klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="abffd-114">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>  
  
-   <span data-ttu-id="abffd-115">Kontrakt WSDL – kontrakt poskytuje ve formě dokumentu WSDL.</span><span class="sxs-lookup"><span data-stu-id="abffd-115">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>  
  
-   <span data-ttu-id="abffd-116">Kontrakt MEX – kontrakt se načte v době běhu z koncového bodu metadat Exchange (MEX).</span><span class="sxs-lookup"><span data-stu-id="abffd-116">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>  
  
## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="abffd-117">Parametry nepodporuje Monikeru služby</span><span class="sxs-lookup"><span data-stu-id="abffd-117">Parameters Supported by the Service Moniker</span></span>  
 <span data-ttu-id="abffd-118">V následující tabulce jsou uvedeny parametry, které jsou podporovány monikeru služby.</span><span class="sxs-lookup"><span data-stu-id="abffd-118">The following table shows the parameters that are supported by the service moniker.</span></span>  
  
|<span data-ttu-id="abffd-119">Parametr</span><span class="sxs-lookup"><span data-stu-id="abffd-119">Parameter</span></span>|<span data-ttu-id="abffd-120">Popis</span><span class="sxs-lookup"><span data-stu-id="abffd-120">Description</span></span>|  
|---------------|-----------------|  
|`address`|<span data-ttu-id="abffd-121">Adresa URL umístění služby.</span><span class="sxs-lookup"><span data-stu-id="abffd-121">URL location of the service.</span></span>|  
|`binding`|<span data-ttu-id="abffd-122">Název oddílu vazby v konfiguraci aplikace.</span><span class="sxs-lookup"><span data-stu-id="abffd-122">Binding section name from the application configuration.</span></span>|  
|`bindingConfiguration`|<span data-ttu-id="abffd-123">Vazba s názvem instance z v části s názvem vazby.</span><span class="sxs-lookup"><span data-stu-id="abffd-123">Named binding instance from within the named binding section.</span></span>|  
|`contract`|<span data-ttu-id="abffd-124">Rozhraní identifikátor (IID), který představuje kontrakt služby nebo název kontraktu (z MEX).</span><span class="sxs-lookup"><span data-stu-id="abffd-124">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|  
|`wsdl`|<span data-ttu-id="abffd-125">WSDL dokument, který poskytuje alternativní forma definici kontraktu.</span><span class="sxs-lookup"><span data-stu-id="abffd-125">WSDL document that provides an alternative form of contract definition.</span></span>|  
|`spnIdentity`|<span data-ttu-id="abffd-126">Identita serveru hlavní název (SPN) pro použití ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="abffd-126">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|  
|`upnIdentity`|<span data-ttu-id="abffd-127">Identita hlavní název (UPN) uživatele, které bude použito ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="abffd-127">User principal name (UPN) identity to be used to communicate with the service.</span></span>|  
|`dnsIdentity`|<span data-ttu-id="abffd-128">Identita DNS, které bude použito ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="abffd-128">DNS identity to be used to communicate with the service.</span></span>|  
|`mexAddress`|<span data-ttu-id="abffd-129">Umístění URL metadat Exchange (MEX) koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="abffd-129">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|  
|`mexBinding`|<span data-ttu-id="abffd-130">Z konfigurace aplikace pro připojení ke koncovému bodu MEX vazby název oddílu.</span><span class="sxs-lookup"><span data-stu-id="abffd-130">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|  
|`mexBindingConfiguration`|<span data-ttu-id="abffd-131">Vazba s názvem instance z v části s názvem vazby pro připojení ke koncovému bodu MEX.</span><span class="sxs-lookup"><span data-stu-id="abffd-131">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|  
|`bindingNamespace`|<span data-ttu-id="abffd-132">Namespace název oddílu vazba z načtené MEX</span><span class="sxs-lookup"><span data-stu-id="abffd-132">Namespace of the binding section name from the retrieved MEX.</span></span>|  
|`contractNamespace`|<span data-ttu-id="abffd-133">Namespace kontraktu z načtené MEX</span><span class="sxs-lookup"><span data-stu-id="abffd-133">Namespace of the contract from the retrieved MEX.</span></span>|  
|`mexSpnIdentity`|<span data-ttu-id="abffd-134">Identity hlavní název (SPN) serveru, které bude použito ke komunikaci s koncovým bodem MEX.</span><span class="sxs-lookup"><span data-stu-id="abffd-134">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexUpnIdentity`|<span data-ttu-id="abffd-135">Identita hlavní název (UPN) uživatele, které bude použito ke komunikaci s koncovým bodem MEX.</span><span class="sxs-lookup"><span data-stu-id="abffd-135">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|  
|`mexDnsIdentity`|<span data-ttu-id="abffd-136">Identita DNS, které bude použito ke komunikaci s koncovým bodem MEX.</span><span class="sxs-lookup"><span data-stu-id="abffd-136">DNS identity to be used to communicate with the MEX endpoint.</span></span>|  
|`serializer`|<span data-ttu-id="abffd-137">Zadejte buď "xml" nebo "kontraktu" serializátor použití.</span><span class="sxs-lookup"><span data-stu-id="abffd-137">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|  
  
> [!NOTE]
>  <span data-ttu-id="abffd-138">I když používají s klienty zcela založená na modelu COM, vyžaduje monikeru služby [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a podpůrné rozhraní .NET Framework 2.0 k instalaci na klientském počítači.</span><span class="sxs-lookup"><span data-stu-id="abffd-138">Even when used with entirely COM-based clients, the service moniker requires [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="abffd-139">Je také důležité, aby klientských aplikací, které použití monikeru služby načíst příslušnou verzi modulu runtime rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="abffd-139">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="abffd-140">Při použití monikeru v rámci aplikace Office, může být nutný k zajištění, že je načteno správnou verzi konfiguračního souboru.</span><span class="sxs-lookup"><span data-stu-id="abffd-140">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="abffd-141">Například v aplikaci Excel, musí být umístěny následující text v souboru s názvem Excel.exe.config ve stejném adresáři jako soubor Excel.exe:</span><span class="sxs-lookup"><span data-stu-id="abffd-141">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>  
>   
>  `<?xml version="1.0" encoding="utf-8"?>`  
>   
>  <span data-ttu-id="abffd-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="abffd-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>  
>   
>  `<startup>`  
>   
>  `<requiredRuntime version="v2.0.50727" />`  
>   
>  `</startup>`  
>   
>  `</configuration>`  
  
## <a name="see-also"></a><span data-ttu-id="abffd-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="abffd-143">See Also</span></span>  
 [<span data-ttu-id="abffd-144">Postupy: registrace a konfigurace Monikeru služby</span><span class="sxs-lookup"><span data-stu-id="abffd-144">How to: Register and Configure a Service Moniker</span></span>](../../../../docs/framework/wcf/feature-details/how-to-register-and-configure-a-service-moniker.md)

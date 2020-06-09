---
title: Přehled integrace s aplikacemi modelu COM
ms.date: 03/30/2017
helpviewer_keywords:
- COM [WCF], integration overview
ms.assetid: 02c5697f-6e2e-47d6-b715-f3a28aebfbd5
ms.openlocfilehash: c283e7cbc4cb4b8bc37dd1313480410df93a93bf
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84596822"
---
# <a name="integrating-with-com-applications-overview"></a><span data-ttu-id="c68be-102">Přehled integrace s aplikacemi modelu COM</span><span class="sxs-lookup"><span data-stu-id="c68be-102">Integrating with COM Applications Overview</span></span>

<span data-ttu-id="c68be-103">Windows Communication Foundation (WCF) poskytuje vývojářům spravovaného kódu prostředí s bohatým prostředím pro vytváření připojených aplikací.</span><span class="sxs-lookup"><span data-stu-id="c68be-103">Windows Communication Foundation (WCF) provides the managed code developer with a rich environment for creating connected applications.</span></span> <span data-ttu-id="c68be-104">Nicméně pokud máte významnou investici do nespravovaného kódu založeného na modelu COM a nechcete migrovat, můžete i nadále integrovat webové služby WCF přímo do stávajícího kódu pomocí monikeru služby WCF.</span><span class="sxs-lookup"><span data-stu-id="c68be-104">However, if you have a substantial investment in unmanaged COM-based code and do not want to migrate, you can still integrate WCF Web services directly into your existing code by using the WCF service moniker.</span></span> <span data-ttu-id="c68be-105">Moniker služby lze použít z široké škály vývojových prostředí založených na modelu COM, jako je například Office VBA, Visual Basic 6,0 nebo Visual C++ 6,0.</span><span class="sxs-lookup"><span data-stu-id="c68be-105">The service moniker can be used from a wide range of COM-based development environments, such as Office VBA, Visual Basic 6.0, or Visual C++ 6.0.</span></span>

> [!NOTE]
> <span data-ttu-id="c68be-106">Moniker služby používá komunikační kanál WCF pro veškerou komunikaci.</span><span class="sxs-lookup"><span data-stu-id="c68be-106">The service moniker uses a WCF communication channel for all communication.</span></span> <span data-ttu-id="c68be-107">Mechanismy zabezpečení a identity pro tento kanál se liší od těch, které se používají ve standardních proxy serverech COM a DCOM.</span><span class="sxs-lookup"><span data-stu-id="c68be-107">The security and identity mechanisms for that channel differ from those used in standard COM and DCOM proxies.</span></span> <span data-ttu-id="c68be-108">Kromě toho, protože moniker služby používá komunikační kanál WCF, je výchozí časový limit jedna minuta pro všechna volání.</span><span class="sxs-lookup"><span data-stu-id="c68be-108">In addition, because the service moniker uses a WCF communication channel the default timeout period is one minute for all calls.</span></span>

<span data-ttu-id="c68be-109">Moniker služby se používá spolu s `GetObject` funkcí k poskytnutí nespravovaného vývojáře se silným typem, který je specifický pro rozhraní COM pro volání webových služeb WCF.</span><span class="sxs-lookup"><span data-stu-id="c68be-109">The service moniker is used with the `GetObject` function to provide the unmanaged developer with a strongly-typed, COM-specific approach for calling WCF Web services.</span></span> <span data-ttu-id="c68be-110">To vyžaduje místní definici kontraktu webové služby WCF, která je viditelná v modelu COM, a vazbu, která se má použít.</span><span class="sxs-lookup"><span data-stu-id="c68be-110">This requires a local, COM-visible definition of the WCF Web service contract and the binding that is to be used.</span></span> <span data-ttu-id="c68be-111">Podobně jako ostatní klienti WCF musí moniker služby pro službu vytvořit typový kanál, i když se tato konstrukce kanálu transparentně nacházela programátorům COM při prvním volání metody.</span><span class="sxs-lookup"><span data-stu-id="c68be-111">Like other WCF clients, the service moniker must construct a typed channel to the service, though this channel construction occurs transparently to the COM programmer on the first method call.</span></span>

<span data-ttu-id="c68be-112">V běžných případech s jinými klienty WCF při použití monikeru aplikace určují adresu, vazbu a kontrakt ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="c68be-112">In common with other WCF clients, when using the moniker, applications specify the address, binding and contract to communicate with a service.</span></span> <span data-ttu-id="c68be-113">Kontrakt lze zadat jedním z následujících způsobů:</span><span class="sxs-lookup"><span data-stu-id="c68be-113">The contract can be specified in one of the following ways:</span></span>

- <span data-ttu-id="c68be-114">Typ kontraktu – kontrakt se na klientském počítači zaregistruje jako viditelný typ modelu COM.</span><span class="sxs-lookup"><span data-stu-id="c68be-114">Typed contract – the contract is registered as a COM visible type on the client machine.</span></span>

- <span data-ttu-id="c68be-115">Smlouva WSDL – smlouva je dodávána ve formě dokumentu WSDL.</span><span class="sxs-lookup"><span data-stu-id="c68be-115">WSDL contract – the contract is supplied in the form of a WSDL document.</span></span>

- <span data-ttu-id="c68be-116">Služba MEX – kontrakt se načítá za běhu z koncového bodu výměny metadat (MEX).</span><span class="sxs-lookup"><span data-stu-id="c68be-116">MEX contract – the contract is retrieved at runtime from a Metadata Exchange (MEX) endpoint.</span></span>

## <a name="parameters-supported-by-the-service-moniker"></a><span data-ttu-id="c68be-117">Parametry podporované Monikerem služby</span><span class="sxs-lookup"><span data-stu-id="c68be-117">Parameters Supported by the Service Moniker</span></span>

<span data-ttu-id="c68be-118">V následující tabulce jsou uvedeny parametry, které jsou podporovány monikerem služby.</span><span class="sxs-lookup"><span data-stu-id="c68be-118">The following table shows the parameters that are supported by the service moniker.</span></span>

|<span data-ttu-id="c68be-119">Parametr</span><span class="sxs-lookup"><span data-stu-id="c68be-119">Parameter</span></span>|<span data-ttu-id="c68be-120">Popis</span><span class="sxs-lookup"><span data-stu-id="c68be-120">Description</span></span>|
|---------------|-----------------|
|`address`|<span data-ttu-id="c68be-121">Umístění adresy URL služby.</span><span class="sxs-lookup"><span data-stu-id="c68be-121">URL location of the service.</span></span>|
|`binding`|<span data-ttu-id="c68be-122">Název oddílu vazby z konfigurace aplikace.</span><span class="sxs-lookup"><span data-stu-id="c68be-122">Binding section name from the application configuration.</span></span>|
|`bindingConfiguration`|<span data-ttu-id="c68be-123">Pojmenovaná instance vazby v rámci pojmenované vazby oddílu.</span><span class="sxs-lookup"><span data-stu-id="c68be-123">Named binding instance from within the named binding section.</span></span>|
|`contract`|<span data-ttu-id="c68be-124">Identifikátor rozhraní (IID), který představuje kontrakt služby nebo název kontraktu (ze MEX).</span><span class="sxs-lookup"><span data-stu-id="c68be-124">Interface identifier (IID) that represents the service contract or the contract name (from MEX).</span></span>|
|`wsdl`|<span data-ttu-id="c68be-125">Dokument WSDL, který poskytuje alternativní formu definice smlouvy.</span><span class="sxs-lookup"><span data-stu-id="c68be-125">WSDL document that provides an alternative form of contract definition.</span></span>|
|`spnIdentity`|<span data-ttu-id="c68be-126">Identita hlavního názvu serveru (SPN), která se má použít ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="c68be-126">Server principal name (SPN) identity to be used to communicate with the service.</span></span>|
|`upnIdentity`|<span data-ttu-id="c68be-127">Identita hlavního názvu uživatele (UPN), která se má použít ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="c68be-127">User principal name (UPN) identity to be used to communicate with the service.</span></span>|
|`dnsIdentity`|<span data-ttu-id="c68be-128">Identita DNS, která se má použít ke komunikaci se službou.</span><span class="sxs-lookup"><span data-stu-id="c68be-128">DNS identity to be used to communicate with the service.</span></span>|
|`mexAddress`|<span data-ttu-id="c68be-129">Umístění adresy URL koncového bodu výměny metadat (MEX) služby.</span><span class="sxs-lookup"><span data-stu-id="c68be-129">URL location of the Metadata Exchange (MEX) endpoint of the service.</span></span>|
|`mexBinding`|<span data-ttu-id="c68be-130">Název oddílu vazby z konfigurace aplikace pro připojení ke koncovému bodu MEX.</span><span class="sxs-lookup"><span data-stu-id="c68be-130">Binding section name from the application configuration to connect with the MEX endpoint.</span></span>|
|`mexBindingConfiguration`|<span data-ttu-id="c68be-131">Pojmenovaná instance vazby z pojmenovaného oddílu vazby pro připojení ke koncovému bodu MEX.</span><span class="sxs-lookup"><span data-stu-id="c68be-131">Named binding instance from within the named binding section to connect with the MEX endpoint.</span></span>|
|`bindingNamespace`|<span data-ttu-id="c68be-132">Obor názvů názvu oddílu vazby z načteného MEX</span><span class="sxs-lookup"><span data-stu-id="c68be-132">Namespace of the binding section name from the retrieved MEX.</span></span>|
|`contractNamespace`|<span data-ttu-id="c68be-133">Obor názvů kontraktu z načteného MEX</span><span class="sxs-lookup"><span data-stu-id="c68be-133">Namespace of the contract from the retrieved MEX.</span></span>|
|`mexSpnIdentity`|<span data-ttu-id="c68be-134">Identita hlavního názvu serveru (SPN), která se má použít ke komunikaci s koncovým bodem MEX.</span><span class="sxs-lookup"><span data-stu-id="c68be-134">Server principal name (SPN) identity to be used to communicate with the MEX endpoint.</span></span>|
|`mexUpnIdentity`|<span data-ttu-id="c68be-135">Identita hlavního názvu uživatele (UPN), která se má použít ke komunikaci s koncovým bodem MEX.</span><span class="sxs-lookup"><span data-stu-id="c68be-135">User principal name (UPN) identity to be used to communicate with the MEX endpoint.</span></span>|
|`mexDnsIdentity`|<span data-ttu-id="c68be-136">Identita DNS, která se má použít ke komunikaci s koncovým bodem MEX.</span><span class="sxs-lookup"><span data-stu-id="c68be-136">DNS identity to be used to communicate with the MEX endpoint.</span></span>|
|`serializer`|<span data-ttu-id="c68be-137">Zadejte použití serializátoru "XML" nebo "DataContract".</span><span class="sxs-lookup"><span data-stu-id="c68be-137">Specify the use of either the "xml" or "datacontract" serializer.</span></span>|

> [!NOTE]
> <span data-ttu-id="c68be-138">I v případě, že se používá výhradně u klientů založených na modelu COM, moniker služby vyžaduje službu WCF a podporu .NET Framework 2,0 pro instalaci do klientského počítače.</span><span class="sxs-lookup"><span data-stu-id="c68be-138">Even when used with entirely COM-based clients, the service moniker requires WCF and the supporting .NET Framework 2.0 to be installed on the client computer.</span></span> <span data-ttu-id="c68be-139">Je také důležité, aby klientské aplikace, které používají moniker služby, načetly příslušnou verzi .NET Framework runtime.</span><span class="sxs-lookup"><span data-stu-id="c68be-139">It is also critical that client applications that use the service moniker load the appropriate version of the .NET Framework runtime.</span></span> <span data-ttu-id="c68be-140">Při použití monikeru v aplikacích Office může být vyžadován konfigurační soubor, aby bylo zajištěno, že bude načtena správná verze rozhraní.</span><span class="sxs-lookup"><span data-stu-id="c68be-140">When using the moniker within Office applications, a configuration file may be required to ensure that the correct framework version is loaded.</span></span> <span data-ttu-id="c68be-141">Například v aplikaci Excel by měl být následující text umístěn do souboru s názvem Excel. exe. config ve stejném adresáři jako soubor aplikace Excel. exe:</span><span class="sxs-lookup"><span data-stu-id="c68be-141">For example, with Excel, the following text should be placed in a file called Excel.exe.config in the same directory as the Excel.exe file:</span></span>
>
> `<?xml version="1.0" encoding="utf-8"?>`
>
> <span data-ttu-id="c68be-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span><span class="sxs-lookup"><span data-stu-id="c68be-142">`<configuration xmlns=` `http://schemas.microsoft.com/.NetConfiguration/v2.0` `>`</span></span>
>
> `<startup>`
>
> `<requiredRuntime version="v2.0.50727" />`
>
> `</startup>`
>
> `</configuration>`

## <a name="see-also"></a><span data-ttu-id="c68be-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="c68be-143">See also</span></span>

- [<span data-ttu-id="c68be-144">Postupy: Registrace a konfigurace monikeru služby</span><span class="sxs-lookup"><span data-stu-id="c68be-144">How to: Register and Configure a Service Moniker</span></span>](how-to-register-and-configure-a-service-moniker.md)

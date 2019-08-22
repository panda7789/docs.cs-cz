---
title: <servicePointManager> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: a6a40d97bf16a3125452311e7762617e657ca384
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659143"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="b1d4e-102">\<Třída ServicePointManager – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="b1d4e-102">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="b1d4e-103">Nakonfiguruje připojení k síťovým prostředkům.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-103">Configures connections to network resources.</span></span>  
  
 <span data-ttu-id="b1d4e-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b1d4e-104">\<configuration></span></span>  
<span data-ttu-id="b1d4e-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b1d4e-105">\<system.net></span></span>  
<span data-ttu-id="b1d4e-106">\<Nastavení ></span><span class="sxs-lookup"><span data-stu-id="b1d4e-106">\<settings></span></span>  
<span data-ttu-id="b1d4e-107">\<servicePointManager></span><span class="sxs-lookup"><span data-stu-id="b1d4e-107">\<servicePointManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1d4e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b1d4e-108">Syntax</span></span>  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b1d4e-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b1d4e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b1d4e-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b1d4e-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="b1d4e-111">Attributes</span></span>  
  
|<span data-ttu-id="b1d4e-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="b1d4e-112">**Attribute**</span></span>|<span data-ttu-id="b1d4e-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b1d4e-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="b1d4e-114">Určuje, zda má systém před použitím certifikátu ověřit, zda název certifikátu odpovídá názvu hostitele serveru.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-114">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="b1d4e-115">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-115">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="b1d4e-116">Určuje, zda má systém před použitím certifikátu ověřit, zda byl certifikát odvolán.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-116">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="b1d4e-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-117">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="b1d4e-118">Určuje, jak dlouho se překlad služby DNS (Domain Name Service) ukládá do mezipaměti v kombinaci s možností kruhové dotazování DNS (v milisekundách).</span><span class="sxs-lookup"><span data-stu-id="b1d4e-118">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="b1d4e-119">Výchozí hodnota je 120 000 milisekund (dvě minuty).</span><span class="sxs-lookup"><span data-stu-id="b1d4e-119">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="b1d4e-120">Určuje, jestli překlad DNS názvů hostitelů s více adresami Internet Protocol (IP) vrací všechny adresy, nebo jenom první z nich.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-120">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="b1d4e-121">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-121">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="b1d4e-122">Určuje zásady šifrování použité pro relaci SSL/TLS na <xref:System.Net.ServicePointManager> instanci.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-122">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="b1d4e-123">Možné hodnoty jsou ekvivalentní hodnotám pro <xref:System.Net.Security.EncryptionPolicy> výčet.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-123">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="b1d4e-124">Pokud je zásada <xref:System.Security.Authentication.CipherAlgorithmType.Null> šifrování nastavena na `NoEncryption`hodnotu, použití je povinné.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-124">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="b1d4e-125">Výchozí hodnota je `RequireEncryption`.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-125">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="b1d4e-126">Určuje, zda by metody post měly očekávat `100-continue` odpověď ze serveru.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-126">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="b1d4e-127">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-127">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="b1d4e-128">Určuje, jestli připojení řízená správcem servisního bodu používají algoritmus Nagle.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-128">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="b1d4e-129">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-129">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b1d4e-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b1d4e-130">Child Elements</span></span>  
 <span data-ttu-id="b1d4e-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="b1d4e-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b1d4e-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b1d4e-132">Parent Elements</span></span>  
  
|<span data-ttu-id="b1d4e-133">**Element**</span><span class="sxs-lookup"><span data-stu-id="b1d4e-133">**Element**</span></span>|<span data-ttu-id="b1d4e-134">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b1d4e-134">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b1d4e-135">Nastavení</span><span class="sxs-lookup"><span data-stu-id="b1d4e-135">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="b1d4e-136">Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="b1d4e-136">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b1d4e-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b1d4e-137">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b1d4e-138">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="b1d4e-138">Configuration Files</span></span>  
 <span data-ttu-id="b1d4e-139">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b1d4e-139">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b1d4e-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b1d4e-140">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="b1d4e-141">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="b1d4e-141">Network Settings Schema</span></span>](index.md)

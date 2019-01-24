---
title: '&lt;servicePointManager&gt; Element (Network Settings)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: e30d38e3b925283b6048730aef2acc865be755b6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54651614"
---
# <a name="ltservicepointmanagergt-element-network-settings"></a><span data-ttu-id="5c341-102">&lt;servicePointManager&gt; Element (Network Settings)</span><span class="sxs-lookup"><span data-stu-id="5c341-102">&lt;servicePointManager&gt; Element (Network Settings)</span></span>
<span data-ttu-id="5c341-103">Nakonfiguruje připojení k síťovým prostředkům.</span><span class="sxs-lookup"><span data-stu-id="5c341-103">Configures connections to network resources.</span></span>  
  
 <span data-ttu-id="5c341-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="5c341-104">\<configuration></span></span>  
<span data-ttu-id="5c341-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="5c341-105">\<system.net></span></span>  
<span data-ttu-id="5c341-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="5c341-106">\<settings></span></span>  
<span data-ttu-id="5c341-107">\<servicePointManager></span><span class="sxs-lookup"><span data-stu-id="5c341-107">\<servicePointManager></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c341-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5c341-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c341-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5c341-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5c341-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5c341-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c341-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="5c341-111">Attributes</span></span>  
  
|<span data-ttu-id="5c341-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="5c341-112">**Attribute**</span></span>|<span data-ttu-id="5c341-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="5c341-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="5c341-114">Určuje, zda systém měli ověřit, název certifikátu odpovídá názvu hostitele serveru před použitím certifikátu.</span><span class="sxs-lookup"><span data-stu-id="5c341-114">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="5c341-115">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="5c341-115">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="5c341-116">Určuje, zda systém by měl kontrolovat, jestli certifikát byl odvolán. před použitím certifikátu.</span><span class="sxs-lookup"><span data-stu-id="5c341-116">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="5c341-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="5c341-117">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="5c341-118">Určuje, jak dlouho služby DNS (Domain Name) jsou uložené v mezipaměti řešení ve spojení s parametrem kruhové dotazování DNS v milisekundách.</span><span class="sxs-lookup"><span data-stu-id="5c341-118">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="5c341-119">Výchozí hodnota je 120 000 milisekund (dvě minuty).</span><span class="sxs-lookup"><span data-stu-id="5c341-119">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="5c341-120">Určuje, zda rozlišení DNS hostitele názvy s více adres Internet Protocol (IP) vrácená všechny adresy, nebo jenom první shoda.</span><span class="sxs-lookup"><span data-stu-id="5c341-120">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="5c341-121">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="5c341-121">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="5c341-122">Určuje zásady šifrování použít relaci protokolu SSL/TLS na <xref:System.Net.ServicePointManager> instance.</span><span class="sxs-lookup"><span data-stu-id="5c341-122">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="5c341-123">Možné hodnoty jsou ekvivalentem hodnoty <xref:System.Net.Security.EncryptionPolicy> výčtu.</span><span class="sxs-lookup"><span data-stu-id="5c341-123">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="5c341-124">Použití <xref:System.Security.Authentication.CipherAlgorithmType.Null> se vyžaduje při šifrování zásady nastavíte `NoEncryption`.</span><span class="sxs-lookup"><span data-stu-id="5c341-124">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="5c341-125">Výchozí hodnota je `RequireEncryption`.</span><span class="sxs-lookup"><span data-stu-id="5c341-125">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="5c341-126">Určuje, zda metody POST by měla by se měl zobrazit `100-continue` odpověď ze serveru.</span><span class="sxs-lookup"><span data-stu-id="5c341-126">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="5c341-127">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="5c341-127">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="5c341-128">Určuje, zda připojení řídí správce bodu služby používat Nagle algoritmus.</span><span class="sxs-lookup"><span data-stu-id="5c341-128">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="5c341-129">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="5c341-129">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c341-130">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5c341-130">Child Elements</span></span>  
 <span data-ttu-id="5c341-131">Žádné</span><span class="sxs-lookup"><span data-stu-id="5c341-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c341-132">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5c341-132">Parent Elements</span></span>  
  
|<span data-ttu-id="5c341-133">**Element**</span><span class="sxs-lookup"><span data-stu-id="5c341-133">**Element**</span></span>|<span data-ttu-id="5c341-134">**Popis**</span><span class="sxs-lookup"><span data-stu-id="5c341-134">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5c341-135">Nastavení</span><span class="sxs-lookup"><span data-stu-id="5c341-135">Settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="5c341-136">Nakonfiguruje možnosti základní sítě pro <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="5c341-136">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5c341-137">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5c341-137">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5c341-138">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="5c341-138">Configuration Files</span></span>  
 <span data-ttu-id="5c341-139">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="5c341-139">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5c341-140">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5c341-140">See also</span></span>
- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="5c341-141">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="5c341-141">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

---
title: <servicePointManager> – element (nastavení sítě)
description: <servicePointManager>Prvek nastavení sítě konfiguruje připojení k možnostem síťových prostředků v .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: eb27716ec7c2936f32a7e4d4c983d1e175c4d044
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504521"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="85ebb-103">\<servicePointManager> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="85ebb-103">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="85ebb-104">Nakonfiguruje připojení k síťovým prostředkům.</span><span class="sxs-lookup"><span data-stu-id="85ebb-104">Configures connections to network resources.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**

## <a name="syntax"></a><span data-ttu-id="85ebb-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="85ebb-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85ebb-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="85ebb-106">Attributes and Elements</span></span>  
 <span data-ttu-id="85ebb-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="85ebb-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85ebb-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="85ebb-108">Attributes</span></span>  
  
|<span data-ttu-id="85ebb-109">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="85ebb-109">**Attribute**</span></span>|<span data-ttu-id="85ebb-110">**Popis**</span><span class="sxs-lookup"><span data-stu-id="85ebb-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="85ebb-111">Určuje, zda má systém před použitím certifikátu ověřit, zda název certifikátu odpovídá názvu hostitele serveru.</span><span class="sxs-lookup"><span data-stu-id="85ebb-111">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="85ebb-112">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="85ebb-112">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="85ebb-113">Určuje, zda má systém před použitím certifikátu ověřit, zda byl certifikát odvolán.</span><span class="sxs-lookup"><span data-stu-id="85ebb-113">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="85ebb-114">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="85ebb-114">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="85ebb-115">Určuje, jak dlouho se překlad služby DNS (Domain Name Service) ukládá do mezipaměti v kombinaci s možností kruhové dotazování DNS (v milisekundách).</span><span class="sxs-lookup"><span data-stu-id="85ebb-115">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="85ebb-116">Výchozí hodnota je 120 000 milisekund (dvě minuty).</span><span class="sxs-lookup"><span data-stu-id="85ebb-116">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="85ebb-117">Určuje, jestli překlad DNS názvů hostitelů s více adresami Internet Protocol (IP) vrací všechny adresy, nebo jenom první z nich.</span><span class="sxs-lookup"><span data-stu-id="85ebb-117">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="85ebb-118">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="85ebb-118">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="85ebb-119">Určuje zásady šifrování použité pro relaci SSL/TLS na <xref:System.Net.ServicePointManager> instanci.</span><span class="sxs-lookup"><span data-stu-id="85ebb-119">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="85ebb-120">Možné hodnoty jsou ekvivalentní hodnotám pro <xref:System.Net.Security.EncryptionPolicy> výčet.</span><span class="sxs-lookup"><span data-stu-id="85ebb-120">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="85ebb-121"><xref:System.Security.Authentication.CipherAlgorithmType.Null>Pokud je zásada šifrování nastavena na hodnotu, použití je povinné `NoEncryption` .</span><span class="sxs-lookup"><span data-stu-id="85ebb-121">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="85ebb-122">Výchozí hodnota je `RequireEncryption`.</span><span class="sxs-lookup"><span data-stu-id="85ebb-122">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="85ebb-123">Určuje, zda by metody POST měly očekávat `100-continue` odpověď ze serveru.</span><span class="sxs-lookup"><span data-stu-id="85ebb-123">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="85ebb-124">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="85ebb-124">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="85ebb-125">Určuje, jestli připojení řízená správcem servisního bodu používají algoritmus Nagle.</span><span class="sxs-lookup"><span data-stu-id="85ebb-125">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="85ebb-126">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="85ebb-126">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85ebb-127">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="85ebb-127">Child Elements</span></span>  
 <span data-ttu-id="85ebb-128">Žádné</span><span class="sxs-lookup"><span data-stu-id="85ebb-128">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85ebb-129">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="85ebb-129">Parent Elements</span></span>  
  
|<span data-ttu-id="85ebb-130">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="85ebb-130">**Element**</span></span>|<span data-ttu-id="85ebb-131">**Popis**</span><span class="sxs-lookup"><span data-stu-id="85ebb-131">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="85ebb-132">Nastavení</span><span class="sxs-lookup"><span data-stu-id="85ebb-132">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="85ebb-133">Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="85ebb-133">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85ebb-134">Poznámky</span><span class="sxs-lookup"><span data-stu-id="85ebb-134">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="85ebb-135">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="85ebb-135">Configuration Files</span></span>  
 <span data-ttu-id="85ebb-136">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="85ebb-136">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85ebb-137">Viz také:</span><span class="sxs-lookup"><span data-stu-id="85ebb-137">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="85ebb-138">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="85ebb-138">Network Settings Schema</span></span>](index.md)

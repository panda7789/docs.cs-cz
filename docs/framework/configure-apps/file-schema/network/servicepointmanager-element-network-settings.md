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
ms.openlocfilehash: b7333016fea2d46285d3c98181c0ca4904c376f8
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089131"
---
# <a name="servicepointmanager-element-network-settings"></a><span data-ttu-id="83291-102">\<servicePointManager> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="83291-102">\<servicePointManager> Element (Network Settings)</span></span>
<span data-ttu-id="83291-103">Nakonfiguruje připojení k síťovým prostředkům.</span><span class="sxs-lookup"><span data-stu-id="83291-103">Configures connections to network resources.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**

## <a name="syntax"></a><span data-ttu-id="83291-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83291-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="83291-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="83291-105">Attributes and Elements</span></span>  
 <span data-ttu-id="83291-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="83291-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="83291-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="83291-107">Attributes</span></span>  
  
|<span data-ttu-id="83291-108">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="83291-108">**Attribute**</span></span>|<span data-ttu-id="83291-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="83291-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`checkCertificateName`|<span data-ttu-id="83291-110">Určuje, zda má systém před použitím certifikátu ověřit, zda název certifikátu odpovídá názvu hostitele serveru.</span><span class="sxs-lookup"><span data-stu-id="83291-110">Specifies whether the system should verify that the name on the certificate matches the server host name before using the certificate.</span></span> <span data-ttu-id="83291-111">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="83291-111">The default value is `true`.</span></span>|  
|`checkCertificateRevocationList`|<span data-ttu-id="83291-112">Určuje, zda má systém před použitím certifikátu ověřit, zda byl certifikát odvolán.</span><span class="sxs-lookup"><span data-stu-id="83291-112">Specifies whether the system should check whether the certificate has been revoked before using the certificate.</span></span> <span data-ttu-id="83291-113">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="83291-113">The default value is `false`.</span></span>|  
|`dnsRefreshTimeout`|<span data-ttu-id="83291-114">Určuje, jak dlouho se překlad služby DNS (Domain Name Service) ukládá do mezipaměti v kombinaci s možností kruhové dotazování DNS (v milisekundách).</span><span class="sxs-lookup"><span data-stu-id="83291-114">Specifies how long Domain Name Service (DNS) resolutions are cached in conjunction with the DNS Round Robin option, in milliseconds.</span></span> <span data-ttu-id="83291-115">Výchozí hodnota je 120 000 milisekund (dvě minuty).</span><span class="sxs-lookup"><span data-stu-id="83291-115">The default value is 120,000 milliseconds (two minutes).</span></span>|  
|`enableDnsRoundRobin`|<span data-ttu-id="83291-116">Určuje, jestli překlad DNS názvů hostitelů s více adresami Internet Protocol (IP) vrací všechny adresy, nebo jenom první z nich.</span><span class="sxs-lookup"><span data-stu-id="83291-116">Specifies whether DNS resolutions of host names with multiple Internet Protocol (IP) addresses return all the addresses, or just the first one.</span></span> <span data-ttu-id="83291-117">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="83291-117">The default value is `false`.</span></span>|  
|`encryptionPolicy`|<span data-ttu-id="83291-118">Určuje zásady šifrování použité pro relaci SSL/TLS na <xref:System.Net.ServicePointManager> instanci.</span><span class="sxs-lookup"><span data-stu-id="83291-118">Specifies the encryption policy applied to an SSL/TLS session on a <xref:System.Net.ServicePointManager> instance.</span></span> <span data-ttu-id="83291-119">Možné hodnoty jsou ekvivalentní hodnotám pro <xref:System.Net.Security.EncryptionPolicy> výčet.</span><span class="sxs-lookup"><span data-stu-id="83291-119">The possible values are equivalent to the values for the <xref:System.Net.Security.EncryptionPolicy> enumeration.</span></span> <span data-ttu-id="83291-120"><xref:System.Security.Authentication.CipherAlgorithmType.Null>Pokud je zásada šifrování nastavena na hodnotu, použití je povinné `NoEncryption` .</span><span class="sxs-lookup"><span data-stu-id="83291-120">The use of <xref:System.Security.Authentication.CipherAlgorithmType.Null> is required when the encryption policy is set to `NoEncryption`.</span></span> <span data-ttu-id="83291-121">Výchozí hodnota je `RequireEncryption`.</span><span class="sxs-lookup"><span data-stu-id="83291-121">The default value is `RequireEncryption`.</span></span>|  
|`expect100Continue`|<span data-ttu-id="83291-122">Určuje, zda by metody POST měly očekávat `100-continue` odpověď ze serveru.</span><span class="sxs-lookup"><span data-stu-id="83291-122">Specifies whether POST methods should expect to receive a `100-continue` response from the server.</span></span> <span data-ttu-id="83291-123">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="83291-123">The default value is `true`.</span></span>|  
|`useNagleAlgorithm`|<span data-ttu-id="83291-124">Určuje, jestli připojení řízená správcem servisního bodu používají algoritmus Nagle.</span><span class="sxs-lookup"><span data-stu-id="83291-124">Specifies whether connections controlled by the service point manager use the Nagle algorithm.</span></span> <span data-ttu-id="83291-125">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="83291-125">The default value is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="83291-126">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="83291-126">Child Elements</span></span>  
 <span data-ttu-id="83291-127">Žádné</span><span class="sxs-lookup"><span data-stu-id="83291-127">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="83291-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="83291-128">Parent Elements</span></span>  
  
|<span data-ttu-id="83291-129">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="83291-129">**Element**</span></span>|<span data-ttu-id="83291-130">**Popis**</span><span class="sxs-lookup"><span data-stu-id="83291-130">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="83291-131">Nastavení</span><span class="sxs-lookup"><span data-stu-id="83291-131">Settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="83291-132">Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="83291-132">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="83291-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83291-133">Remarks</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="83291-134">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="83291-134">Configuration Files</span></span>  
 <span data-ttu-id="83291-135">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="83291-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="83291-136">Viz také</span><span class="sxs-lookup"><span data-stu-id="83291-136">See also</span></span>

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [<span data-ttu-id="83291-137">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="83291-137">Network Settings Schema</span></span>](index.md)

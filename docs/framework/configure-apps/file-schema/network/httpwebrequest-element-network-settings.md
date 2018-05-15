---
title: '&lt;HttpWebRequest –&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1d1dce38e5188824ba1412d3f2a285bd2304f147
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="lthttpwebrequestgt-element-network-settings"></a><span data-ttu-id="04502-102">&lt;HttpWebRequest –&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="04502-102">&lt;httpWebRequest&gt; Element (Network Settings)</span></span>
<span data-ttu-id="04502-103">Přizpůsobí parametry webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="04502-103">Customizes Web request parameters.</span></span>  
  
 <span data-ttu-id="04502-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="04502-104">\<configuration></span></span>  
<span data-ttu-id="04502-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="04502-105">\<system.net></span></span>  
<span data-ttu-id="04502-106">\<Nastavení ></span><span class="sxs-lookup"><span data-stu-id="04502-106">\<settings></span></span>  
<span data-ttu-id="04502-107">\<httpWebRequest ></span><span class="sxs-lookup"><span data-stu-id="04502-107">\<httpWebRequest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04502-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="04502-108">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="04502-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="04502-109">Attributes and Elements</span></span>  
 <span data-ttu-id="04502-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="04502-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="04502-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="04502-111">Attributes</span></span>  
  
|<span data-ttu-id="04502-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="04502-112">**Attribute**</span></span>|<span data-ttu-id="04502-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="04502-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="04502-114">Určuje v kilobajtech maximální délka hlavičky odpovědi.</span><span class="sxs-lookup"><span data-stu-id="04502-114">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="04502-115">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="04502-115">The default is 64.</span></span> <span data-ttu-id="04502-116">Hodnota -1 označuje, že žádné omezení velikosti bude vynucená pro hlavičky odpovědi.</span><span class="sxs-lookup"><span data-stu-id="04502-116">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="04502-117">Maximální délka chybnou odpověď, určuje v kilobajtech.</span><span class="sxs-lookup"><span data-stu-id="04502-117">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="04502-118">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="04502-118">The default is 64.</span></span> <span data-ttu-id="04502-119">Hodnota -1 označuje, že žádné omezení velikosti bude vynucená pro odpovědi na chybu.</span><span class="sxs-lookup"><span data-stu-id="04502-119">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="04502-120">Určuje maximální délku nahrávaný v reakci na neoprávněné chybový kód, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="04502-120">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="04502-121">Výchozí hodnota je -1.</span><span class="sxs-lookup"><span data-stu-id="04502-121">The default is -1.</span></span> <span data-ttu-id="04502-122">Hodnota -1 označuje, že žádné omezení velikosti bude vynucená pro odesílání.</span><span class="sxs-lookup"><span data-stu-id="04502-122">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="04502-123">Určuje, zda je povolena analýza unsafe záhlaví.</span><span class="sxs-lookup"><span data-stu-id="04502-123">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="04502-124">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="04502-124">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="04502-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="04502-125">Child Elements</span></span>  
 <span data-ttu-id="04502-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="04502-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="04502-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="04502-127">Parent Elements</span></span>  
  
|<span data-ttu-id="04502-128">**Element**</span><span class="sxs-lookup"><span data-stu-id="04502-128">**Element**</span></span>|<span data-ttu-id="04502-129">**Popis**</span><span class="sxs-lookup"><span data-stu-id="04502-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="04502-130">Nastavení</span><span class="sxs-lookup"><span data-stu-id="04502-130">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="04502-131">Nakonfiguruje možnosti základní sítě <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="04502-131">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="04502-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="04502-132">Remarks</span></span>  
 <span data-ttu-id="04502-133">Ve výchozím nastavení rozhraní .NET Framework výhradně vynucuje dokumentu RFC 2616 k analýze identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="04502-133">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="04502-134">Některé odezvy serveru může obsahovat řídicí znaky v zakázané pole, které způsobí, že <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> metoda k vyvolání <xref:System.Net.WebException>.</span><span class="sxs-lookup"><span data-stu-id="04502-134">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="04502-135">Pokud **useUnsafeHeaderParsing** je nastaven na **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> nezpůsobí výjimku, v takovém případě; ale, bude vaše aplikace bude zranitelný vůči několika formulářů analýza útoky identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="04502-135">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="04502-136">Nejlepším řešením je změna serveru tak, aby odpověď neobsahuje řídicí znaky.</span><span class="sxs-lookup"><span data-stu-id="04502-136">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="04502-137">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="04502-137">Configuration Files</span></span>  
 <span data-ttu-id="04502-138">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="04502-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="04502-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="04502-139">Example</span></span>  
 <span data-ttu-id="04502-140">Následující příklad ukazuje, jak určit větší než délka normální maximální záhlaví.</span><span class="sxs-lookup"><span data-stu-id="04502-140">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="04502-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="04502-141">See Also</span></span>  
 <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>  
 [<span data-ttu-id="04502-142">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="04502-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

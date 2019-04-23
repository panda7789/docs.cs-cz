---
title: <httpWebRequest> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: 722b2f726c9085f6dee6bad82044da3011b98702
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169296"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="d6677-102">\<httpWebRequest > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="d6677-102">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="d6677-103">Přizpůsobí parametrů webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="d6677-103">Customizes Web request parameters.</span></span>  
  
 <span data-ttu-id="d6677-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="d6677-104">\<configuration></span></span>  
<span data-ttu-id="d6677-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d6677-105">\<system.net></span></span>  
<span data-ttu-id="d6677-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="d6677-106">\<settings></span></span>  
<span data-ttu-id="d6677-107">\<httpWebRequest></span><span class="sxs-lookup"><span data-stu-id="d6677-107">\<httpWebRequest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6677-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6677-108">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6677-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d6677-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d6677-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d6677-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6677-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="d6677-111">Attributes</span></span>  
  
|<span data-ttu-id="d6677-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="d6677-112">**Attribute**</span></span>|<span data-ttu-id="d6677-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="d6677-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="d6677-114">Určuje v kilobajtech maximální délka hlavičky odpovědi.</span><span class="sxs-lookup"><span data-stu-id="d6677-114">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="d6677-115">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="d6677-115">The default is 64.</span></span> <span data-ttu-id="d6677-116">Hodnota -1 znamená, že žádné omezení velikosti se nevyžaduje v hlavičkách odpovědi.</span><span class="sxs-lookup"><span data-stu-id="d6677-116">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="d6677-117">Určuje maximální délku reakce na chybu, v kilobajtech.</span><span class="sxs-lookup"><span data-stu-id="d6677-117">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="d6677-118">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="d6677-118">The default is 64.</span></span> <span data-ttu-id="d6677-119">Hodnota -1 znamená, že žádné omezení velikosti se nevyžaduje v odpovědi na chybu.</span><span class="sxs-lookup"><span data-stu-id="d6677-119">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="d6677-120">Určuje maximální délku nahrání v reakci na neautorizovaný chybový kód, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="d6677-120">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="d6677-121">Výchozí hodnota je -1.</span><span class="sxs-lookup"><span data-stu-id="d6677-121">The default is -1.</span></span> <span data-ttu-id="d6677-122">Hodnota -1 znamená, že žádné omezení velikosti bude vynucená pro nahrávání.</span><span class="sxs-lookup"><span data-stu-id="d6677-122">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="d6677-123">Určuje, zda je povolena analýza nebezpečné záhlaví.</span><span class="sxs-lookup"><span data-stu-id="d6677-123">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="d6677-124">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="d6677-124">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d6677-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d6677-125">Child Elements</span></span>  
 <span data-ttu-id="d6677-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="d6677-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d6677-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d6677-127">Parent Elements</span></span>  
  
|<span data-ttu-id="d6677-128">**Element**</span><span class="sxs-lookup"><span data-stu-id="d6677-128">**Element**</span></span>|<span data-ttu-id="d6677-129">**Popis**</span><span class="sxs-lookup"><span data-stu-id="d6677-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d6677-130">settings</span><span class="sxs-lookup"><span data-stu-id="d6677-130">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="d6677-131">Nakonfiguruje možnosti základní sítě pro <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="d6677-131">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6677-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6677-132">Remarks</span></span>  
 <span data-ttu-id="d6677-133">Ve výchozím nastavení rozhraní .NET Framework přísně dokumentu RFC 2616 k analýze identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="d6677-133">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="d6677-134">Některé odpovědi serveru může obsahovat řídicí znaky zakázaných polí, které způsobí, že <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> metoda k vyvolání <xref:System.Net.WebException>.</span><span class="sxs-lookup"><span data-stu-id="d6677-134">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="d6677-135">Pokud **useUnsafeHeaderParsing** je nastavena na **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> nezpůsobí výjimku v tomto případě; nicméně, vaše aplikace bude zranitelný vůči několik tvarů útoky parsování identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="d6677-135">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="d6677-136">Nejlepším řešením je změnit server tak, aby odpovědi neobsahuje řídicí znaky.</span><span class="sxs-lookup"><span data-stu-id="d6677-136">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d6677-137">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="d6677-137">Configuration Files</span></span>  
 <span data-ttu-id="d6677-138">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d6677-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6677-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6677-139">Example</span></span>  
 <span data-ttu-id="d6677-140">Následující příklad ukazuje, jak určit větší než normální záhlaví maximální délku.</span><span class="sxs-lookup"><span data-stu-id="d6677-140">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d6677-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6677-141">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="d6677-142">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="d6677-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

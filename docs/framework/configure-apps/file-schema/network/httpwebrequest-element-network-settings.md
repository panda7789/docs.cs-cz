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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674542"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="62899-102">\<httpWebRequest > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="62899-102">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="62899-103">Přizpůsobí parametrů webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="62899-103">Customizes Web request parameters.</span></span>  
  
 <span data-ttu-id="62899-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="62899-104">\<configuration></span></span>  
<span data-ttu-id="62899-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="62899-105">\<system.net></span></span>  
<span data-ttu-id="62899-106">\<settings></span><span class="sxs-lookup"><span data-stu-id="62899-106">\<settings></span></span>  
<span data-ttu-id="62899-107">\<httpWebRequest></span><span class="sxs-lookup"><span data-stu-id="62899-107">\<httpWebRequest></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62899-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62899-108">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62899-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="62899-109">Attributes and Elements</span></span>  
 <span data-ttu-id="62899-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="62899-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62899-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="62899-111">Attributes</span></span>  
  
|<span data-ttu-id="62899-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="62899-112">**Attribute**</span></span>|<span data-ttu-id="62899-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="62899-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="62899-114">Určuje v kilobajtech maximální délka hlavičky odpovědi.</span><span class="sxs-lookup"><span data-stu-id="62899-114">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="62899-115">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="62899-115">The default is 64.</span></span> <span data-ttu-id="62899-116">Hodnota -1 znamená, že žádné omezení velikosti se nevyžaduje v hlavičkách odpovědi.</span><span class="sxs-lookup"><span data-stu-id="62899-116">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="62899-117">Určuje maximální délku reakce na chybu, v kilobajtech.</span><span class="sxs-lookup"><span data-stu-id="62899-117">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="62899-118">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="62899-118">The default is 64.</span></span> <span data-ttu-id="62899-119">Hodnota -1 znamená, že žádné omezení velikosti se nevyžaduje v odpovědi na chybu.</span><span class="sxs-lookup"><span data-stu-id="62899-119">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="62899-120">Určuje maximální délku nahrání v reakci na neautorizovaný chybový kód, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="62899-120">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="62899-121">Výchozí hodnota je -1.</span><span class="sxs-lookup"><span data-stu-id="62899-121">The default is -1.</span></span> <span data-ttu-id="62899-122">Hodnota -1 znamená, že žádné omezení velikosti bude vynucená pro nahrávání.</span><span class="sxs-lookup"><span data-stu-id="62899-122">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="62899-123">Určuje, zda je povolena analýza nebezpečné záhlaví.</span><span class="sxs-lookup"><span data-stu-id="62899-123">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="62899-124">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="62899-124">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62899-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="62899-125">Child Elements</span></span>  
 <span data-ttu-id="62899-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="62899-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="62899-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="62899-127">Parent Elements</span></span>  
  
|<span data-ttu-id="62899-128">**Element**</span><span class="sxs-lookup"><span data-stu-id="62899-128">**Element**</span></span>|<span data-ttu-id="62899-129">**Popis**</span><span class="sxs-lookup"><span data-stu-id="62899-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="62899-130">settings</span><span class="sxs-lookup"><span data-stu-id="62899-130">settings</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|<span data-ttu-id="62899-131">Nakonfiguruje možnosti základní sítě pro <xref:System.Net> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="62899-131">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62899-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62899-132">Remarks</span></span>  
 <span data-ttu-id="62899-133">Ve výchozím nastavení rozhraní .NET Framework přísně dokumentu RFC 2616 k analýze identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="62899-133">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="62899-134">Některé odpovědi serveru může obsahovat řídicí znaky zakázaných polí, které způsobí, že <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> metoda k vyvolání <xref:System.Net.WebException>.</span><span class="sxs-lookup"><span data-stu-id="62899-134">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="62899-135">Pokud **useUnsafeHeaderParsing** je nastavena na **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> nezpůsobí výjimku v tomto případě; nicméně, vaše aplikace bude zranitelný vůči několik tvarů útoky parsování identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="62899-135">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="62899-136">Nejlepším řešením je změnit server tak, aby odpovědi neobsahuje řídicí znaky.</span><span class="sxs-lookup"><span data-stu-id="62899-136">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="62899-137">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="62899-137">Configuration Files</span></span>  
 <span data-ttu-id="62899-138">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="62899-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="62899-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="62899-139">Example</span></span>  
 <span data-ttu-id="62899-140">Následující příklad ukazuje, jak určit větší než normální záhlaví maximální délku.</span><span class="sxs-lookup"><span data-stu-id="62899-140">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="62899-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62899-141">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="62899-142">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="62899-142">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

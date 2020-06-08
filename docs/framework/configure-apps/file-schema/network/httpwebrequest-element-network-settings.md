---
title: <httpWebRequest> – element (nastavení sítě)
description: <httpWebRequest>Prvek nastavení sítě přizpůsobí parametry webového požadavku v .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: 59ab425dcef8ac5283035910a9d78a89a16be8b1
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504586"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="2d210-103">\<httpWebRequest> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="2d210-103">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="2d210-104">Přizpůsobuje parametry webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="2d210-104">Customizes Web request parameters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpWebRequest>**

## <a name="syntax"></a><span data-ttu-id="2d210-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2d210-105">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2d210-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2d210-106">Attributes and Elements</span></span>  
 <span data-ttu-id="2d210-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2d210-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2d210-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="2d210-108">Attributes</span></span>  
  
|<span data-ttu-id="2d210-109">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="2d210-109">**Attribute**</span></span>|<span data-ttu-id="2d210-110">**Popis**</span><span class="sxs-lookup"><span data-stu-id="2d210-110">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="2d210-111">Určuje maximální délku hlavičky odpovědi v kilobajtech.</span><span class="sxs-lookup"><span data-stu-id="2d210-111">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="2d210-112">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="2d210-112">The default is 64.</span></span> <span data-ttu-id="2d210-113">Hodnota-1 označuje, že do hlaviček odpovědi nebude uloženo žádné omezení velikosti.</span><span class="sxs-lookup"><span data-stu-id="2d210-113">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="2d210-114">Určuje maximální délku chybové odpovědi v kilobajtech.</span><span class="sxs-lookup"><span data-stu-id="2d210-114">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="2d210-115">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="2d210-115">The default is 64.</span></span> <span data-ttu-id="2d210-116">Hodnota-1 označuje, že při chybové odpovědi nebude uloženo žádné omezení velikosti.</span><span class="sxs-lookup"><span data-stu-id="2d210-116">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="2d210-117">Určuje maximální délku nahrávání jako odpověď na neautorizovaný kód chyby (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="2d210-117">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="2d210-118">Výchozí hodnota je-1.</span><span class="sxs-lookup"><span data-stu-id="2d210-118">The default is -1.</span></span> <span data-ttu-id="2d210-119">Hodnota-1 označuje, že při nahrávání nebude uloženo žádné omezení velikosti.</span><span class="sxs-lookup"><span data-stu-id="2d210-119">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="2d210-120">Určuje, zda je povoleno nebezpečná analýza hlaviček.</span><span class="sxs-lookup"><span data-stu-id="2d210-120">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="2d210-121">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="2d210-121">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2d210-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2d210-122">Child Elements</span></span>  
 <span data-ttu-id="2d210-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="2d210-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2d210-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2d210-124">Parent Elements</span></span>  
  
|<span data-ttu-id="2d210-125">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="2d210-125">**Element**</span></span>|<span data-ttu-id="2d210-126">**Popis**</span><span class="sxs-lookup"><span data-stu-id="2d210-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2d210-127">zdroje dat</span><span class="sxs-lookup"><span data-stu-id="2d210-127">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="2d210-128">Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="2d210-128">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d210-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2d210-129">Remarks</span></span>  
 <span data-ttu-id="2d210-130">Ve výchozím nastavení .NET Framework striktně vynutila specifikaci RFC 2616 pro analýzu identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="2d210-130">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="2d210-131">Některé odpovědi serveru mohou obsahovat řídicí znaky v zakázaných polích, což způsobí, že <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> metoda vyvolá výjimku <xref:System.Net.WebException> .</span><span class="sxs-lookup"><span data-stu-id="2d210-131">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="2d210-132">Pokud je **useUnsafeHeaderParsing** nastavené na **hodnotu true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> v tomto případě se v tomto případě nevyvolává. vaše aplikace ale bude zranitelná vůči několika formám ÚTOKů s analýzou identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="2d210-132">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="2d210-133">Nejlepším řešením je změnit server tak, aby odpověď neobsahovala řídicí znaky.</span><span class="sxs-lookup"><span data-stu-id="2d210-133">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2d210-134">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="2d210-134">Configuration Files</span></span>  
 <span data-ttu-id="2d210-135">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="2d210-135">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2d210-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="2d210-136">Example</span></span>  
 <span data-ttu-id="2d210-137">Následující příklad ukazuje, jak zadat větší než normální maximální délka hlavičky.</span><span class="sxs-lookup"><span data-stu-id="2d210-137">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2d210-138">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d210-138">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="2d210-139">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="2d210-139">Network Settings Schema</span></span>](index.md)

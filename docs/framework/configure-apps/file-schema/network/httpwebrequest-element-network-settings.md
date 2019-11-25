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
ms.openlocfilehash: d33dadc14510feb00e05ca557b507b0cf8fa0dd0
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74087459"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="98536-102">\<element > httpWebRequest (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="98536-102">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="98536-103">Přizpůsobuje parametry webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="98536-103">Customizes Web request parameters.</span></span>  

<span data-ttu-id="98536-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="98536-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="98536-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="98536-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="98536-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<nastavení >** ](settings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="98536-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)</span></span>\
<span data-ttu-id="98536-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpWebRequest >**</span><span class="sxs-lookup"><span data-stu-id="98536-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpWebRequest>**</span></span>

## <a name="syntax"></a><span data-ttu-id="98536-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="98536-108">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="98536-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="98536-109">Attributes and Elements</span></span>  
 <span data-ttu-id="98536-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="98536-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="98536-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="98536-111">Attributes</span></span>  
  
|<span data-ttu-id="98536-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="98536-112">**Attribute**</span></span>|<span data-ttu-id="98536-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="98536-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="98536-114">Určuje maximální délku hlavičky odpovědi v kilobajtech.</span><span class="sxs-lookup"><span data-stu-id="98536-114">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="98536-115">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="98536-115">The default is 64.</span></span> <span data-ttu-id="98536-116">Hodnota-1 označuje, že do hlaviček odpovědi nebude uloženo žádné omezení velikosti.</span><span class="sxs-lookup"><span data-stu-id="98536-116">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="98536-117">Určuje maximální délku chybové odpovědi v kilobajtech.</span><span class="sxs-lookup"><span data-stu-id="98536-117">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="98536-118">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="98536-118">The default is 64.</span></span> <span data-ttu-id="98536-119">Hodnota-1 označuje, že při chybové odpovědi nebude uloženo žádné omezení velikosti.</span><span class="sxs-lookup"><span data-stu-id="98536-119">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="98536-120">Určuje maximální délku nahrávání jako odpověď na neautorizovaný kód chyby (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="98536-120">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="98536-121">Výchozí hodnota je-1.</span><span class="sxs-lookup"><span data-stu-id="98536-121">The default is -1.</span></span> <span data-ttu-id="98536-122">Hodnota-1 označuje, že při nahrávání nebude uloženo žádné omezení velikosti.</span><span class="sxs-lookup"><span data-stu-id="98536-122">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="98536-123">Určuje, zda je povoleno nebezpečná analýza hlaviček.</span><span class="sxs-lookup"><span data-stu-id="98536-123">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="98536-124">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="98536-124">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="98536-125">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="98536-125">Child Elements</span></span>  
 <span data-ttu-id="98536-126">Žádné</span><span class="sxs-lookup"><span data-stu-id="98536-126">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="98536-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="98536-127">Parent Elements</span></span>  
  
|<span data-ttu-id="98536-128">**Element**</span><span class="sxs-lookup"><span data-stu-id="98536-128">**Element**</span></span>|<span data-ttu-id="98536-129">**Popis**</span><span class="sxs-lookup"><span data-stu-id="98536-129">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="98536-130">možnost</span><span class="sxs-lookup"><span data-stu-id="98536-130">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="98536-131">Konfiguruje základní možnosti sítě pro obor názvů <xref:System.Net>.</span><span class="sxs-lookup"><span data-stu-id="98536-131">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="98536-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="98536-132">Remarks</span></span>  
 <span data-ttu-id="98536-133">Ve výchozím nastavení .NET Framework striktně vynutila specifikaci RFC 2616 pro analýzu identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="98536-133">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="98536-134">Některé odpovědi serveru mohou obsahovat řídicí znaky v zakázaných polích, což způsobí, že metoda <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> vyvolá <xref:System.Net.WebException>.</span><span class="sxs-lookup"><span data-stu-id="98536-134">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="98536-135">Pokud je **useUnsafeHeaderParsing** nastavené na **hodnotu true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> v tomto případě se nevyvolá. vaše aplikace ale bude zranitelná vůči několika formám útoků s analýzou identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="98536-135">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="98536-136">Nejlepším řešením je změnit server tak, aby odpověď neobsahovala řídicí znaky.</span><span class="sxs-lookup"><span data-stu-id="98536-136">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="98536-137">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="98536-137">Configuration Files</span></span>  
 <span data-ttu-id="98536-138">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="98536-138">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="98536-139">Příklad</span><span class="sxs-lookup"><span data-stu-id="98536-139">Example</span></span>  
 <span data-ttu-id="98536-140">Následující příklad ukazuje, jak zadat větší než normální maximální délka hlavičky.</span><span class="sxs-lookup"><span data-stu-id="98536-140">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="98536-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98536-141">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="98536-142">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="98536-142">Network Settings Schema</span></span>](index.md)

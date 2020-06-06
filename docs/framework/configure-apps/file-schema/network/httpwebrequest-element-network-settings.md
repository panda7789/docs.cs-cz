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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087459"
---
# <a name="httpwebrequest-element-network-settings"></a><span data-ttu-id="08cb4-102">\<httpWebRequest> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="08cb4-102">\<httpWebRequest> Element (Network Settings)</span></span>
<span data-ttu-id="08cb4-103">Přizpůsobuje parametry webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="08cb4-103">Customizes Web request parameters.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<httpWebRequest>**

## <a name="syntax"></a><span data-ttu-id="08cb4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="08cb4-104">Syntax</span></span>  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="08cb4-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="08cb4-105">Attributes and Elements</span></span>  
 <span data-ttu-id="08cb4-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="08cb4-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="08cb4-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="08cb4-107">Attributes</span></span>  
  
|<span data-ttu-id="08cb4-108">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="08cb4-108">**Attribute**</span></span>|<span data-ttu-id="08cb4-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="08cb4-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|<span data-ttu-id="08cb4-110">Určuje maximální délku hlavičky odpovědi v kilobajtech.</span><span class="sxs-lookup"><span data-stu-id="08cb4-110">Specifies the maximum length of a response header, in kilobytes.</span></span> <span data-ttu-id="08cb4-111">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="08cb4-111">The default is 64.</span></span> <span data-ttu-id="08cb4-112">Hodnota-1 označuje, že do hlaviček odpovědi nebude uloženo žádné omezení velikosti.</span><span class="sxs-lookup"><span data-stu-id="08cb4-112">A value of -1 indicates that no size limit will be imposed on the response headers.</span></span>|  
|`maximumErrorResponseLength`|<span data-ttu-id="08cb4-113">Určuje maximální délku chybové odpovědi v kilobajtech.</span><span class="sxs-lookup"><span data-stu-id="08cb4-113">Specifies the maximum length of an error response, in kilobytes.</span></span> <span data-ttu-id="08cb4-114">Výchozí hodnota je 64.</span><span class="sxs-lookup"><span data-stu-id="08cb4-114">The default is 64.</span></span> <span data-ttu-id="08cb4-115">Hodnota-1 označuje, že při chybové odpovědi nebude uloženo žádné omezení velikosti.</span><span class="sxs-lookup"><span data-stu-id="08cb4-115">A value of -1 indicates that no size limit will be imposed on the error response.</span></span>|  
|`maximumUnauthorizedUploadLength`|<span data-ttu-id="08cb4-116">Určuje maximální délku nahrávání jako odpověď na neautorizovaný kód chyby (v bajtech).</span><span class="sxs-lookup"><span data-stu-id="08cb4-116">Specifies the maximum length of an upload in response to an unauthorized error code, in bytes.</span></span> <span data-ttu-id="08cb4-117">Výchozí hodnota je-1.</span><span class="sxs-lookup"><span data-stu-id="08cb4-117">The default is -1.</span></span> <span data-ttu-id="08cb4-118">Hodnota-1 označuje, že při nahrávání nebude uloženo žádné omezení velikosti.</span><span class="sxs-lookup"><span data-stu-id="08cb4-118">A value of -1 indicates that no size limit will be imposed on the upload.</span></span>|  
|`useUnsafeHeaderParsing`|<span data-ttu-id="08cb4-119">Určuje, zda je povoleno nebezpečná analýza hlaviček.</span><span class="sxs-lookup"><span data-stu-id="08cb4-119">Specifies whether unsafe header parsing is enabled.</span></span> <span data-ttu-id="08cb4-120">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="08cb4-120">The default value is `false`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="08cb4-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="08cb4-121">Child Elements</span></span>  
 <span data-ttu-id="08cb4-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="08cb4-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="08cb4-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="08cb4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="08cb4-124">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="08cb4-124">**Element**</span></span>|<span data-ttu-id="08cb4-125">**Popis**</span><span class="sxs-lookup"><span data-stu-id="08cb4-125">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="08cb4-126">zdroje dat</span><span class="sxs-lookup"><span data-stu-id="08cb4-126">settings</span></span>](settings-element-network-settings.md)|<span data-ttu-id="08cb4-127">Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.</span><span class="sxs-lookup"><span data-stu-id="08cb4-127">Configures basic network options for the <xref:System.Net> namespace.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="08cb4-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="08cb4-128">Remarks</span></span>  
 <span data-ttu-id="08cb4-129">Ve výchozím nastavení .NET Framework striktně vynutila specifikaci RFC 2616 pro analýzu identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="08cb4-129">By default, the .NET Framework strictly enforces RFC 2616 for URI parsing.</span></span> <span data-ttu-id="08cb4-130">Některé odpovědi serveru mohou obsahovat řídicí znaky v zakázaných polích, což způsobí, že <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> metoda vyvolá výjimku <xref:System.Net.WebException> .</span><span class="sxs-lookup"><span data-stu-id="08cb4-130">Some server responses may include control characters in prohibited fields, which will cause the <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> method to throw a <xref:System.Net.WebException>.</span></span> <span data-ttu-id="08cb4-131">Pokud je **useUnsafeHeaderParsing** nastavené na **hodnotu true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> v tomto případě se v tomto případě nevyvolává. vaše aplikace ale bude zranitelná vůči několika formám ÚTOKů s analýzou identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="08cb4-131">If **useUnsafeHeaderParsing** is set to **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> will not throw in this case; however, your application will be vulnerable to several forms of URI parsing attacks.</span></span> <span data-ttu-id="08cb4-132">Nejlepším řešením je změnit server tak, aby odpověď neobsahovala řídicí znaky.</span><span class="sxs-lookup"><span data-stu-id="08cb4-132">The best solution is to change the server so that the response does not include control characters.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="08cb4-133">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="08cb4-133">Configuration Files</span></span>  
 <span data-ttu-id="08cb4-134">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="08cb4-134">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="08cb4-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="08cb4-135">Example</span></span>  
 <span data-ttu-id="08cb4-136">Následující příklad ukazuje, jak zadat větší než normální maximální délka hlavičky.</span><span class="sxs-lookup"><span data-stu-id="08cb4-136">The following example shows how to specify a larger than normal maximum header length.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="08cb4-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="08cb4-137">See also</span></span>

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [<span data-ttu-id="08cb4-138">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="08cb4-138">Network Settings Schema</span></span>](index.md)

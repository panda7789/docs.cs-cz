---
title: <remove> – element pro webRequestModules (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
ms.openlocfilehash: afa1aef8ea71f43a136987ec5b6e1925c6d9fb40
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154722"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="d4957-102">\<remove> – element pro webRequestModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="d4957-102">\<remove> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="d4957-103">Odebere z aplikace vlastní modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="d4957-103">Removes a custom Web request module from the application.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**
  
## <a name="syntax"></a><span data-ttu-id="d4957-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d4957-104">Syntax</span></span>  
  
```xml  
<remove
  prefix="URI prefix"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4957-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d4957-105">Attributes and Elements</span></span>  
 <span data-ttu-id="d4957-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d4957-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4957-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="d4957-107">Attributes</span></span>  
  
|<span data-ttu-id="d4957-108">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="d4957-108">**Attribute**</span></span>|<span data-ttu-id="d4957-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="d4957-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="d4957-110">Předpona identifikátoru URI pro požadavky zpracovávané tímto modulem webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="d4957-110">The URI prefix for requests handled by this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4957-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d4957-111">Child Elements</span></span>  
 <span data-ttu-id="d4957-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="d4957-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4957-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d4957-113">Parent Elements</span></span>  
  
|<span data-ttu-id="d4957-114">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="d4957-114">**Element**</span></span>|<span data-ttu-id="d4957-115">**Popis**</span><span class="sxs-lookup"><span data-stu-id="d4957-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d4957-116">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="d4957-116">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="d4957-117">Určuje moduly, které se použijí k vyžádání informací od hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="d4957-117">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d4957-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d4957-118">Remarks</span></span>  
 <span data-ttu-id="d4957-119">`remove`Prvek odebere registrovaný modul webové žádosti pro zadanou předponu identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="d4957-119">The `remove` element removes the registered Web request module for the specified URI prefix.</span></span>  
  
 <span data-ttu-id="d4957-120">Hodnota `prefix` atributu by měla být předními znaky platného identifikátoru URI – například " `http` " nebo " `http://www.contoso.com` ".</span><span class="sxs-lookup"><span data-stu-id="d4957-120">The value for the `prefix` attribute should be the leading characters of a valid URI -- for example, "`http`", or "`http://www.contoso.com`".</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d4957-121">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="d4957-121">Configuration Files</span></span>  
 <span data-ttu-id="d4957-122">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="d4957-122">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4957-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="d4957-123">Example</span></span>  

<span data-ttu-id="d4957-124">Následující příklad odebere existující modul webové žádosti pro protokol HTTP a pak zaregistruje nový vlastní modul webové žádosti pro požadavky HTTP na `www.contoso.com` .</span><span class="sxs-lookup"><span data-stu-id="d4957-124">The following example removes the existing Web request module for HTTP and then registers a new custom Web request module for HTTP requests to `www.contoso.com`.</span></span>
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d4957-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="d4957-125">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="d4957-126">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="d4957-126">Network Settings Schema</span></span>](index.md)

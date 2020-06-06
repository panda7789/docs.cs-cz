---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252110"
---
# \<chunkedCookieHandler>
<span data-ttu-id="44eee-101">Nakonfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler> .</span><span class="sxs-lookup"><span data-stu-id="44eee-101">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="44eee-102">Tento element může být k dispozici pouze v případě, že `mode` atribut `<cookieHandler>` elementu je "výchozí" nebo "v bloku".</span><span class="sxs-lookup"><span data-stu-id="44eee-102">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**  
  
## <a name="syntax"></a><span data-ttu-id="44eee-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="44eee-103">Syntax</span></span>  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration>  
    <cookieHandler mode="Chunked||Default" >  
      <chunkedCookieHandler size=xs:int >  
      </chunkedCookieHandler>  
    </cookieHandler>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="44eee-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="44eee-104">Attributes and Elements</span></span>  
 <span data-ttu-id="44eee-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="44eee-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="44eee-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="44eee-106">Attributes</span></span>  
  
|<span data-ttu-id="44eee-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="44eee-107">Attribute</span></span>|<span data-ttu-id="44eee-108">Popis</span><span class="sxs-lookup"><span data-stu-id="44eee-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="44eee-109">Mění</span><span class="sxs-lookup"><span data-stu-id="44eee-109">chunkSize</span></span>|<span data-ttu-id="44eee-110">Maximální velikost dat souborů cookie protokolu HTTP v znacích pro libovolný soubor cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="44eee-110">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="44eee-111">Při upravování velikosti bloku dat musíte být opatrní.</span><span class="sxs-lookup"><span data-stu-id="44eee-111">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="44eee-112">Webové prohlížeče mají různá omezení velikosti souborů cookie a počtu povolených v každé doméně.</span><span class="sxs-lookup"><span data-stu-id="44eee-112">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="44eee-113">Původní specifikace aplikace Netscape například stanovila tyto limity: 300 souborů cookie celkem, 4096 bajtů na hlavičku souboru cookie (včetně metadat, nikoli jenom hodnota souboru cookie) a 20 souborů cookie na doménu.</span><span class="sxs-lookup"><span data-stu-id="44eee-113">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="44eee-114">Výchozí hodnota je 2000.</span><span class="sxs-lookup"><span data-stu-id="44eee-114">The default is 2000.</span></span> <span data-ttu-id="44eee-115">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="44eee-115">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="44eee-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="44eee-116">Child Elements</span></span>  
 <span data-ttu-id="44eee-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="44eee-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="44eee-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="44eee-118">Parent Elements</span></span>  
  
|<span data-ttu-id="44eee-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="44eee-119">Element</span></span>|<span data-ttu-id="44eee-120">Description</span><span class="sxs-lookup"><span data-stu-id="44eee-120">Description</span></span>|  
|-------------|-----------------|  
|[\<cookieHandler>](cookiehandler.md)|<span data-ttu-id="44eee-121">Nakonfiguruje <xref:System.IdentityModel.Services.CookieHandler> , <xref:System.IdentityModel.Services.SessionAuthenticationModule> jak bude (SAM) používat ke čtení a zápisu souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="44eee-121">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="44eee-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="44eee-122">Remarks</span></span>  
 <span data-ttu-id="44eee-123">Pokud určíte <xref:System.IdentityModel.Services.ChunkedCookieHandler> nastavením `mode` atributu `<cookieHandler>` pro element na "výchozí" nebo "bloků", můžete určit velikost bloku dat, kterou obslužná rutina souborů cookie používá ke čtení a zápisu souborů cookie, a to zahrnutím `<chunkedCookieHandler>` podřízeného prvku a nastavením jeho `chunkSize` atributu.</span><span class="sxs-lookup"><span data-stu-id="44eee-123">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="44eee-124">Pokud `<chunkedCookieHandler>` element není přítomen, je použita výchozí velikost bloku 2000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="44eee-124">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="44eee-125">Tento element nejde zadat, pokud `mode` je atribut nastavený na Custom (vlastní).</span><span class="sxs-lookup"><span data-stu-id="44eee-125">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="44eee-126">`<chunkedCookieHandler>`Element je reprezentován <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> třídou.</span><span class="sxs-lookup"><span data-stu-id="44eee-126">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="44eee-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="44eee-127">Example</span></span>  
 <span data-ttu-id="44eee-128">V následujícím příkladu se konfiguruje obslužná rutina souborů cookie s proměnlivým blokem, která zapisuje soubory cookie v blocích po 3000 bajtech.</span><span class="sxs-lookup"><span data-stu-id="44eee-128">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="44eee-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="44eee-129">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>

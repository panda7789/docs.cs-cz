---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 6aad95033b99f1472284f838f3ede2e74ea8324c
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252110"
---
# <a name="chunkedcookiehandler"></a><span data-ttu-id="794b7-101">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="794b7-101">\<chunkedCookieHandler></span></span>
<span data-ttu-id="794b7-102">Nakonfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="794b7-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="794b7-103">Tento element může být k dispozici pouze `mode` v případě, `<cookieHandler>` že atribut elementu je "výchozí" nebo "v bloku".</span><span class="sxs-lookup"><span data-stu-id="794b7-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
<span data-ttu-id="794b7-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="794b7-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="794b7-105">&nbsp;&nbsp;[ **\<> System. identityModel. Services**](system-identitymodel-services.md)</span><span class="sxs-lookup"><span data-stu-id="794b7-105">&nbsp;&nbsp;[**\<system.identityModel.services>**](system-identitymodel-services.md)</span></span>\
<span data-ttu-id="794b7-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<federationConfiguration >** ](federationconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="794b7-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<federationConfiguration>**](federationconfiguration.md)</span></span>\
<span data-ttu-id="794b7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<cookieHandler >** ](cookiehandler.md)</span><span class="sxs-lookup"><span data-stu-id="794b7-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<cookieHandler>**](cookiehandler.md)</span></span>\
<span data-ttu-id="794b7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<chunkedCookieHandler >**</span><span class="sxs-lookup"><span data-stu-id="794b7-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<chunkedCookieHandler>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="794b7-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="794b7-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="794b7-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="794b7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="794b7-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="794b7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="794b7-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="794b7-112">Attributes</span></span>  
  
|<span data-ttu-id="794b7-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="794b7-113">Attribute</span></span>|<span data-ttu-id="794b7-114">Popis</span><span class="sxs-lookup"><span data-stu-id="794b7-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="794b7-115">Mění</span><span class="sxs-lookup"><span data-stu-id="794b7-115">chunkSize</span></span>|<span data-ttu-id="794b7-116">Maximální velikost dat souborů cookie protokolu HTTP v znacích pro libovolný soubor cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="794b7-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="794b7-117">Při upravování velikosti bloku dat musíte být opatrní.</span><span class="sxs-lookup"><span data-stu-id="794b7-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="794b7-118">Webové prohlížeče mají různá omezení velikosti souborů cookie a počtu povolených v každé doméně.</span><span class="sxs-lookup"><span data-stu-id="794b7-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="794b7-119">Například původní specifikace Netscape tato omezení stanovila: 300 souborů cookie celkem, 4096 bajtů na hlavičku souboru cookie (včetně metadat, nikoli jenom hodnoty cookie) a 20 souborů cookie na doménu.</span><span class="sxs-lookup"><span data-stu-id="794b7-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="794b7-120">Výchozí hodnota je 2000.</span><span class="sxs-lookup"><span data-stu-id="794b7-120">The default is 2000.</span></span> <span data-ttu-id="794b7-121">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="794b7-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="794b7-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="794b7-122">Child Elements</span></span>  
 <span data-ttu-id="794b7-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="794b7-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="794b7-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="794b7-124">Parent Elements</span></span>  
  
|<span data-ttu-id="794b7-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="794b7-125">Element</span></span>|<span data-ttu-id="794b7-126">Popis</span><span class="sxs-lookup"><span data-stu-id="794b7-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="794b7-127">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="794b7-127">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="794b7-128"><xref:System.IdentityModel.Services.SessionAuthenticationModule> Nakonfiguruje <xref:System.IdentityModel.Services.CookieHandler> , jak bude (SAM) používat ke čtení a zápisu souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="794b7-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="794b7-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="794b7-129">Remarks</span></span>  
 <span data-ttu-id="794b7-130"><xref:System.IdentityModel.Services.ChunkedCookieHandler> Pokud určíte `mode` nastavením atributu `<cookieHandler>` elementu na "výchozí" nebo "bloků", můžete určit velikost bloku dat, kterou obslužná rutina souborů cookie používá `<chunkedCookieHandler>` ke čtení a zápisu souborů cookie zahrnutím podřízeného prvku a nastavení jeho `chunkSize` atributu.</span><span class="sxs-lookup"><span data-stu-id="794b7-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="794b7-131">`<chunkedCookieHandler>` Pokud element není přítomen, je použita výchozí velikost bloku 2000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="794b7-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="794b7-132">Tento element nejde zadat, pokud `mode` je atribut nastavený na Custom (vlastní).</span><span class="sxs-lookup"><span data-stu-id="794b7-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="794b7-133">Element je reprezentován <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement>třídou. `<chunkedCookieHandler>`</span><span class="sxs-lookup"><span data-stu-id="794b7-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="794b7-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="794b7-134">Example</span></span>  
 <span data-ttu-id="794b7-135">V následujícím příkladu se konfiguruje obslužná rutina souborů cookie s proměnlivým blokem, která zapisuje soubory cookie v blocích po 3000 bajtech.</span><span class="sxs-lookup"><span data-stu-id="794b7-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="794b7-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="794b7-136">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>

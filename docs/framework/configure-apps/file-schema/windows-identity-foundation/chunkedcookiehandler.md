---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: b3b4cf0d7c2748079af7a94534622b1dbadd3ab5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941894"
---
# <a name="chunkedcookiehandler"></a><span data-ttu-id="9d3af-101">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="9d3af-101">\<chunkedCookieHandler></span></span>
<span data-ttu-id="9d3af-102">Nakonfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="9d3af-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="9d3af-103">Tento element může být k dispozici pouze `mode` v případě, `<cookieHandler>` že atribut elementu je "výchozí" nebo "v bloku".</span><span class="sxs-lookup"><span data-stu-id="9d3af-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="9d3af-104">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="9d3af-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="9d3af-105">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="9d3af-105">\<federationConfiguration></span></span>  
<span data-ttu-id="9d3af-106">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="9d3af-106">\<cookieHandler></span></span>  
<span data-ttu-id="9d3af-107">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="9d3af-107">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9d3af-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9d3af-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9d3af-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9d3af-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9d3af-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9d3af-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9d3af-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="9d3af-111">Attributes</span></span>  
  
|<span data-ttu-id="9d3af-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="9d3af-112">Attribute</span></span>|<span data-ttu-id="9d3af-113">Popis</span><span class="sxs-lookup"><span data-stu-id="9d3af-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9d3af-114">Mění</span><span class="sxs-lookup"><span data-stu-id="9d3af-114">chunkSize</span></span>|<span data-ttu-id="9d3af-115">Maximální velikost dat souborů cookie protokolu HTTP v znacích pro libovolný soubor cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="9d3af-115">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="9d3af-116">Při upravování velikosti bloku dat musíte být opatrní.</span><span class="sxs-lookup"><span data-stu-id="9d3af-116">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="9d3af-117">Webové prohlížeče mají různá omezení velikosti souborů cookie a počtu povolených v každé doméně.</span><span class="sxs-lookup"><span data-stu-id="9d3af-117">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="9d3af-118">Například původní specifikace Netscape tato omezení stanovila: 300 souborů cookie celkem, 4096 bajtů na hlavičku souboru cookie (včetně metadat, nikoli jenom hodnoty cookie) a 20 souborů cookie na doménu.</span><span class="sxs-lookup"><span data-stu-id="9d3af-118">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="9d3af-119">Výchozí hodnota je 2000.</span><span class="sxs-lookup"><span data-stu-id="9d3af-119">The default is 2000.</span></span> <span data-ttu-id="9d3af-120">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="9d3af-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9d3af-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9d3af-121">Child Elements</span></span>  
 <span data-ttu-id="9d3af-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="9d3af-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9d3af-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9d3af-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9d3af-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="9d3af-124">Element</span></span>|<span data-ttu-id="9d3af-125">Popis</span><span class="sxs-lookup"><span data-stu-id="9d3af-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9d3af-126">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="9d3af-126">\<cookieHandler></span></span>](cookiehandler.md)|<span data-ttu-id="9d3af-127"><xref:System.IdentityModel.Services.SessionAuthenticationModule> Nakonfiguruje <xref:System.IdentityModel.Services.CookieHandler> , jak bude (SAM) používat ke čtení a zápisu souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="9d3af-127">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9d3af-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9d3af-128">Remarks</span></span>  
 <span data-ttu-id="9d3af-129"><xref:System.IdentityModel.Services.ChunkedCookieHandler> Pokud určíte `mode` nastavením atributu `<cookieHandler>` elementu na "výchozí" nebo "bloků", můžete určit velikost bloku dat, kterou obslužná rutina souborů cookie používá `<chunkedCookieHandler>` ke čtení a zápisu souborů cookie zahrnutím podřízeného prvku a nastavení jeho `chunkSize` atributu.</span><span class="sxs-lookup"><span data-stu-id="9d3af-129">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="9d3af-130">`<chunkedCookieHandler>` Pokud element není přítomen, je použita výchozí velikost bloku 2000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="9d3af-130">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="9d3af-131">Tento element nejde zadat, pokud `mode` je atribut nastavený na Custom (vlastní).</span><span class="sxs-lookup"><span data-stu-id="9d3af-131">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="9d3af-132">Element je reprezentován <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement>třídou. `<chunkedCookieHandler>`</span><span class="sxs-lookup"><span data-stu-id="9d3af-132">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9d3af-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="9d3af-133">Example</span></span>  
 <span data-ttu-id="9d3af-134">V následujícím příkladu se konfiguruje obslužná rutina souborů cookie s proměnlivým blokem, která zapisuje soubory cookie v blocích po 3000 bajtech.</span><span class="sxs-lookup"><span data-stu-id="9d3af-134">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9d3af-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9d3af-135">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>

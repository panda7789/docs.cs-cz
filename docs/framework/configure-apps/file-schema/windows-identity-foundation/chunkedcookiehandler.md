---
title: '&lt;chunkedCookieHandler&gt;'
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: 1726d4ade9405543bdfdb4e4803f87f258de791e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691278"
---
# <a name="ltchunkedcookiehandlergt"></a><span data-ttu-id="88b23-102">&lt;chunkedCookieHandler&gt;</span><span class="sxs-lookup"><span data-stu-id="88b23-102">&lt;chunkedCookieHandler&gt;</span></span>
<span data-ttu-id="88b23-103">Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="88b23-103">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="88b23-104">Tento element může být pouze přítomen, pokud `mode` atribut `<cookieHandler>` elementu je "Výchozí" nebo "Rozdělený do bloků dat".</span><span class="sxs-lookup"><span data-stu-id="88b23-104">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="88b23-105">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="88b23-105">\<system.identityModel.services></span></span>  
<span data-ttu-id="88b23-106">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="88b23-106">\<federationConfiguration></span></span>  
<span data-ttu-id="88b23-107">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="88b23-107">\<cookieHandler></span></span>  
<span data-ttu-id="88b23-108">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="88b23-108">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88b23-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88b23-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="88b23-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="88b23-110">Attributes and Elements</span></span>  
 <span data-ttu-id="88b23-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="88b23-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="88b23-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="88b23-112">Attributes</span></span>  
  
|<span data-ttu-id="88b23-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="88b23-113">Attribute</span></span>|<span data-ttu-id="88b23-114">Popis</span><span class="sxs-lookup"><span data-stu-id="88b23-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="88b23-115">chunkSize</span><span class="sxs-lookup"><span data-stu-id="88b23-115">chunkSize</span></span>|<span data-ttu-id="88b23-116">Maximální velikost ve znacích dat souboru cookie HTTP pro všechny jednoho souboru cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="88b23-116">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="88b23-117">Musíte být opatrní při nastavování velikosti bloku.</span><span class="sxs-lookup"><span data-stu-id="88b23-117">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="88b23-118">Webových prohlížečů mají různá omezení velikosti souborů cookie a počet povolený v každé doméně.</span><span class="sxs-lookup"><span data-stu-id="88b23-118">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="88b23-119">Například původní Netscape specifikace, které stanovila tato omezení: Celkový počet souborů cookie 300, 4096 bajtů na hlavička cookie (včetně metadat, ne jenom hodnoty souboru cookie) a 20 souborů cookie na jednu doménu.</span><span class="sxs-lookup"><span data-stu-id="88b23-119">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="88b23-120">Výchozí hodnota je 2000.</span><span class="sxs-lookup"><span data-stu-id="88b23-120">The default is 2000.</span></span> <span data-ttu-id="88b23-121">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="88b23-121">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="88b23-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="88b23-122">Child Elements</span></span>  
 <span data-ttu-id="88b23-123">Žádná</span><span class="sxs-lookup"><span data-stu-id="88b23-123">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="88b23-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="88b23-124">Parent Elements</span></span>  
  
|<span data-ttu-id="88b23-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="88b23-125">Element</span></span>|<span data-ttu-id="88b23-126">Popis</span><span class="sxs-lookup"><span data-stu-id="88b23-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="88b23-127">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="88b23-127">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="88b23-128">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> , který <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) používá ke čtení a zápis souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="88b23-128">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88b23-129">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88b23-129">Remarks</span></span>  
 <span data-ttu-id="88b23-130">Při zadání <xref:System.IdentityModel.Services.ChunkedCookieHandler> nastavením `mode` atribut `<cookieHandler>` prvků "Výchozí" nebo "Bloku dat", můžete zadat velikost bloku dat, která soubor cookie obslužná rutina se používá ke čtení a zápis souborů cookie zahrnutím `<chunkedCookieHandler>` podřízený element a nastavení jeho `chunkSize` atribut.</span><span class="sxs-lookup"><span data-stu-id="88b23-130">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="88b23-131">Pokud `<chunkedCookieHandler>` prvek není k dispozici, je použit výchozí velikost bloku 2 000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="88b23-131">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="88b23-132">Tento element nemůže být zadán při `mode` atribut je nastaven na "Vlastní".</span><span class="sxs-lookup"><span data-stu-id="88b23-132">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="88b23-133">`<chunkedCookieHandler>` Prvek je reprezentován <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="88b23-133">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88b23-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="88b23-134">Example</span></span>  
 <span data-ttu-id="88b23-135">Následující příklad nastaví bloku dat souboru cookie obslužnou rutinu, která zapisuje soubory cookie v blocích 3000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="88b23-135">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="88b23-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="88b23-136">See also</span></span>
- <xref:System.IdentityModel.Services.ChunkedCookieHandler>

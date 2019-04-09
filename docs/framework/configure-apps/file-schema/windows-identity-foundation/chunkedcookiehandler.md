---
title: <chunkedCookieHandler>
ms.date: 03/30/2017
ms.assetid: 7220de45-1d14-4aec-a29e-4a2ea8ac861f
author: BrucePerlerMS
ms.openlocfilehash: d9c81d5de7bea343f0d67fa00037763fbae7b8c5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59120780"
---
# <a name="chunkedcookiehandler"></a><span data-ttu-id="0a3dc-101">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="0a3dc-101">\<chunkedCookieHandler></span></span>
<span data-ttu-id="0a3dc-102">Konfiguruje <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span><span class="sxs-lookup"><span data-stu-id="0a3dc-102">Configures the <xref:System.IdentityModel.Services.ChunkedCookieHandler>.</span></span> <span data-ttu-id="0a3dc-103">Tento element může být pouze přítomen, pokud `mode` atribut `<cookieHandler>` elementu je "Výchozí" nebo "Rozdělený do bloků dat".</span><span class="sxs-lookup"><span data-stu-id="0a3dc-103">This element may only be present if the `mode` attribute of the `<cookieHandler>` element is "Default" or "Chunked".</span></span>  
  
 <span data-ttu-id="0a3dc-104">\<system.identityModel.services></span><span class="sxs-lookup"><span data-stu-id="0a3dc-104">\<system.identityModel.services></span></span>  
<span data-ttu-id="0a3dc-105">\<federationConfiguration></span><span class="sxs-lookup"><span data-stu-id="0a3dc-105">\<federationConfiguration></span></span>  
<span data-ttu-id="0a3dc-106">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="0a3dc-106">\<cookieHandler></span></span>  
<span data-ttu-id="0a3dc-107">\<chunkedCookieHandler></span><span class="sxs-lookup"><span data-stu-id="0a3dc-107">\<chunkedCookieHandler></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a3dc-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0a3dc-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a3dc-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0a3dc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="0a3dc-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0a3dc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a3dc-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="0a3dc-111">Attributes</span></span>  
  
|<span data-ttu-id="0a3dc-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="0a3dc-112">Attribute</span></span>|<span data-ttu-id="0a3dc-113">Popis</span><span class="sxs-lookup"><span data-stu-id="0a3dc-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a3dc-114">chunkSize</span><span class="sxs-lookup"><span data-stu-id="0a3dc-114">chunkSize</span></span>|<span data-ttu-id="0a3dc-115">Maximální velikost ve znacích dat souboru cookie HTTP pro všechny jednoho souboru cookie HTTP.</span><span class="sxs-lookup"><span data-stu-id="0a3dc-115">The maximum size, in characters, of the HTTP cookie data for any one HTTP cookie.</span></span> <span data-ttu-id="0a3dc-116">Musíte být opatrní při nastavování velikosti bloku.</span><span class="sxs-lookup"><span data-stu-id="0a3dc-116">You must be careful when adjusting the chunk size.</span></span> <span data-ttu-id="0a3dc-117">Webových prohlížečů mají různá omezení velikosti souborů cookie a počet povolený v každé doméně.</span><span class="sxs-lookup"><span data-stu-id="0a3dc-117">Web browsers have different limits on the size of cookies and number allowed per domain.</span></span> <span data-ttu-id="0a3dc-118">Například původní Netscape specifikace, které stanovila tato omezení: Celkový počet souborů cookie 300, 4096 bajtů na hlavička cookie (včetně metadat, ne jenom hodnoty souboru cookie) a 20 souborů cookie na jednu doménu.</span><span class="sxs-lookup"><span data-stu-id="0a3dc-118">For example, the original Netscape specification stipulated these limits: 300 cookies total, 4096 bytes per cookie header (including metadata, not just the cookie value), and 20 cookies per domain.</span></span> <span data-ttu-id="0a3dc-119">Výchozí hodnota je 2000.</span><span class="sxs-lookup"><span data-stu-id="0a3dc-119">The default is 2000.</span></span> <span data-ttu-id="0a3dc-120">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="0a3dc-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a3dc-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0a3dc-121">Child Elements</span></span>  
 <span data-ttu-id="0a3dc-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="0a3dc-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a3dc-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0a3dc-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0a3dc-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="0a3dc-124">Element</span></span>|<span data-ttu-id="0a3dc-125">Popis</span><span class="sxs-lookup"><span data-stu-id="0a3dc-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a3dc-126">\<cookieHandler></span><span class="sxs-lookup"><span data-stu-id="0a3dc-126">\<cookieHandler></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|<span data-ttu-id="0a3dc-127">Konfiguruje <xref:System.IdentityModel.Services.CookieHandler> , který <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) používá ke čtení a zápis souborů cookie.</span><span class="sxs-lookup"><span data-stu-id="0a3dc-127">Configures the <xref:System.IdentityModel.Services.CookieHandler> that the <xref:System.IdentityModel.Services.SessionAuthenticationModule> (SAM) uses to read and write cookies.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a3dc-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0a3dc-128">Remarks</span></span>  
 <span data-ttu-id="0a3dc-129">Při zadání <xref:System.IdentityModel.Services.ChunkedCookieHandler> nastavením `mode` atribut `<cookieHandler>` prvků "Výchozí" nebo "Bloku dat", můžete zadat velikost bloku dat, která soubor cookie obslužná rutina se používá ke čtení a zápis souborů cookie zahrnutím `<chunkedCookieHandler>` podřízený element a nastavení jeho `chunkSize` atribut.</span><span class="sxs-lookup"><span data-stu-id="0a3dc-129">When you specify a <xref:System.IdentityModel.Services.ChunkedCookieHandler> by setting the `mode` attribute of the `<cookieHandler>` element to "Default" or "Chunked", you can specify the chunk size that the cookie handler uses to read and write cookies by including a `<chunkedCookieHandler>` child element and setting its `chunkSize` attribute.</span></span> <span data-ttu-id="0a3dc-130">Pokud `<chunkedCookieHandler>` prvek není k dispozici, je použit výchozí velikost bloku 2 000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="0a3dc-130">If the `<chunkedCookieHandler>` element is not present, the default chunk size of 2000 bytes is used.</span></span> <span data-ttu-id="0a3dc-131">Tento element nemůže být zadán při `mode` atribut je nastaven na "Vlastní".</span><span class="sxs-lookup"><span data-stu-id="0a3dc-131">This element cannot be specified when the `mode` attribute is set to "Custom".</span></span>  
  
 <span data-ttu-id="0a3dc-132">`<chunkedCookieHandler>` Prvek je reprezentován <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> třídy.</span><span class="sxs-lookup"><span data-stu-id="0a3dc-132">The `<chunkedCookieHandler>` element is represented by the <xref:System.IdentityModel.Services.ChunkedCookieHandlerElement> class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a3dc-133">Příklad</span><span class="sxs-lookup"><span data-stu-id="0a3dc-133">Example</span></span>  
 <span data-ttu-id="0a3dc-134">Následující příklad nastaví bloku dat souboru cookie obslužnou rutinu, která zapisuje soubory cookie v blocích 3000 bajtů.</span><span class="sxs-lookup"><span data-stu-id="0a3dc-134">The following example configures a chunked cookie handler that writes cookies in chunks of 3000 bytes.</span></span>  
  
```xml  
<cookieHandler mode="Chunked">  
    <chunkedCookieHandler chunkSize=3000/>  
</cookieHandler>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a3dc-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0a3dc-135">See also</span></span>

- <xref:System.IdentityModel.Services.ChunkedCookieHandler>

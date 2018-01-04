---
title: "&lt;Přidat&gt; Element pro webRequestModules – (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
caps.latest.revision: "16"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 9b7d2c0f52ea42fcb98be149ab005cd67c2db46a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="a1bd0-102">&lt;Přidat&gt; Element pro webRequestModules – (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="a1bd0-102">&lt;add&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="a1bd0-103">Přidá vlastní modul žádost webové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a1bd0-103">Adds a custom Web request module to the application.</span></span>  
  
 <span data-ttu-id="a1bd0-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="a1bd0-104">\<configuration></span></span>  
<span data-ttu-id="a1bd0-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="a1bd0-105">\<system.net></span></span>  
<span data-ttu-id="a1bd0-106">\<webRequestModules – ></span><span class="sxs-lookup"><span data-stu-id="a1bd0-106">\<webRequestModules></span></span>  
<span data-ttu-id="a1bd0-107">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="a1bd0-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1bd0-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a1bd0-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a1bd0-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a1bd0-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a1bd0-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a1bd0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a1bd0-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="a1bd0-111">Attributes</span></span>  
  
|<span data-ttu-id="a1bd0-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="a1bd0-112">**Attribute**</span></span>|<span data-ttu-id="a1bd0-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="a1bd0-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="a1bd0-114">Předpony identifikátoru URI pro tento webový modul požadavek zpracovává požadavky.</span><span class="sxs-lookup"><span data-stu-id="a1bd0-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="a1bd0-115">Plně kvalifikovaného názvu (indikován <xref:System.Type.FullName%2A> vlastnosti) a název sestavení (indikován <xref:System.Reflection.Assembly.FullName%2A> vlastnost), oddělené čárkou, který implementuje tento modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="a1bd0-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a1bd0-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a1bd0-116">Child Elements</span></span>  
 <span data-ttu-id="a1bd0-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="a1bd0-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a1bd0-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a1bd0-118">Parent Elements</span></span>  
  
|<span data-ttu-id="a1bd0-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="a1bd0-119">**Element**</span></span>|<span data-ttu-id="a1bd0-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="a1bd0-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a1bd0-121">webRequestModules –</span><span class="sxs-lookup"><span data-stu-id="a1bd0-121">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="a1bd0-122">Určuje moduly sloužící k požadavku na informace z hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="a1bd0-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1bd0-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a1bd0-123">Remarks</span></span>  
 <span data-ttu-id="a1bd0-124">`prefix` Atribut definuje předpony identifikátoru URI, který používá zadaný modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="a1bd0-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="a1bd0-125">Webové žádosti moduly jsou běžně registrovány pro zpracování určitého protokolu, jako je například HTTP nebo FTP, ale lze zaregistrovat pro zpracování požadavku na konkrétní server nebo k adresáři na serveru.</span><span class="sxs-lookup"><span data-stu-id="a1bd0-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="a1bd0-126">Modul webové žádosti se vytvoří při porovnávání předpony identifikátoru URI je předána <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="a1bd0-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="a1bd0-127">Hodnota `prefix` atribut by měl mít počáteční znaky platný identifikátor URI – například "http" nebo "http://www.contoso.com".</span><span class="sxs-lookup"><span data-stu-id="a1bd0-127">The value for the `prefix` attribute should be the leading characters of a valid URI --for example, "http", or "http://www.contoso.com".</span></span>  
  
 <span data-ttu-id="a1bd0-128">Hodnota `type` atribut by měl mít název platného typu a odpovídající název sestavení, oddělených čárkou.</span><span class="sxs-lookup"><span data-stu-id="a1bd0-128">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma .</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a1bd0-129">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="a1bd0-129">Configuration Files</span></span>  
 <span data-ttu-id="a1bd0-130">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="a1bd0-130">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a1bd0-131">Příklad</span><span class="sxs-lookup"><span data-stu-id="a1bd0-131">Example</span></span>  
 <span data-ttu-id="a1bd0-132">Následující příklad zaregistruje vlastní modul webové žádosti HTTP.</span><span class="sxs-lookup"><span data-stu-id="a1bd0-132">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="a1bd0-133">Měli byste nahradit hodnoty verze a PublicKeyToken správné hodnoty pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="a1bd0-133">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a1bd0-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="a1bd0-134">See Also</span></span>  
 <xref:System.Net.WebRequest>  
 [<span data-ttu-id="a1bd0-135">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="a1bd0-135">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

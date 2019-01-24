---
title: '&lt;Přidat&gt; – Element pro webRequestModules (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
ms.openlocfilehash: d78405546d00797677134e038bbaa69bf088f88e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54575707"
---
# <a name="ltaddgt-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="4d2c9-102">&lt;Přidat&gt; – Element pro webRequestModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="4d2c9-102">&lt;add&gt; Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="4d2c9-103">Přidá vlastní modul webové žádosti do aplikace.</span><span class="sxs-lookup"><span data-stu-id="4d2c9-103">Adds a custom Web request module to the application.</span></span>  
  
 <span data-ttu-id="4d2c9-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="4d2c9-104">\<configuration></span></span>  
<span data-ttu-id="4d2c9-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="4d2c9-105">\<system.net></span></span>  
<span data-ttu-id="4d2c9-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="4d2c9-106">\<webRequestModules></span></span>  
<span data-ttu-id="4d2c9-107">\<add></span><span class="sxs-lookup"><span data-stu-id="4d2c9-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d2c9-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4d2c9-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d2c9-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4d2c9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4d2c9-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4d2c9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d2c9-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="4d2c9-111">Attributes</span></span>  
  
|<span data-ttu-id="4d2c9-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="4d2c9-112">**Attribute**</span></span>|<span data-ttu-id="4d2c9-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="4d2c9-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="4d2c9-114">Předponu identifikátoru URI pro žádosti zpracovat tento modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="4d2c9-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="4d2c9-115">Plně kvalifikovaného názvu (indikován <xref:System.Type.FullName%2A> vlastnost) a název sestavení (indikován <xref:System.Reflection.Assembly.FullName%2A> vlastnost), oddělená čárkou, která implementuje tento modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="4d2c9-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d2c9-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4d2c9-116">Child Elements</span></span>  
 <span data-ttu-id="4d2c9-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="4d2c9-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d2c9-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4d2c9-118">Parent Elements</span></span>  
  
|<span data-ttu-id="4d2c9-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="4d2c9-119">**Element**</span></span>|<span data-ttu-id="4d2c9-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="4d2c9-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="4d2c9-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="4d2c9-121">webRequestModules</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|<span data-ttu-id="4d2c9-122">Určuje moduly, které použijte k vyžádání informace z hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="4d2c9-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4d2c9-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4d2c9-123">Remarks</span></span>  
 <span data-ttu-id="4d2c9-124">`prefix` Atribut definuje předponu identifikátoru URI, který používá zadaný modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="4d2c9-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="4d2c9-125">Webové žádosti moduly jsou běžně registrovány pro zpracování konkrétní protokolu, jako je například HTTP nebo FTP, ale může být registrován pro obsluhu žádost pro konkrétní server nebo cesta na serveru.</span><span class="sxs-lookup"><span data-stu-id="4d2c9-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="4d2c9-126">Webový požadavek modul se vytvoří při odpovídající předpony identifikátoru URI je předán <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="4d2c9-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="4d2c9-127">Hodnota `prefix` atribut by měl mít počáteční znaky platný identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="4d2c9-127">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="4d2c9-128">Například `http` nebo `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="4d2c9-128">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="4d2c9-129">Hodnota `type` atribut by měl být platný název typu a odpovídající název sestavení, oddělených čárkami.</span><span class="sxs-lookup"><span data-stu-id="4d2c9-129">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="4d2c9-130">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="4d2c9-130">Configuration Files</span></span>  
 <span data-ttu-id="4d2c9-131">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="4d2c9-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4d2c9-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="4d2c9-132">Example</span></span>  
 <span data-ttu-id="4d2c9-133">Následující příklad registruje vlastní modul webového požadavku pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="4d2c9-133">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="4d2c9-134">Měli byste nahradit hodnoty pro verzi a PublicKeyToken správné hodnoty pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="4d2c9-134">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="4d2c9-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4d2c9-135">See also</span></span>
- <xref:System.Net.WebRequest>
- [<span data-ttu-id="4d2c9-136">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="4d2c9-136">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

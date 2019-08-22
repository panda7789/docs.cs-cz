---
title: <add> – element pro webRequestModules (nastavení sítě)
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
ms.openlocfilehash: f99c5b0dc7eab57d4e3e86f49dbbb3228c7b7d8b
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664209"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="cda3e-102">\<Přidat > element pro webRequestModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="cda3e-102">\<add> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="cda3e-103">Přidá do aplikace vlastní modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="cda3e-103">Adds a custom Web request module to the application.</span></span>  
  
 <span data-ttu-id="cda3e-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="cda3e-104">\<configuration></span></span>  
<span data-ttu-id="cda3e-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="cda3e-105">\<system.net></span></span>  
<span data-ttu-id="cda3e-106">\<webRequestModules></span><span class="sxs-lookup"><span data-stu-id="cda3e-106">\<webRequestModules></span></span>  
<span data-ttu-id="cda3e-107">\<add></span><span class="sxs-lookup"><span data-stu-id="cda3e-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cda3e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cda3e-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cda3e-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cda3e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="cda3e-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cda3e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cda3e-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="cda3e-111">Attributes</span></span>  
  
|<span data-ttu-id="cda3e-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="cda3e-112">**Attribute**</span></span>|<span data-ttu-id="cda3e-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="cda3e-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="cda3e-114">Předpona identifikátoru URI pro požadavky zpracovávané tímto modulem webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="cda3e-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="cda3e-115">Plně kvalifikovaný název typu (uvedený <xref:System.Type.FullName%2A> vlastností) a název sestavení (označeno <xref:System.Reflection.Assembly.FullName%2A> vlastností), které jsou odděleny čárkou, která implementuje tento modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="cda3e-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cda3e-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cda3e-116">Child Elements</span></span>  
 <span data-ttu-id="cda3e-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="cda3e-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cda3e-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cda3e-118">Parent Elements</span></span>  
  
|<span data-ttu-id="cda3e-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="cda3e-119">**Element**</span></span>|<span data-ttu-id="cda3e-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="cda3e-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cda3e-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="cda3e-121">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="cda3e-122">Určuje moduly, které se použijí k vyžádání informací od hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="cda3e-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cda3e-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cda3e-123">Remarks</span></span>  
 <span data-ttu-id="cda3e-124">`prefix` Atribut definuje předponu identifikátoru URI, která používá zadaný modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="cda3e-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="cda3e-125">Moduly webových požadavků jsou obvykle registrovány pro zpracování konkrétního protokolu, například HTTP nebo FTP, ale mohou být registrovány pro zpracování požadavku na konkrétní server nebo cestu na serveru.</span><span class="sxs-lookup"><span data-stu-id="cda3e-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="cda3e-126">Modul webové žádosti je vytvořen při předání <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> předpony odpovídajícího identifikátoru URI metodě.</span><span class="sxs-lookup"><span data-stu-id="cda3e-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="cda3e-127">Hodnota `prefix` atributu by měla být předními znaky platného identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="cda3e-127">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="cda3e-128">Například `http` nebo `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="cda3e-128">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="cda3e-129">Hodnota `type` atributu by měla být platný název typu a odpovídající název sestavení oddělený čárkou.</span><span class="sxs-lookup"><span data-stu-id="cda3e-129">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="cda3e-130">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="cda3e-130">Configuration Files</span></span>  
 <span data-ttu-id="cda3e-131">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="cda3e-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cda3e-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="cda3e-132">Example</span></span>  
 <span data-ttu-id="cda3e-133">Následující příklad registruje vlastní modul webové žádosti pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="cda3e-133">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="cda3e-134">Hodnoty pro Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="cda3e-134">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="cda3e-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cda3e-135">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="cda3e-136">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="cda3e-136">Network Settings Schema</span></span>](index.md)

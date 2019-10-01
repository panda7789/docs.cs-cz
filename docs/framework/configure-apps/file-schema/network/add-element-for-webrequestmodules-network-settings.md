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
ms.openlocfilehash: 0248706ed78de160ef0131a0c7595374febf1aa9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699578"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="8032b-102">@no__t – element > 0add pro webRequestModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="8032b-102">\<add> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="8032b-103">Přidá do aplikace vlastní modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="8032b-103">Adds a custom Web request module to the application.</span></span>  
  
[<span data-ttu-id="8032b-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="8032b-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="8032b-105">&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8032b-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="8032b-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<webRequestModules >** ](webrequestmodules-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8032b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)</span></span>  
<span data-ttu-id="8032b-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<add >**</span><span class="sxs-lookup"><span data-stu-id="8032b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8032b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8032b-108">Syntax</span></span>  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8032b-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8032b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8032b-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8032b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8032b-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="8032b-111">Attributes</span></span>  
  
|<span data-ttu-id="8032b-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="8032b-112">**Attribute**</span></span>|<span data-ttu-id="8032b-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="8032b-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="8032b-114">Předpona identifikátoru URI pro požadavky zpracovávané tímto modulem webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="8032b-114">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="8032b-115">Plně kvalifikovaný název typu (uvedený vlastností <xref:System.Type.FullName%2A>) a název sestavení (s vlastností <xref:System.Reflection.Assembly.FullName%2A>), které jsou odděleny čárkou, která implementuje tento modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="8032b-115">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8032b-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8032b-116">Child Elements</span></span>  
 <span data-ttu-id="8032b-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="8032b-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8032b-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8032b-118">Parent Elements</span></span>  
  
|<span data-ttu-id="8032b-119">**Element**</span><span class="sxs-lookup"><span data-stu-id="8032b-119">**Element**</span></span>|<span data-ttu-id="8032b-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="8032b-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8032b-121">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="8032b-121">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="8032b-122">Určuje moduly, které se použijí k vyžádání informací od hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="8032b-122">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8032b-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8032b-123">Remarks</span></span>  
 <span data-ttu-id="8032b-124">Atribut `prefix` definuje předponu identifikátoru URI, která používá zadaný modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="8032b-124">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="8032b-125">Moduly webových požadavků jsou obvykle registrovány pro zpracování konkrétního protokolu, například HTTP nebo FTP, ale mohou být registrovány pro zpracování požadavku na konkrétní server nebo cestu na serveru.</span><span class="sxs-lookup"><span data-stu-id="8032b-125">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="8032b-126">Modul webové žádosti se vytvoří, když je předpona odpovídajícího identifikátoru URI předána metodě <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8032b-126">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="8032b-127">Hodnota atributu `prefix` by měla být předními znaky platného identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="8032b-127">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="8032b-128">Například `http` nebo `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="8032b-128">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="8032b-129">Hodnota pro atribut `type` by měla být platný název typu a odpovídající název sestavení oddělený čárkou.</span><span class="sxs-lookup"><span data-stu-id="8032b-129">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="8032b-130">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="8032b-130">Configuration Files</span></span>  
 <span data-ttu-id="8032b-131">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="8032b-131">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8032b-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="8032b-132">Example</span></span>  
 <span data-ttu-id="8032b-133">Následující příklad registruje vlastní modul webové žádosti pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="8032b-133">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="8032b-134">Hodnoty pro Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="8032b-134">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8032b-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8032b-135">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="8032b-136">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="8032b-136">Network Settings Schema</span></span>](index.md)

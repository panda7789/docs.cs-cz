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
ms.openlocfilehash: f4edce948033478aab59a2aff61abadc55a327ce
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155021"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a><span data-ttu-id="57cd5-102">\<add> – element pro webRequestModules (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="57cd5-102">\<add> Element for webRequestModules (Network Settings)</span></span>
<span data-ttu-id="57cd5-103">Přidá do aplikace vlastní modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="57cd5-103">Adds a custom Web request module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="57cd5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="57cd5-104">Syntax</span></span>  
  
```xml  
<add
  prefix="URI prefix"
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="57cd5-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="57cd5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="57cd5-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="57cd5-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="57cd5-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="57cd5-107">Attributes</span></span>  
  
|<span data-ttu-id="57cd5-108">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="57cd5-108">**Attribute**</span></span>|<span data-ttu-id="57cd5-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="57cd5-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`prefix`|<span data-ttu-id="57cd5-110">Předpona identifikátoru URI pro požadavky zpracovávané tímto modulem webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="57cd5-110">The URI prefix for requests handled by this Web request module.</span></span>|  
|`type`|<span data-ttu-id="57cd5-111">Plně kvalifikovaný název typu (uvedený <xref:System.Type.FullName%2A> vlastností) a název sestavení (označeno <xref:System.Reflection.Assembly.FullName%2A> vlastností), které jsou odděleny čárkou, která implementuje tento modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="57cd5-111">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements this Web request module.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="57cd5-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="57cd5-112">Child Elements</span></span>  
 <span data-ttu-id="57cd5-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="57cd5-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="57cd5-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="57cd5-114">Parent Elements</span></span>  
  
|<span data-ttu-id="57cd5-115">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="57cd5-115">**Element**</span></span>|<span data-ttu-id="57cd5-116">**Popis**</span><span class="sxs-lookup"><span data-stu-id="57cd5-116">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="57cd5-117">webRequestModules</span><span class="sxs-lookup"><span data-stu-id="57cd5-117">webRequestModules</span></span>](webrequestmodules-element-network-settings.md)|<span data-ttu-id="57cd5-118">Určuje moduly, které se použijí k vyžádání informací od hostitelů v síti.</span><span class="sxs-lookup"><span data-stu-id="57cd5-118">Specifies modules to use to request information from network hosts.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="57cd5-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="57cd5-119">Remarks</span></span>  
 <span data-ttu-id="57cd5-120">`prefix`Atribut definuje předponu identifikátoru URI, která používá zadaný modul webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="57cd5-120">The `prefix` attribute defines the URI prefix that uses the specified Web request module.</span></span> <span data-ttu-id="57cd5-121">Moduly webových požadavků jsou obvykle registrovány pro zpracování konkrétního protokolu, například HTTP nebo FTP, ale mohou být registrovány pro zpracování požadavku na konkrétní server nebo cestu na serveru.</span><span class="sxs-lookup"><span data-stu-id="57cd5-121">Web request modules are typically registered to handle a specific protocol, such as HTTP or FTP, but can be registered to handle a request to a specific server or path on a server.</span></span>  
  
 <span data-ttu-id="57cd5-122">Modul webové žádosti je vytvořen při předání předpony odpovídajícího identifikátoru URI <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metodě.</span><span class="sxs-lookup"><span data-stu-id="57cd5-122">The Web request module is created when a URI matching prefix is passed to the <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="57cd5-123">Hodnota `prefix` atributu by měla být předními znaky platného identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="57cd5-123">The value for the `prefix` attribute should be the leading characters of a valid URI.</span></span> <span data-ttu-id="57cd5-124">Příkladem je `http` nebo `http://www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="57cd5-124">For example, `http` or `http://www.contoso.com`.</span></span>
  
 <span data-ttu-id="57cd5-125">Hodnota `type` atributu by měla být platný název typu a odpovídající název sestavení oddělený čárkou.</span><span class="sxs-lookup"><span data-stu-id="57cd5-125">The value for the `type` attribute should be a valid type name and corresponding assembly name, separated by a comma.</span></span>
  
## <a name="configuration-files"></a><span data-ttu-id="57cd5-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="57cd5-126">Configuration Files</span></span>  
 <span data-ttu-id="57cd5-127">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="57cd5-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="57cd5-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="57cd5-128">Example</span></span>  
 <span data-ttu-id="57cd5-129">Následující příklad registruje vlastní modul webové žádosti pro protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="57cd5-129">The following example registers a custom Web request module for HTTP.</span></span> <span data-ttu-id="57cd5-130">Hodnoty pro Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.</span><span class="sxs-lookup"><span data-stu-id="57cd5-130">You should replace the values for Version and PublicKeyToken with the correct values for the specified module.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="57cd5-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="57cd5-131">See also</span></span>

- <xref:System.Net.WebRequest>
- [<span data-ttu-id="57cd5-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="57cd5-132">Network Settings Schema</span></span>](index.md)

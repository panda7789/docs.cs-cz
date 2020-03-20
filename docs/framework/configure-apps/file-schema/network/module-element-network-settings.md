---
title: <module> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: ed28ae4a52085cbfa781b4baf2ee1eafbeff6eb4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154826"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="05381-102">\<modul> Element (Nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="05381-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="05381-103">Přidá do aplikace nový proxy modul.</span><span class="sxs-lookup"><span data-stu-id="05381-103">Adds a new proxy module to the application.</span></span>  

<span data-ttu-id="05381-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="05381-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="05381-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="05381-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="05381-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="05381-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)</span></span>\
<span data-ttu-id="05381-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>modulu**</span><span class="sxs-lookup"><span data-stu-id="05381-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**</span></span>

## <a name="syntax"></a><span data-ttu-id="05381-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05381-108">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05381-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="05381-109">Attributes and Elements</span></span>  
 <span data-ttu-id="05381-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="05381-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05381-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="05381-111">Attributes</span></span>  
  
|<span data-ttu-id="05381-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="05381-112">**Attribute**</span></span>|<span data-ttu-id="05381-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="05381-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="05381-114">Plně kvalifikovaný název typu (označený <xref:System.Type.FullName%2A> vlastností) a název sestavení <xref:System.Reflection.Assembly.FullName%2A> (označený vlastností), oddělený čárkou, který implementuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="05381-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05381-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="05381-115">Child Elements</span></span>  
 <span data-ttu-id="05381-116">Žádné.</span><span class="sxs-lookup"><span data-stu-id="05381-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05381-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="05381-117">Parent Elements</span></span>  
  
|<span data-ttu-id="05381-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="05381-118">**Element**</span></span>|<span data-ttu-id="05381-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="05381-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="05381-120">výchozí proxy</span><span class="sxs-lookup"><span data-stu-id="05381-120">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="05381-121">Konfiguruje proxy server HTTP (HTTP).</span><span class="sxs-lookup"><span data-stu-id="05381-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05381-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05381-122">Remarks</span></span>  
 <span data-ttu-id="05381-123">Prvek `module` registruje proxy třídy, které implementují <xref:System.Net.IWebProxy> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="05381-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="05381-124">Po registraci třídy `module` proxy lze požádat o informace prostřednictvím podporovaného proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="05381-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="05381-125">Hodnotou atributu `type` by měl být název třídy modulu a název odpovídající knihovny dynamických odkazů (DLL).</span><span class="sxs-lookup"><span data-stu-id="05381-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="05381-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="05381-126">Configuration Files</span></span>  
 <span data-ttu-id="05381-127">Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="05381-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05381-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="05381-128">Example</span></span>  
 <span data-ttu-id="05381-129">Následující příklad registruje vlastní třídu proxy.</span><span class="sxs-lookup"><span data-stu-id="05381-129">The following example registers a custom proxy class.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="05381-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="05381-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="05381-131">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="05381-131">Network Settings Schema</span></span>](index.md)

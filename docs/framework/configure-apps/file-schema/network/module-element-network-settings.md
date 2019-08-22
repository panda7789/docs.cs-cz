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
ms.openlocfilehash: 851a63b41dfb5d3b4058e1373148f48d47d9d6ae
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664073"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="415c4-102">\<Module > – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="415c4-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="415c4-103">Přidá do aplikace nový modul proxy.</span><span class="sxs-lookup"><span data-stu-id="415c4-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="415c4-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="415c4-104">\<configuration></span></span>  
<span data-ttu-id="415c4-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="415c4-105">\<system.net></span></span>  
<span data-ttu-id="415c4-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="415c4-106">\<defaultProxy></span></span>  
<span data-ttu-id="415c4-107">\<> modulu</span><span class="sxs-lookup"><span data-stu-id="415c4-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="415c4-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="415c4-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="415c4-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="415c4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="415c4-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="415c4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="415c4-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="415c4-111">Attributes</span></span>  
  
|<span data-ttu-id="415c4-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="415c4-112">**Attribute**</span></span>|<span data-ttu-id="415c4-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="415c4-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="415c4-114">Plně kvalifikovaný název typu (uvedený <xref:System.Type.FullName%2A> vlastností) a název sestavení (označeno <xref:System.Reflection.Assembly.FullName%2A> vlastností), které jsou odděleny čárkou, která implementuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="415c4-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="415c4-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="415c4-115">Child Elements</span></span>  
 <span data-ttu-id="415c4-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="415c4-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="415c4-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="415c4-117">Parent Elements</span></span>  
  
|<span data-ttu-id="415c4-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="415c4-118">**Element**</span></span>|<span data-ttu-id="415c4-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="415c4-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="415c4-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="415c4-120">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="415c4-121">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="415c4-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="415c4-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="415c4-122">Remarks</span></span>  
 <span data-ttu-id="415c4-123">Element registruje proxy třídy, které <xref:System.Net.IWebProxy> implementují rozhraní. `module`</span><span class="sxs-lookup"><span data-stu-id="415c4-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="415c4-124">Po registraci třídy `module` proxy lze použít k žádosti o informace prostřednictvím podporovaného proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="415c4-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="415c4-125">Hodnota `type` atributu by měla být název třídy modulu a název odpovídající knihovny DLL (Dynamic Link Library).</span><span class="sxs-lookup"><span data-stu-id="415c4-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="415c4-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="415c4-126">Configuration Files</span></span>  
 <span data-ttu-id="415c4-127">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="415c4-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="415c4-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="415c4-128">Example</span></span>  
 <span data-ttu-id="415c4-129">Následující příklad registruje vlastní třídu proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="415c4-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="415c4-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="415c4-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="415c4-131">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="415c4-131">Network Settings Schema</span></span>](index.md)

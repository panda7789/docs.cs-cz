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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154826"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="0ce1d-102">\<module> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="0ce1d-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="0ce1d-103">Přidá do aplikace nový modul proxy.</span><span class="sxs-lookup"><span data-stu-id="0ce1d-103">Adds a new proxy module to the application.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultProxy>**](defaultproxy-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<module>**

## <a name="syntax"></a><span data-ttu-id="0ce1d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ce1d-104">Syntax</span></span>  
  
```xml  
<module
  type="type_fullname, assembly_fullname"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ce1d-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="0ce1d-105">Attributes and Elements</span></span>  
 <span data-ttu-id="0ce1d-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="0ce1d-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ce1d-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="0ce1d-107">Attributes</span></span>  
  
|<span data-ttu-id="0ce1d-108">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="0ce1d-108">**Attribute**</span></span>|<span data-ttu-id="0ce1d-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="0ce1d-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="0ce1d-110">Plně kvalifikovaný název typu (uvedený <xref:System.Type.FullName%2A> vlastností) a název sestavení (označeno <xref:System.Reflection.Assembly.FullName%2A> vlastností), které jsou odděleny čárkou, která implementuje proxy server.</span><span class="sxs-lookup"><span data-stu-id="0ce1d-110">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0ce1d-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="0ce1d-111">Child Elements</span></span>  
 <span data-ttu-id="0ce1d-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="0ce1d-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0ce1d-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="0ce1d-113">Parent Elements</span></span>  
  
|<span data-ttu-id="0ce1d-114">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="0ce1d-114">**Element**</span></span>|<span data-ttu-id="0ce1d-115">**Popis**</span><span class="sxs-lookup"><span data-stu-id="0ce1d-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="0ce1d-116">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="0ce1d-116">defaultProxy</span></span>](defaultproxy-element-network-settings.md)|<span data-ttu-id="0ce1d-117">Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).</span><span class="sxs-lookup"><span data-stu-id="0ce1d-117">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ce1d-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ce1d-118">Remarks</span></span>  
 <span data-ttu-id="0ce1d-119">`module`Element registruje proxy třídy, které implementují <xref:System.Net.IWebProxy> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0ce1d-119">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="0ce1d-120">Po registraci třídy proxy `module` lze použít k žádosti o informace prostřednictvím podporovaného proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="0ce1d-120">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="0ce1d-121">Hodnota `type` atributu by měla být název třídy modulu a název odpovídající knihovny DLL (Dynamic Link Library).</span><span class="sxs-lookup"><span data-stu-id="0ce1d-121">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="0ce1d-122">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="0ce1d-122">Configuration Files</span></span>  
 <span data-ttu-id="0ce1d-123">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="0ce1d-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ce1d-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ce1d-124">Example</span></span>  
 <span data-ttu-id="0ce1d-125">Následující příklad registruje vlastní třídu proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="0ce1d-125">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0ce1d-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="0ce1d-126">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="0ce1d-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="0ce1d-127">Network Settings Schema</span></span>](index.md)

---
title: '&lt;modul&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 06c653d8759224e1112183a7e86e9797a97402af
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753765"
---
# <a name="ltmodulegt-element-network-settings"></a><span data-ttu-id="2ed0b-102">&lt;modul&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="2ed0b-102">&lt;module&gt; Element (Network Settings)</span></span>
<span data-ttu-id="2ed0b-103">Přidá nový modul proxy serveru k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="2ed0b-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="2ed0b-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="2ed0b-104">\<configuration></span></span>  
<span data-ttu-id="2ed0b-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="2ed0b-105">\<system.net></span></span>  
<span data-ttu-id="2ed0b-106">\<defaultProxy – ></span><span class="sxs-lookup"><span data-stu-id="2ed0b-106">\<defaultProxy></span></span>  
<span data-ttu-id="2ed0b-107">\<modul ></span><span class="sxs-lookup"><span data-stu-id="2ed0b-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ed0b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ed0b-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ed0b-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2ed0b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2ed0b-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2ed0b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ed0b-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2ed0b-111">Attributes</span></span>  
  
|<span data-ttu-id="2ed0b-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="2ed0b-112">**Attribute**</span></span>|<span data-ttu-id="2ed0b-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="2ed0b-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="2ed0b-114">Zadejte plně kvalifikovaný název (indikován <xref:System.Type.FullName%2A> vlastnost) a název sestavení (indikován <xref:System.Reflection.Assembly.FullName%2A> vlastnost), oddělené čárkou, který implementuje proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="2ed0b-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ed0b-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2ed0b-115">Child Elements</span></span>  
 <span data-ttu-id="2ed0b-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="2ed0b-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ed0b-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2ed0b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="2ed0b-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="2ed0b-118">**Element**</span></span>|<span data-ttu-id="2ed0b-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="2ed0b-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2ed0b-120">defaultProxy –</span><span class="sxs-lookup"><span data-stu-id="2ed0b-120">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="2ed0b-121">Nakonfiguruje server proxy protokolu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="2ed0b-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ed0b-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ed0b-122">Remarks</span></span>  
 <span data-ttu-id="2ed0b-123">`module` Element zaregistruje třídy proxy, které implementují <xref:System.Net.IWebProxy> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2ed0b-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="2ed0b-124">Po registraci třídu proxy `module` slouží k vyžádání informací prostřednictvím podporovaných proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="2ed0b-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="2ed0b-125">Hodnota `type` atribut by měl mít název třídy modulu a názvu z jeho odpovídající dynamického propojení knihovny (DLL).</span><span class="sxs-lookup"><span data-stu-id="2ed0b-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2ed0b-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="2ed0b-126">Configuration Files</span></span>  
 <span data-ttu-id="2ed0b-127">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="2ed0b-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ed0b-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="2ed0b-128">Example</span></span>  
 <span data-ttu-id="2ed0b-129">Následující příklad zaregistruje třídu vlastní proxy server.</span><span class="sxs-lookup"><span data-stu-id="2ed0b-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ed0b-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ed0b-130">See Also</span></span>  
 <xref:System.Net.IWebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="2ed0b-131">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="2ed0b-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

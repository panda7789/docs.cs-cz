---
title: "&lt;modul&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a039f6ed985997c5557659abd299fe0fc7699a1b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltmodulegt-element-network-settings"></a><span data-ttu-id="eca22-102">&lt;modul&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="eca22-102">&lt;module&gt; Element (Network Settings)</span></span>
<span data-ttu-id="eca22-103">Přidá nový modul proxy serveru k aplikaci.</span><span class="sxs-lookup"><span data-stu-id="eca22-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="eca22-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="eca22-104">\<configuration></span></span>  
<span data-ttu-id="eca22-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="eca22-105">\<system.net></span></span>  
<span data-ttu-id="eca22-106">\<defaultProxy – ></span><span class="sxs-lookup"><span data-stu-id="eca22-106">\<defaultProxy></span></span>  
<span data-ttu-id="eca22-107">\<modul ></span><span class="sxs-lookup"><span data-stu-id="eca22-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="eca22-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="eca22-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="eca22-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="eca22-109">Attributes and Elements</span></span>  
 <span data-ttu-id="eca22-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="eca22-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="eca22-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="eca22-111">Attributes</span></span>  
  
|<span data-ttu-id="eca22-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="eca22-112">**Attribute**</span></span>|<span data-ttu-id="eca22-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="eca22-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="eca22-114">Zadejte plně kvalifikovaný název (indikován <xref:System.Type.FullName%2A> vlastnost) a název sestavení (indikován <xref:System.Reflection.Assembly.FullName%2A> vlastnost), oddělené čárkou, který implementuje proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="eca22-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="eca22-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="eca22-115">Child Elements</span></span>  
 <span data-ttu-id="eca22-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="eca22-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="eca22-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="eca22-117">Parent Elements</span></span>  
  
|<span data-ttu-id="eca22-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="eca22-118">**Element**</span></span>|<span data-ttu-id="eca22-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="eca22-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="eca22-120">defaultProxy –</span><span class="sxs-lookup"><span data-stu-id="eca22-120">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="eca22-121">Nakonfiguruje server proxy protokolu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="eca22-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="eca22-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="eca22-122">Remarks</span></span>  
 <span data-ttu-id="eca22-123">`module` Element zaregistruje třídy proxy, které implementují <xref:System.Net.IWebProxy> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="eca22-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="eca22-124">Po registraci třídu proxy `module` slouží k vyžádání informací prostřednictvím podporovaných proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="eca22-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="eca22-125">Hodnota `type` atribut by měl mít název třídy modulu a názvu z jeho odpovídající dynamického propojení knihovny (DLL).</span><span class="sxs-lookup"><span data-stu-id="eca22-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="eca22-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="eca22-126">Configuration Files</span></span>  
 <span data-ttu-id="eca22-127">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="eca22-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="eca22-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="eca22-128">Example</span></span>  
 <span data-ttu-id="eca22-129">Následující příklad zaregistruje třídu vlastní proxy server.</span><span class="sxs-lookup"><span data-stu-id="eca22-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="eca22-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="eca22-130">See Also</span></span>  
 <xref:System.Net.IWebProxy?displayProperty=nameWithType>  
 [<span data-ttu-id="eca22-131">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="eca22-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

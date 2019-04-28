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
ms.openlocfilehash: 0d108f2350d82666e3dc24f0f6854fe64ea4755f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61674478"
---
# <a name="module-element-network-settings"></a><span data-ttu-id="05707-102">\<modul > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="05707-102">\<module> Element (Network Settings)</span></span>
<span data-ttu-id="05707-103">Přidá nový modul proxy serveru do aplikace.</span><span class="sxs-lookup"><span data-stu-id="05707-103">Adds a new proxy module to the application.</span></span>  
  
 <span data-ttu-id="05707-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="05707-104">\<configuration></span></span>  
<span data-ttu-id="05707-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="05707-105">\<system.net></span></span>  
<span data-ttu-id="05707-106">\<defaultProxy></span><span class="sxs-lookup"><span data-stu-id="05707-106">\<defaultProxy></span></span>  
<span data-ttu-id="05707-107">\<modul ></span><span class="sxs-lookup"><span data-stu-id="05707-107">\<module></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05707-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05707-108">Syntax</span></span>  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05707-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="05707-109">Attributes and Elements</span></span>  
 <span data-ttu-id="05707-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="05707-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05707-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="05707-111">Attributes</span></span>  
  
|<span data-ttu-id="05707-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="05707-112">**Attribute**</span></span>|<span data-ttu-id="05707-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="05707-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`type`|<span data-ttu-id="05707-114">Plně kvalifikovaného názvu (indikován <xref:System.Type.FullName%2A> vlastnost) a název sestavení (indikován <xref:System.Reflection.Assembly.FullName%2A> vlastnost), oddělená čárkou, která implementuje proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="05707-114">The fully qualified type name (indicated by the <xref:System.Type.FullName%2A> property) and the assembly name (indicated by the <xref:System.Reflection.Assembly.FullName%2A> property), separated by a comma, that implements the proxy.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05707-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="05707-115">Child Elements</span></span>  
 <span data-ttu-id="05707-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="05707-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05707-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="05707-117">Parent Elements</span></span>  
  
|<span data-ttu-id="05707-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="05707-118">**Element**</span></span>|<span data-ttu-id="05707-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="05707-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="05707-120">defaultProxy</span><span class="sxs-lookup"><span data-stu-id="05707-120">defaultProxy</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/defaultproxy-element-network-settings.md)|<span data-ttu-id="05707-121">Konfiguruje server proxy protokolu HTTP (Hypertext Transfer).</span><span class="sxs-lookup"><span data-stu-id="05707-121">Configures the Hypertext Transfer Protocol (HTTP) proxy server.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05707-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05707-122">Remarks</span></span>  
 <span data-ttu-id="05707-123">`module` Zaregistruje element třídy proxy, které implementují <xref:System.Net.IWebProxy> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="05707-123">The `module` element registers proxy classes that implement the <xref:System.Net.IWebProxy> interface.</span></span> <span data-ttu-id="05707-124">Po registraci třídu proxy `module` slouží k vyžádání informací prostřednictvím podporovaných proxy.</span><span class="sxs-lookup"><span data-stu-id="05707-124">After registering the proxy class, `module` can be used to request information through the supported proxy.</span></span>  
  
 <span data-ttu-id="05707-125">Hodnota `type` atribut by měl být název třídy modulu a název z jeho odpovídající dynamické propojení knihovna (DLL).</span><span class="sxs-lookup"><span data-stu-id="05707-125">The value for the `type` attribute should be the class name of the module and the name of its corresponding Dynamic Link Library (DLL).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="05707-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="05707-126">Configuration Files</span></span>  
 <span data-ttu-id="05707-127">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="05707-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05707-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="05707-128">Example</span></span>  
 <span data-ttu-id="05707-129">Následující příklad registruje třídu vlastní proxy server.</span><span class="sxs-lookup"><span data-stu-id="05707-129">The following example registers a custom proxy class.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05707-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="05707-130">See also</span></span>

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [<span data-ttu-id="05707-131">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="05707-131">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

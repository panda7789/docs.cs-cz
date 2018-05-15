---
title: '&lt;connectionManagement –&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: a7e1609df0a7a1de4e70f425e649115459b43f8c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltconnectionmanagementgt-element-network-settings"></a><span data-ttu-id="99a53-102">&lt;connectionManagement –&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="99a53-102">&lt;connectionManagement&gt; Element (Network Settings)</span></span>
<span data-ttu-id="99a53-103">Určuje maximální počet připojení k síti hostitele.</span><span class="sxs-lookup"><span data-stu-id="99a53-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="99a53-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="99a53-104">\<configuration></span></span>  
<span data-ttu-id="99a53-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="99a53-105">\<system.net></span></span>  
<span data-ttu-id="99a53-106">\<connectionManagement – ></span><span class="sxs-lookup"><span data-stu-id="99a53-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99a53-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99a53-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99a53-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="99a53-108">Attributes and Elements</span></span>  
 <span data-ttu-id="99a53-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="99a53-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99a53-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="99a53-110">Attributes</span></span>  
 <span data-ttu-id="99a53-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="99a53-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="99a53-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="99a53-112">Child Elements</span></span>  
  
|<span data-ttu-id="99a53-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="99a53-113">**Element**</span></span>|<span data-ttu-id="99a53-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="99a53-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="99a53-115">add</span><span class="sxs-lookup"><span data-stu-id="99a53-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="99a53-116">Přidá do seznamu pro správu připojení IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="99a53-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="99a53-117">Zrušte zaškrtnutí</span><span class="sxs-lookup"><span data-stu-id="99a53-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="99a53-118">Vymaže seznam pro správu připojení.</span><span class="sxs-lookup"><span data-stu-id="99a53-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="99a53-119">remove</span><span class="sxs-lookup"><span data-stu-id="99a53-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="99a53-120">Odebere ze seznamu pro správu připojení IP adresy nebo názvu DNS.</span><span class="sxs-lookup"><span data-stu-id="99a53-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99a53-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="99a53-121">Parent Elements</span></span>  
  
|<span data-ttu-id="99a53-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="99a53-122">**Element**</span></span>|<span data-ttu-id="99a53-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="99a53-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="99a53-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="99a53-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="99a53-125">Obsahuje nastavení, které určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="99a53-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99a53-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="99a53-126">Remarks</span></span>  
 <span data-ttu-id="99a53-127">`connectionManagement` Element definuje maximální počet připojení k serveru nebo skupiny serverů.</span><span class="sxs-lookup"><span data-stu-id="99a53-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="99a53-128">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="99a53-128">Configuration Files</span></span>  
 <span data-ttu-id="99a53-129">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="99a53-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="99a53-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="99a53-130">Example</span></span>  
 <span data-ttu-id="99a53-131">Následující příklad konfiguruje aplikaci použít čtyři připojení k serveru www.contoso.com a dvě připojení na jiné servery.</span><span class="sxs-lookup"><span data-stu-id="99a53-131">The following example configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="99a53-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="99a53-132">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="99a53-133">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="99a53-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

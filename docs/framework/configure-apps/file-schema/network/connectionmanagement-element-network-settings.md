---
title: '&lt;Element connectionManagement&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 7cc5f2a37c0520ee48a10afeb4b9bc83ffd61033
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201540"
---
# <a name="ltconnectionmanagementgt-element-network-settings"></a><span data-ttu-id="54c22-102">&lt;Element connectionManagement&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="54c22-102">&lt;connectionManagement&gt; Element (Network Settings)</span></span>
<span data-ttu-id="54c22-103">Určuje maximální počet připojení k síti hostitele.</span><span class="sxs-lookup"><span data-stu-id="54c22-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="54c22-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="54c22-104">\<configuration></span></span>  
<span data-ttu-id="54c22-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="54c22-105">\<system.net></span></span>  
<span data-ttu-id="54c22-106">\<connectionManagement – ></span><span class="sxs-lookup"><span data-stu-id="54c22-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54c22-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54c22-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54c22-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="54c22-108">Attributes and Elements</span></span>  
 <span data-ttu-id="54c22-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="54c22-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54c22-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="54c22-110">Attributes</span></span>  
 <span data-ttu-id="54c22-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="54c22-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="54c22-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="54c22-112">Child Elements</span></span>  
  
|<span data-ttu-id="54c22-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="54c22-113">**Element**</span></span>|<span data-ttu-id="54c22-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="54c22-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="54c22-115">add</span><span class="sxs-lookup"><span data-stu-id="54c22-115">add</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="54c22-116">Přidá do seznamu pro správu připojení IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="54c22-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="54c22-117">Vymazat</span><span class="sxs-lookup"><span data-stu-id="54c22-117">clear</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="54c22-118">Zruší připojení seznamu pro správu.</span><span class="sxs-lookup"><span data-stu-id="54c22-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="54c22-119">remove</span><span class="sxs-lookup"><span data-stu-id="54c22-119">remove</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="54c22-120">Odebere ze seznamu pro správu připojení IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="54c22-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="54c22-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="54c22-121">Parent Elements</span></span>  
  
|<span data-ttu-id="54c22-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="54c22-122">**Element**</span></span>|<span data-ttu-id="54c22-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="54c22-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="54c22-124">System.NET</span><span class="sxs-lookup"><span data-stu-id="54c22-124">system.net</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|<span data-ttu-id="54c22-125">Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="54c22-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54c22-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54c22-126">Remarks</span></span>  
 <span data-ttu-id="54c22-127">`connectionManagement` Element definuje maximální počet připojení k serveru nebo skupiny serverů.</span><span class="sxs-lookup"><span data-stu-id="54c22-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="54c22-128">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="54c22-128">Configuration Files</span></span>  
 <span data-ttu-id="54c22-129">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="54c22-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="54c22-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="54c22-130">Example</span></span>  
 <span data-ttu-id="54c22-131">Následující příklad nastaví použití čtyř připojení k serveru aplikace `www.contoso.com` a dvě spojení na všechny ostatní servery.</span><span class="sxs-lookup"><span data-stu-id="54c22-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54c22-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="54c22-132">See Also</span></span>  
- <xref:System.Net.ServicePoint>  
- <xref:System.Net.ServicePointManager>  
- [<span data-ttu-id="54c22-133">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="54c22-133">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

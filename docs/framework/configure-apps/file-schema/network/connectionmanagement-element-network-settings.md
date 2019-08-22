---
title: <connectionManagement> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: faaba1b9de302ed916ad1a81c7e80b3fb5a67170
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664159"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="e28ca-102">\<connectionManagement – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="e28ca-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="e28ca-103">Určuje maximální počet připojení k síťovému hostiteli.</span><span class="sxs-lookup"><span data-stu-id="e28ca-103">Specifies the maximum number of connections to a network host.</span></span>  
  
 <span data-ttu-id="e28ca-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="e28ca-104">\<configuration></span></span>  
<span data-ttu-id="e28ca-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="e28ca-105">\<system.net></span></span>  
<span data-ttu-id="e28ca-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="e28ca-106">\<connectionManagement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e28ca-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e28ca-107">Syntax</span></span>  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e28ca-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e28ca-108">Attributes and Elements</span></span>  
 <span data-ttu-id="e28ca-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e28ca-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e28ca-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="e28ca-110">Attributes</span></span>  
 <span data-ttu-id="e28ca-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="e28ca-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e28ca-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e28ca-112">Child Elements</span></span>  
  
|<span data-ttu-id="e28ca-113">**Element**</span><span class="sxs-lookup"><span data-stu-id="e28ca-113">**Element**</span></span>|<span data-ttu-id="e28ca-114">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e28ca-114">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e28ca-115">add</span><span class="sxs-lookup"><span data-stu-id="e28ca-115">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="e28ca-116">Přidá IP adresu nebo název DNS do seznamu správy připojení.</span><span class="sxs-lookup"><span data-stu-id="e28ca-116">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="e28ca-117">jejich</span><span class="sxs-lookup"><span data-stu-id="e28ca-117">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="e28ca-118">Vymaže seznam správy připojení.</span><span class="sxs-lookup"><span data-stu-id="e28ca-118">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="e28ca-119">remove</span><span class="sxs-lookup"><span data-stu-id="e28ca-119">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="e28ca-120">Odebere IP adresu nebo název DNS ze seznamu správy připojení.</span><span class="sxs-lookup"><span data-stu-id="e28ca-120">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e28ca-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e28ca-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e28ca-122">**Element**</span><span class="sxs-lookup"><span data-stu-id="e28ca-122">**Element**</span></span>|<span data-ttu-id="e28ca-123">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e28ca-123">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e28ca-124">system.net</span><span class="sxs-lookup"><span data-stu-id="e28ca-124">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="e28ca-125">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="e28ca-125">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e28ca-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e28ca-126">Remarks</span></span>  
 <span data-ttu-id="e28ca-127">`connectionManagement` Element definuje maximální počet připojení k serveru nebo skupině serverů.</span><span class="sxs-lookup"><span data-stu-id="e28ca-127">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e28ca-128">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="e28ca-128">Configuration Files</span></span>  
 <span data-ttu-id="e28ca-129">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="e28ca-129">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e28ca-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="e28ca-130">Example</span></span>  
 <span data-ttu-id="e28ca-131">Následující příklad nakonfiguruje aplikaci tak, aby používala čtyři připojení k `www.contoso.com` serveru a dvě připojení ke všem ostatním serverům.</span><span class="sxs-lookup"><span data-stu-id="e28ca-131">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e28ca-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e28ca-132">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="e28ca-133">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="e28ca-133">Network Settings Schema</span></span>](index.md)

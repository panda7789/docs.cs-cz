---
title: <connectionManagement> – element (nastavení sítě)
description: <connectionManagement>Prvek nastavení sítě určuje maximální počet připojení k síťovému hostiteli v .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 4ceec06fb0e21bfae67038efe0ce758d3d5b708f
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504612"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="70171-103">\<connectionManagement> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="70171-103">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="70171-104">Určuje maximální počet připojení k síťovému hostiteli.</span><span class="sxs-lookup"><span data-stu-id="70171-104">Specifies the maximum number of connections to a network host.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a><span data-ttu-id="70171-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="70171-105">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="70171-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="70171-106">Attributes and Elements</span></span>  
 <span data-ttu-id="70171-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="70171-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="70171-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="70171-108">Attributes</span></span>  
 <span data-ttu-id="70171-109">Žádné</span><span class="sxs-lookup"><span data-stu-id="70171-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="70171-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="70171-110">Child Elements</span></span>  
  
|<span data-ttu-id="70171-111">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="70171-111">**Element**</span></span>|<span data-ttu-id="70171-112">**Popis**</span><span class="sxs-lookup"><span data-stu-id="70171-112">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="70171-113">add</span><span class="sxs-lookup"><span data-stu-id="70171-113">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="70171-114">Přidá IP adresu nebo název DNS do seznamu správy připojení.</span><span class="sxs-lookup"><span data-stu-id="70171-114">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="70171-115">jejich</span><span class="sxs-lookup"><span data-stu-id="70171-115">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="70171-116">Vymaže seznam správy připojení.</span><span class="sxs-lookup"><span data-stu-id="70171-116">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="70171-117">remove</span><span class="sxs-lookup"><span data-stu-id="70171-117">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="70171-118">Odebere IP adresu nebo název DNS ze seznamu správy připojení.</span><span class="sxs-lookup"><span data-stu-id="70171-118">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="70171-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="70171-119">Parent Elements</span></span>  
  
|<span data-ttu-id="70171-120">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="70171-120">**Element**</span></span>|<span data-ttu-id="70171-121">**Popis**</span><span class="sxs-lookup"><span data-stu-id="70171-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="70171-122">system.net</span><span class="sxs-lookup"><span data-stu-id="70171-122">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="70171-123">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="70171-123">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="70171-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="70171-124">Remarks</span></span>  
 <span data-ttu-id="70171-125">`connectionManagement`Element definuje maximální počet připojení k serveru nebo skupině serverů.</span><span class="sxs-lookup"><span data-stu-id="70171-125">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="70171-126">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="70171-126">Configuration Files</span></span>  
 <span data-ttu-id="70171-127">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="70171-127">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="70171-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="70171-128">Example</span></span>  
 <span data-ttu-id="70171-129">Následující příklad nakonfiguruje aplikaci tak, aby používala čtyři připojení k serveru `www.contoso.com` a dvě připojení ke všem ostatním serverům.</span><span class="sxs-lookup"><span data-stu-id="70171-129">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="70171-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="70171-130">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="70171-131">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="70171-131">Network Settings Schema</span></span>](index.md)

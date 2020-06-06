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
ms.openlocfilehash: 9f1e382bbbaad2cb95e2c33bbbdfb4c505378c9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154891"
---
# <a name="connectionmanagement-element-network-settings"></a><span data-ttu-id="05dbe-102">\<connectionManagement> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="05dbe-102">\<connectionManagement> Element (Network Settings)</span></span>
<span data-ttu-id="05dbe-103">Určuje maximální počet připojení k síťovému hostiteli.</span><span class="sxs-lookup"><span data-stu-id="05dbe-103">Specifies the maximum number of connections to a network host.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a><span data-ttu-id="05dbe-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="05dbe-104">Syntax</span></span>  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05dbe-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="05dbe-105">Attributes and Elements</span></span>  
 <span data-ttu-id="05dbe-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="05dbe-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05dbe-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="05dbe-107">Attributes</span></span>  
 <span data-ttu-id="05dbe-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="05dbe-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="05dbe-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="05dbe-109">Child Elements</span></span>  
  
|<span data-ttu-id="05dbe-110">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="05dbe-110">**Element**</span></span>|<span data-ttu-id="05dbe-111">**Popis**</span><span class="sxs-lookup"><span data-stu-id="05dbe-111">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="05dbe-112">add</span><span class="sxs-lookup"><span data-stu-id="05dbe-112">add</span></span>](add-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="05dbe-113">Přidá IP adresu nebo název DNS do seznamu správy připojení.</span><span class="sxs-lookup"><span data-stu-id="05dbe-113">Adds an IP address or DNS name to the connection management list.</span></span>|  
|[<span data-ttu-id="05dbe-114">jejich</span><span class="sxs-lookup"><span data-stu-id="05dbe-114">clear</span></span>](clear-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="05dbe-115">Vymaže seznam správy připojení.</span><span class="sxs-lookup"><span data-stu-id="05dbe-115">Clears the connection management list.</span></span>|  
|[<span data-ttu-id="05dbe-116">odebrány</span><span class="sxs-lookup"><span data-stu-id="05dbe-116">remove</span></span>](remove-element-for-connectionmanagement-network-settings.md)|<span data-ttu-id="05dbe-117">Odebere IP adresu nebo název DNS ze seznamu správy připojení.</span><span class="sxs-lookup"><span data-stu-id="05dbe-117">Removes an IP address or DNS name from the connection management list.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="05dbe-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="05dbe-118">Parent Elements</span></span>  
  
|<span data-ttu-id="05dbe-119">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="05dbe-119">**Element**</span></span>|<span data-ttu-id="05dbe-120">**Popis**</span><span class="sxs-lookup"><span data-stu-id="05dbe-120">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="05dbe-121">system.net</span><span class="sxs-lookup"><span data-stu-id="05dbe-121">system.net</span></span>](system-net-element-network-settings.md)|<span data-ttu-id="05dbe-122">Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.</span><span class="sxs-lookup"><span data-stu-id="05dbe-122">Contains settings that specify how the .NET Framework connects to the network.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="05dbe-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="05dbe-123">Remarks</span></span>  
 <span data-ttu-id="05dbe-124">`connectionManagement`Element definuje maximální počet připojení k serveru nebo skupině serverů.</span><span class="sxs-lookup"><span data-stu-id="05dbe-124">The `connectionManagement` element defines the maximum number of connections to a server or group of servers.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="05dbe-125">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="05dbe-125">Configuration Files</span></span>  
 <span data-ttu-id="05dbe-126">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="05dbe-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="05dbe-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="05dbe-127">Example</span></span>  
 <span data-ttu-id="05dbe-128">Následující příklad nakonfiguruje aplikaci tak, aby používala čtyři připojení k serveru `www.contoso.com` a dvě připojení ke všem ostatním serverům.</span><span class="sxs-lookup"><span data-stu-id="05dbe-128">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="05dbe-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="05dbe-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="05dbe-130">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="05dbe-130">Network Settings Schema</span></span>](index.md)

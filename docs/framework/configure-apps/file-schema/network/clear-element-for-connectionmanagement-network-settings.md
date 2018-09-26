---
title: '&lt;Vymazat&gt; – Element pro connectionManagement (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/clear
- http://schemas.microsoft.com/.NetConfiguration/v2.0#clear
helpviewer_keywords:
- <clear> element, connectionManagement
- connectionManagement, clear element
- clear element, connectionManagement
- <connectionManagement>, clear element
ms.assetid: fb259282-84c4-4dc4-a226-78d904a6edc3
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 9542332085d0b0319c55db63fd98c9dd8eb3f576
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47070497"
---
# <a name="ltcleargt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="2ba0f-102">&lt;Vymazat&gt; – Element pro connectionManagement (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="2ba0f-102">&lt;clear&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="2ba0f-103">Zruší připojení seznamu pro správu.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-103">Clears the connection management list.</span></span>  
  
 <span data-ttu-id="2ba0f-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="2ba0f-104">\<configuration></span></span>  
<span data-ttu-id="2ba0f-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="2ba0f-105">\<system.net></span></span>  
<span data-ttu-id="2ba0f-106">\<connectionManagement – ></span><span class="sxs-lookup"><span data-stu-id="2ba0f-106">\<connectionManagement></span></span>  
<span data-ttu-id="2ba0f-107">\<Vymazat ></span><span class="sxs-lookup"><span data-stu-id="2ba0f-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ba0f-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ba0f-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ba0f-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2ba0f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2ba0f-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ba0f-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2ba0f-111">Attributes</span></span>  
 <span data-ttu-id="2ba0f-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="2ba0f-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2ba0f-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2ba0f-113">Child Elements</span></span>  
 <span data-ttu-id="2ba0f-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="2ba0f-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ba0f-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2ba0f-115">Parent Elements</span></span>  
  
|<span data-ttu-id="2ba0f-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="2ba0f-116">**Element**</span></span>|<span data-ttu-id="2ba0f-117">**Popis**</span><span class="sxs-lookup"><span data-stu-id="2ba0f-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2ba0f-118">connectionManagement –</span><span class="sxs-lookup"><span data-stu-id="2ba0f-118">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="2ba0f-119">Určuje maximální počet připojení k síti hostitele.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ba0f-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ba0f-120">Remarks</span></span>  
 <span data-ttu-id="2ba0f-121">`clear` Element vymaže všechny položky v seznamu připojení správy.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2ba0f-122">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="2ba0f-122">Configuration Files</span></span>  
 <span data-ttu-id="2ba0f-123">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="2ba0f-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ba0f-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="2ba0f-124">Example</span></span>  
 <span data-ttu-id="2ba0f-125">Následující příklad vymaže seznamu pro správu připojení a pak přidá nové položky správy připojení pro server www.contoso.com a všechny ostatní sítě hostitele.</span><span class="sxs-lookup"><span data-stu-id="2ba0f-125">The following example clears the connection management list and then adds new connection management entries for the server www.contoso.com and all other network hosts.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <clear/>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2ba0f-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="2ba0f-126">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="2ba0f-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="2ba0f-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

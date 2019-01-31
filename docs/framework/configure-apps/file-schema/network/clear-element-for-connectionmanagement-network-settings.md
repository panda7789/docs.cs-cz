---
title: <clear> – element pro element connectionManagement (nastavení sítě)
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
ms.openlocfilehash: b90bdacc962eba1cd449f347f958f04cd72225d4
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55273920"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="41f76-102">\<Vymazat > – Element pro connectionManagement (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="41f76-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="41f76-103">Zruší připojení seznamu pro správu.</span><span class="sxs-lookup"><span data-stu-id="41f76-103">Clears the connection management list.</span></span>  
  
 <span data-ttu-id="41f76-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="41f76-104">\<configuration></span></span>  
<span data-ttu-id="41f76-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="41f76-105">\<system.net></span></span>  
<span data-ttu-id="41f76-106">\<connectionManagement></span><span class="sxs-lookup"><span data-stu-id="41f76-106">\<connectionManagement></span></span>  
<span data-ttu-id="41f76-107">\<clear></span><span class="sxs-lookup"><span data-stu-id="41f76-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="41f76-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="41f76-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="41f76-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="41f76-109">Attributes and Elements</span></span>  
 <span data-ttu-id="41f76-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="41f76-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="41f76-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="41f76-111">Attributes</span></span>  
 <span data-ttu-id="41f76-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="41f76-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="41f76-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="41f76-113">Child Elements</span></span>  
 <span data-ttu-id="41f76-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="41f76-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="41f76-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="41f76-115">Parent Elements</span></span>  
  
|<span data-ttu-id="41f76-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="41f76-116">**Element**</span></span>|<span data-ttu-id="41f76-117">**Popis**</span><span class="sxs-lookup"><span data-stu-id="41f76-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="41f76-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="41f76-118">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="41f76-119">Určuje maximální počet připojení k síti hostitele.</span><span class="sxs-lookup"><span data-stu-id="41f76-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="41f76-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="41f76-120">Remarks</span></span>  
 <span data-ttu-id="41f76-121">`clear` Element vymaže všechny položky v seznamu připojení správy.</span><span class="sxs-lookup"><span data-stu-id="41f76-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="41f76-122">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="41f76-122">Configuration Files</span></span>  
 <span data-ttu-id="41f76-123">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="41f76-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="41f76-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="41f76-124">Example</span></span>  
 <span data-ttu-id="41f76-125">V následujícím příkladu vymaže seznamu pro správu připojení a pak přidá nové položky správy připojení pro server `www.contoso.com` a všechny ostatní sítě hostitele.</span><span class="sxs-lookup"><span data-stu-id="41f76-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="41f76-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="41f76-126">See also</span></span>
- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="41f76-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="41f76-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

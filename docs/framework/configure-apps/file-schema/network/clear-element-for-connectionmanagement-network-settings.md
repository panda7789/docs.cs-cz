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
ms.openlocfilehash: dba05128220b34bed34da4309a4994cbc4e1bd40
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/29/2018
ms.locfileid: "50205097"
---
# <a name="ltcleargt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="d25a5-102">&lt;Vymazat&gt; – Element pro connectionManagement (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="d25a5-102">&lt;clear&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="d25a5-103">Zruší připojení seznamu pro správu.</span><span class="sxs-lookup"><span data-stu-id="d25a5-103">Clears the connection management list.</span></span>  
  
 <span data-ttu-id="d25a5-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="d25a5-104">\<configuration></span></span>  
<span data-ttu-id="d25a5-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="d25a5-105">\<system.net></span></span>  
<span data-ttu-id="d25a5-106">\<connectionManagement – ></span><span class="sxs-lookup"><span data-stu-id="d25a5-106">\<connectionManagement></span></span>  
<span data-ttu-id="d25a5-107">\<Vymazat ></span><span class="sxs-lookup"><span data-stu-id="d25a5-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d25a5-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d25a5-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d25a5-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d25a5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d25a5-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d25a5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d25a5-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="d25a5-111">Attributes</span></span>  
 <span data-ttu-id="d25a5-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="d25a5-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d25a5-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d25a5-113">Child Elements</span></span>  
 <span data-ttu-id="d25a5-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="d25a5-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d25a5-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d25a5-115">Parent Elements</span></span>  
  
|<span data-ttu-id="d25a5-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="d25a5-116">**Element**</span></span>|<span data-ttu-id="d25a5-117">**Popis**</span><span class="sxs-lookup"><span data-stu-id="d25a5-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="d25a5-118">connectionManagement –</span><span class="sxs-lookup"><span data-stu-id="d25a5-118">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="d25a5-119">Určuje maximální počet připojení k síti hostitele.</span><span class="sxs-lookup"><span data-stu-id="d25a5-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d25a5-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d25a5-120">Remarks</span></span>  
 <span data-ttu-id="d25a5-121">`clear` Element vymaže všechny položky v seznamu připojení správy.</span><span class="sxs-lookup"><span data-stu-id="d25a5-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="d25a5-122">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="d25a5-122">Configuration Files</span></span>  
 <span data-ttu-id="d25a5-123">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="d25a5-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d25a5-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="d25a5-124">Example</span></span>  
 <span data-ttu-id="d25a5-125">V následujícím příkladu vymaže seznamu pro správu připojení a pak přidá nové položky správy připojení pro server `www.contoso.com` a všechny ostatní sítě hostitele.</span><span class="sxs-lookup"><span data-stu-id="d25a5-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d25a5-126">Viz také</span><span class="sxs-lookup"><span data-stu-id="d25a5-126">See Also</span></span>  
- <xref:System.Net.ServicePoint>  
- <xref:System.Net.ServicePointManager>  
- [<span data-ttu-id="d25a5-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="d25a5-127">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

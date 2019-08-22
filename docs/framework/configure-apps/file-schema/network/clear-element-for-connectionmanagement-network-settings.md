---
title: <clear> – element pro connectionManagement (nastavení sítě)
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
ms.openlocfilehash: 86a7a0ab402c8c40ec3b824402a1dba984412b68
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659450"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="b8548-102">\<Clear – element > pro connectionManagement (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="b8548-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="b8548-103">Vymaže seznam správy připojení.</span><span class="sxs-lookup"><span data-stu-id="b8548-103">Clears the connection management list.</span></span>  
  
 <span data-ttu-id="b8548-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="b8548-104">\<configuration></span></span>  
<span data-ttu-id="b8548-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="b8548-105">\<system.net></span></span>  
<span data-ttu-id="b8548-106">\<connectionManagement ></span><span class="sxs-lookup"><span data-stu-id="b8548-106">\<connectionManagement></span></span>  
<span data-ttu-id="b8548-107">\<Vymazat ></span><span class="sxs-lookup"><span data-stu-id="b8548-107">\<clear></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8548-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b8548-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8548-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b8548-109">Attributes and Elements</span></span>  
 <span data-ttu-id="b8548-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b8548-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8548-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="b8548-111">Attributes</span></span>  
 <span data-ttu-id="b8548-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="b8548-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="b8548-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b8548-113">Child Elements</span></span>  
 <span data-ttu-id="b8548-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="b8548-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8548-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b8548-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b8548-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="b8548-116">**Element**</span></span>|<span data-ttu-id="b8548-117">**Popis**</span><span class="sxs-lookup"><span data-stu-id="b8548-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="b8548-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="b8548-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="b8548-119">Určuje maximální počet připojení k síťovému hostiteli.</span><span class="sxs-lookup"><span data-stu-id="b8548-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8548-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b8548-120">Remarks</span></span>  
 <span data-ttu-id="b8548-121">`clear` Element vymaže všechny položky ze seznamu správy připojení.</span><span class="sxs-lookup"><span data-stu-id="b8548-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="b8548-122">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="b8548-122">Configuration Files</span></span>  
 <span data-ttu-id="b8548-123">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="b8548-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8548-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="b8548-124">Example</span></span>  
 <span data-ttu-id="b8548-125">Následující příklad vymaže seznam správy připojení a pak přidá nové položky správy připojení pro server `www.contoso.com` a všechny další síťové hostitele.</span><span class="sxs-lookup"><span data-stu-id="b8548-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b8548-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b8548-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="b8548-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="b8548-127">Network Settings Schema</span></span>](index.md)

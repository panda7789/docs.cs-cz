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
ms.openlocfilehash: 17b380b12977423669fd413132d69a3082daca41
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698361"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="a7eb8-102">@no__t – element > 0clear pro connectionManagement (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="a7eb8-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="a7eb8-103">Vymaže seznam správy připojení.</span><span class="sxs-lookup"><span data-stu-id="a7eb8-103">Clears the connection management list.</span></span>  
  
[<span data-ttu-id="a7eb8-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="a7eb8-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="a7eb8-105">&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a7eb8-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="a7eb8-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="a7eb8-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>  
<span data-ttu-id="a7eb8-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<clear >**</span><span class="sxs-lookup"><span data-stu-id="a7eb8-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7eb8-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="a7eb8-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a7eb8-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="a7eb8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="a7eb8-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="a7eb8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a7eb8-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="a7eb8-111">Attributes</span></span>  
 <span data-ttu-id="a7eb8-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="a7eb8-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="a7eb8-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="a7eb8-113">Child Elements</span></span>  
 <span data-ttu-id="a7eb8-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="a7eb8-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a7eb8-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="a7eb8-115">Parent Elements</span></span>  
  
|<span data-ttu-id="a7eb8-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="a7eb8-116">**Element**</span></span>|<span data-ttu-id="a7eb8-117">**Popis**</span><span class="sxs-lookup"><span data-stu-id="a7eb8-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="a7eb8-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="a7eb8-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="a7eb8-119">Určuje maximální počet připojení k síťovému hostiteli.</span><span class="sxs-lookup"><span data-stu-id="a7eb8-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a7eb8-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a7eb8-120">Remarks</span></span>  
 <span data-ttu-id="a7eb8-121">Element `clear` vymaže všechny položky ze seznamu správy připojení.</span><span class="sxs-lookup"><span data-stu-id="a7eb8-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="a7eb8-122">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="a7eb8-122">Configuration Files</span></span>  
 <span data-ttu-id="a7eb8-123">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="a7eb8-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7eb8-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="a7eb8-124">Example</span></span>  
 <span data-ttu-id="a7eb8-125">Následující příklad vymaže seznam správy připojení a pak přidá nové položky správy připojení pro server `www.contoso.com` a všechny další síťové hostitele.</span><span class="sxs-lookup"><span data-stu-id="a7eb8-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a7eb8-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a7eb8-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="a7eb8-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="a7eb8-127">Network Settings Schema</span></span>](index.md)

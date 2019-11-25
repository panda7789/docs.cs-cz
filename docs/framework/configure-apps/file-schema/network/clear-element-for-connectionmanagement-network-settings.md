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
ms.openlocfilehash: a76df48a9de084e1121a5e96b22edf7aa3acba23
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088489"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="8d409-102">\<Clear > element pro connectionManagement (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="8d409-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="8d409-103">Vymaže seznam správy připojení.</span><span class="sxs-lookup"><span data-stu-id="8d409-103">Clears the connection management list.</span></span>  

<span data-ttu-id="8d409-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="8d409-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="8d409-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8d409-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="8d409-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="8d409-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="8d409-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<vymazat >**</span><span class="sxs-lookup"><span data-stu-id="8d409-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>

## <a name="syntax"></a><span data-ttu-id="8d409-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8d409-108">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8d409-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8d409-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8d409-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8d409-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8d409-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="8d409-111">Attributes</span></span>  
 <span data-ttu-id="8d409-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="8d409-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8d409-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8d409-113">Child Elements</span></span>  
 <span data-ttu-id="8d409-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="8d409-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8d409-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8d409-115">Parent Elements</span></span>  
  
|<span data-ttu-id="8d409-116">**Element**</span><span class="sxs-lookup"><span data-stu-id="8d409-116">**Element**</span></span>|<span data-ttu-id="8d409-117">**Popis**</span><span class="sxs-lookup"><span data-stu-id="8d409-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8d409-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="8d409-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="8d409-119">Určuje maximální počet připojení k síťovému hostiteli.</span><span class="sxs-lookup"><span data-stu-id="8d409-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8d409-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8d409-120">Remarks</span></span>  
 <span data-ttu-id="8d409-121">Element `clear` vymaže všechny položky ze seznamu správy připojení.</span><span class="sxs-lookup"><span data-stu-id="8d409-121">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="8d409-122">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="8d409-122">Configuration Files</span></span>  
 <span data-ttu-id="8d409-123">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="8d409-123">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d409-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="8d409-124">Example</span></span>  
 <span data-ttu-id="8d409-125">Následující příklad vymaže seznam správy připojení a pak přidá nové položky správy připojení pro server `www.contoso.com` a všechny další síťové hostitele.</span><span class="sxs-lookup"><span data-stu-id="8d409-125">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8d409-126">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8d409-126">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="8d409-127">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="8d409-127">Network Settings Schema</span></span>](index.md)

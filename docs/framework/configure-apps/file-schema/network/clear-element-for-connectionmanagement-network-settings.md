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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74088489"
---
# <a name="clear-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="25361-102">\<clear> – element pro connectionManagement (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="25361-102">\<clear> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="25361-103">Vymaže seznam správy připojení.</span><span class="sxs-lookup"><span data-stu-id="25361-103">Clears the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a><span data-ttu-id="25361-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="25361-104">Syntax</span></span>  
  
```xml  
<clear/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="25361-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="25361-105">Attributes and Elements</span></span>  
 <span data-ttu-id="25361-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="25361-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="25361-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="25361-107">Attributes</span></span>  
 <span data-ttu-id="25361-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="25361-108">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="25361-109">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="25361-109">Child Elements</span></span>  
 <span data-ttu-id="25361-110">Žádné</span><span class="sxs-lookup"><span data-stu-id="25361-110">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="25361-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="25361-111">Parent Elements</span></span>  
  
|<span data-ttu-id="25361-112">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="25361-112">**Element**</span></span>|<span data-ttu-id="25361-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="25361-113">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="25361-114">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="25361-114">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="25361-115">Určuje maximální počet připojení k síťovému hostiteli.</span><span class="sxs-lookup"><span data-stu-id="25361-115">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25361-116">Poznámky</span><span class="sxs-lookup"><span data-stu-id="25361-116">Remarks</span></span>  
 <span data-ttu-id="25361-117">`clear`Element vymaže všechny položky ze seznamu správy připojení.</span><span class="sxs-lookup"><span data-stu-id="25361-117">The `clear` element clears all entries from the connection management list.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="25361-118">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="25361-118">Configuration Files</span></span>  
 <span data-ttu-id="25361-119">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="25361-119">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="25361-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="25361-120">Example</span></span>  
 <span data-ttu-id="25361-121">Následující příklad vymaže seznam správy připojení a pak přidá nové položky správy připojení pro server `www.contoso.com` a všechny další síťové hostitele.</span><span class="sxs-lookup"><span data-stu-id="25361-121">The following example clears the connection management list and then adds new connection management entries for the server `www.contoso.com` and all other network hosts.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="25361-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="25361-122">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="25361-123">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="25361-123">Network Settings Schema</span></span>](index.md)

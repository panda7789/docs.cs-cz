---
title: <remove> – element pro connectionManagement (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
ms.openlocfilehash: 39ce85c3c15a2d4bdfce801a35e9ca088bd5091b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154735"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="cd1bf-102">\<remove> – element pro connectionManagement (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="cd1bf-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="cd1bf-103">Odebere IP adresu nebo název DNS ze seznamu správy připojení.</span><span class="sxs-lookup"><span data-stu-id="cd1bf-103">Removes an IP address or DNS name from the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a><span data-ttu-id="cd1bf-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cd1bf-104">Syntax</span></span>  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cd1bf-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cd1bf-105">Attributes and Elements</span></span>  
 <span data-ttu-id="cd1bf-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cd1bf-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cd1bf-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="cd1bf-107">Attributes</span></span>  
  
|<span data-ttu-id="cd1bf-108">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="cd1bf-108">**Attribute**</span></span>|<span data-ttu-id="cd1bf-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="cd1bf-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="cd1bf-110">IP adresa nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="cd1bf-110">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cd1bf-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cd1bf-111">Child Elements</span></span>  
 <span data-ttu-id="cd1bf-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="cd1bf-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cd1bf-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cd1bf-113">Parent Elements</span></span>  
  
|<span data-ttu-id="cd1bf-114">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="cd1bf-114">**Element**</span></span>|<span data-ttu-id="cd1bf-115">**Popis**</span><span class="sxs-lookup"><span data-stu-id="cd1bf-115">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="cd1bf-116">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="cd1bf-116">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="cd1bf-117">Určuje maximální počet připojení k síťovému hostiteli.</span><span class="sxs-lookup"><span data-stu-id="cd1bf-117">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cd1bf-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cd1bf-118">Remarks</span></span>  
 <span data-ttu-id="cd1bf-119">`remove`Element odebere položku seznamu správy připojení pro zadaný server.</span><span class="sxs-lookup"><span data-stu-id="cd1bf-119">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="cd1bf-120">Hodnota `address` atributu musí být platná IP adresa nebo název hostitele.</span><span class="sxs-lookup"><span data-stu-id="cd1bf-120">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="cd1bf-121">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="cd1bf-121">Configuration Files</span></span>  
 <span data-ttu-id="cd1bf-122">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="cd1bf-122">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd1bf-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd1bf-123">Example</span></span>  
 <span data-ttu-id="cd1bf-124">Následující příklad odebere všechny položky seznamu správy připojení pro server `www.adventure-works.com` a pak nakonfiguruje aplikaci tak, aby používala čtyři připojení k serveru `www.contoso.com` a dvě připojení ke všem ostatním serverům.</span><span class="sxs-lookup"><span data-stu-id="cd1bf-124">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <remove address="http://www.adventure-works.com" />  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="cd1bf-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd1bf-125">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="cd1bf-126">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="cd1bf-126">Network Settings Schema</span></span>](index.md)

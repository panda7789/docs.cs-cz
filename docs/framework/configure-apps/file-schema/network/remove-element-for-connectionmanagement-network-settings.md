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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154735"
---
# <a name="remove-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="db242-102">\<odebrat> Element pro connectionManagement (Nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="db242-102">\<remove> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="db242-103">Odebere adresu IP nebo název DNS ze seznamu správy připojení.</span><span class="sxs-lookup"><span data-stu-id="db242-103">Removes an IP address or DNS name from the connection management list.</span></span>  

<span data-ttu-id="db242-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="db242-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="db242-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="db242-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="db242-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="db242-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>\
<span data-ttu-id="db242-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<odebrat>**</span><span class="sxs-lookup"><span data-stu-id="db242-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**</span></span>

## <a name="syntax"></a><span data-ttu-id="db242-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="db242-108">Syntax</span></span>  
  
```xml  
<remove
  address="server name or IP address"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="db242-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="db242-109">Attributes and Elements</span></span>  
 <span data-ttu-id="db242-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="db242-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="db242-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="db242-111">Attributes</span></span>  
  
|<span data-ttu-id="db242-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="db242-112">**Attribute**</span></span>|<span data-ttu-id="db242-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="db242-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="db242-114">Adresa IP nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="db242-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="db242-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="db242-115">Child Elements</span></span>  
 <span data-ttu-id="db242-116">Žádné.</span><span class="sxs-lookup"><span data-stu-id="db242-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="db242-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="db242-117">Parent Elements</span></span>  
  
|<span data-ttu-id="db242-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="db242-118">**Element**</span></span>|<span data-ttu-id="db242-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="db242-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="db242-120">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="db242-120">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="db242-121">Určuje maximální počet připojení k síťovému hostiteli.</span><span class="sxs-lookup"><span data-stu-id="db242-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="db242-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="db242-122">Remarks</span></span>  
 <span data-ttu-id="db242-123">Prvek `remove` odebere položku seznamu správy připojení pro zadaný server.</span><span class="sxs-lookup"><span data-stu-id="db242-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="db242-124">Hodnota atributu `address` by měla být platná adresa IP nebo název hostitele.</span><span class="sxs-lookup"><span data-stu-id="db242-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="db242-125">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="db242-125">Configuration Files</span></span>  
 <span data-ttu-id="db242-126">Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="db242-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="db242-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="db242-127">Example</span></span>  
 <span data-ttu-id="db242-128">Následující příklad odebere všechny položky seznamu `www.adventure-works.com` správy připojení pro server a potom `www.contoso.com` nakonfiguruje aplikaci tak, aby používala čtyři připojení k serveru a dvě připojení ke všem ostatním serverům.</span><span class="sxs-lookup"><span data-stu-id="db242-128">The following example removes any connection management list entries for the server `www.adventure-works.com` and then configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="db242-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="db242-129">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="db242-130">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="db242-130">Network Settings Schema</span></span>](index.md)

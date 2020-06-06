---
title: <add> – element pro connectionManagement (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
ms.openlocfilehash: 093b68d31e03094bedefa96a2f2d53eb3d84edf0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155008"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="e1c45-102">\<add> – element pro connectionManagement (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="e1c45-102">\<add> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="e1c45-103">Přidá IP adresu nebo název DNS do seznamu správy připojení.</span><span class="sxs-lookup"><span data-stu-id="e1c45-103">Adds an IP address or DNS name to the connection management list.</span></span>  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**

## <a name="syntax"></a><span data-ttu-id="e1c45-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e1c45-104">Syntax</span></span>  
  
```xml  
<add
  address="address expression"
  maxconnection="integer"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e1c45-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e1c45-105">Attributes and Elements</span></span>  
 <span data-ttu-id="e1c45-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e1c45-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e1c45-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="e1c45-107">Attributes</span></span>  
  
|<span data-ttu-id="e1c45-108">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="e1c45-108">**Attribute**</span></span>|<span data-ttu-id="e1c45-109">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e1c45-109">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="e1c45-110">Řetězec popisující IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="e1c45-110">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="e1c45-111">Maximální počet připojení povolených pro server.</span><span class="sxs-lookup"><span data-stu-id="e1c45-111">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="e1c45-112">Pokud není zadaný, použije se výchozí hodnota 2.</span><span class="sxs-lookup"><span data-stu-id="e1c45-112">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e1c45-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e1c45-113">Child Elements</span></span>  
 <span data-ttu-id="e1c45-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="e1c45-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e1c45-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e1c45-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e1c45-116">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="e1c45-116">**Element**</span></span>|<span data-ttu-id="e1c45-117">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e1c45-117">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e1c45-118">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="e1c45-118">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="e1c45-119">Určuje maximální počet připojení k síťovému hostiteli.</span><span class="sxs-lookup"><span data-stu-id="e1c45-119">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e1c45-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e1c45-120">Remarks</span></span>  
 <span data-ttu-id="e1c45-121">Hodnota `address` atributu musí být buď hvězdička, která označuje všechna připojení, nebo řetězec formuláře `<schema>://<idn_hostname>[:<port>]` .</span><span class="sxs-lookup"><span data-stu-id="e1c45-121">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="e1c45-122">Pokud identifikátor URI předaný do libovolného rozhraní API HTTP obsahuje Unicode, název se převede interně pomocí <xref:System.Uri.DnsSafeHost%2A> toho, který může vracet punicode řetězec (chování závisí na aktuální konfiguraci IDN).</span><span class="sxs-lookup"><span data-stu-id="e1c45-122">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e1c45-123">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="e1c45-123">Configuration Files</span></span>  
 <span data-ttu-id="e1c45-124">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="e1c45-124">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e1c45-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="e1c45-125">Example</span></span>  
 <span data-ttu-id="e1c45-126">Následující příklad nakonfiguruje aplikaci tak, aby používala čtyři připojení k serveru `www.contoso.com` a dvě připojení ke všem ostatním serverům.</span><span class="sxs-lookup"><span data-stu-id="e1c45-126">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e1c45-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="e1c45-127">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="e1c45-128">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="e1c45-128">Network Settings Schema</span></span>](index.md)

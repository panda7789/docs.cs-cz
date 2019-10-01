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
ms.openlocfilehash: 3742a040e8c16c38e495a0fd886c4c1f23780758
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698385"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="2deca-102">@no__t – element > 0add pro connectionManagement (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="2deca-102">\<add> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="2deca-103">Přidá IP adresu nebo název DNS do seznamu správy připojení.</span><span class="sxs-lookup"><span data-stu-id="2deca-103">Adds an IP address or DNS name to the connection management list.</span></span>  
  
[<span data-ttu-id="2deca-104"> **@no__t – 2configuration >** </span><span class="sxs-lookup"><span data-stu-id="2deca-104">**\<configuration>**</span></span>](../configuration-element.md)  
<span data-ttu-id="2deca-105">&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2deca-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>  
<span data-ttu-id="2deca-106">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="2deca-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)</span></span>  
<span data-ttu-id="2deca-107">&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<add >**</span><span class="sxs-lookup"><span data-stu-id="2deca-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2deca-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2deca-108">Syntax</span></span>  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2deca-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2deca-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2deca-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2deca-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2deca-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2deca-111">Attributes</span></span>  
  
|<span data-ttu-id="2deca-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="2deca-112">**Attribute**</span></span>|<span data-ttu-id="2deca-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="2deca-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="2deca-114">Řetězec popisující IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="2deca-114">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="2deca-115">Maximální počet připojení povolených pro server.</span><span class="sxs-lookup"><span data-stu-id="2deca-115">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="2deca-116">Pokud není zadaný, použije se výchozí hodnota 2.</span><span class="sxs-lookup"><span data-stu-id="2deca-116">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2deca-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2deca-117">Child Elements</span></span>  
 <span data-ttu-id="2deca-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="2deca-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2deca-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2deca-119">Parent Elements</span></span>  
  
|<span data-ttu-id="2deca-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="2deca-120">**Element**</span></span>|<span data-ttu-id="2deca-121">**Popis**</span><span class="sxs-lookup"><span data-stu-id="2deca-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="2deca-122">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="2deca-122">connectionManagement</span></span>](connectionmanagement-element-network-settings.md)|<span data-ttu-id="2deca-123">Určuje maximální počet připojení k síťovému hostiteli.</span><span class="sxs-lookup"><span data-stu-id="2deca-123">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2deca-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2deca-124">Remarks</span></span>  
 <span data-ttu-id="2deca-125">Hodnota atributu `address` by měla být buď hvězdička, která označuje všechna připojení, nebo řetězec formuláře `<schema>://<idn_hostname>[:<port>]`.</span><span class="sxs-lookup"><span data-stu-id="2deca-125">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="2deca-126">Pokud identifikátor URI předaný do libovolného rozhraní API HTTP obsahuje Unicode, název se převede interně pomocí <xref:System.Uri.DnsSafeHost%2A>, což může vracet punicode řetězec (chování závisí na aktuální konfiguraci IDN).</span><span class="sxs-lookup"><span data-stu-id="2deca-126">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="2deca-127">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="2deca-127">Configuration Files</span></span>  
 <span data-ttu-id="2deca-128">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).</span><span class="sxs-lookup"><span data-stu-id="2deca-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2deca-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="2deca-129">Example</span></span>  
 <span data-ttu-id="2deca-130">V následujícím příkladu je nakonfiguruje aplikace tak, aby na všech ostatních serverech používala čtyři připojení k serveru `www.contoso.com` a dvě připojení.</span><span class="sxs-lookup"><span data-stu-id="2deca-130">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2deca-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2deca-131">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="2deca-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="2deca-132">Network Settings Schema</span></span>](index.md)

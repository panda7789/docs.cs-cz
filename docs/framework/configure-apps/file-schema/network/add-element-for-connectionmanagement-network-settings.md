---
title: <add> – Element pro connectionManagement (nastavení sítě)
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
ms.openlocfilehash: 3a046fd386536b29ea2dcad5660c65c08b7e4478
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59204247"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="54c94-102">\<Přidat > – Element pro connectionManagement (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="54c94-102">\<add> Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="54c94-103">Přidá do seznamu pro správu připojení IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="54c94-103">Adds an IP address or DNS name to the connection management list.</span></span>  
  
 <span data-ttu-id="54c94-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="54c94-104">\<configuration></span></span>  
<span data-ttu-id="54c94-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="54c94-105">\<system.net></span></span>  
<span data-ttu-id="54c94-106">\<connectionManagement></span><span class="sxs-lookup"><span data-stu-id="54c94-106">\<connectionManagement></span></span>  
<span data-ttu-id="54c94-107">\<add></span><span class="sxs-lookup"><span data-stu-id="54c94-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54c94-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="54c94-108">Syntax</span></span>  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54c94-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="54c94-109">Attributes and Elements</span></span>  
 <span data-ttu-id="54c94-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="54c94-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54c94-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="54c94-111">Attributes</span></span>  
  
|**<span data-ttu-id="54c94-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="54c94-112">Attribute</span></span>**|**<span data-ttu-id="54c94-113">Popis</span><span class="sxs-lookup"><span data-stu-id="54c94-113">Description</span></span>**|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="54c94-114">Řetězec, který popisuje IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="54c94-114">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="54c94-115">Maximální počet povolených připojení k serveru.</span><span class="sxs-lookup"><span data-stu-id="54c94-115">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="54c94-116">Pokud není zadán, výchozí hodnota je 2.</span><span class="sxs-lookup"><span data-stu-id="54c94-116">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54c94-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="54c94-117">Child Elements</span></span>  
 <span data-ttu-id="54c94-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="54c94-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54c94-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="54c94-119">Parent Elements</span></span>  
  
|**<span data-ttu-id="54c94-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="54c94-120">Element</span></span>**|**<span data-ttu-id="54c94-121">Popis</span><span class="sxs-lookup"><span data-stu-id="54c94-121">Description</span></span>**|  
|-----------------|---------------------|  
|[<span data-ttu-id="54c94-122">connectionManagement</span><span class="sxs-lookup"><span data-stu-id="54c94-122">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="54c94-123">Určuje maximální počet připojení k síti hostitele.</span><span class="sxs-lookup"><span data-stu-id="54c94-123">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54c94-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="54c94-124">Remarks</span></span>  
 <span data-ttu-id="54c94-125">Hodnota `address` atribut by měl mít hvězdičky označující všechna připojení nebo řetězec ve formě `<schema>://<idn_hostname>[:<port>]`.</span><span class="sxs-lookup"><span data-stu-id="54c94-125">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="54c94-126">Pokud identifikátor URI předána žádná rozhraní HTTP API obsahuje kódování Unicode, název se převedou interně pomocí <xref:System.Uri.DnsSafeHost%2A> které může vrátit řetězec punicode (chování závisí na aktuální konfiguraci IDN).</span><span class="sxs-lookup"><span data-stu-id="54c94-126">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="54c94-127">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="54c94-127">Configuration Files</span></span>  
 <span data-ttu-id="54c94-128">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="54c94-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="54c94-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="54c94-129">Example</span></span>  
 <span data-ttu-id="54c94-130">Následující příklad nastaví použití čtyř připojení k serveru aplikace `www.contoso.com` a dvě spojení na všechny ostatní servery.</span><span class="sxs-lookup"><span data-stu-id="54c94-130">The following example configures an application to use four connections to the server `www.contoso.com` and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="54c94-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="54c94-131">See also</span></span>

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [<span data-ttu-id="54c94-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="54c94-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

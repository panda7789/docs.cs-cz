---
title: "&lt;Přidat&gt; Element pro connectionManagement – (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
caps.latest.revision: "14"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 654ada55d30ad95937fa05475ebcbf23ca86652d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="5ca1b-102">&lt;Přidat&gt; Element pro connectionManagement – (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="5ca1b-102">&lt;add&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="5ca1b-103">Přidá do seznamu pro správu připojení IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="5ca1b-103">Adds an IP address or DNS name to the connection management list.</span></span>  
  
 <span data-ttu-id="5ca1b-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="5ca1b-104">\<configuration></span></span>  
<span data-ttu-id="5ca1b-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="5ca1b-105">\<system.net></span></span>  
<span data-ttu-id="5ca1b-106">\<connectionManagement – ></span><span class="sxs-lookup"><span data-stu-id="5ca1b-106">\<connectionManagement></span></span>  
<span data-ttu-id="5ca1b-107">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="5ca1b-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5ca1b-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5ca1b-108">Syntax</span></span>  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5ca1b-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5ca1b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="5ca1b-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5ca1b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5ca1b-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="5ca1b-111">Attributes</span></span>  
  
|<span data-ttu-id="5ca1b-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="5ca1b-112">**Attribute**</span></span>|<span data-ttu-id="5ca1b-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="5ca1b-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="5ca1b-114">Řetězec popisující IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="5ca1b-114">A string describing an IP address or DNS name.</span></span>|  
|`maxconnection`|<span data-ttu-id="5ca1b-115">Maximální počet připojení povolených pro server.</span><span class="sxs-lookup"><span data-stu-id="5ca1b-115">The maximum number of connections allowed to a server.</span></span> <span data-ttu-id="5ca1b-116">Pokud nejsou zadané, výchozí hodnota je 2.</span><span class="sxs-lookup"><span data-stu-id="5ca1b-116">If not supplied, the default is 2.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5ca1b-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5ca1b-117">Child Elements</span></span>  
 <span data-ttu-id="5ca1b-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="5ca1b-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5ca1b-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5ca1b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="5ca1b-120">**Element**</span><span class="sxs-lookup"><span data-stu-id="5ca1b-120">**Element**</span></span>|<span data-ttu-id="5ca1b-121">**Popis**</span><span class="sxs-lookup"><span data-stu-id="5ca1b-121">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="5ca1b-122">connectionManagement –</span><span class="sxs-lookup"><span data-stu-id="5ca1b-122">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="5ca1b-123">Určuje maximální počet připojení k síti hostitele.</span><span class="sxs-lookup"><span data-stu-id="5ca1b-123">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5ca1b-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5ca1b-124">Remarks</span></span>  
 <span data-ttu-id="5ca1b-125">Hodnota `address` atribut by měl mít buď hvězdičku označíte, všechna připojení, nebo řetězec ve formátu `<schema>://<idn_hostname>[:<port>]`.</span><span class="sxs-lookup"><span data-stu-id="5ca1b-125">The value of the `address` attribute should be either an asterisk to indicate all connections, or a string of the form `<schema>://<idn_hostname>[:<port>]`.</span></span>  
  
 <span data-ttu-id="5ca1b-126">Pokud identifikátor URI předaný všechny rozhraní API HTTP obsahuje znakové sady Unicode, název bude převeden interně pomocí <xref:System.Uri.DnsSafeHost%2A> kterého může vrátit řetězec punicode (chování závisí na aktuální konfiguraci IDN).</span><span class="sxs-lookup"><span data-stu-id="5ca1b-126">If the URI passed to any HTTP APIs contains Unicode, the name will be converted internally using <xref:System.Uri.DnsSafeHost%2A> which might return a punicode string (behavior dependent on the current IDN configuration).</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="5ca1b-127">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="5ca1b-127">Configuration Files</span></span>  
 <span data-ttu-id="5ca1b-128">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="5ca1b-128">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5ca1b-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="5ca1b-129">Example</span></span>  
 <span data-ttu-id="5ca1b-130">Následující příklad konfiguruje aplikaci použít čtyři připojení k serveru www.contoso.com a dvě připojení na jiné servery.</span><span class="sxs-lookup"><span data-stu-id="5ca1b-130">The following example configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5ca1b-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="5ca1b-131">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="5ca1b-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="5ca1b-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

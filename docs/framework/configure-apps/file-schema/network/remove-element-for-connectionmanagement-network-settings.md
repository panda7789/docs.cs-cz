---
title: "&lt;Odebrat&gt; Element pro connectionManagement – (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- connectionManagement, remove element
- <remove> element, connectionManagement
- <connectionManagement>, remove element
- remove element, connectionManagement
ms.assetid: 94b81775-5a22-4975-8c47-8620c40c3f35
caps.latest.revision: "12"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 947150ce0ff9a5ec5fa87fef8c2e24f3ebf6b4cb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltremovegt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="e0ef2-102">&lt;Odebrat&gt; Element pro connectionManagement – (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="e0ef2-102">&lt;remove&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="e0ef2-103">Odebere ze seznamu pro správu připojení IP adresy nebo názvu DNS.</span><span class="sxs-lookup"><span data-stu-id="e0ef2-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
 <span data-ttu-id="e0ef2-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="e0ef2-104">\<configuration></span></span>  
<span data-ttu-id="e0ef2-105">\<System.NET ></span><span class="sxs-lookup"><span data-stu-id="e0ef2-105">\<system.net></span></span>  
<span data-ttu-id="e0ef2-106">\<connectionManagement – ></span><span class="sxs-lookup"><span data-stu-id="e0ef2-106">\<connectionManagement></span></span>  
<span data-ttu-id="e0ef2-107">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="e0ef2-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0ef2-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0ef2-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0ef2-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e0ef2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e0ef2-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e0ef2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0ef2-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e0ef2-111">Attributes</span></span>  
  
|<span data-ttu-id="e0ef2-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="e0ef2-112">**Attribute**</span></span>|<span data-ttu-id="e0ef2-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e0ef2-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="e0ef2-114">IP adresa nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="e0ef2-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0ef2-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e0ef2-115">Child Elements</span></span>  
 <span data-ttu-id="e0ef2-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="e0ef2-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0ef2-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e0ef2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="e0ef2-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="e0ef2-118">**Element**</span></span>|<span data-ttu-id="e0ef2-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="e0ef2-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="e0ef2-120">connectionManagement –</span><span class="sxs-lookup"><span data-stu-id="e0ef2-120">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="e0ef2-121">Určuje maximální počet připojení k síti hostitele.</span><span class="sxs-lookup"><span data-stu-id="e0ef2-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0ef2-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0ef2-122">Remarks</span></span>  
 <span data-ttu-id="e0ef2-123">`remove` Element odebere položku seznamu správu připojení pro zadaný server.</span><span class="sxs-lookup"><span data-stu-id="e0ef2-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="e0ef2-124">Hodnota `address` atribut by měl mít platnou IP adresu nebo název hostitele.</span><span class="sxs-lookup"><span data-stu-id="e0ef2-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="e0ef2-125">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="e0ef2-125">Configuration Files</span></span>  
 <span data-ttu-id="e0ef2-126">Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="e0ef2-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0ef2-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0ef2-127">Example</span></span>  
 <span data-ttu-id="e0ef2-128">V následujícím příkladu odebere všechny položky připojení správy seznamu pro www.adventure-works.com serveru a poté konfiguruje aplikaci použít čtyři připojení k serveru www.contoso.com a dvě připojení na jiné servery.</span><span class="sxs-lookup"><span data-stu-id="e0ef2-128">The following example removes any connection management list entries for the server www.adventure-works.com and then configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e0ef2-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="e0ef2-129">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="e0ef2-130">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="e0ef2-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

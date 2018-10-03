---
title: '&lt;Odebrat&gt; – Element pro connectionManagement (nastavení sítě)'
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
author: mcleblanc
ms.author: markl
ms.openlocfilehash: d249cc412a1638e62b57b4976adc23fdf8f36e80
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/02/2018
ms.locfileid: "48024581"
---
# <a name="ltremovegt-element-for-connectionmanagement-network-settings"></a><span data-ttu-id="6d31e-102">&lt;Odebrat&gt; – Element pro connectionManagement (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="6d31e-102">&lt;remove&gt; Element for connectionManagement (Network Settings)</span></span>
<span data-ttu-id="6d31e-103">Odebere ze seznamu pro správu připojení IP adresu nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="6d31e-103">Removes an IP address or DNS name from the connection management list.</span></span>  
  
 <span data-ttu-id="6d31e-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="6d31e-104">\<configuration></span></span>  
<span data-ttu-id="6d31e-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="6d31e-105">\<system.net></span></span>  
<span data-ttu-id="6d31e-106">\<connectionManagement – ></span><span class="sxs-lookup"><span data-stu-id="6d31e-106">\<connectionManagement></span></span>  
<span data-ttu-id="6d31e-107">\<Odebrat ></span><span class="sxs-lookup"><span data-stu-id="6d31e-107">\<remove></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d31e-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6d31e-108">Syntax</span></span>  
  
```xml  
<remove   
  address="server name or IP address"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6d31e-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6d31e-109">Attributes and Elements</span></span>  
 <span data-ttu-id="6d31e-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6d31e-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6d31e-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="6d31e-111">Attributes</span></span>  
  
|<span data-ttu-id="6d31e-112">**Atribut**</span><span class="sxs-lookup"><span data-stu-id="6d31e-112">**Attribute**</span></span>|<span data-ttu-id="6d31e-113">**Popis**</span><span class="sxs-lookup"><span data-stu-id="6d31e-113">**Description**</span></span>|  
|-------------------|---------------------|  
|`address`|<span data-ttu-id="6d31e-114">IP adresa nebo název DNS.</span><span class="sxs-lookup"><span data-stu-id="6d31e-114">An IP address or DNS name.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6d31e-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6d31e-115">Child Elements</span></span>  
 <span data-ttu-id="6d31e-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="6d31e-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6d31e-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6d31e-117">Parent Elements</span></span>  
  
|<span data-ttu-id="6d31e-118">**Element**</span><span class="sxs-lookup"><span data-stu-id="6d31e-118">**Element**</span></span>|<span data-ttu-id="6d31e-119">**Popis**</span><span class="sxs-lookup"><span data-stu-id="6d31e-119">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="6d31e-120">connectionManagement –</span><span class="sxs-lookup"><span data-stu-id="6d31e-120">connectionManagement</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|<span data-ttu-id="6d31e-121">Určuje maximální počet připojení k síti hostitele.</span><span class="sxs-lookup"><span data-stu-id="6d31e-121">Specifies the maximum number of connections to a network host.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6d31e-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6d31e-122">Remarks</span></span>  
 <span data-ttu-id="6d31e-123">`remove` Element odstraní položku seznamu správy připojení na určeném serveru.</span><span class="sxs-lookup"><span data-stu-id="6d31e-123">The `remove` element removes the connection management list entry for the specified server.</span></span>  
  
 <span data-ttu-id="6d31e-124">Hodnota `address` atribut by měl mít platnou IP adresu nebo název hostitele.</span><span class="sxs-lookup"><span data-stu-id="6d31e-124">The value of the `address` attribute should be a valid IP address or host name.</span></span>  
  
## <a name="configuration-files"></a><span data-ttu-id="6d31e-125">Konfigurační soubory</span><span class="sxs-lookup"><span data-stu-id="6d31e-125">Configuration Files</span></span>  
 <span data-ttu-id="6d31e-126">Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).</span><span class="sxs-lookup"><span data-stu-id="6d31e-126">This element can be used in the application configuration file or the machine configuration file (Machine.config).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d31e-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="6d31e-127">Example</span></span>  
 <span data-ttu-id="6d31e-128">Následující příklad odebere všechny položky seznamu správu připojení pro server www.adventure-works.com a pak nakonfiguruje aplikaci pro použití čtyř připojení k serveru www.contoso.com a dvě spojení na všechny ostatní servery.</span><span class="sxs-lookup"><span data-stu-id="6d31e-128">The following example removes any connection management list entries for the server www.adventure-works.com and then configures an application to use four connections to the server www.contoso.com and two connections to all other servers.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6d31e-129">Viz také</span><span class="sxs-lookup"><span data-stu-id="6d31e-129">See Also</span></span>  
 <xref:System.Net.ServicePoint>  
 <xref:System.Net.ServicePointManager>  
 [<span data-ttu-id="6d31e-130">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="6d31e-130">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

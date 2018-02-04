---
title: "&lt;SMTP&gt; – Element (nastavení sítě)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: f5b2a3b7eec17fbdd12181c29f610d2b2ad32bd4
ms.sourcegitcommit: cf22b29db780e532e1090c6e755aa52d28273fa6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/01/2018
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="1e166-102">&lt;SMTP&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="1e166-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="1e166-103">Nakonfiguruje formát doručení, metodu doručení a z adresy pro odesílání e-mailů.</span><span class="sxs-lookup"><span data-stu-id="1e166-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="1e166-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="1e166-104">\<configuration></span></span>  
<span data-ttu-id="1e166-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="1e166-105">\<system.net></span></span>  
<span data-ttu-id="1e166-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="1e166-106">\<mailSettings></span></span>  
<span data-ttu-id="1e166-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="1e166-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1e166-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1e166-108">Syntax</span></span>  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1e166-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1e166-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1e166-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1e166-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1e166-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="1e166-111">Attributes</span></span>  
  
|<span data-ttu-id="1e166-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="1e166-112">Attribute</span></span>|<span data-ttu-id="1e166-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1e166-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="1e166-114">Určuje formát doručení pro odchozí e-mailů.</span><span class="sxs-lookup"><span data-stu-id="1e166-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="1e166-115">Přípustné hodnoty jsou SevenBit a mezinárodní.</span><span class="sxs-lookup"><span data-stu-id="1e166-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="1e166-116">Určuje metodu doručení e-mailů.</span><span class="sxs-lookup"><span data-stu-id="1e166-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="1e166-117">Přípustné hodnoty jsou sítě, pickupDirectoryFromIis a specifiedpickupdirectory –.</span><span class="sxs-lookup"><span data-stu-id="1e166-117">Acceptable values are network, pickupDirectoryFromIis, and specifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="1e166-118">Určuje z adresy pro odchozí e-mailů.</span><span class="sxs-lookup"><span data-stu-id="1e166-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1e166-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1e166-119">Child Elements</span></span>  
  
|<span data-ttu-id="1e166-120">Atribut</span><span class="sxs-lookup"><span data-stu-id="1e166-120">Attribute</span></span>|<span data-ttu-id="1e166-121">Popis</span><span class="sxs-lookup"><span data-stu-id="1e166-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="1e166-122">Nakonfiguruje místní adresář pro přenos protokolu SMTP (Simple Mail) serveru.</span><span class="sxs-lookup"><span data-stu-id="1e166-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="1e166-123">Nakonfiguruje možnosti sítě pro externí server SMTP.</span><span class="sxs-lookup"><span data-stu-id="1e166-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1e166-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1e166-124">Parent Elements</span></span>  
  
|<span data-ttu-id="1e166-125">**Element**</span><span class="sxs-lookup"><span data-stu-id="1e166-125">**Element**</span></span>|<span data-ttu-id="1e166-126">**Popis**</span><span class="sxs-lookup"><span data-stu-id="1e166-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="1e166-127">\<mailSettings – > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="1e166-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="1e166-128">Nakonfiguruje možnosti odesílání e-mailu.</span><span class="sxs-lookup"><span data-stu-id="1e166-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1e166-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="1e166-129">Example</span></span>  
 <span data-ttu-id="1e166-130">Následující příklad určuje vhodné parametry SMTP pro odeslání e-mailu pomocí výchozích pověření sítě.</span><span class="sxs-lookup"><span data-stu-id="1e166-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1e166-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e166-131">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [<span data-ttu-id="1e166-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="1e166-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

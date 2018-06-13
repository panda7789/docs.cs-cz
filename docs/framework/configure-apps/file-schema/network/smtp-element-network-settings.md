---
title: '&lt;SMTP&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 56912e09d24fc83e93a91cc42b1d96dcc68210f2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32741890"
---
# <a name="ltsmtpgt-element-network-settings"></a><span data-ttu-id="21468-102">&lt;SMTP&gt; – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="21468-102">&lt;smtp&gt; Element (Network Settings)</span></span>
<span data-ttu-id="21468-103">Nakonfiguruje formát doručení, metodu doručení a z adresy pro odesílání e-mailů.</span><span class="sxs-lookup"><span data-stu-id="21468-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
 <span data-ttu-id="21468-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="21468-104">\<configuration></span></span>  
<span data-ttu-id="21468-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="21468-105">\<system.net></span></span>  
<span data-ttu-id="21468-106">\<mailSettings – ></span><span class="sxs-lookup"><span data-stu-id="21468-106">\<mailSettings></span></span>  
<span data-ttu-id="21468-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="21468-107">\<smtp></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="21468-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="21468-108">Syntax</span></span>  
  
```xml  
      <smtp  
        deliveryFormat="format"   
        deliveryMethod="method"   
        from="from address">
          <specifiedPickupDirectory> … </ specifiedPickupDirectory >  
          <network> … </network>  
      </smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="21468-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="21468-109">Attributes and Elements</span></span>  
 <span data-ttu-id="21468-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="21468-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="21468-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="21468-111">Attributes</span></span>  
  
|<span data-ttu-id="21468-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="21468-112">Attribute</span></span>|<span data-ttu-id="21468-113">Popis</span><span class="sxs-lookup"><span data-stu-id="21468-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="21468-114">Určuje formát doručení pro odchozí e-mailů.</span><span class="sxs-lookup"><span data-stu-id="21468-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="21468-115">Přípustné hodnoty jsou SevenBit a mezinárodní.</span><span class="sxs-lookup"><span data-stu-id="21468-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="21468-116">Určuje metodu doručení e-mailů.</span><span class="sxs-lookup"><span data-stu-id="21468-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="21468-117">Přípustné hodnoty jsou sítě, pickupDirectoryFromIis a specifiedpickupdirectory –.</span><span class="sxs-lookup"><span data-stu-id="21468-117">Acceptable values are network, pickupDirectoryFromIis, and specifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="21468-118">Určuje z adresy pro odchozí e-mailů.</span><span class="sxs-lookup"><span data-stu-id="21468-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="21468-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="21468-119">Child Elements</span></span>  
  
|<span data-ttu-id="21468-120">Atribut</span><span class="sxs-lookup"><span data-stu-id="21468-120">Attribute</span></span>|<span data-ttu-id="21468-121">Popis</span><span class="sxs-lookup"><span data-stu-id="21468-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="21468-122">Nakonfiguruje místní adresář pro přenos protokolu SMTP (Simple Mail) serveru.</span><span class="sxs-lookup"><span data-stu-id="21468-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="21468-123">Nakonfiguruje možnosti sítě pro externí server SMTP.</span><span class="sxs-lookup"><span data-stu-id="21468-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="21468-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="21468-124">Parent Elements</span></span>  
  
|<span data-ttu-id="21468-125">**Element**</span><span class="sxs-lookup"><span data-stu-id="21468-125">**Element**</span></span>|<span data-ttu-id="21468-126">**Popis**</span><span class="sxs-lookup"><span data-stu-id="21468-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="21468-127">\<mailSettings – > elementu (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="21468-127">\<mailSettings> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/mailsettings-element-network-settings.md)|<span data-ttu-id="21468-128">Nakonfiguruje možnosti odesílání e-mailu.</span><span class="sxs-lookup"><span data-stu-id="21468-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="21468-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="21468-129">Example</span></span>  
 <span data-ttu-id="21468-130">Následující příklad určuje vhodné parametry SMTP pro odeslání e-mailu pomocí výchozích pověření sítě.</span><span class="sxs-lookup"><span data-stu-id="21468-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="21468-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="21468-131">See Also</span></span>  
 <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>  
 <xref:System.Net.Mail.SmtpDeliveryFormat>  
 <xref:System.Net.Mail.SmtpDeliveryMethod>  
 [<span data-ttu-id="21468-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="21468-132">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)

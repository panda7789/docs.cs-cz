---
title: <smtp> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp
- http://schemas.microsoft.com/.NetConfiguration/v2.0#smtp
helpviewer_keywords:
- <smtp> element
- smtp element
ms.assetid: 220b0329-e384-4e0c-86b4-0945ad17efd9
ms.openlocfilehash: 625c3cb82a8659c742b540724e5cf31be65a705e
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089104"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="99a49-102">\<element > SMTP (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="99a49-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="99a49-103">Konfiguruje formát doručení, způsob doručení a adresu odesílatele pro odesílání e-mailů.</span><span class="sxs-lookup"><span data-stu-id="99a49-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
<span data-ttu-id="99a49-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="99a49-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="99a49-105">&nbsp;&nbsp;[ **\<System. net >** ](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="99a49-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="99a49-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<mailSettings >** ](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="99a49-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="99a49-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<smtp >**</span><span class="sxs-lookup"><span data-stu-id="99a49-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**</span></span>
  
## <a name="syntax"></a><span data-ttu-id="99a49-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="99a49-108">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="99a49-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="99a49-109">Attributes and Elements</span></span>  
 <span data-ttu-id="99a49-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="99a49-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="99a49-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="99a49-111">Attributes</span></span>  
  
|<span data-ttu-id="99a49-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="99a49-112">Attribute</span></span>|<span data-ttu-id="99a49-113">Popis</span><span class="sxs-lookup"><span data-stu-id="99a49-113">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="99a49-114">Určuje formát doručení odchozích e-mailů.</span><span class="sxs-lookup"><span data-stu-id="99a49-114">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="99a49-115">Přijatelné hodnoty jsou SevenBit a International.</span><span class="sxs-lookup"><span data-stu-id="99a49-115">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="99a49-116">Určuje způsob doručování e-mailů.</span><span class="sxs-lookup"><span data-stu-id="99a49-116">Specifies the delivery method for emails.</span></span> <span data-ttu-id="99a49-117">Přijatelné hodnoty jsou Network, PickupDirectoryFromIis a SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="99a49-117">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="99a49-118">Určuje adresu od v případě odchozích e-mailů.</span><span class="sxs-lookup"><span data-stu-id="99a49-118">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="99a49-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="99a49-119">Child Elements</span></span>  
  
|<span data-ttu-id="99a49-120">Atribut</span><span class="sxs-lookup"><span data-stu-id="99a49-120">Attribute</span></span>|<span data-ttu-id="99a49-121">Popis</span><span class="sxs-lookup"><span data-stu-id="99a49-121">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="99a49-122">Nakonfiguruje místní adresář pro server SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="99a49-122">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="99a49-123">Nakonfiguruje možnosti sítě pro externí server SMTP.</span><span class="sxs-lookup"><span data-stu-id="99a49-123">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="99a49-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="99a49-124">Parent Elements</span></span>  
  
|<span data-ttu-id="99a49-125">**Element**</span><span class="sxs-lookup"><span data-stu-id="99a49-125">**Element**</span></span>|<span data-ttu-id="99a49-126">**Popis**</span><span class="sxs-lookup"><span data-stu-id="99a49-126">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="99a49-127">\<element > mailSettings (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="99a49-127">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="99a49-128">Nakonfiguruje možnosti odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="99a49-128">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="99a49-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="99a49-129">Example</span></span>  
 <span data-ttu-id="99a49-130">Následující příklad určuje vhodné parametry protokolu SMTP pro odesílání e-mailů s použitím výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="99a49-130">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network" deliveryFormat="SevenBit"  from="ben@contoso.com">  
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
  
## <a name="see-also"></a><span data-ttu-id="99a49-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99a49-131">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="99a49-132">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="99a49-132">Network Settings Schema</span></span>](index.md)

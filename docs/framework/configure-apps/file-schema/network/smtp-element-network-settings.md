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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74089104"
---
# <a name="smtp-element-network-settings"></a><span data-ttu-id="8413b-102">\<smtp> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="8413b-102">\<smtp> Element (Network Settings)</span></span>
<span data-ttu-id="8413b-103">Konfiguruje formát doručení, způsob doručení a adresu odesílatele pro odesílání e-mailů.</span><span class="sxs-lookup"><span data-stu-id="8413b-103">Configures the delivery format, delivery method, and from address for sending emails.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<smtp>**
  
## <a name="syntax"></a><span data-ttu-id="8413b-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8413b-104">Syntax</span></span>  
  
```xml  
<smtp  
  deliveryFormat="format"  
  deliveryMethod="method"  
  from="from address">
    <specifiedPickupDirectory>...</specifiedPickupDirectory>  
    <network>...</network>  
</smtp>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8413b-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8413b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8413b-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8413b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8413b-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="8413b-107">Attributes</span></span>  
  
|<span data-ttu-id="8413b-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="8413b-108">Attribute</span></span>|<span data-ttu-id="8413b-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8413b-109">Description</span></span>|  
|---------------|-----------------|  
|`deliveryFormat`|<span data-ttu-id="8413b-110">Určuje formát doručení odchozích e-mailů.</span><span class="sxs-lookup"><span data-stu-id="8413b-110">Specifies the delivery format for outgoing emails.</span></span> <span data-ttu-id="8413b-111">Přijatelné hodnoty jsou SevenBit a International.</span><span class="sxs-lookup"><span data-stu-id="8413b-111">Acceptable values are SevenBit and International.</span></span>|  
|`deliveryMethod`|<span data-ttu-id="8413b-112">Určuje způsob doručování e-mailů.</span><span class="sxs-lookup"><span data-stu-id="8413b-112">Specifies the delivery method for emails.</span></span> <span data-ttu-id="8413b-113">Přijatelné hodnoty jsou Network, PickupDirectoryFromIis a SpecifiedPickupDirectory.</span><span class="sxs-lookup"><span data-stu-id="8413b-113">Acceptable values are Network, PickupDirectoryFromIis, and SpecifiedPickupDirectory.</span></span>|  
|`from`|<span data-ttu-id="8413b-114">Určuje adresu od v případě odchozích e-mailů.</span><span class="sxs-lookup"><span data-stu-id="8413b-114">Specifies the from address for outgoing emails.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8413b-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8413b-115">Child Elements</span></span>  
  
|<span data-ttu-id="8413b-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="8413b-116">Attribute</span></span>|<span data-ttu-id="8413b-117">Popis</span><span class="sxs-lookup"><span data-stu-id="8413b-117">Description</span></span>|  
|---------------|-----------------|  
|`specifiedPickupDirectory`|<span data-ttu-id="8413b-118">Nakonfiguruje místní adresář pro server SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="8413b-118">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>|  
|`network`|<span data-ttu-id="8413b-119">Nakonfiguruje možnosti sítě pro externí server SMTP.</span><span class="sxs-lookup"><span data-stu-id="8413b-119">Configures the network options for an external SMTP server.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8413b-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8413b-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8413b-121">**Objekt**</span><span class="sxs-lookup"><span data-stu-id="8413b-121">**Element**</span></span>|<span data-ttu-id="8413b-122">**Popis**</span><span class="sxs-lookup"><span data-stu-id="8413b-122">**Description**</span></span>|  
|-----------------|---------------------|  
|[<span data-ttu-id="8413b-123">\<mailSettings>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="8413b-123">\<mailSettings> Element (Network Settings)</span></span>](mailsettings-element-network-settings.md)|<span data-ttu-id="8413b-124">Nakonfiguruje možnosti odesílání pošty.</span><span class="sxs-lookup"><span data-stu-id="8413b-124">Configures mail sending options.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8413b-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="8413b-125">Example</span></span>  
 <span data-ttu-id="8413b-126">Následující příklad určuje vhodné parametry protokolu SMTP pro odesílání e-mailů s použitím výchozích síťových přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="8413b-126">The following example specifies the appropriate SMTP parameters to send email using the default network credentials.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8413b-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="8413b-127">See also</span></span>

- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Mail.SmtpDeliveryFormat>
- <xref:System.Net.Mail.SmtpDeliveryMethod>
- [<span data-ttu-id="8413b-128">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="8413b-128">Network Settings Schema</span></span>](index.md)

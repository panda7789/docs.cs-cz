---
title: <specifiedPickupDirectory> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: 4b0cbaf9a7bfe2a9b1610811f4201253d219a6b2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154605"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="f35aa-102">\<specifiedPickupDirectory> Element (Nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="f35aa-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="f35aa-103">Konfiguruje místní adresář serveru SMTP (SMTP) protokolu SMTP (SMTP).</span><span class="sxs-lookup"><span data-stu-id="f35aa-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
<span data-ttu-id="f35aa-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f35aa-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f35aa-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f35aa-105">&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)</span></span>\
<span data-ttu-id="f35aa-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailNastavení>**](mailsettings-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f35aa-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)</span></span>\
<span data-ttu-id="f35aa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span><span class="sxs-lookup"><span data-stu-id="f35aa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)</span></span>\
<span data-ttu-id="f35aa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifikovaný>služby PickupDirectory**</span><span class="sxs-lookup"><span data-stu-id="f35aa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f35aa-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f35aa-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f35aa-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f35aa-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f35aa-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f35aa-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f35aa-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f35aa-112">Attributes</span></span>  
  
|<span data-ttu-id="f35aa-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f35aa-113">Attribute</span></span>|<span data-ttu-id="f35aa-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f35aa-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="f35aa-115">Adresář, do kterého aplikace ukládají e-maily pro pozdější zpracování serverem SMTP.</span><span class="sxs-lookup"><span data-stu-id="f35aa-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f35aa-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f35aa-116">Child Elements</span></span>  
 <span data-ttu-id="f35aa-117">Žádné.</span><span class="sxs-lookup"><span data-stu-id="f35aa-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f35aa-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f35aa-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f35aa-119">Element</span><span class="sxs-lookup"><span data-stu-id="f35aa-119">Element</span></span>|<span data-ttu-id="f35aa-120">Popis</span><span class="sxs-lookup"><span data-stu-id="f35aa-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f35aa-121">\<smtp> Element (Nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="f35aa-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="f35aa-122">Konfiguruje možnosti odesílání pošty protokolu SMTP (SMTP) protokolu SMTP.</span><span class="sxs-lookup"><span data-stu-id="f35aa-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f35aa-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f35aa-123">Remarks</span></span>  
 <span data-ttu-id="f35aa-124">Atribut `specifiedPickupDirectory` nastaví adresář, do kterého aplikace ukládají poštovní zprávy, které mají být zpracovány serverem SMTP.</span><span class="sxs-lookup"><span data-stu-id="f35aa-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f35aa-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="f35aa-125">Example</span></span>  
 <span data-ttu-id="f35aa-126">Následující příklad určuje c:\maildrop jako adresář vyzvednutí pošty.</span><span class="sxs-lookup"><span data-stu-id="f35aa-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="SpecifiedPickupDirectory">  
        <specifiedPickupDirectory  
          pickupDirectoryLocation="c:\maildrop"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="f35aa-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="f35aa-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="f35aa-128">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="f35aa-128">Network Settings Schema</span></span>](index.md)

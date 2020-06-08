---
title: <specifiedPickupDirectory> – element (nastavení sítě)
description: <specifiedPickupDirectory>Prvek nastavení sítě konfiguruje místní adresář pro možnosti serveru SMTP v .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: f0c4c1845e9542d0f3b836ff03f16bdf2979ebd8
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504495"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="f9f44-103">\<specifiedPickupDirectory> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="f9f44-103">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="f9f44-104">Nakonfiguruje místní adresář pro server SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="f9f44-104">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**  
  
## <a name="syntax"></a><span data-ttu-id="f9f44-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9f44-105">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9f44-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f9f44-106">Attributes and Elements</span></span>  
 <span data-ttu-id="f9f44-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f9f44-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9f44-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="f9f44-108">Attributes</span></span>  
  
|<span data-ttu-id="f9f44-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="f9f44-109">Attribute</span></span>|<span data-ttu-id="f9f44-110">Popis</span><span class="sxs-lookup"><span data-stu-id="f9f44-110">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="f9f44-111">Adresář, ve kterém aplikace ukládají e-mail pro pozdější zpracování serverem SMTP.</span><span class="sxs-lookup"><span data-stu-id="f9f44-111">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9f44-112">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f9f44-112">Child Elements</span></span>  
 <span data-ttu-id="f9f44-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="f9f44-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9f44-114">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f9f44-114">Parent Elements</span></span>  
  
|<span data-ttu-id="f9f44-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="f9f44-115">Element</span></span>|<span data-ttu-id="f9f44-116">Description</span><span class="sxs-lookup"><span data-stu-id="f9f44-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9f44-117">\<smtp>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="f9f44-117">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="f9f44-118">Konfiguruje možnosti odesílání pošty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="f9f44-118">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9f44-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f9f44-119">Remarks</span></span>  
 <span data-ttu-id="f9f44-120">`specifiedPickupDirectory`Atribut nastavuje adresář, ve kterém aplikace ukládají e-mailové zprávy, které server SMTP zpracuje.</span><span class="sxs-lookup"><span data-stu-id="f9f44-120">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f9f44-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="f9f44-121">Example</span></span>  
 <span data-ttu-id="f9f44-122">Následující příklad určuje c:\maildrop jako předávací adresář pošty.</span><span class="sxs-lookup"><span data-stu-id="f9f44-122">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f9f44-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9f44-123">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="f9f44-124">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="f9f44-124">Network Settings Schema</span></span>](index.md)

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
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154605"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="8917e-102">\<specifiedPickupDirectory> – element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="8917e-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="8917e-103">Nakonfiguruje místní adresář pro server SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="8917e-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<mailSettings>**](mailsettings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<smtp>**](smtp-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<specifiedPickupDirectory>**  
  
## <a name="syntax"></a><span data-ttu-id="8917e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8917e-104">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8917e-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8917e-105">Attributes and Elements</span></span>  
 <span data-ttu-id="8917e-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8917e-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8917e-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="8917e-107">Attributes</span></span>  
  
|<span data-ttu-id="8917e-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="8917e-108">Attribute</span></span>|<span data-ttu-id="8917e-109">Popis</span><span class="sxs-lookup"><span data-stu-id="8917e-109">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="8917e-110">Adresář, ve kterém aplikace ukládají e-mail pro pozdější zpracování serverem SMTP.</span><span class="sxs-lookup"><span data-stu-id="8917e-110">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8917e-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8917e-111">Child Elements</span></span>  
 <span data-ttu-id="8917e-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="8917e-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8917e-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8917e-113">Parent Elements</span></span>  
  
|<span data-ttu-id="8917e-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="8917e-114">Element</span></span>|<span data-ttu-id="8917e-115">Description</span><span class="sxs-lookup"><span data-stu-id="8917e-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8917e-116">\<smtp>– Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="8917e-116">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="8917e-117">Konfiguruje možnosti odesílání pošty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="8917e-117">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8917e-118">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8917e-118">Remarks</span></span>  
 <span data-ttu-id="8917e-119">`specifiedPickupDirectory`Atribut nastavuje adresář, ve kterém aplikace ukládají e-mailové zprávy, které server SMTP zpracuje.</span><span class="sxs-lookup"><span data-stu-id="8917e-119">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8917e-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="8917e-120">Example</span></span>  
 <span data-ttu-id="8917e-121">Následující příklad určuje c:\maildrop jako předávací adresář pošty.</span><span class="sxs-lookup"><span data-stu-id="8917e-121">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8917e-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="8917e-122">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="8917e-123">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="8917e-123">Network Settings Schema</span></span>](index.md)

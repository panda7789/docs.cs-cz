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
ms.openlocfilehash: b2e31dee4f5aff2bf6cedf5c4e9ca235695b0a53
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659095"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="2ee69-102">\<specifiedPickupDirectory – element > (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="2ee69-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="2ee69-103">Nakonfiguruje místní adresář pro server SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="2ee69-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="2ee69-104">\<> Konfigurace</span><span class="sxs-lookup"><span data-stu-id="2ee69-104">\<configuration></span></span>  
<span data-ttu-id="2ee69-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="2ee69-105">\<system.net></span></span>  
<span data-ttu-id="2ee69-106">\<mailSettings ></span><span class="sxs-lookup"><span data-stu-id="2ee69-106">\<mailSettings></span></span>  
<span data-ttu-id="2ee69-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="2ee69-107">\<smtp></span></span>  
<span data-ttu-id="2ee69-108">\<specifiedPickupDirectory></span><span class="sxs-lookup"><span data-stu-id="2ee69-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ee69-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2ee69-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2ee69-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2ee69-110">Attributes and Elements</span></span>  
 <span data-ttu-id="2ee69-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2ee69-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2ee69-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="2ee69-112">Attributes</span></span>  
  
|<span data-ttu-id="2ee69-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="2ee69-113">Attribute</span></span>|<span data-ttu-id="2ee69-114">Popis</span><span class="sxs-lookup"><span data-stu-id="2ee69-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="2ee69-115">Adresář, ve kterém aplikace ukládají e-mail pro pozdější zpracování serverem SMTP.</span><span class="sxs-lookup"><span data-stu-id="2ee69-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2ee69-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2ee69-116">Child Elements</span></span>  
 <span data-ttu-id="2ee69-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="2ee69-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2ee69-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2ee69-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2ee69-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="2ee69-119">Element</span></span>|<span data-ttu-id="2ee69-120">Popis</span><span class="sxs-lookup"><span data-stu-id="2ee69-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2ee69-121">\<> elementu SMTP (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="2ee69-121">\<smtp> Element (Network Settings)</span></span>](smtp-element-network-settings.md)|<span data-ttu-id="2ee69-122">Konfiguruje možnosti odesílání pošty SMTP (Simple Mail Transport Protocol).</span><span class="sxs-lookup"><span data-stu-id="2ee69-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ee69-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2ee69-123">Remarks</span></span>  
 <span data-ttu-id="2ee69-124">`specifiedPickupDirectory` Atribut nastavuje adresář, ve kterém aplikace ukládají e-mailové zprávy, které server SMTP zpracuje.</span><span class="sxs-lookup"><span data-stu-id="2ee69-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2ee69-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="2ee69-125">Example</span></span>  
 <span data-ttu-id="2ee69-126">Následující příklad určuje c:\maildrop jako předávací adresář pošty.</span><span class="sxs-lookup"><span data-stu-id="2ee69-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2ee69-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2ee69-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="2ee69-128">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="2ee69-128">Network Settings Schema</span></span>](index.md)

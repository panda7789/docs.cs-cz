---
title: <specifiedPickupDirectory> – Element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#specifiedPickupDirectory
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings/smtp/specifiedPickupDirectory
helpviewer_keywords:
- specifiedPickupDirectory element
- <specifiedPickupDirectory> element
ms.assetid: 0121f49d-bff2-4bc6-af06-f1628dcd61f1
ms.openlocfilehash: a459fee557285935c383dcfaf512c8a8a9aea570
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59099271"
---
# <a name="specifiedpickupdirectory-element-network-settings"></a><span data-ttu-id="93cc8-102">\<specifiedpickupdirectory – > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="93cc8-102">\<specifiedPickupDirectory> Element (Network Settings)</span></span>
<span data-ttu-id="93cc8-103">Konfiguruje místní adresář pro server Simple Mail Transport Protocol (SMTP).</span><span class="sxs-lookup"><span data-stu-id="93cc8-103">Configures the local directory for a Simple Mail Transport Protocol (SMTP) server.</span></span>  
  
 <span data-ttu-id="93cc8-104">\<Konfigurace ></span><span class="sxs-lookup"><span data-stu-id="93cc8-104">\<configuration></span></span>  
<span data-ttu-id="93cc8-105">\<system.net></span><span class="sxs-lookup"><span data-stu-id="93cc8-105">\<system.net></span></span>  
<span data-ttu-id="93cc8-106">\<mailSettings></span><span class="sxs-lookup"><span data-stu-id="93cc8-106">\<mailSettings></span></span>  
<span data-ttu-id="93cc8-107">\<smtp></span><span class="sxs-lookup"><span data-stu-id="93cc8-107">\<smtp></span></span>  
<span data-ttu-id="93cc8-108">\<specifiedPickupDirectory></span><span class="sxs-lookup"><span data-stu-id="93cc8-108">\<specifiedPickupDirectory></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93cc8-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="93cc8-109">Syntax</span></span>  
  
```xml  
<specifiedPickupDirectory  
  pickupDirectoryLocation="directory"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="93cc8-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="93cc8-110">Attributes and Elements</span></span>  
 <span data-ttu-id="93cc8-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="93cc8-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="93cc8-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="93cc8-112">Attributes</span></span>  
  
|<span data-ttu-id="93cc8-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="93cc8-113">Attribute</span></span>|<span data-ttu-id="93cc8-114">Popis</span><span class="sxs-lookup"><span data-stu-id="93cc8-114">Description</span></span>|  
|---------------|-----------------|  
|`pickupDirectoryLocation`|<span data-ttu-id="93cc8-115">Adresář, kde aplikace ukládat e-mailu pro pozdější zpracování serverem SMTP.</span><span class="sxs-lookup"><span data-stu-id="93cc8-115">The directory where applications save email for later processing by the SMTP server.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="93cc8-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="93cc8-116">Child Elements</span></span>  
 <span data-ttu-id="93cc8-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="93cc8-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="93cc8-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="93cc8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="93cc8-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="93cc8-119">Element</span></span>|<span data-ttu-id="93cc8-120">Popis</span><span class="sxs-lookup"><span data-stu-id="93cc8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="93cc8-121">\<SMTP > – Element (nastavení sítě)</span><span class="sxs-lookup"><span data-stu-id="93cc8-121">\<smtp> Element (Network Settings)</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/smtp-element-network-settings.md)|<span data-ttu-id="93cc8-122">Konfiguruje možnosti pro odesílání pošty Simple Mail Transport Protocol (SMTP).</span><span class="sxs-lookup"><span data-stu-id="93cc8-122">Configures Simple Mail Transport Protocol (SMTP) mail sending options.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="93cc8-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="93cc8-123">Remarks</span></span>  
 <span data-ttu-id="93cc8-124">`specifiedPickupDirectory` Atribut nastaví adresář, kde aplikace ukládat e-mailové zprávy na zpracování serverem SMTP.</span><span class="sxs-lookup"><span data-stu-id="93cc8-124">The `specifiedPickupDirectory` attribute sets the directory where applications save mail messages to be processed by the SMTP server.</span></span>  
  
## <a name="example"></a><span data-ttu-id="93cc8-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="93cc8-125">Example</span></span>  
 <span data-ttu-id="93cc8-126">Následující příklad určuje c:\maildrop jako předávací adresář pošty.</span><span class="sxs-lookup"><span data-stu-id="93cc8-126">The following example specifies c:\maildrop as the mail pickup directory.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="93cc8-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="93cc8-127">See also</span></span>

- <xref:System.Net.Mail.SmtpClient?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSection?displayProperty=nameWithType>
- <xref:System.Net.Configuration.SmtpSpecifiedPickupDirectoryElement?displayProperty=nameWithType>
- [<span data-ttu-id="93cc8-128">Schéma nastavení sítě</span><span class="sxs-lookup"><span data-stu-id="93cc8-128">Network Settings Schema</span></span>](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
